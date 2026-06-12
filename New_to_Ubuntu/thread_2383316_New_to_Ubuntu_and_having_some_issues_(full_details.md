---
title: "New to Ubuntu and having some issues (full details below)"
date: 2018-01-23
forum: New to Ubuntu
---

### Post by marcus314 on 2018-01-23
Hi everyone, my name is **Marco **and I'm new to Ubuntu. Recently I got an old computer my father stopped using. It is an HP Pavilion CPU model a6803w. He gave me the computer because he got an All In One HP computer and because Windows 7 was not booting anymore. After trying to fix it and not succeeding I asked myself: why don't I install another OS like Ubuntu to try something new? So I formatted the PC using the infamous DBAN and installed Ubuntu 17.10, all using a USB stick. At first glance I thought it would be easy to use Ubuntu as I decided to install it because of **ease of use, safety, and the most important: IT IS FREE**. So I installed Ubuntu using the USB stick and now I'm writing this post using the Ubuntu OS. However, I've experienced many problems like the following:
[LIST=1]
[*]The login loop.
[*]Several features are not working: like trying to change the background wallpaper, accessing the system's Settings, and so on; and sometimes the system would freeze abruptly. The freezing also happens sometimes when I reboot the computer using the terminal.
[*]Sometimes when booting and after logging on the system freezes/crashes.
[/LIST]
I would like to know if there's anything I could do to fix these issues. If so, what cautions should I take in the future? Should I format my PC? I would appreciate your answers. Thanks.

---

### Post by ajgreeny on 2018-01-23
Give us details of that HP hardware by opening a terminal and typing ```
inxi -F
``` then copy the output back here using **Code-Tags** for that output. See my signature below for a **How-to**

---

### Post by haplorrhine on 2018-01-24
P.S. Various utilities/commands output similar hardware information.

---

### Post by mastablasta on 2018-01-25
> **marcus314 said:**
>  If so, what cautions should I take in the future? Should I format my PC? 

it could be faulty hardware (hard disk).

---

### Post by leunam12 on 2018-01-25
Open the disks utility and check the SMART data for Hard disk problems such as Seek Error Rate; Read Error Rate, Reported Uncorrectable, reallocated sectors and sectors pending reallocation, etc.

---

