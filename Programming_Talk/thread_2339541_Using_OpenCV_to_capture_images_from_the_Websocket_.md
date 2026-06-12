---
title: "Using OpenCV to capture images from the Websocket stream"
date: 2016-10-10
forum: Programming Talk
---

### Post by DBQ on 2016-10-10
Hi Everybody.

I have the following setup:

1. A server which is receiving a video stream from a client. The clients can view the video stream through a websocket at ws://1.2.3.4:8888.

2. Now, I would like to use OpenCV in order to capture frames from that stream. I tried using cap = cv2.VideoCapture('ws://1.2.3.4:8888/') and it does not work. Gives me an error (note: the socket works; I tried displaying the stream on a canvas).

My question is, is there any way for me to read (in Python) frame-by-frame the stream that is available through websocket? Preferably using opencv?

Please help! I have tried many things, but none work.

Thank you!

---

