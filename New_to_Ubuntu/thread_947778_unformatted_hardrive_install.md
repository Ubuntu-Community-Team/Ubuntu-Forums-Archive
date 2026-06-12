---
title: "unformatted hardrive install"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by nkingcade on 2008-10-14
I have a new machine. it has a 1 terabyte hard drive that is unformatted. when attempting to install from a cd, I get dumped into 'initramfs'. I suspect this is because the disk can not be mounted and really does not exist in a useable form by the install software. Would it be possible for someone to point out to me what the problem is and provide a solution. Thanks in advance.

---

### Post by LowSky on 2008-10-14
```
BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built in commands.

(initramfs)_
```

is this the actual code your getting?
this thread might help

[http://ubuntuforums.org/showthread.php?t=591746&page=2](http://ubuntuforums.org/showthread.php?t=591746&page=2)

---

### Post by Keen101 on 2008-10-14
I don't really know why you are having problems, but you could try and see what your hard disk looks like in the gparted Live-CD.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by nkingcade on 2008-10-14
yes. the drive is unformatted. Where is the debug file located?

---

### Post by nkingcade on 2008-10-14
All,

I failed to mention that I have a "64" bit processor in this box. I "was" attempting to load the 32 bit version of desktop on the machine. I don't believe this is a good thing. In any event, I'm currently in the process of downloading the proper version of the o/s and will start the install when I have that done. Thanks for the responses.

---

### Post by jamesrfla on 2008-10-14
You should be able to run a 32 bit version on a 64 bit computer. When you get the options to install Ubunut or boot Ubuntu press F6 and hit F6 again I think. You should get a few options like acpi=off. Select the first three options using enter then press b to boot. Also if you have any PCI video cards you want to take then out. You can put then in later after the install. Let me know if this works.

---

### Post by nkingcade on 2008-10-14
I will give it a shot and let you know. thanks.

---

### Post by LowSky on 2008-10-14
I can solve you problem, if you built your own PC which I'm assuming.

Is the CD/DVD ROM Drive an IDE cable (normal the 1.5 inch think flat grey kind), if it is make sure to use a 80 Pin cable and not a 40 Pin cable. A 80 Pin is much smoother than a 40Pin one. For some Reason Every version of Ubuntu past 7.04 has this issue, at least for me.

Hope this helped

---

### Post by nkingcade on 2008-10-15
My thanks to everyone, particularly Jamesrfla. I downloaded and burned the 64 bit version of the o/s and everything worked fine. I'm having a little problem with the wireless wep key, however, the o/s is doing just fine. Thanks everyone for your assistance and hopefully I can help someone at some  point.

---

### Post by hyper_ch on 2008-10-15
you may want to use WICD as network manager. I have found it superior to any default ones on Ubuntu: [http://wicd.sourceforge.net](http://wicd.sourceforge.net) --> Add their Ubuntu repository and then install it.

---

