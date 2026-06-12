---
title: "!Help Needed! Ubuntu won't start on HP Windows 8"
date: 2013-05-29
forum: New to Ubuntu
---

### Post by Ishmam on 2013-05-29
Recently I bought a new laptop form HP. It had Windows 8 pre-installed. I get tired of windows 8 after 2 months, and i decide to look for something new. I come across Ubuntu. It looked fantastic. So i go ahead to install it, following the instructions for windows 8 UEFI. To my surprise, a black screen appears, which looks like this:

[IMG]http://s22.postimg.org/lcqc0ks6p/DSC02016.jpg[/IMG]

But i can still boot to Win 8
Now, I have disabled secure boot, and enabled Legacy support alongside UEFI (which cant be disabled for me). No problems occured during installation. I even tried the bootable CD method, but it all failed. I have read through countless amounts of posts, all of which weren't helpful. They all lead into saying that Ubuntu 13.04 has an EFI installation, and just disable secure boot. That didn't do the job for me. And the laptop is a REALLY good laptop, with Nvidia 680 graphics and a quad core processor at 3.4Ghz, and it would be nice to expeience Ubuntu on High End fronts.

It worked fine on my old laptop, which was 7 years old (that is how i am typing/ed this :] ). But with only 2gb of ram and a crappy processor i cant do much, and it would be great if i could get help setting up Ubuntu on a pre-installed, perma-uefi windows 8.

---

### Post by overdrank on 2013-05-29
Moved to Absolute Beginners Section. :)

---

### Post by mansonfan78 on 2013-05-29
Okay, if I understand you correctly you installed Ubuntu from within Windows (a wubi install)?  When you start your computer do you first see a screen that allows to choose Windows or Ubuntu, and if you choose Windows if boots fine but if you choose Ubuntu you see the screen you posted?

---

### Post by fantab on 2013-05-30
WUBI has problems running in Windows 8. This is the reason perhaps, why WUBI was dropped from 13.04. That is your problem. Even if it ran well earlier Windows8 updates will break it. 

Consider Removing it completely from Windows and re-install Ubuntu as 'true' dual-boot in its own partition. Read: [https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation) to safely remove WUBI. But first BACKUP any important DATA that you may have saved there. Reboot Widnows8 a couple of times to ensure that there are no problems with Windows. Windows 8 'hibernates' secretly rather than 'shut down' make sure you 'shut it down'. 

If you decide on 'true' dual-boot then let us know and we'll help you with it.

---

### Post by mastablasta on 2013-05-30
or you can install it in virtualbox if you just want to give it a try: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

btw ubuntu is an Operating system so to install it you either need to overwrite your current OS or install next two it as two operating systems can not run at the same time (unless you use virtualisaiton)

---

