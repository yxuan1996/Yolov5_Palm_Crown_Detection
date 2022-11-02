# Yolov5_Palm_Crown_Detection
This Repository contains project files for the YoloV5 image detection model to detect the top or 'crown' of oil palm trees.

The YoloV5 documentation can be found in the official YoloV5 github repository: https://github.com/ultralytics/yolov5

## Training

The code for training the palm crown detection model is contained in the `Palm Crown Detection - YoloV5 Training` jupyter notebook. 

Training can be done on any GPU-enabled computer or Google Colab (Recommended). 

#### Dataset
The dataset consists of 400 aerial palm crown images, taken using a DJI Mavic Air 2 Drone. 

Prior to training, the images were split into train, test and validation datasets. 

The data configurations are specified in the `palm_data.yaml` file 

I would like to credit and give thanks to my colleagues `Muhamad Hanif Hazemi` and `Muhammad Yusuf Musa`, they are the superstars who flew the drone and did most of the data collection on the field. 

**Example Palm Crown Image from the Dataset**


#### Labelling and Annotations
YOLOv5 accepts annotations / labels in the following format:

```class x_center y_center width height```

- We can use [Roboflow](https://roboflow.com/) to label the images, or manually label the images using LabelImg. 
- Labels should be saved as a txt file, one file per image. 


#### Results

The trained models were successful in detecting palm crowns from image and video inputs. 

**Inference Results**

For object detection, mean average precision (mAP) is the primary metric that is used to measure model performance.

On the other hand, Intersection over Union (IOU) measures the amount of overlap between the detected object pixels and actual object pixels. We use IOU as a threshold to calculate precision. 

- mAP@0.5 refers to mean average precision at an IOU threshold above 0.5
- mAP@0.5:0.95 refers to the average mAP over different IOU thresholds between 0.5 to 0.95

For the trained models, the following metrics were obtained:
| Model        | mAP@0.5   | mAP@0.5:0.95 |
|--------------|-----------|--------------|
| YoloV5_Small | 0.97379   | 0.61941      |
| YoloV5_Nano  | 0.91846   | 0.57329      |

**Training Results for YoloV5_Small model**


**Training Results for YoloV5_Nano model**



## Deployment on Nvidia Jetson

After training, the models are saved in the project folder in Pytorch format (.pt)
We transfer and deploy the trained model into the Nvidia Jetson Platform for inference. 



## Communication



## Performance Benchmarks

These benchmarks were measured using 

In general, the inferencing speed of the models can be increased by:
- Using a smaller YoloV5 model with lesser weights (Small --> Nano)
- Using a smaller image size (640 --> 320)

However, the smaller models with smaller image sizes generated a lot of false positives 

- benchmark table 1
- benchmark chart small
- benchmark chart nano

## References

1. https://github.com/ultralytics/yolov5
2. https://roboflow.com/
3. https://jonathan-hui.medium.com/map-mean-average-precision-for-object-detection-45c121a31173
4. https://datascience.stackexchange.com/questions/16797/what-does-the-notation-map-5-95-mean

