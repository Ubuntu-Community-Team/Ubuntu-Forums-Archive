---
title: "Finding Serial Devices in C"
date: 2010-10-22
forum: Programming Talk
---

### Post by DuneSoldier on 2010-10-22
Hi, I'm writing a small application in C++ that basically accepts data coming in on a network port and redirects it to a serial port.

Basically I'm working on a little tcp server that you can telnet into and send some commands to see what is linked with what. 

IE:

Command>List Links

Links
<device> - <port>

and allow you to create and teardown links as you feel like it. It's basically me learning to play with the serial port under linux (and play on a beagleboard xm too). My issue is I would like to list all the serial devices present in the system. My first thought would be to list all the tty devices under /dev, but there are way too many. Is there a way I can easily figure out what are actual serial devices?

For example, I'm doing this on my laptop. The only "real" serial device I have is located at /dev/ttyUSB0. If I do an ls -l | grep tty I'm getting:

/dev/tty[0->63]
/dev/ttyS[0->3]
/dev/ttyUSB0

Thanks

---

