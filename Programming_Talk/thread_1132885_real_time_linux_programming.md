---
title: "real time linux programming"
date: 2009-04-22
forum: Programming Talk
---

### Post by Darryl Moore on 2009-04-22
I'm trying to write an application that will run under the RT-Linux kernel which is installable from the repos.

I've installed linux-rt, but there do not seem to be any development libraries or headers so that I can write my own application to use the real time extensions provided.

Where should I be going to get the header files I need? Are there more libraries I need to install? I think the API I should have access to is the one documented here: [http://euler.aero.iitb.ac.in/docs/rtlinux-3.0/doc/html/man/rtl_index.4.html](http://euler.aero.iitb.ac.in/docs/rtlinux-3.0/doc/html/man/rtl_index.4.html)

I think it will work well for my purposes which is th create a real time serial port that can measure the time between characters hopefully with about 0.2mS accuracy.

Any help or comments would be gratefully appreciated.

---

### Post by darthmob on 2009-04-22
maybe in the package 'linux-headers-rt'? ;)

---

### Post by Darryl Moore on 2009-04-22
Nope. That just has headers for the kernel. Not for any of the APIs. Nice try though.

---

### Post by JK3mp on 2009-04-22
Did you update after installing the new kernel?

---

### Post by Darryl Moore on 2009-04-22
I did do a full update at the same time. I don't think it should matter though. linux-rt is a meta package which installs the kernel, headers, and modules. What it does not appear to install is any API.

A real time extension for Linux is of very limited usefulness if I can't write any programs to make use of it.

I am presuming that the API libraries were installed as part of "apt-get install linux-rt". Now in order to make use of those libraries I need the appropriate API header files.

---

### Post by darthmob on 2009-04-23
> **Darryl Moore said:**
> Nope. That just has headers for the kernel. Not for any of the APIs. Nice try though.I already expected that it would have been too easy!

---

### Post by Darryl Moore on 2009-04-23
Sigh. :( Has anybody in these forums actually written code for this kernel? I'd love to hear from you if you have. Thx

---

### Post by stroyan on 2009-04-23
You could try the 'rtai', 'rtai-doc', and 'rtai-source' packages from the
ubuntu universe repository.  But I would favor first trying the posix realtime
functions provided by librt.so in the very standard 'libc6-dev' package.
The manuals for those functions are part of the 'glibc-doc' package.

---

### Post by mmix on 2009-04-23
[http://stackoverflow.com/questions/240058/1ms-resolution-timer-under-linux-recommended-way/240176#240176](http://stackoverflow.com/questions/240058/1ms-resolution-timer-under-linux-recommended-way/240176#240176)

---

