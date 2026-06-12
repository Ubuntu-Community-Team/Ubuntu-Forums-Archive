---
title: "Webcamstudio modprobe fails causing boot to hang"
date: 2012-01-14
forum: New to Ubuntu
---

### Post by dadsy on 2012-01-14
After upgrading from 10.10 to 11.04 without too many dramas (I couldn't get the gnome-theme-icon package but got around that), upon the reboot it hangs after showing
```
install: cannot stat `webcamstudio.ko': No such file or directory
make: *** [install] Error 1

 * Modprobe webcamstudio failed. Please use 'dmesg' to find out why.
```
The vboxdrv modprobe also fails but it gets past that.
Everything I've found refers to problems with the 2.6.38-9 Kernel but I'm using 2.6.38-13 (other users say their problem was fixed by installing the 2.6.38-11 kernel).

Has anyone got any ideas before I go for a clean install?

---

### Post by dadsy on 2012-01-17
I managed to remove webcamstudio and move onto the next problem, boot hanging at check battery state. 
I removed webcamstudio by 
```
sudo apt-get remove webcamstudio
```
For the check battery state, after mucking around with reinstalling nvidia drivers, I came across some text saying 
```
 kernel source for this kernel does not seem to be installed
```
I ran 
```
 sudo apt-get install linux-headers-(insert kernel version here)
```
I then rebooted and have got a working system. There's still a few bugs but I'll get to them later.

---

