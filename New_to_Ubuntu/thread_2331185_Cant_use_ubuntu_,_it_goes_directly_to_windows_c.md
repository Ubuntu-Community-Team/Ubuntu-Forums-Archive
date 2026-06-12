---
title: "Cant use ubuntu , it goes directly to windows :c"
date: 2016-07-19
forum: New to Ubuntu
---

### Post by nubu22 on 2016-07-19
I need your help guys . I have an Acer laptop that already have windows 10 preinstalled . I wanted to use ubuntu and installed it with its partitions, but when i reboot i cant see the screens that allows me which operation system i want to start.

I have use boot -repair and this is the result :

[http://paste2.org/cbzOCJft](http://paste2.org/cbzOCJft)

Hope you guys can help me with this , because i really want to have ubuntu .

Thank you so much

---

### Post by oldfred on 2016-07-19
Acer has a unique requirement where you have to in UEFI set (at least temporarily) a supervisory password and enable "trust" on the grub/ubuntu .efi boot files in the ESP.

       Acer Trust Settings - details:
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)

Some older threads mention downgradeing UEFI to an older version to make it work. Newer ones now say to upgrade to newest UEFI and that now works.
So make sure you also have newest UEFI from Acer for your system.

---

### Post by mook765 on 2016-07-25
In line No 6 off your screenshotit says "=> No boot loader is installed in the MBR of /dev/sda."
Wich install-option did you choose when installing ubuntu?

---

### Post by oldfred on 2016-07-25
@mmok765
With UEFI, you do not have a boot loader in the gpt protective MBR. 
The gpt protective MBR has only one partition entry that says drive is gpt so older partition tools that only look in a MBR at least see drive is partitioned.

---

### Post by mook765 on 2016-07-25
@oldfred
Thanks for advice...
I bookmarked the link and will read a lot next days...

---

