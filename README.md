# Photo-Realistic Monocular Gaze Redirection Using Generative Adversarial Networks

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)


## Dependencies

 tensorflow == 1.7  
 numpy == 1.13.1  
 scipy == 0.19.1  

## Dataset

The dataset contains eye patch images parsed from [Columbia Gaze Dataset](http://www.cs.columbia.edu/~brian/projects/columbia_gaze.html). It can be downloaded via this [link](https://drive.google.com/file/d/1tE3QfFjxtRco4ruLZwYyUhjyYSp2QIJL/view?usp=sharing).

```Bash
tar -xvf dataset.tar
```

The dataset contains six subfolders, N30P/, N15P/, 0P/, P15P/, P30P/ and all/. Prefix 'N' means negative head pose, and 'P' means positive head pose. Folder all/ contains all eye patch images with different head poses.

## VGG-16 pretrained weights

```Bash
wget http://download.tensorflow.org/models/vgg_16_2016_08_28.tar.gz .
tar -xvf vgg_16_2016_08_28.tar.gz
```

## Train

```Bash
python main.py --mode train --data_path ./dataset/all/ --log_dir ./log/ --batch_size 32 --vgg_path ./vgg_16.ckpt
```

## Test

To test the model on frontal faces, run the following command.

```Bash
python main.py --mode eval --data_path ./dataset/0P/ --log_dir ./log/ --batch_size 21
```

Then, a folder named **eval** will be generated in folder **./log/**. Generated images, input images and target images will be stored in **eval/**.
