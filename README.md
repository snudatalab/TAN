# Transfer Alignment Network for Blind Unsupervised Domain Adaptation

This package provides implementations of Transfer Alignment Network.
Transfer Alignment Network is a stack of autoencoder, transfer aligner
layers and mlp networks.

## Code structure
`./src/model`: python scripts for model definition

`./src/train`: python scripts for train and test models defined in `./src/model`

`./src/demo`: demo shell script for batch execution of training codes in `./src/train`

## Naming convention
**auto_encoder** (ae): Autoencoder

**mlp**: Multilayer Perceptron

**v1**: Multilayer Perceptron on top of Autoencoder

**transfer aligner** (aligner): Transfer Alignment Layer connecting source and
target Autoencoder

**v2**: Multilayer Perceptron on top of Transfer Alignment Layer and Autoencoder

## Usage
source ae_train -> source v1_train -> target ae_train -> target mn_train -> target v2_test

## Dependencies

* Numpy
* TensorFlow

## Data description
* Download multivariate data from https://archive.ics.uci.edu/ml/datasets/

## Output folder structure
* Output of the model training is stored in the directory specified in argument log_dir
* Output folder sturcture
	* `train.log`: log file having results
	* `test.log`: log file having results for every test step
	* `best.log`: log file having only the best result
	* `hyperparameter`: json file having hyperparameter configuration for the current step
	* `weight/`: folder having csv files of trained weights
* log file columns
	* columns in log files for autoencoder and aligner training are loss, test loss, test_diff, test_rel_diff
	* columns in log files for classifier training are loss, test loss, test_accuracy, auc_roc, auc_pr

## Demo
* There is a demo script `src/demo/script.sh`
    * Input: `data/{$data_name}/`
    * Output: `src/results/step1`, `src/results/step2`, `src/results/step3`, `src/results/step4`, `src/results/test`
        * log files for step1, 3, 4 are loss, test loss, test_diff, test_rel_diff
        * log files for step2 is loss, test loss, test_accuracy, auc_roc, auc_pr
        * log files for test is test loss, test_accuracy, auc_roc, auc_pr

## Reference
If you use this code, please cite the following paper.
```
@article{DBLP:journals/kais/XuK21,
  author    = {Huiwen Xu and
               U Kang},
  title     = {Transfer Alignment Network for Blind Unsupervised Domain Adaptation},
  journal   = {Knowl. Inf. Syst.},
  volume    = {63},
  number    = {11},
  pages     = {2861--2881},
  year      = {2021}
}
```
