---
title: "ATI Radeon 7870 problem"
date: 2013-03-06
forum: New to Ubuntu
---

### Post by Ary Angeli Maynart on 2013-03-06
**Hardware:**
MB: Asus M2N68-AM PLUS (Nvidia Chipset)
PROC: Phenom X3 720 BE
MEM: 2x 2GB Kingstom
VGA: ATI Radeon Saphire 7870 2GB DDR3
Wireless: Ralink 3060
Pci Snd: CMPCI

**Ubuntu version:**
Ubuntu 12.10 Quantal

**Problem:**
Video is very slow. When I drag a window from one side to the other I see the trail formed by the window.
I found that the problem could be drivers. Searching on google and some forums, I found this: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
and this:
[http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide)
The driver used was downloaded directly from ATI
[http://www2.ati.com/drivers/linux/amd-driver-installer-catalyst-13.1-linux-x86.x86_64.zip](http://www2.ati.com/drivers/linux/amd-driver-installer-catalyst-13.1-linux-x86.x86_64.zip)


To make sure I was doing it right, I copied the tutorial in a txt, ctrl alt F1 and did everything by text mode.
During the process there were no errors.
When I generated the xorg, rebooted the computer and typed:
**$ fglrxinfo**
Returned an error: (bad request).
When trying to load the module manually:
**$ modprobe fglrx**
Module not found.
I looked into / etc / modprobe.d / blacklist-local.conf if the card was not in the blacklist, but I did not find neither the file.
I checked the settings in xorg.conf and everything was correct.
**$ lsmod**
Fglrx Does not appear in the list.


How do I solve this problem?


**Note:** I noticed that the performance of the system is very slow in relation to my hardware configuration. I want to believe that this is just because of the problem with the video card, but only solving to know for sure.

---

### Post by kclark on 2013-03-06
Just a shot in the dark here but I had similar problems to that + xorg was constantly crashing.  I reseated the video card and nothing.  Then I tried moving it to another PCIx slot and it seemed to have solved all of my problems.  Might not work, but it's an easy step to try :D

---

### Post by Ary Angeli Maynart on 2013-03-06
I only have 1 PCIx Slot.

---

### Post by Ary Angeli Maynart on 2013-03-11
It worked.
Updated the headers and installed the driver in recovery mode.
Remember that in recovery mode had to give a [code] mount-w-o remount / [/ code] to be able to be allowed to take the escrita.Para who doubt who is having the same problem, follow the steps below to x64 :


[b] Download packages compilation [/ b]
[code] sudo apt-get install build-essential cdbs dh-dh-make execstack modaliases dkms linux-headers-generic lib32gcc1 [/ code]


[b] Update the headers [/ b]
[code] sudo apt-get install linux-headers-`uname-r` [/ code]


[b] Download the driver from ATI site [/ b]
[url] http://www2.ati.com/drivers/linux/amd-driver-installer-catalyst-13.1-linux-x86.x86_64.zip [/ url]


[b] Unpack the driver in the Downloads folder (or wherever you want) [/ b]
Right extract here.


[b] Open the terminal and enter the folder where you unzipped the file and give it execute permissions: [/ b]
[code] chmod x amd-driver-installer-catalyst-13.1-linux-x86.x86_64.run [/ code]


[b] Now contrua packages. deb [/ b]
[code] sudo sh ./amd-driver-installer-catalyst-13.1-linux-x86.x86_64.run - buildpkg Ubuntu / quantal [/ code]


[b] restart recovery mode [/ b]
Advanced Options - Recovery Mode


[b] Reassemble units to be writable [/ b]
mount-w-o remount /


[b] Install the package [/ b]
sudo dpkg-i fglrx *. deb [/ code]


Gere Xorg:
[code] sudo amdconfig - initial-f [/ code]


restart
[code] sudo reboot [/ code]


Enjoy ......!!!

---

