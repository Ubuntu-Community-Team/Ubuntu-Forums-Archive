---
title: "How to define kernel version in DEBIAN/control file and access it in postinst script"
date: 2011-06-11
forum: Packaging and Compiling Programs
---

### Post by argupt on 2011-06-11
Hi,

I am trying to create a deb package for a file system kernel module, which depends on kernel 'uname -r'. I am using cons to compile the kernel module (I can't use make as I don't have any make file in my source tree). I have successfully compiled the module and I want to create deb package for it. In my postinst script I want to run depmod for this particular kernel, so I need the value of kernel 'uname -r' there (I can't depend on 'uname -r' command as the machine may be booted in different kernel at the time of installing deb package). Can anyone guide me on how to define kernel version (for which module is compiled) in control file and parse it in pre/post inst/rm scripts? This is urgent and any help or refference to any link will be appriciated. I can't use tools which use make files. I am writing my DEBIAN/control file in a script so I have full control over it.

---

