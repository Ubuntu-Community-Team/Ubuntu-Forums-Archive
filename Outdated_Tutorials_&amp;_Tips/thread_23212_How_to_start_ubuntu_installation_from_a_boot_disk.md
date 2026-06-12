---
title: "How to start ubuntu installation from a boot disk"
date: 2005-03-31
forum: Outdated Tutorials &amp; Tips
---

### Post by Doctor Orange on 2005-03-31
I am trying to install Ubuntu on an old compaq to use as a server.

My problem is that this compaq is evil, and I can't change the boot order to boot from the CD Drive. 

From a windows 98 boot disk I can browse the CD.

What should I do to initiate the installation? Which file should I run?

Thanks a lot. :0)

---

### Post by gw90se on 2005-03-31
See if the info in this thread helps [Click Here](http://www.ubuntuforums.org/showthread.php?t=20140&highlight=install+boot+floppy) 

Look down about the 3rd or 4th reply.

---

### Post by Doctor Orange on 2005-04-01
Thanks, that helped a lot :0)

---

### Post by dceddy1 on 2011-08-09
Does anyone have a suggestion for where to find the right boot disk for a Linux OS PC?  The problem that I have is that the PC now won't boot up to get to any sort of prompt needed to enter the boot from a disk command.  The current error message appears as:
 
Several different Journal has aborted messages followed by:

/etc/init.d/rc: 2: /etc/rc$.d/S85urandom: Input/output error
init:  rc-default main process (6229) terminated with status 2
[ 394.369813] Buffer I/O error on devece sda4, logical block 0
[ 394.369902] Buffer I/O error on devece sda4, logical block 786434
[ 394.369973] Buffer I/O error on devece sda4, logical block 786435
[ 394.370043] Buffer I/O error on devece sda4, logical block 786436
[ 394.370126] Buffer I/O error on devece sda4, logical block 786438

After that the cursor just sits there forever no matter what commands we type in.

We haven't been able to start up anything since we lost power last week.  The UPS was connected.

---

### Post by lkraemer on 2011-08-10
If you are interested I have an image of a boot floppy that boots from
the Floppy and transfers the boot to a USB device even if the Computer's
BIOS doesn't support booting from USB.  I got the information from a
website on the internet.....but don't have that site readily available
on this computer.  I'll try to locate that url, and if you want the image
I'll upload or send it.

[http://ubuntuforums.org/showthread.php?t=1705972&highlight=boot+floppy](http://ubuntuforums.org/showthread.php?t=1705972&highlight=boot+floppy)
Posting #4

[http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi?;act=ST;f=17;t=20721](http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi?;act=ST;f=17;t=20721)


Another thing you can try is Plop.
[http://www.plop.at/](http://www.plop.at/)

Either should work.

lk

---

