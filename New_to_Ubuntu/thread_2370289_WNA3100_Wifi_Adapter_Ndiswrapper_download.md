---
title: "WNA3100 Wifi Adapter Ndiswrapper download"
date: 2017-09-01
forum: New to Ubuntu
---

### Post by currymuncher1127 on 2017-09-01
Hello all, I recently just partitioned my hard drive to run Linux, so I am very new to this. When I first got my computer, I also purchased the Netgear 300 WiFi Adapter (WNA3100). When I opened Linux i realized the adapter was not working, so I searched online for while looking for help. I found many threads; however, none of the solutions were working for me. I downloaded Ndiswrapper from here: [https://sourceforge.net/projects/ndiswrapper/files/stable/](https://sourceforge.net/projects/ndiswrapper/files/stable/) 

I downloaded this file on windows onto a flash drive. When I restarted my computer and launched Linux, I opened the file. The instructions said, "You need a recent kernel, at least 2.6.13, with header files for the kernel. Make sure there is a link to the kernel source from the modules directory." Then it told me to use the following command:

```
ls /lib/modules/'uname -r'/build
```

I did this (i replaced uname -r with my actual kernel version) and it gave me a bunch of lines of code. Next, the instructions say to download the latest version of ndiswrapper sources from the files and extract it with the following command:

```
tar zxvf diswrapper-verion.tar.gz
```

I replaced version with 1.61 (the ndiswrapper that I am installing) The following code is the output:

```
tar (child): ndiswrapper-1.61.tar.gz: Cannot open: No such file or directory 
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
```

Can someone please make sense of this all? I am very confused, and I would appreciate as much help as I can get. Thanks all.

---

### Post by johnerin22 on 2017-09-02
you do wrong command, tar **zxvf** diswrapper-verion.tar.gz

try to use: tar **-zxvf** diswrapper-verion.tar.gz

or if you just typo, you are in the wrong directory (based on the error "Cannot open: No such file or directory"),

---

### Post by currymuncher1127 on 2017-09-02
Thank you johnerin22 for responding to my post. I tried your suggestion, but I received the same error. To my understanding, this command is supposed to extract the file, correct? If so, is it possible to just extract it manually in the file system? If so, how would I enter that specific directory?

---

### Post by jeremy31 on 2017-09-02
You should be able to right click on the file on choose extract here

---

### Post by currymuncher1127 on 2017-09-02
Thank you jeremy31, do you happen to know how to access the directory from the terminal after I have extracted the files?

---

### Post by jeremy31 on 2017-09-02
Open the location in file manager and right click in an empty area and choose "Open in terminal"

---

### Post by currymuncher1127 on 2017-09-02
Thank you so much jeremy31, you have been a big help. I only have one more problem, I followed th instructions on this link here to download the driver for my net gear wifi adapter:
[https://ubuntuforums.org/showthread.php?t=1946875&page=4](https://ubuntuforums.org/showthread.php?t=1946875&page=4)

However, when I type the following command in my terminal, nothing happens:
```
sudo modprobe ndiswrspper
```

If I continue by typing **iwconfig**, it says there is no wireless connection. Is there a step I am missing or is this just not the correct driver? (The driver they tell you to use is on page 1)

---

### Post by jeremy31 on 2017-09-02
Just reboot and see if it loads on it's own if it was installed correctly

---

### Post by currymuncher1127 on 2017-09-02
It seems this did not work either, is it possible to just download the driver from the installation CD?

---

### Post by jeremy31 on 2017-09-02
Does the device you have show up in lsusb results as
```
ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
```
If it does, look at [https://ubuntuforums.org/showthread.php?t=2264020&highlight=WNA3100](https://ubuntuforums.org/showthread.php?t=2264020&highlight=WNA3100) as it doesn't work very well even if you can get ndiswrapper to work
I have a TP Link WN722N version 1 150mbps model for a USB backup and is plug and play in Ubuntu 16.04, in Ubuntu 17.04 you have to disable MAC randomization for it to work

---

### Post by kurt18947 on 2017-09-02
Jeremy gives you good advice IMO. If you look in the networking and wireless section, the Netgear WNA3100 has many posts. [Edit:I think the WNDA3100v.x is the problem child.]That is not a good sign, things that work well don't get many posts. Netgear does make a wifi adapter that works well with linux, WNA1100. If you want a source of hardware that has a high likelihood of working without fuss, consider this vendor:

[https://www.thinkpenguin.com/catalog/wireless-networking-gnulinux](https://www.thinkpenguin.com/catalog/wireless-networking-gnulinux)

I have no association with them.

---

### Post by currymuncher1127 on 2017-09-03
It does show up in the results. After trying out the instructions on the link you provided, I am trying to restart my computer, but it is taking an unusuallly longer time. I also had another problem while trying out the instructions. Whenever I type **sudo modprobe ndiswrapper **either nothing happens or the output is **Killing**, is this a problem?

---

