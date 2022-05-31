# Stereo-vision-based-Object-Detection-and-Distance-Estimation-Algorithm.
In this project we try to capture images from Intel RealSense D-435 stereo camera ,try to identify various objects in the image (like pedestrians & various types of vehicles)  and try to estimate the distance of these objects from the camera.

INTRODUCTION:

In present world object detection and distance estimation in Autonomous vehicles (AVs) play a 
pivotal role. In order to prevent the collision in autonomous vehicle there is a need for an 
intelligence that is to be given to autonomous vehicles so that vehicle can identify the objects 
ahead, classify them and estimate the distance of objects as well. In order to achieve this present 
system heavily rely on LIDAR, RADAR and cameras. Even though LIDAR sensors are widely used in 
present autonomous vehicles when compared to camera based system there are some disadvantage like 
higher cost and shorter perception range .In order to overcome these disadvantages of LIDAR, we 
propose an algorithm to calculate the distance of the detected object and implementing on the 
Nvidia ACX development kit with help of Intel Realsense D-435 stereo camera.



OBJECTIVES:

• Capturing the left and right IR(Infra red)images from Intel Realsense D-435 stereo camera.

• Capturing the RGB images from Intel Realsense D-435 stereo camera.

• Camera calibration and Rectification.

• Computation of Disparity map.

• Object detection and classification from the RGB images.

• Distance estimation of the classified objects.

METHODOLOGY:

In this methodology firstly we obtain the RGB,Left and Right IR (Infra red) images from Intel 
Realsense D-435 camera by pipelining the camera to our system. RGB image is used to detect the 
objects in the image and classify them. Right and Left IR(Infra red) images are used as stereo 
pairs to compute Disparity map.With the help of disparity map and object detected we calculate the 
distance of the detected object.This algorithm is implemented on Nvidia AGX development kit.

1.Stereo Rectification: 

Rectify the images for radial and tangential distortions when captured from stereo camera.

2.Disparity Mapping:

To obtain disparity map we use SGMB (Semi Global Block Matching) algorithm .It focuses on sub pixel 
matching and obtaining smooth textured images.

Algorithm follows 2 steps:

• Normalization of brightness and enhancement of images.

• Corresponding search along horizontal epipolar line using SAD window.

3.Object detection and classification:

We have used SSD (Single Shot Detection) algorithm which follows VGG-16 architecture.  It consists 
of alternative convolution and max pooling layers (deeper the layers more features will be 
extracted). Rectified images are passed through  convolution and pooling layer and we get 
probaility distribution for each class across softmax layer. Then we draw bounding boxes to objects 
classified.

4.Distance Estimation:

We know the values of focal length,Baseline and we calculated the disparity values,focal length in 
mm is converted to pixel values and then by using the below formula we estimate the distance:

Distance=F*B/Disparity_value.

F-Focal Length in milimeter.

B-Baseline of stereo camera.



CONCLUSION:

In the above work we were successfully able to identify the objects and classify them and obtain 
the distance of the detected object from camera. In order to achieve this we first divided our 
problem statement into various stage and tried to obtain optimized model for respective stages and 
in the end we combined all the optimized model to obtain the desired results.We have considered 
inputs with respect to different distances from the camera and calculated the average distance 
from our algorithm and later it compared to actual distance,we have obtained  results with deviation  of 0.2mtrs.
