# RingClassifier

![img](https://cdn.glitch.global/e5a0073c-51a7-49c3-9e59-c94e5732abbf/schema%20graph.jpeg?v=1705119210206)

## File Structure
```
RingClassifier
│   README.md
│   clustered_values.csv   
│   stage1_visualization.html
|
└─── code
│   │   stage1.ipynb
│   │   stage2.ipynb
│   
└─── width0.5_original
|
└─── width0.5_cleaned
|
└─── clustered_imgs
│   │   cluster_1
│   │   cluster_2
│   │   cluster_3
│   │   cluster_4
   
```

- `width0.5_original` contains 91 images that are width 0.5. They are original screenshots from the heated coils recordings.
- `width0.5_cleaned` includes 59 images that are cleaned from `width0.5_original`. The images where the rings are blended with the background are dropped. 
- `code` contains two python code notebooks for RingClassifier, `stage1.ipynb` and `stage2.ipynb`. In `stage1`, the images are resized to (224, 224) and transformed to grayscale. The pretrained model, ResNetV2, is applied to extract image features. These extracted features are further clustered by K-Means, which assigns a cluster number to each of the images. In `stage2`, a KNeighbors Classifier is trained using the parameter values (curvature, torsion, and cut degree) and the cluster numbers obtained from stage 1. With this, at inference time, the classifier predicts which cluster the unseen shape most likely belongs to, given its parameter values.
- `clustered_values.csv` contains five columns: image id, curvature, torsion, degree, and cluster number obtained from stage 1. It is the input data file for stage 2.
- `stage1_visualization.html` is an interactive 3-D plot of `clustered_values.csv`
- `clustered_imgs` includes 4 subfolders, each containing the images grouped into that cluster. 
