## Stream Video to your browser

### Add video element to index.html file
_File: index.html_

```html
<video id="video"></video>
```

### Stream video from device camera to video element
* Find the video element and store it in variable.
* create another variable named videoStream. 
_File: /scripts/video.html_

```javascript
//video.js - step 1
  const videoElement = document.getElementById("video"); //video element created in index.html file
  let videoStream;
  ```
  
 * Get device's media and select video.
 * Access the stream and assign the stream to video elements src object.
 
 _File: /scripts/video.html_
  ```javascript
  //video.js - step 2
    navigator.mediaDevices.getUserMedia({ video: { facingMode: 'user' } }) //get user media, select video
      .then(stream => { //then get the stream of the video
        videoStream = stream; //store the stream in videostream 
        videoElement.srcObject = videoStream; //assign the stream to video element's src object.
     })
  ```

### Play/Stop Video
* Play button is already added to index.html file with id "play"
* Access the play button and create a function that will run when the button is clicked
* Replace code in video.js -step 2 with following code to start video when play button is clicked
 
 _File: /scripts/video.html_
```javascript
  //replace video.js - step 2 with following code
  //video.js - step 3
  $('#play').click(function () {
    //this part of code will run when play button is clicked   
    navigator.mediaDevices.getUserMedia({ video: { facingMode: 'user' } }) //get user media, select video
      .then(stream => { //then get the stream of the video
        videoStream = stream; //store the stream in videostream 
        videoElement.srcObject = videoStream; //assign the stream to video element's src object.
     })      
  })
```
* To stop the video access stop button and create function that will run when the stop button is clicked
* Check if videostream is available.
* If it is available, stop the first track. (Note: In live stream there is only one track)
_File: /scripts/video.html_
```javascript
  //video.js - step 5
  $('#stop').click(function () {
    //this part of code will run when stop button is clicked       
    if(videoStream != undefined){
      videoStream.getTracks()[0].stop();
    }
  })
```

## After these steps
* Video should start when you click Play button
* Video should stream live from camera
* Video should stop when you click Stop button

 
