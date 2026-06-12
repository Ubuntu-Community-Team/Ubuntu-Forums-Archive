---
title: "Building a cross compiling toolchain"
date: 2014-11-01
forum: Programming Talk
---

### Post by Matthew_Harrop on 2014-11-01
I am attempting to build an Ubuntu server that will run as my code store. As such, I don't want to connect it to the outside world, but just to my company network.

Ubuntu server doesn't come with useful tools like GCC or make, which makes things quite tricky. Does anybody know where I can find information/instructions on using the tools on my mac to compile and install tools for my Ubuntu server. 

If not, does anybody know where I can find information on cross compilers in general? I've read the information on wikipedia and am a little confused...

---

### Post by steeldriver on 2014-11-01
Is there any particular reason you want to *build* the tools, rather than simply downloading the relevant pre-compiled deb packages and transferring those across to the Ubuntu server?

---

### Post by Matthew_Harrop on 2014-11-01
I'm just curious about how one would go about it really. 
I plan to build myself a code safe, build server and other assorted virtualized servers eventually, and I don't want them all to have to carry all of the compilation tools - If that makes sense.

---

