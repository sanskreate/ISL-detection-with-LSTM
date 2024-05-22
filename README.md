
# Word Level Indian Sign Language Recognition 

This project aims to bridge the communication gap for the deaf community by providing them with a mobile/web app that predicts the meaning of sign gestures captured in a video, allowing them to interact with non-sign language users effectively.


#### Brief Explanation:
- This project is aimed at developing a word-level Indian Sign Language (ISL) recognition system on Videos. Sign language is an action word which cannot be encompassed in a single frame, so a video of 2-3 seconds is required to determine the word signified by the action. The project's primary objective is to bridge the communication gap for the deaf community by enabling them to interact with non-sign language users effectively. The code sample provided here showcases the functionality of the system, demonstrating how it processes video input to recognize and predict the words signified by specific sign language actions.

- The code begins by accepting a video feed, which can be obtained from various sources such as a camera, a saved video file, or a web application. From this feed, the system selects 45 frames evenly to ensure it doesn't lose information if number of frames is greater than 45 in videos. Using Mediapipe PoseNet, an advanced pose-estimation model, the code detects and captures key body, left hand, and right-hand coordinates present in each frame.For example, movements of the right thumb across frames can help identify specific signs.

- These extracted coordinates are then saved as a Numpy array, preserving the spatial information of the key points. Shape: (45 frames, 22 coordinate information in x and y axis) Subsequently, the Numpy array is fed into an LSTM (Long Short-Term Memory) deep learning model. The LSTM model is crucial for processing sequential data and understanding the temporal dynamics of sign language gestures.

- Finally, the LSTM model predicts the word corresponding to the sign language action in the video. This predicted word is the system's output, representing the meaningful interpretation of the sign language gesture


### Output Words: [Hello, How are you, Thank you]


## Project WorkFlow :



## Installation and Usage

1. Install Necessary Libraries: 

```bash
pip install -r requirements.txt
```

2. Create a web-app:

```python
python app.py
```


3. Run with laptop camera (live feed):

```python
python deploy_code.py
```

4. Process saved video from the command line:

```python
python run_through_cmd_line.py -i input_file_path
```


## API Reference

#### Upload Video in form:

```http
POST /upload-video/
```

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `file`    | `file`   | Video                      |

#### Test API call:

```http
GET /test/
```


## Data 

##### Actions: [Hello, How are you, Thank you]
Real Time Test Data : 

| Videos per action| Total   Data |
| :-------- | :------- | 
| 8 Videos  | 24 Videos  | 




## Input Shape

We experimented with various mobile devices to detect the number of frames captured per second and decided that 45 frames would provide sufficient information for predicting a class without losing crucial details.

```
If there are more than 45 frames in the captured video:
     We evenly select frames to avoid losing information.
Else if the number of frames is less than 45:
     We add empty frames to maintain a constant input shape.
```


## Mediapipe PoseNet Detection 

Mediapipe PoseNet for Sign Language Project:
Mediapipe PoseNet, a real-time pose estimation model, lies at the core of our sign language project. Leveraging PoseNet's robustness, we achieve precise tracking of body keypoints, enabling accurate interpretation of sign gestures. With seamless integration and customization options, our application empowers effective communication for the deaf and hard of hearing community.


## Architectures


V1: LSTM Architecture (Final Version)
   - Numpy array containing keypoint coordinates in each frame as a separate array. Array Shape: (45, 24, 2)
   - These are fed through LSTMs to classify the actions.
```
## Results 

LSTM Model performed significantly well both in validation set and exceptionally well in real time test data.

Categorical Accuracy  : 
 | Train | Validation   | Real-Time Test Data                |
| :-------- | :------- | :------------------------- |
| 78   % | 74.6 % | 95 %                     |





