---
title: "[REPOST] Can someone PLEASE help w/ Microphone Issues?"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by OKnotOK on 2008-06-15
I've already posted this a couple times, but nobody has responded. 

I am trying to get my webcam to work with Cheese. It is a Logitech Quickcam Deluxe.

We have ubuntu 8.1 on a 64-bit system. 

I've already tried alsamixer, and even with everything turned up, I'm not getting any sound.

---

### Post by sam_delta on 2008-06-15
take a look at the following links

[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

[https://help.ubuntu.com/community/EasyCam](https://help.ubuntu.com/community/EasyCam) (driver installer software)

sam

---

### Post by OKnotOK on 2008-06-15
> **sam_delta said:**
> take a look at the following links

[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

[https://help.ubuntu.com/community/EasyCam](https://help.ubuntu.com/community/EasyCam) (driver installer software)

sam

Okay, I installed Camorama, and when I start it up, it says "Could not connect to video device (/dev/video0)" ... The camera works already with cheese (just without sound) so I know I've properly connected it. 

Is there some way to fix the audio problem with Cheese?

---

### Post by sam_delta on 2008-06-15
hey, i have no experience with this, im just trying to do some research on this in the internet. what driver did you installed for your camera? or it just worked out of the box?

also, what happens if you go into system>preferences>audio, try to play with the settings, or audio input device

you might find this thread interesting
[http://ubuntuforums.org/showthread.php?t=294474](http://ubuntuforums.org/showthread.php?t=294474)

sam

---

### Post by OKnotOK on 2008-06-15
> **sam_delta said:**
> hey, i have no experience with this, im just trying to do some research on this in the internet. what driver did you installed for your camera? or it just worked out of the box?

you might find this thread interesting
[http://ubuntuforums.org/showthread.php?t=294474](http://ubuntuforums.org/showthread.php?t=294474)

sam

It's cool. I am just relieved that SOMEONE finally responded. (Sorry if I sound frustrated, I've been trying to fix this for days now)

My camera just worked out of the box. I typed "Cheese" into the add/remove programs box, clicked on it, and that's all. 

It has a built-in mic, I don't know if that's the problem, or what?

---

### Post by master5o1 on 2008-06-15
I thought Cheese was only video, not audio.

---

### Post by OKnotOK on 2008-06-15
> **master5o1 said:**
> I thought Cheese was only video, not audio.

Is it? I don't really know. Come to think of it, there is nothing in Cheese's help files about audio troubleshooting. Could it be because the program doesn't do audio?! :mad:

Camorama says "/dev/video0" when I try to use it.

---

### Post by sam_delta on 2008-06-15
try doing it with VLC , you can install it from add/remove then

> You should be able to do this with VLC player which can be installed from the repositories. It's extremely powerful and can let you view, stream or save video/audio from any source.

To create a file from your webcam... Go to "File" -> "Open capture device". Make sure the "Video device name" and "Audio device name" are correct (for me the dialog defaults to /dev/video when in fact my webcam it is /dev/video0" so do check this). Then under "advanced options" at the bottom of the dialog, tick "stream/save" then settings. Check the "file" option under "outputs" and adjust the desired output format to taste with the transcoding options and you're good to go. VLC won't show the webcam while it saves, so if you want to see if it is working go to where ever you set it to save and inspect the file.
quoted from [http://ubuntuforums.org/showthread.php?t=377517](http://ubuntuforums.org/showthread.php?t=377517)

ima go sleep now, ill be back tomorrow
sam

---

### Post by kevin11951 on 2008-06-15
> **OKnotOK said:**
> Is it? I don't really know. Come to think of it, there is nothing in Cheese's help files about audio troubleshooting. Could it be because the program doesn't do audio?! :mad:

Camorama says "/dev/video0" when I try to use it.

no... no... cheese does audio, dont worry, but as for the microphone, try getting an external plugin one... just to test.

---

### Post by OKnotOK on 2008-06-15
> **kevin11951 said:**
> no... no... cheese does audio, dont worry, but as for the microphone, try getting an external plugin one... just to test.

I was thinking of that... I don't have one, and its nearly 4am where I am, so I'll have to get one and I guess resurrect this thread when I can test it. 

Thanks for the help everyone.

---

### Post by OKnotOK on 2008-06-16
> **kevin11951 said:**
> no... no... cheese does audio, dont worry, but as for the microphone, try getting an external plugin one... just to test.

Okay, I've acquired and tested an external mic... The audio is THERE, but its extremely quiet. I can't make out what I'm saying -- its that low. 

Alsamixer is cranked up as high as I can get it. 

Any suggestions?

---

### Post by OKnotOK on 2008-06-16
**Bump**

Please? Someone? Anyone? 

PLEASE?!

---

### Post by markbuntu on 2008-06-17
I have a Logitech Quickcam Communicate STX and I got it working.

I used ekiga which which can detect the camera and tell you its name and you can find out if it is working. I had a picture in cheese but none in ekiga. I had to get v4l for it to work because v4l2 did not find any camera. Once I got v4l with synaptic and I selected v4l in ekiga and checked detect devices or whatever that got the video working. I also selected alsa in audio.

Then I had to go into my gnome-alsamixer and use the USB section (which came out of nowhere when I plugged in the camera and rebooted) to unmute the microphone and turn up the level. Now it works, audio, video.

If you are using pulseaudio or oss I have no idea how you could get this to work but that is basically the idea.

---

### Post by markbuntu on 2008-06-19
The camera also works in camorama and cheese and I would imagine anything else. The key was getting V4l from the repo.

---

### Post by OKnotOK on 2008-06-19
> **markbuntu said:**
>  The key was getting V4l from the repo.

I don't think I know what this means though. 

Repo = repository, but I don't remember what that means. I've only done it once, and I was majorly having my hand held the whole time! :) 

(hint hint)

---

