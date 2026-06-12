---
title: "Building Device Drivers - Kernel Source or Headers Required ?"
date: 2009-08-23
forum: Packaging and Compiling Programs
---

### Post by Kerubu on 2009-08-23
Hello,

I'm beginning tinkering with writing my own device drivers and am following the guide here :

[http://www.freesoftwaremagazine.com/articles/drivers_linux?page=0%2C1]("http://www.freesoftwaremagazine.com/articles/drivers_linux?page=0%2C1")

as well as using 'Linux Device Drivers' from O'Reilly.

One issue that is mentioned in both these sources is that as of kernel 2.6.xx the full kernel source is required to build kernel modules, however I'm not sure if this is the case.

I have build from source device drivers for 'Phidget' robotic modules and I didn't have the full kernel source installed on my machine (Ubuntu 8.10) though I *may* have had the headers installed at the time. Also I am sure I have read somewhere in the Ubuntu community documentation that it is not necessary to install the full source to build kernel modules, just the headers still.

Could someone possibly advise me on is the correct case for building kernel modules ? Do I need full kernel source or will headers suffice ?

Many thanks

Kerubu

---

### Post by Kerubu on 2009-08-23
Found the answer by 'doing' i.e. just installed headers and complied.

Answer : No the full source is not required.

---

