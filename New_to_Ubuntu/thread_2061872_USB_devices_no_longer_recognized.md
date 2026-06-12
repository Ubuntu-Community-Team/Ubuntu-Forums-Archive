---
title: "USB devices no longer recognized"
date: 2012-09-23
forum: New to Ubuntu
---

### Post by mrh840 on 2012-09-23
Hey! I installed Xubuntu as my OS about a week ago and have been very happy with it. I  had some trouble setting up dual monitor display but eventually got it working. However, today when I plugged my VGA cable into my laptop, both displays flashed on and off a few times and conked out  -- basically into an unusable state. I unplugged it and rebooted.

Things are working OK now except that the laptop no longer recognizes USB devices. My mouse lights up when it's plugged in-- but in the Settings Manager, it is no longer recognized a device. (Same with my drawing tablet & flash drive.)

What happened and how can I fix it?

Thanks for any advice!

---

### Post by daslinkard on 2012-09-23
You can try the following sudo commands to fix the issue....
```
sudo apt-get update
```
```
 sudo apt-get install -f

``````
sudo update-pciids
``` 
```
sudo update-usbids

``````
sudo dpkg --configure -a
```

You may have to reboot your system but let me know if this works for you!

---

### Post by tmfdia on 2012-09-29
I found this thread because I had a similar problem.  I tried the steps listed and now I can see the missing USB devices...

To make sure I understand what I just did, let me say what I THINK I did in each step; feel free to correct me.... I prefer to UNDERSTAND what I did, rather than just copy/paste.


> **daslinkard said:**
> You can try the following sudo commands to fix the issue....
```
sudo apt-get update
```Make sure I have the latest library sources

```
 sudo apt-get install -f
```Install any needed sources

```
sudo update-pciids
```Update PCI ID Database

```
sudo update-usbids
```Update USB  ID Database
```
sudo dpkg --configure -a
```Configure Changes

You may have to reboot your system but let me know if this works for you!
I did not have to, but thanks for the heads up.


Tmfdia

---

