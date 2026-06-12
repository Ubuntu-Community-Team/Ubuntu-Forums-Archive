---
title: "call to ioctl() returns with -1 and sets errno to 5 (EIO)"
date: 2010-01-19
forum: Programming Talk
---

### Post by rholton on 2010-01-19
In all the documentation I've found, ioctl should never set errno to 5 (EIO). That wouldn't bother me too much, except that I don't know what's wrong.

It's a C program running under Ubuntu Jaunty Jackalope. The program uses serial I/O to communicate with a modem and thus to a program on another computer (Windows / VB, fwiw).

Just before the error, I use system() to use rz to receive a file via Zmodem. If the line is lost in the middle of the file transfer (i.e. I unplug the phone line from the modem), rz eventually times out and returns 65536 (-1?). Then, I try to figure out the nature of the failure, by calling 

ioctl(fd, TIOCMGET, &argp)

which returns -1 and errno is set to EIO. fd is the file descriptor.

Note that if I don't trigger the failure (rz succeeds), then I have no problems.

Any ideas what would cause an "Input/Output Error" in this case? Or why losing the carrier would trigger this?

GNU C Library stable release version 2.9
gcc (Ubuntu 4.3.3-5ubuntu4) 4.3.3
Kernel Linux 2.6.28-17-generic
Zoom 3095 USB Mini External Modem (Conexant® CX930xx) CX93001-EIS_V0.2002-V92

Thanks in advance!
-Rich

---

