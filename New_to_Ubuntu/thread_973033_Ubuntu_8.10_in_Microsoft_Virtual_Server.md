---
title: "Ubuntu 8.10 in Microsoft Virtual Server"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by jonny75904 on 2008-11-06
I work in a primarily asp.net shop, but we've recently taken on a php project.  I want to install Ubuntu 8.10 to a VM.  I mount the iso as a virtual CD-ROM and boot the new VM.  The CD loads but when I go to install or even run it from CD I get a long trace message stream that ends with: 

[0.152009][<c04ab3e4] ? unknown_bootoptions+0x0.0x200.

the boot options are:

file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity initrd=/casper/initrd.gz quiet splash --

Can anyone help me out?

---

### Post by superprash2003 on 2008-11-06
ensure that you have given atleast 256mb of memory to ubuntu

---

### Post by jonny75904 on 2008-11-06
I have 1024 assigned

---

### Post by billyp on 2008-11-07
I have the exact same problem/question - using an IDE drive with 1024 MB RAM.

---

### Post by billyp on 2008-11-07
Made some progress - added the following to the boot option:
vga=791 noreplace-paravirt

Found this on:[http://arcanecode.wordpress.com/2008/04/24/installing-ubuntu-804-under-microsoft-virtual-pc-2007/](http://arcanecode.wordpress.com/2008/04/24/installing-ubuntu-804-under-microsoft-virtual-pc-2007/)
way down in the comments.

---

