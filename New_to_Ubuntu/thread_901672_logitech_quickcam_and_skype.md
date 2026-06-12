---
title: "logitech quickcam and skype"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by mattjack66 on 2008-08-26
Hi.
I have a logitech quickcam 5.0.1 and skype but my video wont work! why?

---

### Post by Zwalther on 2008-08-27
Could you give a little more information? What do you see exactly?

Does the camera show up in the video configuration screen in the Skype options?

---

### Post by Crafty Kisses on 2008-08-27
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If Ekiga doesn't work post results of the command > lsusb

---

