# iCarl2.0
This is an on-going pytorch implementation of iCarl[1].

## Interface to run experiments

``` bash
usage: runExperiment.py [-h] [--batch-size N] [--lr LR]
                        [--schedule SCHEDULE [SCHEDULE ...]]
                        [--gammas GAMMAS [GAMMAS ...]] [--momentum M]
                        [--no-cuda] [--random-init] [--no-distill]
                        [--distill-only-exemplars] [--no-random]
                        [--no-herding] [--seeds SEEDS [SEEDS ...]]
                        [--log-interval N] [--model-type MODEL_TYPE]
                        [--name NAME] [--outputDir OUTPUTDIR] [--upsampling]
                        [--pp] [--distill-step] [--hs]
                        [--unstructured-size UNSTRUCTURED_SIZE]
                        [--alphas ALPHAS [ALPHAS ...]] [--decay DECAY]
                        [--alpha-increment ALPHA_INCREMENT] [--l1 L1]
                        [--step-size STEP_SIZE] [--T T]
                        [--memory-budgets MEMORY_BUDGETS [MEMORY_BUDGETS ...]]
                        [--epochs-class EPOCHS_CLASS] [--dataset DATASET]
                        [--lwf] [--no-nl] [--rand] [--adversarial]
```
## Dependencies 

1. Pytorch 0.3.0.post4
2. Python 3.6 
3. torchnet (https://github.com/pytorch/tnt) 
4. tqdm (pip install tqdm)
5. OpenCV 

Please see requirements.txt for a complete list. 

## Setting up enviroment 
The easiest way to install the required dependencies is to use conda package manager. 
1. Install Anaconda with Python 3
2. Install pytorch and torchnet 
3. Install tqdm (pip install progressbar2)
Done. 

## Branches
1. GAN driven incremental learning is being done in the branch gan.
2. iCaRL + Dynamic Threshold Moving is implemented in "Autoencoders" branch.

=======
## Results 
### Removing Bias by using higher Temperature (T=3)
![alt text](https://github.com/Khurramjaved96/incremental-learning/blob/autoencoders/images/2step.png) "Incremental Learning on CIFAR100 with T=3")

### Removing Bias by Dynamic Threshold Moving
![alt text](https://github.com/Khurramjaved96/incremental-learning/blob/autoencoders/images/thresholdmoving) "Dynamic Threshold Moving on MNIST")

### Confusion Matrix with and without Dynamic Threshold Moving
![alt text](https://github.com/Khurramjaved96/incremental-learning/blob/autoencoders/images/confusion) "Dynamic Threshold Moving Confusion Matrix")
### Experiment Meta-file Details
![alt text](https://github.com/Khurramjaved96/incremental-learning/blob/autoencoders/images/protocol) "Dynamic Threshold Moving Confusion Matrix")
Protocol used to store the state of an experiment. The green coded text is the git hash corresponding to the version of the repository used to run the experiment, the blue coded string is the arguments used for running the experiment, and the red coded string has the results of the experiment. By storing all three, we are able to easily reproduce the results and compare to existing results

## FAQs
### How do I implement more models? 
A. Add the model in model/ModelFactory and make sure the forward method of the model satisfy the API of model/resnet32.py
### How do I add a new dataset? 
A. Add the new dataset in DatasetFactory and specify the details in the dataHandler/dataset.py class. Make sure the dataset implements all the variables set by other datasets. 

## References
[1] https://arxiv.org/abs/1611.07725
