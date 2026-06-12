---
title: "Linux Device Driver Programming"
date: 2010-09-20
forum: Programming Talk
---

### Post by aprilmot on 2010-09-20
Hi,
I am new to Linux/Ubuntu. I am currently using the Lucid version
"Linux 2.6.32-24-generic #43-Ubuntu SMP Thu Sep 16 14:17:33 UTC 2010 i686 GNU/Linux"
I would like to learn Linux Device Driver Programming.  I am following LinuxDeviceDriver Programming <http://lwn.net/Kernel/LDD3/> ebook.  The book requests to compile the kernel before starting with DeviceDriver Programming.  I googled to find a way to compile the Linux Kernel.  But I am little confused afraid of spoiling the currently system/Kernel.  Is there any safeway of compiling the Kernel.  Please let me know some precautions before compiling and booting the Kernel.  Also please let me know the link for more information related to Ubuntu / Linux Kernel Compilation and Device Driver Programming.

Thank you in Advance
Aprilmot

---

### Post by s.fox on 2010-09-20
Thread moved at op request.

---

### Post by TeoBigusGeekus on 2010-09-20
For driver programming, you first need to know C and Assembly.
Secondly, you must have a thorough knowledge of how linux works.
[http://www.linuxfromscratch.org/]("http://www.linuxfromscratch.org/")
If you manage to create a (working) system using linux from scratch, you will have made a big step towards understanding the linux/unix architecture.

---

### Post by interval1066 on 2010-09-20
You don't nessessarily (or even usually) need to re-compile the kernel to get a device accessible to it. Often a loadable module is sufficient, and safer.

---

### Post by aprilmot on 2010-09-20
Thank you very much for your reply.
For Device Driver Programming is it sufficient to just have the current Kernel Source Tree. 
If so where should I place these source files.

Thank you in Advance.
Aprilmot

---

### Post by worksofcraft on 2010-09-20
There are different variants of the Linux kernel, like there is one for Ubuntu called "ultimate edition" that seems quite popular and another one specifically for processing multi-media that needs to have short latency times. I think it's called Ubuntu Studio.

If you want to experiment safely with building the kernel and writing device drivers I really recommend doing so in a virtual environment with virtualbox. That will let you take snapshots that you can restore to when things go wrong and won't be intrusive on your desktop configuration.

I could give you various links like [http://www.xml.com/ldd/chapter/book/index.html](http://www.xml.com/ldd/chapter/book/index.html), but I'm sure Google can find them and many more for you too ;)

Let us know how you get on :)

---

### Post by SledgeHammer_999 on 2010-09-20
Install the "linux-kernel-headers" from the repos and you're set to go.

---

