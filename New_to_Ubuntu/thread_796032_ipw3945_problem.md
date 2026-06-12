---
title: "ipw3945 problem"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by anarki007 on 2008-05-16
Hello, i need some help over here,
 i got a wireless bug after upgrading to kubuntu 8.04, kernel 2.6.24-17-generic, I cant connect throw wireless or even see the wireless, i follow some threads in many forums and nothing working
 my wireless card driver is ipw3945 (using hp pavilion dv2775cc)
 i reinstalled the driver and done alot of works at the last 3 days please some one help me.
 Thanks

---

### Post by hermes0710 on 2008-05-16
Have you tried the linux-backport-modules package?

---

### Post by anarki007 on 2008-05-16
trying it now, any program can help me out ?

---

### Post by hermes0710 on 2008-05-16
Run synaptic package manager (System>Administration>Synaptic Package Manager) and search for it (the package has also a version on its name reflecting your kernel version so don't try to find it exactly as i said. It will be something like : linux-backport-modules-2.6????. Just Search in synaptics by **Name** and type "**backport**" as a mask)

---

### Post by anarki007 on 2008-05-16
dosent work with that package too, btw i tryed to reinstall kubuntu 8.02 fresh installation.

---

### Post by hermes0710 on 2008-05-16
Can you post the output of "dmesg" command?

---

### Post by anarki007 on 2008-05-16
ok this is it

---

### Post by hermes0710 on 2008-05-16
It seems to be a kernel bug:

[https://lists.ubuntu.com/archives/kernel-bugs/2008-April/035291.html]("https://lists.ubuntu.com/archives/kernel-bugs/2008-April/035291.html")

As you can see in the above link, installing the kernel that 7.10 had you will be fine

---

### Post by anarki007 on 2008-05-16
ok it was working good on kernel 2.6.24-14-generic, i tryed to reinstall the driver but also i got nothing, Thanks anyway for your Time :)

---

### Post by hermes0710 on 2008-05-16
The guy in the posted url installed another kernel, not the one shipped with hardy... I am not refering to the driver but to the kernel

---

### Post by anarki007 on 2008-05-16
well i'm a new user, can u tell me if i understand right or wrong, should i reinstall kubuntu 7 or reinstall older kernal , and if your answer is reinstall older kernal can u explane how or link a page that do. thanks

---

### Post by hermes0710 on 2008-05-16
I'll try to find a "how to" that will help you through the process. My answer is to install previous kernel version not kubuntu.

---

### Post by anarki007 on 2008-05-16
OMG it works now i found a very good thread that helps me alot :)
just add iwl3945 into etc/modprobe.d and type in it 
alias wlan0 iwl3945
options iwl3945 disable_hw_scan=1

---

### Post by hermes0710 on 2008-05-16
Great, cause what i've found for downgrading the kernel was far away from tutorials!

---

### Post by anarki007 on 2008-05-16
btw i want to get some practice in the terminal commands, can u help me find a good tutorial to start with ?

---

### Post by anarki007 on 2008-05-16
and about the HP quick touch buttons dose it work with u ? also fingerprint

---

### Post by hermes0710 on 2008-05-16
The touch buttons yes. Fingerprint not available in my model :)

---

### Post by anarki007 on 2008-05-16
when u press (mute) button dose it change to red color?

---

### Post by hermes0710 on 2008-05-16
No, but it mutes accordingly

---

### Post by Bernardo1966 on 2008-07-14
> **anarki007 said:**
> OMG it works now i found a very good thread that helps me alot :)
just add iwl3945 into etc/modprobe.d and type in it 
alias wlan0 iwl3945
options iwl3945 disable_hw_scan=1

HELLO !!!

I'm not a total beginner as Linux user, however there are some informations I can not process entirely.

I've a Dell Latitude D520 with an Intel Wireless card IPW3945.
**I used to run Ubuntu 7.10** in order to connect with wi-fi card as well a broadband dielled up connection (Mobile CDMA) which is today my main internet connection. As the best way to use it was with KPPP, **I switched from Ubuntu to Kubuntu 8.10 Hardy Heron** to get familiar with KDE as well.

After long trials I detected the problem might be with the card driver or something like it.
[B]I found .DEB packages in DEBIAN repositories: ipw3945-source and ipw3945d. I installed them and nothing changed.
[/B]

I found and followed today these tips from you guys but my case seems to be a bit different.

This page shows an error in wi-fi card detection / handling:
[https://lists.ubuntu.com/archives/kernel-bugs/2008-April/035291.html](https://lists.ubuntu.com/archives/kernel-bugs/2008-April/035291.html)

My case is:
bernardo@D520:~$ dmesg |grep -i 3945
[   29.795136] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   29.795143] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   29.795351] iwl3945: **Detected Intel PRO/Wireless 3945ABG Network Connection**
[   31.926030] iwl3945: **Tunable channels: 11 802.11bg, 13 802.11a channels**
[   31.934969] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[ 5956.705993] iwl3945: Radio Frequency Kill Switch is On:
bernardo@D520:~$ less /etc/modprobe.d/
/etc/modprobe.d/ is a directory
bernardo@D520:~$ ls /etc/modprobe.d/
aliases       blacklist-framebuffer  ipw3945d           options
alsa-base     blacklist-modem        isapnp             toshiba_acpi.modprobe
arch          blacklist-oss          libsane
arch-aliases  blacklist-watchdog     lrm-video
blacklist     fuse                   nvidia-kernel-nkc
bernardo@D520:~$ cd /etc/modprobe.d/
bernardo@D520:/etc/modprobe.d$ less ipw3945d
bernardo@D520:/etc/modprobe.d$ man ln
bernardo@D520:/etc/modprobe.d$ info coreutils 'ln information'
bernardo@D520:/etc/modprobe.d$ info ln
bernardo@D520:/etc/modprobe.d$ uname -r
2.6.24-19-generic
bernardo@D520:/etc/modprobe.d$ cat ipw3945d
install ipw3945 modprobe --ignore-install ipw3945 && /etc/init.d/ipw3945d modprobe-start
remove  ipw3945 /etc/init.d/ipw3945d modprobe-stop && modprobe -r --ignore-remove ipw3945
bernardo@D520:/etc/modprobe.d$    


**I probably could downgrade the kernel, but if there were a diferent solution,** like the one presented by ANARKI007,[B] I'd prefer it. Even more if I could not follow the upgrades in kernel evolution.
.
.
QUESTIONS:[/B]
How do I exactly shall proceed in order to make it work?

by 
alias wlan0 iwl3945
options iwl3945 disable_hw_scan=1
Do you reffer to a symbolic / hard link ? if so, Whats the syntax for the LN command proposed above?

In Ubuntu 7.10 I could press FN+F2 to turn radio on/of. If this key combination comes back to life is my wi-fi board back to work as well???

Thanks
Bernardo

---

