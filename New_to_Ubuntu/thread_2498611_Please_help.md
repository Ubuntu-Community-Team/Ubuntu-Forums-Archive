---
title: "Please help"
date: 2024-06-21
forum: New to Ubuntu
---

### Post by livingwithoutlying on 2024-06-21
[COLOR=#202124][FONT=Roboto]Hello everyone. I have a macbook air with Xubuntu and I downloaded too much from the internet and now I get GNU GRUB version 2.06! Can someone help me? Thank you very much![/FONT][/COLOR]

---

### Post by yancek on 2024-06-21
Not until you post some useful information.  Has your Xubuntu been working without problem for some time?  Did you get a message indicating that your / (root) filesystem partition was full?  Do you have a 'live' LInux such as the USB/DVD you used to install Xubuntu?  If you have gparted on your USB/DVD or some other partition manager, you should be able to see how full each partition is so do that first.  Or you can try to mount the partition from the 'live' Linux and get that information with either df -h or du -h commands.  You should run one of these commands on a regular basis if you are doing a lot of downloads to avoid the problem in the future.

---

### Post by grahammechanical on 2024-06-21
For those who do not know, GNU GRUB version 2.06 is a bootloader. The standard bootloader used on Ubuntu and its flavours such as Xubuntu. There are two reasons why we see GNU GRUB as we load the operating system. 

1) We are booting more than one operating system. Grub will show us a menu from which we choose an operating system.

2) The Grub bootloader cannot find the files that it needs to use to load the operating system.

Item 2) is something to think about in my opinion.

Regards

---

### Post by Impavidus on 2024-06-22
A third reason why grub might appear is that you may have configured it to be visible. You would have known that if you did so consciously, but some tools affecting grub (boot-repair being one) may reconfigure grub too.

What version of Xubuntu is on that computer?

---

