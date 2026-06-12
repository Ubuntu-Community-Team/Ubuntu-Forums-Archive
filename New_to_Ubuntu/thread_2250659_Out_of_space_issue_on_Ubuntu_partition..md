---
title: "Out of space issue on Ubuntu partition."
date: 2014-10-30
forum: New to Ubuntu
---

### Post by rohan6 on 2014-10-30
I recently dual booted Ubuntu with Windows 8.1. I used the option "Install alongside with Windows " and did not use a separate partition.

Now I am facing problem with respect to memory, even though I have about 80Gb left on C: (my only drive) when I use Ubuntu it shows warning messages that I only have 700 Mb left on my machine ...

IMAGES:

[http://postimg.org/image/s3n9tuvx5/](http://postimg.org/image/s3n9tuvx5/)
[http://postimg.org/image/z8532w36h/](http://postimg.org/image/z8532w36h/)

I use LinuxDC++ heavily and quite regularly and this poses some serious problems for me as the downloads stop midway. I have cleared away the unfinished downloads from .dc++ folder but still there is a space problem.

Can someone please clarify what to do ??

---

### Post by Bucky Ball on 2014-10-30
Welcome. If you didn't install Ubuntu to a separate partition then you have not done a dual-boot install, you have done a Wubi install.

Please open Gparted in Ubuntu and take a screenshot of the disk in question so we can see how it is partitioned and setup.

PS: When you say memory you actually mean storage space. Memory refers to the RAM (random access memory). ;)

---

### Post by Impavidus on 2014-10-30
If you installed alongside Windows you did use a separate partition. Your C partition (yes, that's a partition, not a drive, but Windows always confuses the terms) may have 80GB free space, but that is space for Windows. Your Ubuntu system uses the Ubuntu partition (which, in case of wubi, would be a virtual partition). Windows doesn't see the Ubuntu space and Ubuntu sees, but by default doesn't use the Windows space.

And yes, that screenshot mentioned by Bucky Ball may be nice.

---

### Post by grahammechanical on 2014-10-30
Wubi.exe does not work with Windows 8. So, let us assume that this is a true dual boot and that the installer did not allow enough space on the hard drive for your Ubuntu needs. The solution is to resize some partitions.

We must always use Windows tools to defrag Windows and we must do it more than once, making sure that Windows loads each time. And we must use Windows tools to resize Window's partitions (drives, in Microsoft speak). We should also have Windows recovery discs around. And our data in Windows backed up

Then we can use the Linux tool that comes on a Ubuntu live session disc to resize the Ubuntu partition into the newly created unallocated space. Specific advice can be given when we see the partition layout in that requested screen shot. Meanwhile become familiar with partitioning in Ubuntu.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Regards.

---

### Post by Bucky Ball on 2014-10-30
* I have changed the title of the thread to improve your chances of support and for accuracy. Good luck. ;)

---

### Post by rohan6 on 2014-10-31
Thanks for the response! 

Here is the required image
[http://postimg.org/image/dcmut5r6r/](http://postimg.org/image/dcmut5r6r/)

---

### Post by Bucky Ball on 2014-10-31
Well, everything looks fine there, unless I'm missing something. What is the warning message exactly (you might want to provide a screenshot of that) and please use the linux terminology: c: drive is a Win thing and = sda in Linux. ;)

Don't know what's on sda5 in your screenshot, but not much being used there. You could boo from Live media, delete that partition using Gparted, delete the /swap and recreate at the end of the free space and expand your / partition into the rest of the free space you've left. That should give you another 16Gb.

Might work, but don't think that's the issue because, as I say, everything looks alright from your screenshot (I have quadruple checked and still see nothing, but I am pretty busy doing five things). Na, looks fine.

* Which release are you using BTW?

---

