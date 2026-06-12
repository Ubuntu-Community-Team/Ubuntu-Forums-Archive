---
title: "AMDGPU problems"
date: 2018-01-02
forum: New to Ubuntu
---

### Post by oldbikerpete on 2018-01-02
I have a similar system problem to barbera85, although the symptoms are different. I've tried installing Ubuntu Desktop AMD64 in both 17.10 and 16.04.3  versions.
I have been using and writing C/C++ programs for Linux since Version 0.95 which had to be loaded from about 20 floppy disks, so I'm not new to either computers or Linux but I am new to Ubuntu and to this forum, thanks for the add.

I have built the following system.
CPU:     AMD A10 9700   (10 cores, 4CPU + 6GPU)
RAM:     Kingston ValueRAM KVR24N17S8/4 (2 off 4Gb)
MB:      MSI AX370 Gaming Carbon (has video in AX370 chipset on MB + GPU in CPU)
POWER:   Corsair CMPSU-HX850i (850W Gold)
HDD:     Samsung 850 EVO MZ-75E250BW   (250Gb SATA 3 SSD)
DVD:     LG DVD RW-SATA
VIDEO:   Gigabyte NVIDIA N710   PCI-E x8 (in a PCI-E x4 slot - this is the console)
EXTRA GPU:   MSI 8G RX580 Armor OC PCI-E VGA card (in x16 slot)

In both cases, I installed Ubuntu, did 'sudo apt update',  'sudo apt upgrade', 'apt install joe', 'apt install cifs-tools'
In the latest reload of an Ubuntu image, 'Xorg-Xserver-video-amdgpu'  for the RX580 has NOT been installed, nor has 'bumblebee' for
the NVIDIA card. Seems to make no difference whether they are installed or not.

The machine needs to run 24x365 to do its job but hangs after as little as 10 minutes or sometimes several hours.
When it hangs, the keyboard and mouse are both unresponsive, hitting 'NumLock' on the keyboard shows no
change in the relevant status LED, the HDD activity light, however is blinking regularly (like a car indicator).
Sometimes I've optimistically left it running overnight to find next morning that all the above applies except that the HDD light and the display are both off.

The same symptoms occur if I take  RX580 gpu card out of the system.

This morning, about 2 hours ago, I found it dead as above but immediately after I rebooted, a window reporting 'System Internal error' briefly appeared then disappeared and a few seconds later appeared again for long enough for me to follow the error reporting procedure.

I have a sneaking suspicion that the problem lies in drivers for the very new AX370 chipset.  !!!

I'm about the try installing the 17.10 Server version, but the image size suggests that X is not included but I do need the multiple windows that X provides.

Any ideas?

---

### Post by QIII on 2018-01-02
Moved to its own thread from [https://ubuntuforums.org/showthread.php?t=2381605](https://ubuntuforums.org/showthread.php?t=2381605)

Please don't horn in on the threads of others.  While it may seem that your issues are similar, the root cause may be entirely different.  When a thread is hijacked, it quickly becomes confusing for the OP, for the other poster and everyone who is trying to help.

Each person gets individual attention on the Ubuntu Forums.  Please allow those who start threads to get individual support like you should now expect in this thread.

---

### Post by oldbikerpete on 2018-01-02
Point taken.    

I should have pointed out above that the problem occurs even if the RX580 GPU card is removed.

Perhaps the thread should have a different title?

---

