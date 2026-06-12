---
title: "Unix network programming help"
date: 2007-09-08
forum: Programming Talk
---

### Post by kvorion on 2007-09-08
Hi All,

I started reading the Unix Network Programming book by Richard Stevens. I tried to compile the basic daytime client program that is given in the book (the program tries to connect to port 13 on the local machine). The program kept failing saying "**connection refused**". I realized that I am not able to telnet to any of the standard ports on my machine. Do I have to enable some setting on my Ubuntu to be able to create and listen to socket connections? Please help me with this.

I am using Ubuntu 7.04.

Edit: I just scanned my machine using NMap and I realised that there is only a single open port on my machine and that the generic daytime service is not installed by default on Ubuntu.

---

### Post by dwhitney67 on 2007-09-08
There is probably "no one" listening on port 13 of your system.  Do you have an SSH daemon running on your system?  If so, try connecting to port 22.

Alternatively, if you are at the stage where you have a server application written, try opening a port of your choosing, say 9000.  Then try to connect with your client.

---

