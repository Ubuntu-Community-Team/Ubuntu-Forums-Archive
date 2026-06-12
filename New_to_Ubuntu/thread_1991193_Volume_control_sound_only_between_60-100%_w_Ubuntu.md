---
title: "Volume control sound only between 60-100% w Ubuntu 12.04"
date: 2012-05-30
forum: New to Ubuntu
---

### Post by alienexplorers on 2012-05-30
After installing Ununtu 12.04 I noticed I have no sound between 0 and 60% on the volume slider.  Once I go past 60% the volume goes up to around 100%.  I have checked pavucontrol and alsamixer.  Alsamixer is set to full on all channels, white pavucontrol follows the volume slider in the panel.  My sound card as far as I can tell is a VT1708B.  What is up and how do I go about fixing this problem.

Thanks in Advance,

Donnie

---

### Post by alienexplorers on 2012-05-31
> **alienexplorers said:**
> After installing Ununtu 12.04 I noticed I have no sound between 0 and 60% on the volume slider.  Once I go past 60% the volume goes up to around 100%.  I have checked pavucontrol and alsamixer.  Alsamixer is set to full on all channels, white pavucontrol follows the volume slider in the panel.  My sound card as far as I can tell is a VT1708B.  What is up and how do I go about fixing this problem.

Thanks in Advance,

Donnie

Finally got the sound slider working by replacing several of the -pulse files with -gstreamer files.  The version I am using has the mate desktop and I swapped the files and it worked.

---

### Post by alienexplorers on 2012-05-31
> **alienexplorers said:**
> Finally got the sound slider working by replacing several of the -pulse files with -gstreamer files.  The version I am using has the mate desktop and I swapped the files and it worked.

Just found out the problem is back.  Don't know why this is happening.  Anyone heard about a driver problem or kernel problem with sound output?

---

### Post by NikTh on 2012-05-31
Hi ,
Try to uninstall this and tell me if something happen 
```
sudo apt-get remove pulseaudio-module-x11
``` 
reboot

---

### Post by ebin on 2012-12-11
What was the result here?

---

