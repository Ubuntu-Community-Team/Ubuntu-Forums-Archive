---
title: "Help Installing Ubuntu on to HP Proliant ML310"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by rev-pizza on 2008-09-28
I'm breaking free from Messieurs Gates and Jobs and need some help.

Purchased a Proliant ML 310 Desktop, pentium 4 with no OS.  System has two hard drives (IDE1 and IDE2).  Began the installation and received Grub Error 2 when I tryed to reboot without the CD.  Went through several threads that talked about adjusting the BIOS/RAIDS which was a bit over my head.  

I tryed a manual intallation and partitioned on IDE1 with a "/", "/swap" and "/home".  It would not let me partition the second drive.  Still getting grub error 2.

Any advice would be much appreciated.

Thanks

---

### Post by Keen101 on 2008-09-29
hmm.... strange....

It sounds like grub can't find Ubuntu. This is probably happening because GRUB installed on the wrong drive, or something weird. Try installing with only one drive first.

You can also use GPARTED live-cd to double check the Partitions/partition the second drive. The gparted live-cd is a very nice GUI partition editor.

If you need to restore or install GRUB on the other hard drive... try using the SUPER GRUB DISK.

---

### Post by rev-pizza on 2008-09-29
Thanks.  Even stranger, I went through the guided installation after writing the first thread.  I'm now getting error 21.  I'm downloading super grub now.  I'm going to give this a try and see what happens.

---

### Post by iponeverything on 2008-09-29
Try installing grub from the command line so that you see if it prints anything to std out.

See the second post is this thread for how:

[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

---

### Post by luvdemheels on 2008-10-06
You are havin the same problem I have. The problem is the server has an integrated ultra ata ide raid controller. You need a driver for when you install as I do.

If you find anything update this thread as I will also.

---

