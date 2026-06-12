---
title: "Changing Makefile of latest kernel, then dropped to busybox after reboot"
date: 2015-07-18
forum: New to Ubuntu
---

### Post by Timothy_Leung on 2015-07-18
I have downloaded the latest kernel from git 

I change the EXTRAVERSION field in Makefile to something else (-timothy), then I saved and closed it. 

Run `sudo make` and reboot. After reboot, it seems like I am unable to load the operating system and dropped to busyshell with an alert "dev/dish/uuid/... does not exists" 

I tried to read the log files but the log files aren't there and the shell is pretty limited, I tried to run fdisk or sudo, and it returns command not found. 

Is there any reasons for this?

Thank you so much.

---

### Post by dino99 on 2015-07-18
here is a recent howto
[https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel](https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel)

---

