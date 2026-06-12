---
title: "No Audio Problem"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by Jamessharpshooter on 2008-09-20
My p4p800 deluxe motherboard cannot put out any sound to my speakers... i need help to install the drivers, the GStreamer plugins are fine. The os cant seem to see the "device"... please help.


RUNNING MINT!

---

### Post by sayakb on 2008-09-21
At a terminal (Applications->Accessories->Terminal)
Type in:
```
sudo apt-get install linux-backports-modules-hardy
``` .. for Hardy.
```
sudo apt-get install linux-backports-modules
``` .. for older releases.
After installing, reboot your PC.

---

### Post by Jamessharpshooter on 2008-09-21
thanks, trying it out now... even tho you saying accessories>terminal made me feel dumb. cuz i already knew that

---

### Post by Jamessharpshooter on 2008-09-21
the first  command didn't fix it... it turned my screen resolution to 800x600 when its supposed to be 1280x1024. i fixed the reolution, but now am going to try the older command.

---

### Post by Jamessharpshooter on 2008-09-21
no go

---

### Post by markbuntu on 2008-09-21
Try the first part of my guide here for basic sound troubleshooting:


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by Jamessharpshooter on 2008-09-26
I FIXED THE PROBLEM MYSELF! When i was fooling around the first day i had mint, i played with the sound settings. I reinstalled Mint and everything works fine!

---

