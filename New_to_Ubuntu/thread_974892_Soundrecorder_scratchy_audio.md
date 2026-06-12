---
title: "Soundrecorder scratchy audio?"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by saxamo on 2008-11-07
Hi, I was wondering if anyone else was experiencing scratchy audio from anything you try to record with sound recorder. I am putting a line into the microphone jack from a tape recorder and there is a constant static. Is it from the tape itself or does sound recorder do this to others?

---

### Post by w4ett on 2008-11-08
You are probably experiencing an impedance mismatch......Computer soundcards supply voltage to an electret condenser microphone which have a  output 10-100 Mvolt....

the output from the tape recorder is much higher from the line out and you will need to adapt the output from the recorder to match the input of the soundcard by using preamplification and filtering.

It's far preferable to use a line in jack to make the connection. 

Here's some further info: [http://www.andybrain.com/qna/2007/12/11/will-plugging-in-a-stereo-to-a-computers-mic-jack-damage-the-microphone/](http://www.andybrain.com/qna/2007/12/11/will-plugging-in-a-stereo-to-a-computers-mic-jack-damage-the-microphone/)

If you don't have a line input, consider getting a decent soundcard.  Loads are available for $25.

---

### Post by saxamo on 2008-11-08
Thanks, that makes a lot of sense. My laptop does not have a line in port but I do have a USB soundcard that I will try to use. Thanks again!

---

