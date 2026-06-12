---
title: "wolvix usb boot help"
date: 2008-06-21
forum: Other OS Talk
---

### Post by waspbr on 2008-06-21
Hello everyone

Sorry for posting this here, but I am having problems with the wolvix forum and I guessed some wolvix users may come by here.

Anyway, I was searching for a distro I could use in my new 8 GB USB stick, I thought it would be cool to be able to carry a portable linux around, and since it is USB I though I'd use wolvix which from what I've heard is pretty fast. 

SO I downloaded the new CD, ran it on my desktop and it was fine, I tried the USB isntall script and rebooted, my bios would not boot the pen(flash) drive, So I googled it a little and saw that some people recommended the hdd install, I tried the frugal version and RESULT, I could boot from the USB.But there were quite a few packages missing from the full install, so I thought since I had 8 Gb I might as well do the full install. 

So I went on to partition the drive , yes I actually made a swap partition, 2 Gb big and the rest was left for the root directory, the order of the partitions was sda1 and sda2 respectively.

So I installed and rebooted, the good news was that my Bios didn't mind it, so grub went on and I selected the partition, then in the middle of the bootup I get something like (may not be exact words):

Kernel Panic: VFS: Unable to mount root fs on unknown-block(0,0), redefine "root=" 


Since I had disconnect my harddrives before doing all of the above at grub it said it was booting hd0,1, and root was defined as root=/dev/sda2

but it did not recognized sda2 as a root, any pointers?

---

