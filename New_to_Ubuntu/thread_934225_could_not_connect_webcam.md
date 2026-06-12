---
title: "could not connect webcam"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by abhilash1989 on 2008-09-30
hiii im a beginner of linux..........
im unable to connect my webcam......yahoo plugin  not accepting it........
what is the problem.....
DO HELP

---

### Post by Crafty Kisses on 2008-09-30
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

To test your webcam you can do this:

There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If Ekiga doesn't work post results of the command > lsusb

---

### Post by wolfen69 on 2008-09-30
kopete also has webcam support. has worked for me. also there is a chance that your webcam may not be supported in linux. what kind is it?

---

