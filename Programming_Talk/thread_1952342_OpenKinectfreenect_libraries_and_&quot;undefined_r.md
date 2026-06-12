---
title: "OpenKinect/freenect libraries and &quot;undefined reference&quot; errors"
date: 2012-04-04
forum: Programming Talk
---

### Post by practisevoodoo on 2012-04-04
Hi all, I trying to do this on a a 32bit Ubuntu 11.10 install.

I am trying to compile some c++ code that uses libfreenect, i have followed instructions on the openkinect website to get these built/installed.

This is the command I'm using to compile the code
> g++ `pkg-config libfreenect --libs --cflags` nod.cpp -o nod
 
and the error is
> 
nod.cpp:(.text+0x21): undefined reference to `freenect_init'
nod.cpp:(.text+0x4f): undefined reference to `freenect_num_devices'
collect2: ld returned 1 exit status

 
but if I check the pkg-config output it is giving me
> -I/usr/local/include/freenect -I/usr/include/libusb-1.0 -L/usr/local/lib -lfreenect
which is all correct
 
I really don't have that much experience with linux so I'm pretty much stumped at this point. I assume that g++ just isn't finding the linker files but I'm listing the right directory.

Any help you can give would be great.

---

### Post by CynicRus on 2012-04-04
try g++ nod.cpp nod.o -o nod -lfreenect

---

### Post by practisevoodoo on 2012-04-04
> g++ nod.cpp nod.o -o nod -lfreenect

just gave me
> nod.o: No such file or directory

but a quick google let me know that I needed to run 
> g++ -c nod.cpp
first and then run
> g++ nod.o -o nod -lfreenect

Which works! thanks CynicRus!

---

