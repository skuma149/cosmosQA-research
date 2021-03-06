Status:
=======

- random baseline model provided by Allen AI setup, ran and tested

- wilburOne's baseline model setup in progress

- research paper reading in progress

___

Individual Efforts:
=======

- Kunal : Trying to run cosmosqa_wilburOne on asu agave. Current status is that the cluster is not picking up my job. 

- Jay : Was able to run the cosmosqa_wilburOne on my local CPU machine (without GPUs), but since the training + evaluation with huge datasize shall take time, trying to host the process on either Google Colab/Cloud Shell - but facing issues with installing Nvidia/Apex and few other version conflicts. 
Also, trying to read the [https://arxiv.org/pdf/1904.01172.pdf] paper in order to come up with model tweaks for error analysis.

- Aditya :
1. random baseline model provided by Allen AI setup, ran and tested
2. Tried running cosmosqa_wilburOne on Windows + GPU setup, but couldn't proceed further since 'apex' library by NVIDIA has limited support for CUDA in Windows.
3. Tried running cosmosqa_wilburOne on Windows Subsystem for Linux (WSL), couldn't proceed further since WSL doesn't have GPU access
4. Currently debugging running cosmosqa_wilburOne on [Google Colab](https://colab.research.google.com/drive/1sQ61kjP3AB1fxOCj_vJfIXnHn_X1CF9D).

- Vasishta : Evaluating the use of Amazon Web Service GPU instances K80 P2.xlarge to run cosmosqa_wilburOne for the project along with Aditya. Trying to understand the project in hand better.
___

Guide to setup cosmos conda environment
---------------------------------------

Installing and creating conda environment:

- Get the installer from here: https://docs.conda.io/en/latest/miniconda.html, install conda (make sure it is available in $path)

- Redirect to github project base directory in command line

- Execute: `conda env create -f conda-env.yml` # this will install required project dependencies

- Activate environment: `conda activate cosmos` # this will activate conda environment


Updating conda environment:

- In order to update depdendencies, add that dependency in conda-env.yml file and run `conda env update -f conda-env.yml`

Deleting conda environment:

- `conda deactivate`

- `conda env remove -n cosmos`

___

Running cosmosqa_baseline:
--------------------------
This random baseline is provided by [Allen AI](https://leaderboard.allenai.org/cosmosqa/submissions/public) for demonstrating input and output of data. ([GitHub](https://github.com/allenai/mosaic-leaderboard/tree/master/cosmosqa))

Make sure you have activated cosmos conda environment

Run random model:
`python ./cosmosqa_baseline/baselines/random-baseline/random_baseline.py --input-file ./official_data/train.jsonl --output-file ./results/random_predictions.lst`

Evaluate random model:
`python ./cosmosqa_baseline/evaluator/eval.py --labels_file ./official_data/train-labels.lst --preds_file ./results/random_predictions.lst --metrics_output_file ./results/random_metrics.json`


