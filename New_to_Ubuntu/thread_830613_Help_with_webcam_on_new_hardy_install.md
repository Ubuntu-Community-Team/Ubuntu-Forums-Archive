---
title: "Help with webcam on new hardy install"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by tpund on 2008-06-16
Hello,

I just installed Hardy Heron on my HP dv9700 laptop and everything installed great, but I'm having some trouble with the webcam.

I'm fairly new to linux and I'd appreciate some help or advice.  I've installed a couple programs that are supposed to help with the webcam, but so far the results are pretty weird.

First I installed camorama to test the webcam, but when I start it I get the message "Could not connect to video device (/dev/video0).  Please check connection."

Then I installed easycam, which is supposed to help with installing webcam drivers, but I get this message when I start it.  "No camera, or compatible camera found."

Then I found [this post]("http://ubuntuforums.org/showthread.php?t=829203&highlight=hp+dv*+webcam") and followed the directions and thought it worked because when I used xawtv to test the camera as the instructions directed a window popped up and there I was on the screen in a lil bitty video window.

But when I try to do anything else with the camera I still get the previous errors I had been getting.  Only xawtv will connect to the camera.

Any help?

---

### Post by nothingspecial on 2008-06-16
Did you try cheese, 
```
sudo apt-get install cheese
```

Then to run it simply ```
cheese
```

Also try skype -
Make sure you have the medibuntu repositries checked in your sources list then,
```

sudo apt-get install skype
```

Both these work with my laptop`s webcam but nothing else will.

---

### Post by markbuntu on 2008-06-16
make sure you have V4l and V4l2, Video for Linux installed. My Logitech Quickcam CommunicateSTX didn't work until I installed V4L because V4L2 did not see it. 

skype, cheese, none of that will work without v4l or v4l2 to find and operate the camera. Ekiga already comes installed with hardy and you can use that to find out what your camera works with, that's what I did.

---

