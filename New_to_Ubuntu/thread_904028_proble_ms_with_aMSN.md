---
title: "proble ms with aMSN"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by patchido on 2008-08-28
well... aMSN isnt getting my webcam or sound... it wont make sounds when the events happen... i did the configuration and it did recognize the webcam but it still wont work on a conversation.... by the other part microphone and sound wasnt recognized in the congiguration wizard

---

### Post by Crafty Kisses on 2008-08-28
Have you seen if the webcam even works with Linux?

Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If Ekiga doesn't work post results of the command > lsusb

---

