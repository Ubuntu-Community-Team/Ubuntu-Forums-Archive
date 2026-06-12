---
title: "Ubuntu 20.04.2 LTS: icewm-menu-fdo[4751]: segfault at 0 ip"
date: 2021-05-20
forum: New to Ubuntu
---

### Post by maketopsite on 2021-05-20
```
journalctl -r
May 20 10:17:13 ubu: Code: f8 5b 5d c3 66 90 f3 0f 1e fa 48 83 ec 08 e8 33 ce fd ff 85 c0 0f 94 c0 48 83 c4 >
May 20 10:17:13 ubu: icewm-menu-fdo[4751]: segfault at 0 ip  00007f38fd39b5f4 sp 00007ffd56494e88 error 4 in  libglib-2.0.so.0.6400.6[7f38fd377000+84000]
```

Is it please safe and secure to use icewm on that machine ?

---

### Post by grahammechanical on 2021-05-20
A segfault is not necessarily an indication of a security vulnerability or that the security of the operating system has been compromised. 

> A segmentation fault, or segfault, is a memory error in which a program  tries to access a memory address that does not exist or the program does  not have the rights to access. It is a common bug in poorly written C  and C++ programs. When a program hits a segmentation fault, it often  crashes with the error phrase "Segmentation Fault."

[https://smallbusiness.chron.com/segmentation-fault-linux-27699.html](https://smallbusiness.chron.com/segmentation-fault-linux-27699.html)

icewm is still being developed and maintained. Which is good news. Make sure that you are using the latest version. It will have the latest fixes for any program bugs reported as well as security vulnerabilities identified

[https://github.com/bbidulock/icewm](https://github.com/bbidulock/icewm)

Regards

---

### Post by Holger_Gehrke on 2021-05-20
In addition to what grahammechanical wrote: it's not the window manager itself that crashed, it's [icewm-menu-fdo]("https://ice-wm.org/man/icewm-menu-fdo") - a small utility that is used to start programs via their desktop files; you probably tried to run a program from the menu and the desktop file for it contained something that crashed that tool.

Holger

---

### Post by maketopsite on 2021-05-22
Well thank you. I'm using latest versions of packages.

---

