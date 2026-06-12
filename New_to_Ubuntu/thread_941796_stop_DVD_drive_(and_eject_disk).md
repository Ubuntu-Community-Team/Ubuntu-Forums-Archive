---
title: "stop DVD drive (and eject disk) ??"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by Mount on 2008-10-08
Hi, 

Sounds like a really easy problem but its got me. 

I've just done a complete reinstall and upgraded to Hardy. I've just put a DVD in the drive and tried to play it. I soon realised/remembered that I have to do something to enable DVD play back which I'm going to do.
The problem is that for the moment I can not stop the DVD drive spinning and I can not get the DVD out by pressing the drive's eject button. I have tried 'sudo umount cdrom' but it says the cdrom drive is not mounted. Does anyone have another suggestion? 

In addition to the above problem it also sounds like the DVD drive is spinning faster than normal. Is it possible that Hardy has not recognised the optimum setup of my drive? 

Thanks in advance, 
M



p.s. In the time I have written this message (ca. 10min) the drive has stopped spinning and I have been able to eject the disk. despite this i would still like to be able to stop/eject the disk at will instead of waiting X minutes to do it.

---

### Post by Cpuboye11 on 2008-10-08
Hey...

I don't know if this will help you.. I have never had the cd dvd problem. Is there any sort of shortcut on your desktop that would come up just like a CD? If so just right click and click unmount... Or on mine eject :-D...

Any ways, don't know ... Best of Luck!!!!!:guitar::guitar:

---

### Post by Mount on 2008-10-08
Hi Cpuboye11, 

Thanks for the suggestion. Unfortunately I already tried that. The icon on the desktop disappeared but the drive was still spinning and unresponsive. 

Cheers

---

### Post by _sAm_ on 2008-10-08
Try **eject** in a terminal next time(and **eject -t** to close it). 

If it dosnt work try; eject -t /dev/cdrom

---

### Post by Waugh on 2008-10-08
If nothing else works, you could always use the manual eject button.  I usually push it in with a straightened paper clip.

---

### Post by philinux on 2008-10-08
To enable DVD playback, which will probably cure the non-ejecting problem, click the Medibuntu link below. Follow the instructions there.

---

### Post by uncannybuzzard on 2008-10-08
```
sudo fuser -k /dev/[name of your dvd drive]
```

this will kill whatever process is using the dvd drive. you'll have to find out what your drive is called in /dev though. you should be able to eject it fine afterwards

---

