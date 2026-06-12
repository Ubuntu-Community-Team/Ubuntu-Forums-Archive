---
title: "web camera and mic"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by manjunaathsiegen on 2008-11-17
Hi,
I switched my operating system completely to Ubuntu 8.10.
But my laptop inbuilt webcamera and mic are not functioning.  Is any driver require for this to function. Please help me in this.
laptop: sony vaio VGN-FZ18M

---

### Post by Crafty Kisses on 2008-11-17
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If Ekiga doesn't work post results of the command > lsusb

---

### Post by spiderbatdad on 2008-11-17
make sure you have run updates...libv4l-0 that installed with intrepid had a bug that existed in almost all webcam related packages: [https://bugs.launchpad.net/debian/+bug/260918](https://bugs.launchpad.net/debian/+bug/260918)

---

### Post by manjunaathsiegen on 2008-11-17
Hi,
It is completely not responding.  Even I tried both V4L and V4L2 but I couldn't see image.
What I suppose to do now.
Thanking you,

> **Codename said:**
> Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If Ekiga doesn't work post results of the command > lsusb

---

### Post by halitech on 2008-11-17
see your other thread and keep all info in 1 thread. makes it hard to help if you have 2 (or more) threads on the same issue)

---

