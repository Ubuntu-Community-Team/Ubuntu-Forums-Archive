---
title: "Ho to do a blocking read of serial port with a timeout?"
date: 2009-11-21
forum: Programming Talk
---

### Post by rohitkugve on 2009-11-21
Hi,

I am writing a program in C which is supposed to read ttyS0. For some reason I need it to do a blocking read. However it should not block indefinitely in case the data never arrives. I am using open() and read() system calls.
Also I have installed a dummy signal handler that catches SIGCONT. I thought that if a SIGCONT arrives when read() is blocked, the control comes out of read() with an error. But that does not seem to be happening. Any thoughts?
Thank you,
Rohit.

---

### Post by lloyd_b on 2009-11-21
"man select" in a terminal window.  select() watches file descriptors, returning when one is ready to be read/written, but it includes a timeout so that it will return after a set amount of time, even if none of the watched descriptors is ready.

Note: If there's no man page for select, "sudo apt-get install manpages-dev"

Lloyd B.

---

