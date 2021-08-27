# qstp-2021-deep-learning

## Layout

This repository was created towards the fulfillment of the Introduction to Deep Learning Quark Summer Technical Project 2021. My project of choice was in the computer vision domain, where I trained image processing models on the STL-10 dataset using TensorFlow and Keras. I implemented transfer learning by attaching the convolution base of the VGG16 model to a custom data augmentation preprocessor and a classifier head. The model was constructed in two ways:

1. The "tensorflow-vgg16-frozen" files contain an implementation wherein the weights of the VGG16 model are frozen and only the classifier head's weights are fine-tuned during training. 
2. The "tensorflow-vgg16-unfrozen" files contain an implementation wherein the convolutional base of VGG16 is unfrozen, such that the weights in the convolutional base are also fine-tuned during training along with the rest of the network.

## Results

Accuracies of 80.6375 % for the frozen model and 10.0000 % for the unfrozen model were obtained on the test set. Hence, the frozen model had a better categorization accuracy by a margin of 70.6375 %. This is down to the fact that unfreezing the convolutional base completely destroyed all the training that went into obtaining the weights for the VGG16 model. This erased the feature-extraction capabilities of the convolutional base which had been built up on the ImageNet dataset. These capabilities had to be rebuilt from scratch on the brand-new STL-10 dataset. Twenty epochs was not enough training time for the network to get close to the feature-extraction performance of the original VGG16 model. Hence, a large disparity in the accuracy scores of the two models was observed.
