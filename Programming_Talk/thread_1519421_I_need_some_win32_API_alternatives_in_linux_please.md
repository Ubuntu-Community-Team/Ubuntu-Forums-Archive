---
title: "I need some win32 API alternatives in linux please?!"
date: 2010-06-28
forum: Programming Talk
---

### Post by jeremy28 on 2010-06-28
Hi all,

I'm porting a Win32 program into linux.
The program's name is "Serial Wrapper" that is intended to open a handle to a device in COM port and read or write some data to it by functions and structures such:

DCB
CreateFile
GetCommState
SetCommState
SetCommMask
WriteFile
ReadFile
SetCommTimeouts
...

but I have problem in replacing them by the appropriate alternatives in linux, because I'm new to linux APIs!

I've searched and found that the related header files are "sys/select.h" and " termios.h", I saw them but they didn't help me so much!!

Please share your experiences with me in this issue...

TIA.

---

### Post by simeon87 on 2010-06-28
First of all, the application may already work using Wine: [www.winehq.org/](www.winehq.org/) . If that's not an option, then someone else will have to point you in a better direction...

---

### Post by regala on 2010-06-28
> **simeon87 said:**
> First of all, the application may already work using Wine: [www.winehq.org/](www.winehq.org/) . If that's not an option, then someone else will have to point you in a better direction...

or simply have a look into the POSIX standard. and to some examples that already "handle COM ports", like cu, minicom or screen.

oh and really have a look into the POSIX standard or any reference to term control in Unix systems.

---

### Post by pbrane on 2010-06-28
GtkTerm may provide some good example code you can look at. Here is one possible site with the source listing. Or apt-get the source fro GtkTerm.

[http://www.codase.com/search/display?file=L2dlbnRvbzIvdmFyL3RtcC9yZXBvcy9jb2Rhc2UuYy9ndGt0ZXJtLTAuOTkuNC93b3JrL2d0a3Rlcm0tMC45OS40L3NyYy9zZXJpZS5j&lang=c]("http://www.codase.com/search/display?file=L2dlbnRvbzIvdmFyL3RtcC9yZXBvcy9jb2Rhc2UuYy9ndGt0ZXJtLTAuOTkuNC93b3JrL2d0a3Rlcm0tMC45OS40L3NyYy9zZXJpZS5j&lang=c")

---

### Post by dribeas on 2010-06-28
I would recommend using a portable library to encapsulate the platform specific code. In this case, boost::asio and boost::filesystem seem like a good option. Another option would be ACE. This way you can code once and use everywhere, without the need of learning the gory details of each platform.

---

