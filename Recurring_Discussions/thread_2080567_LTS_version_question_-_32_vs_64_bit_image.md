---
title: "LTS version question - 32 vs 64 bit image"
date: 2012-11-04
forum: Recurring Discussions
---

### Post by RH9R on 2012-11-04
Uninformed question: I'm used to the i386 images being the ones to choose for the 32 bit machines. The 64bit versions all seem to have AMD in the file name. Is the 64AMD the right image to use for an intel 64b machine? 
 
The intended destination is for an i5 intel chip on an Asus k55a
 
Many Thanks in advance

---

### Post by westie457 on 2012-11-04
> **RH9R said:**
> Uninformed question: I'm used to the i386 images being the ones to choose for the 32 bit machines. The 64bit versions all seem to have AMD in the file name. Is the 64AMD the right image to use for an intel 64b machine? 
 
The intended destination is for an i5 intel chip on an Asus k55a
 
Many Thanks in advance

Yes the AMD64 is the right one to use on Intel 64-bit machines.

AFAIK the AMD part of the name is used because AMD designed the 64-bit architecture.

---

### Post by uRock on 2012-11-04
> **westie457 said:**
> Yes the AMD64 is the right one to use on Intel 64-bit machines.

AFAIK the AMD part of the name is used because AMD designed the 64-bit architecture.

+1 Use the AMD 64 image.

---

### Post by Abhinav Kumar on 2012-11-04
> **westie457 said:**
> Yes the AMD64 is the right one to use on Intel 64-bit machines.

AFAIK the AMD part of the name is used because AMD designed the 64-bit architecture.
+1 for westie457 .
64 bit OS are made for 64 bit machines. :) Just try it out.

---

### Post by oldfred on 2012-11-04
Moved to Recurring Discussions.

In fact if you have an i-series processor, the motherboard is likely to be UEFI/BIOS. If configured for UEFI you have to use the 64 bit version.

[http://ubuntuforums.org/showthread.php?t=2028717](http://ubuntuforums.org/showthread.php?t=2028717)
Ubuntu 12.10: 32-bit vs. 64-bit Linux Performance
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_3264&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_3264&num=1)
Assuming your hardware is x86_64 capable (basically any modern Intel/AMD CPU) and have at least 2GB of RAM, you really should be running the 64-bit version.
Essentially says if you can use the 64bit kernel you should.April 2011
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1)
[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)
Ubuntu 32-bit, 32-bit PAE, 64-bit Kernel Benchmarks Dec 2009
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)
Linus does not like PAE or 32 bit.
[http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/](http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/)

Many of the old arguements on 64 vs. 32 recommended
[https://bugs.launchpad.net/ubuntu-website-content/+bug/585940](https://bugs.launchpad.net/ubuntu-website-content/+bug/585940)
Why Ubuntu officially suggests 32bit (25% have 32bit systems)
[https://lists.ubuntu.com/archives/ubuntu-devel/2012-April/035088.html](https://lists.ubuntu.com/archives/ubuntu-devel/2012-April/035088.html)
[http://www.techsupportalert.com/content/32-bit-and-64-bit-explained.htm](http://www.techsupportalert.com/content/32-bit-and-64-bit-explained.htm)

---

### Post by RH9R on 2012-11-04
Thank you so much! I appreciate your kind help!

---

