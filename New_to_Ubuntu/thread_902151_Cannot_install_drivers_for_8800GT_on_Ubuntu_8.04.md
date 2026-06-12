---
title: "Cannot install drivers for 8800GT on Ubuntu 8.04"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by csk1007 on 2008-08-27
I went to this forum to install the drivers.
[http://ubuntuforums.org/showthread.php?p=4119312](http://ubuntuforums.org/showthread.php?p=4119312)

I tried installing the drivers that way, I then tried installing the suggested way on the nVidia site.

Either way, my screen resolution is stuck on "low" mode (800x600) when it should be 1680x1050.

The drivers are "enabled" in the drivers manager, but its still not working. Also, the OS boots into BusyBox 1.1.3 3 out of 4 boots. I have to boot the computer multiple times to get to actually boot. I think this is a driver issue as well.

Any clues? I've tried installing them multiple ways, if anyone can suggest something else, that'd be swell.

---

### Post by kpkeerthi on 2008-08-27
Install using envy
[https://launchpad.net/envy](https://launchpad.net/envy)

---

### Post by C.S.Cameron on 2008-08-27
My 8800GT seems to work pretty good in 8.04 just using the hardware drivers manager.

---

### Post by csk1007 on 2008-08-27
Thanks, none of those worked.

Still having problems, still keeps booting to busybox 3/4 boots.

---

### Post by Crafty Kisses on 2008-08-27
Remove any drivers you have installed, then try installing them with Envy.

You can reconfigure your X by doing the following:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by knattlhuber on 2008-08-27
I found these instructions quite useful:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")
[https://help.ubuntu.com/community/NvidiaManual]("https://help.ubuntu.com/community/NvidiaManual")

---

### Post by csk1007 on 2008-08-27
Alright,

So when I tried out Envy, it seemed like it installed OK. It has some messages, but I am not very familiar with Linux, so I'm not sure what they meant.

Anyways, when I tried to install the nVidia Drivers, it gave me an error message, saying to check /var/log/envy-installer.log

So, I went to tty1, typed sudo nano /var/log/envy-installer.log

And it said "ENVY ERROR: Your operating System does not seem to be supported by Envy"

I just got the regular vanilla Ubuntu, from Ubuntu.com/downloads...

So, I still have no clue what's going on. And it still boots to BusyBox almost everytime. It's REALLY annoying having to restart the computer 4 or 5 times to get Ubuntu to load.

---

