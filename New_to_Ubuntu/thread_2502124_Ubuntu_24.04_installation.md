---
title: "Ubuntu 24.04 installation"
date: 2024-11-01
forum: New to Ubuntu
---

### Post by planemad on 2024-11-01
Im trying to install to 2nd usb drive. i got a fair way though the installation. then it stopped here..(attachment)
If anyone knows why that is that would be great. thank you.

---

### Post by grahammechanical on 2024-11-02
How do you know it stopped? Did the blue bars stop? They slow down and speed up and sometimes they stop. USB is comparatively slow. If I remember correctly, stuff is downloaded from the internet repositories. It has to be stored somewhere. It seems to be stored in a temporary file (tmp8fi_91bu in your case). The process has stopped while trying to extract the data in that file. Why?

Did not wait long enough? System memory low? Size of USB memory too small? I do know from my own recent experience that installation is slow. Even to a NVME drive. I am guessing that a change in method is being used. 

Have System Monitor open and watch the Resources page. On my system with 16GB RAM I have seen almost 4GB used as cache memory. And at times during the process there has been very little CPU activity from the 8 cores.

Regards

---

### Post by planemad on 2024-11-02
Thanks for the reply. Yes, lots of going on, the blue lines, CPU and memory very busy.i waited 2hrs , both my laptops stuck at same command, (surface pro 5,8gb ram, xps9530,16gb ram) no progress after[ extracting image from tmp/mount. ]

---

### Post by deadflowr on 2024-11-02
1 hr feels long.

Did it ever finish?

---

### Post by planemad on 2024-11-03
No. Same result in 2 fairly high spec tho old laptops.
O well. I've tried for a month.

---

### Post by ajgreeny on 2024-11-03
Is the USB drive USB-2 or USB-3 and is the cable that attaches it rated for version 2 or 3?

Version 2 will always be slow both to install and then to run.

---

### Post by planemad on 2024-11-03
Usb 3 . Straight into usb3 port (XPS) or powered USB 3 hub(surface pro)I just tried another distro, more lightweight. The 128gb Kingston became unmounted at 11% of the installation every time. I'm totally new to Linux. I'm seeing a pattern. 2 reasonable laptops. Same or similar problem on both on 2 distros. 
I think the problem may be lack of power to the USB hubs

---

### Post by ajgreeny on 2024-11-04
It could also be simply a bad USB drive that you are using with the installer on it.

Try with another USB stick to install as a trial.

However I see you gave marked this as solved so maybe I'm too late!

---

### Post by lucant on 2024-11-04
Try downloading another iso via torrent.

---

