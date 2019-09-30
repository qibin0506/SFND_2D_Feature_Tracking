# SFND 2D Feature Tracking

<img src="images/keypoints.png" width="820" height="248" />

The idea of the camera course is to build a collision detection system - that's the overall goal for the Final Project. As a preparation for this, you will now build the feature tracking part and test various detector / descriptor combinations to see which ones perform best. This mid-term project consists of four parts:

* First, you will focus on loading images, setting up data structures and putting everything into a ring buffer to optimize memory load. 
* Then, you will integrate several keypoint detectors such as HARRIS, FAST, BRISK and SIFT and compare them with regard to number of keypoints and speed. 
* In the next part, you will then focus on descriptor extraction and matching using brute force and also the FLANN approach we discussed in the previous lesson. 
* In the last part, once the code framework is complete, you will test the various algorithms in different combinations and compare them with regard to some performance measures. 

See the classroom instruction and code comments for more details on each of these parts. Once you are finished with this project, the keypoint matching part will be set up and you can proceed to the next lesson, where the focus is on integrating Lidar points and on object detection using deep-learning. 

## Rubric

1. MP.1 Data Buffer Optimization
> I use a method names `erase` to ensure the size of dataBuffer less than or equal 2.

2. MP.2 Keypoint Detection
> For detection method, I write 7 method for each detection method of SHITOMASI, HARRIS, FAST, BRISK, ORB, AKAZE, SIFT.

3. MP.3 Keypoint Removal
> I determined the ROI by using a method names `contains` of `Rect` class, and put the result to a new vector.

4. MP.4 Keypoint Descriptors
> My implemention of descriptors is using the opencv's method in `descKeypoints` function.

5. MP.5 Descriptor Matching
> First, I convert `descSource` and `descRef` to `CV_32F` when the type of `descSource` is not `CV_32F`. Then, use the `knnMatch` method from opencv to match the result.

6. MP.6 Descriptor Distance Ratio
> For `knn match` algorithm, I set ratio to `0.8` and use the code `knn_matches[i][0].distance < ratio * knn_matches[i][1].distance` to filter result.

7. MP.7 Performance Evaluation 1, MP.8 Performance Evaluation 2, MP.9 Performance Evaluation 3
> My Result at [https://drive.google.com/open?id=1Q5G8rdBjI1QjRTCYiGcSzEKOnsv9eynE](https://drive.google.com/open?id=1Q5G8rdBjI1QjRTCYiGcSzEKOnsv9eynE)


## Result
Time of extractor and descriptor at [https://drive.google.com/open?id=1Q5G8rdBjI1QjRTCYiGcSzEKOnsv9eynE](https://drive.google.com/open?id=1Q5G8rdBjI1QjRTCYiGcSzEKOnsv9eynE).

Top 3 best result
1. FAST-BRIEF
2. FAST-ORB
3. FAST-BRISK

## Dependencies for Running Locally
* cmake >= 2.8
  * All OSes: [click here for installation instructions](https://cmake.org/install/)
* make >= 4.1 (Linux, Mac), 3.81 (Windows)
  * Linux: make is installed by default on most Linux distros
  * Mac: [install Xcode command line tools to get make](https://developer.apple.com/xcode/features/)
  * Windows: [Click here for installation instructions](http://gnuwin32.sourceforge.net/packages/make.htm)
* OpenCV >= 4.1
  * This must be compiled from source using the `-D OPENCV_ENABLE_NONFREE=ON` cmake flag for testing the SIFT and SURF detectors.
  * The OpenCV 4.1.0 source code can be found [here](https://github.com/opencv/opencv/tree/4.1.0)
* gcc/g++ >= 5.4
  * Linux: gcc / g++ is installed by default on most Linux distros
  * Mac: same deal as make - [install Xcode command line tools](https://developer.apple.com/xcode/features/)
  * Windows: recommend using [MinGW](http://www.mingw.org/)

## Basic Build Instructions

1. Clone this repo.
2. Make a build directory in the top level directory: `mkdir build && cd build`
3. Compile: `cmake .. && make`
4. Run it: `./2D_feature_tracking`.
