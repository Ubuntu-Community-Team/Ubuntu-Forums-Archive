---
title: "Cheese giving only greyscale images from webcam"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by dileepdinesh on 2008-08-17
Hi,
    Cheese program in my ubuntu has detected my webcam,but gives only greyscale images..but when i try with ekiga softphone and some other programs(i dont remember)..i get color images......any ideas?

---

### Post by fluteflute on 2008-08-25
Have you check that under the 'Effects' button check that the 'Noir/Blanc' (aka greyscale) image/box is not selected?

---

### Post by Crafty Kisses on 2008-08-25
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If Ekiga doesn't work post results of the command > lsusb

---

