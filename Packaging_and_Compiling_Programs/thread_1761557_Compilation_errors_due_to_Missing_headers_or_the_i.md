---
title: "Compilation errors due to Missing headers or the including of Kernel Source Headers"
date: 2011-05-18
forum: Packaging and Compiling Programs
---

### Post by aka_rich on 2011-05-18
Hi Guys,

I am still new to Linux and i am trying to do some network programming on Ubuntu 10.10, where i am trying to leverage the "Checksum.h" header file. This is so i can use the TCP Checksum functions defined within it. However, when i #include <net/checksum.h> in my program, it does not compile because gcc cannot find it. Gcc seems to be looking for the header in "/usr/include" and not where i have found it to be, which is in the Kernel's source headers ("/usr/src/linux-header<Version>/include").

After looking around on the Internet i found that i did not have a sym link to the Kernel's source headers called "linux" in "/usr/src". From what i have read, there should be a sym link to the current Kernel's source headers to become "/usr/src/linux". So i am a bit confused because, even after creating a sym link and using "-I" to include extra Dirs on the command line, gcc throws more header file errors where it tries to link the header files that are listed within "checksum.h". I definitely got something wrong.

I thought i was able to use the Kernel header files as they were the source for the Kernel? Also, i dont understand why my header files are not all in one location like "/usr/include"?

I dont get how to properly include/use any header files in the Kernel's source header location.

Im trying to finish a project and this is slowing me down, so any help is appreciated.

Thanks,

Rich.

---

### Post by SevenMachines on 2011-05-18
the headers that are designed to be used *are* in /usr/include, kernel headers are a little different. see [http://kernelnewbies.org/KernelHeaders](http://kernelnewbies.org/KernelHeaders)
If you really want to use the kernel headers then there is a link there about makefiles for building against kernel components and so on, note that its kernel version dependent these days. 
By the sound of it though, you probably want to be using something else, sadly its not something i know much about/can remember, i tend to use much higher level libraries these days (at lot of boost libraries :) ).  but you might want to take a look at the headers from,
/usr/include/linux from linux-libc-dev
or
/usr/include/net from libc6-dev
for relatively low level access.

Hopefully there are some more low level socket users out there who can give you a better answer!

---

### Post by aka_rich on 2011-05-18
Thank you, that was helpful.

Basically those Kernel headers are not designed to be used for normal use, as they are only mean for Compiling a Kernel and not normal C/C++ code.

However, im not positive if i can get at the functions that i wanted without compiling for/with the Kernel (This is out of my area already). So i will search for another way of getting the same thing done.

Rich.

---

