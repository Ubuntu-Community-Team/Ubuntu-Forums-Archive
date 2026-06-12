---
title: "New to Ubuntu - installed, computer won't boot -"
date: 2016-02-15
forum: New to Ubuntu
---

### Post by michael351 on 2016-02-15
I downloaded and installed Ubuntu 32 bit (14.04) to an old Pentium machine that has Windows XP installed.
After installing normally, reboot produced "normal.mod" not found and put me into grub rescue.

I loaded Ubuntu - live and ran boot-repair:

here is the link to the report:

[http://paste.ubuntu.com/15085192](http://paste.ubuntu.com/15085192)

I tried much what was suggested on-line, but still have this error. 

Thanks for helping

---

### Post by yancek on 2016-02-15
Can you boot the installation medium and mount sda6 and look in the /boot/grub/i386-pc directory to see if all the files, including normal.mod are there?  Some suggestions at the link below.

[http://unix.stackexchange.com/questions/70538/grub-error-file-grub-i386-pc-normal-mod-not-found](http://unix.stackexchange.com/questions/70538/grub-error-file-grub-i386-pc-normal-mod-not-found)

---

### Post by michael351 on 2016-02-15
Yes - when I mount sda6 (via the live CD) I see the i386-pc directory and all of the files including normal.mod 
I'll review your link - thanks

---

### Post by michael351 on 2016-02-15
I followed the suggestions in the link you provided. The commands worked without error, but when I rebooted - same problem: "error: file 'grub/i386-pc/normal.mod' not found".

I also tried these steps:

[http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd#.Uz6B0vllHuM](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd#.Uz6B0vllHuM)

and each step proceeded without error. But when I rebooted - no grub ... normal.mod not found.
At this point I have no idea where grub is looking for that file. It's in /boot/grub/i386-pc in the correct partition.

---

