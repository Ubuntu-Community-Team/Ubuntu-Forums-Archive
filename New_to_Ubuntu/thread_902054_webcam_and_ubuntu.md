---
title: "webcam and ubuntu"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by patchido on 2008-08-26
well i have a dell inspiron 1420 with webcam included and i can run cheese, i cant run camorama, and neighter run webcam on aMSN i really want to use my webcam on aMSN and maybe this might fix camorama isnt it?

---

### Post by meanburrito920 on 2008-08-27
What webcam are you using? many webcams seem to have issues with Ubuntu.

---

### Post by patchido on 2008-08-27
how can i know??? it is integrated within the laptop.. i told ....

---

### Post by Bradtek on 2008-08-27
> how can i know???

You could always try looking in the manual or the Dell website 
or open a terminal and type
```
lsusb
```
this will tell you what usb devices are in your laptop
 (only guessing it uses usb)


and post the output here


or try searching the forum for same/similar problem
[http://ubuntuforums.org/showthread.php?t=861433](http://ubuntuforums.org/showthread.php?t=861433)

[http://ubuntuforums.org/showthread.php?t=751881](http://ubuntuforums.org/showthread.php?t=751881)

Also try turning off Compiz (if you have it enabled)

---

### Post by patrickballeux on 2008-08-27
The Dell 1420 has an Omni Vision, like the one I have in my Dell 1521.

This is a V4L2 device and it will not work in Camorama since it does not support V4L2 device if my memory is good.

As for aMSN, it should work to my knowledge (I am usung Amsn from the repository).

Also, as a good news, if you install Flash 10 RC (from Adobe site), it will be available for site like Stickam or BlogTV.  There is a little instability but it is highly usable.


If you still have problems, have a look at the flashcam project that will convert your V4L2 into a Vl4 device and make it work with EffecTv and Camorama.

But you could start your amsn from the console to see if there are error messages related to the webcam detection...

Just to be sure, you have run the wizard in aMSN for the configuration of your webcam? right?

---

### Post by Crafty Kisses on 2008-08-27
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If Ekiga doesn't work post results of the command > lsusb

---

