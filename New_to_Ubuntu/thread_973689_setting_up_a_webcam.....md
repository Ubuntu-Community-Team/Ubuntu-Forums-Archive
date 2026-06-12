---
title: "setting up a webcam...."
date: 2008-11-06
forum: New to Ubuntu
---

### Post by B34ST1Y on 2008-11-06
Hey, i've been trying for the last day to set up my webcam to run in ubuntu. Its a dynex 1.3mp webcam. Does anyone have any tips on how to get this thing going? I dont understand...

---

### Post by randy78 on 2008-11-06
Check here: [http://ubuntuforums.org/showthread.php?t=913832]("http://ubuntuforums.org/showthread.php?t=913832")

---

### Post by B34ST1Y on 2008-11-06
anyone??.. 

cheese can "see" my webcam...but anytime I try to access it, the light illuminates on my camera (as though its in use) ...but the program just hangs and crashes....

---

### Post by B34ST1Y on 2008-11-07
I followed the guide, and while all the commands completely successfully...I still get nothing but a blank screen when I try to run cheese, or luvcview. Any suggestions? :( =/

---

### Post by Crafty Kisses on 2008-11-07
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

To test your webcam you can do this:

There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If Ekiga doesn't work post results of the command > lsusb

---

### Post by B34ST1Y on 2008-11-07
whattttt.....ok so I ran through ekiga's setup...and now I can see the video output on my webcam through that program! (yay! DEFINITELY thanks to you! ) but....now I go back into Cheese.....and instead of a blank display...it shows the test bars of color...and in the lower right...static like from a tv. no signal from webcam though :(

---

### Post by patrickballeux on 2008-11-07
A good way to test a webcam is using gstreamer-properties...

In a terminal (or pressing ALT-F2), run: gstreamer-properties

You will have an interface where you can configure your audio and video settings with some advanced features. Look into the video setting, in "Capture" at the bottom.  You have a "Test" button available for your settings.

About Cheese, it does not work for me either and both my webcams are working well.

Let me know!

---

### Post by patrickballeux on 2008-11-07
> **B34ST1Y said:**
> whattttt.....ok so I ran through ekiga's setup...and now I can see the video output on my webcam through that program! (yay! DEFINITELY thanks to you! ) but....now I go back into Cheese.....and instead of a blank display...it shows the test bars of color...and in the lower right...static like from a tv. no signal from webcam though :(

It means that Cheese was not able to detect your webcam (probably in use by Ekiga)

---

### Post by Crafty Kisses on 2008-11-07
What are the results of this command?
```
lsusb
```

---

### Post by crispy_420 on 2008-11-07
[https://help.ubuntu.com/community/EasyCam](https://help.ubuntu.com/community/EasyCam)

---

### Post by B34ST1Y on 2008-11-07
```
:~$ lsusb
Bus 002 Device 002: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 19ff:0102 Best Buy 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
:~$ 

```

easycam just set up my webcam...then launched cheese, which did nothing still, hehe. :-P

---

### Post by Crafty Kisses on 2008-11-07
This might be your webcam, I'm not sure.
```
Bus 001 Device 008: ID 19ff:0102 Best Buy
```
Did you buy your webcam from Best Buy?

---

### Post by B34ST1Y on 2008-11-07
lol yes. its a dynex 1.3mp webcam

---

### Post by B34ST1Y on 2008-11-07
its still not working :(

---

### Post by spiderbatdad on 2008-11-07
the version of libv4l-0 in the repos is not currently working with previously used drivers...[http://ubuntuforums.org/showthread.php?t=966436](http://ubuntuforums.org/showthread.php?t=966436)

see that report and workaround...try to start cheese from the command line with either of the LD_PRELOAD commands```
sudo LD_PRELOAD=/usr/lib/libv4l/libv4l2convert.so cheese
```

---

### Post by B34ST1Y on 2008-11-07
same thing :'(. ........I can use the webcam just fine in Skype....why not anything else?

---

### Post by kushykush on 2008-11-07
I am having the same problem with my Sonix 1.3.  Here is my lusb output:
user1@user1-desktop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0c45:628f Microdia Composite Device
Bus 001 Device 002: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I need some one tell me what is wrong here?  The Microdia Composite device is my Webcam connected on the NEC hisghspeec USB Hub.

---

