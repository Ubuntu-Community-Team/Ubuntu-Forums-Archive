---
title: "record video from webcam using java gstreamer"
date: 2014-01-03
forum: Programming Talk
---

### Post by ilan.hakimi on 2014-01-03
[COLOR=#000000][FONT=Verdana]Hello, [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]I'm tring to wirte an application which records video from my web cam to a file using gstreamer for java (working with eclipse on ubuntu). I'm quite new to gstreamer so to begin with, I just built a src element which is my webcam and a sink which is a file I created. Then I added them to a pipeline, linked and played the pipeline for 10 seconds. [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]The application "worked fine" and a file was created (pretty large). But, when I try to play the file with VLC (or any other media player) I see nothing. I don't know if it has anything to do with the fact the video wan't encoded or something like that. I wanted to try to encode the video before putting it into the file but I don't know how -  I can't seem to find any element in the "gstramer for java" package which encodes video. [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]I would be more than glad to get your help to record the video with and without encoding (if possible). [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Thanks in advance, [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Ilan. [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Comment: Please don't tell me to go to "gst-launch" because I did it already and it worked, but I couldn't find a way to translate it to java code.[/FONT][/COLOR]

---

### Post by ofnuts on 2014-01-03
What does a tool such as 'mediainfo' tell you about the file produced?

---

