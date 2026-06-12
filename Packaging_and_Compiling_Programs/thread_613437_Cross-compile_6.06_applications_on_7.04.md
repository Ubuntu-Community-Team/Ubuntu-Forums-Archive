---
title: "Cross-compile 6.06 applications on 7.04"
date: 2007-11-14
forum: Packaging and Compiling Programs
---

### Post by Arcquist on 2007-11-14
Hello,

I'm trying to write some software to run on a machine I have running 6.06 LTS server but the machine is normally without a monitor, keyboard, etc. and for various reasons I don't want to install the development tools on it and compile locally.

I have a 7.04 desktop (kubuntu) as well and can compile fine on this machine but moving the executables to the 6.06 server of course doesn't work because it complains of incompatible glibc versions.

Is there a relatively easy way to do this? ie. Some package or other I can install and switch between compilers? If not what would be the recommended way of doing this? Do I need to go through and learn the entire process of building a cross compiler from scratch? If so are there any recommended sites for how-tos for that?

Thanks for your help,
-Arcquist

---

### Post by thegnuguru on 2007-11-15
No you do not need to learn how to build a cross compiler (allthough that would be kinda fun). All you need to do is download or build a chroot of dapper ([http://en.wikipedia.org/wiki/Chroot](http://en.wikipedia.org/wiki/Chroot)) the easiest way i know to create a chroot is to fallow the instructions in the Ubuntu Packaging Guide [http://doc.ubuntu.com/ubuntu/packagingguide/C/appendix-chroot.html](http://doc.ubuntu.com/ubuntu/packagingguide/C/appendix-chroot.html)

Good Luck 

Matt Arnold

---

### Post by Arcquist on 2007-11-15
Ok thank you for the help and the link.

I had a question while reading the "Ubuntu Packaging Guide". It says that I need to install (at least) the version of debootstrap from the version of Ubuntu for which I'm trying to create the chroot. Does that mean I have to find the Dapper version of debootstrap?

[http://packages.ubuntu.com](http://packages.ubuntu.com) lists a bunch of different debootstraps including one for dapper ([http://packages.ubuntu.com/dapper/admin/debootstrap](http://packages.ubuntu.com/dapper/admin/debootstrap)), one for dapper-backports ([http://packages.ubuntu.com/dapper-backports/admin/debootstrap](http://packages.ubuntu.com/dapper-backports/admin/debootstrap)) and similarly ones for feisty and feisty-backports. I assume I manually download the one for dapper (not backports) and install it with dpkg -i?

Thanks again for your help,
-Arcquist

---

### Post by thegnuguru on 2007-11-15
I think so but if I'm wrong somebody please correct me

---

