---
title: "How to install my webcam drivers?"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by andy_blah on 2008-04-27
I`m using Ubuntu 8.04 LTS and I`m having some problems with a Trust 620 PowerC@m. I have tried to plug it in and the computer/OS did not react at all. Skype cannot detect it. I have also tried to install EasyCam2, but it says "No camera, or no compatible camera found". What sould I do to fix this?

Thank-you,
>-Andy-<

---

### Post by linuxwizard on 2008-04-27
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings.

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If Ekiga didn't work post results of the command > lsusb

---

### Post by andy_blah on 2008-04-27
Nethier Ekiga detects my webcam. And as I expected it does not work (the Ekiga logo is bouncing).
Here is the output of the command:
```
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 006: ID 052b:1511 Tekom Technologies, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

---

### Post by djdarrin91 on 2008-04-27
Not sure if this will help you but it did me-download Cheese and see if your cam is detected. Good Luck:)

---

### Post by andy_blah on 2008-04-27
That does not solve the problem at all.

---

### Post by linuxwizard on 2008-04-27
I am going to do more searching to see if I can find something on your webcam in the mean time try this > open Ekiga > Edit > Preferences > Devices > Video Devices > try changing Video Plugin if it shows V4L change to V4L2 or if it shows V4L2 change to V4L. Than see if cam will work.

The best way I have found to test a webcam to see if it going to work is using Ekiga. Cheese is a waste of time.

---

### Post by andy_blah on 2008-04-27
Changing the video plugin does not make the webcam work. Also, I have forgot to mention that under Video Devices, in the Preferences window, at devices it says: "No devices found" (see the attachment).

Thank-you for your time, and for your (further) search.

---

### Post by linuxwizard on 2008-04-27
I have searched everywhere I can think of and can not find anything on your webcam or a driver. Not sure what else to tell you but it does not look like your cam is supported and not going to work in Linux.

---

### Post by andy_blah on 2008-04-27
Then what should I do so it would be supportable? Maybe somebody who develops drivers for Ubuntu/Linux?
Thank-you so far for your help

---

### Post by vlaklak on 2008-04-27
I had a webcam "Made in China" a very cheap one!  Ubuntu could not detect the driver. But because of curious I bought a Logitech Webcam "it is cheap too" and now I can communicate with webcam.

I think your webcam comes from the ancient times, so Ubuntu could'nt recognize it.  Sorry pall.

---

### Post by Timbothecat on 2008-06-02
This may sound like a really stupid question, but can you make calls to and from skype on ekiga? The reason I ask is that when I changed the settings then to v4l my camera started to work, yet I can't seem to find out how to do this on skype. (Edit: on skype, it get's picked up but as soon as I go to run a test it crashes and won't let me actually use the cam. I did get it to work for about 30 seconds earlier tonight -not using test- and it was all but unusable, colours all out of whack across the screen.)

I'm using a Vimicro301 Neptune, EZCool USB PC Camera on Hardy. Ekiga would serve my purposes if I can get it to work with skype, otherwise I'll just have to soldier on and see if I can't get it to function properly.

Sorry to hi-jack the thread btw. :oops:[-o<

---

### Post by philinux on 2008-06-02
If all else fails this cam is working for me.

[http://www.ebuyer.com/product/119159](http://www.ebuyer.com/product/119159)

I'm sure there are loads of others that will work.

---

