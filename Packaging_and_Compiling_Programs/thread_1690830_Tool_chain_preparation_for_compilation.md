---
title: "Tool chain preparation for compilation"
date: 2011-02-19
forum: Packaging and Compiling Programs
---

### Post by Dave1024 on 2011-02-19
I would like to compile my program for embedded platform and my target processor is Cortex A8. I know there is a compiler is necessary for the compilation of any program. but when i search sites i saw the exact name is tool chain for embedded platforms, and we are customize the library's for our specific usage. I need a direction for making a tool chain for embedded platforms and how can i customize the tool chain for different platforms.
Please provide spots for some tutorials to make a tool chain
Packages like gcc,glibc,binutils have support for the embedded platforms like cortex a8, cortex a9, arm 926-ejs etc....?
The work is for to prepare a .out file and run on beegle board 

Thanks in Advance 
Dave

---

### Post by SevenMachines on 2011-02-19
I'm guessing you could be compiling for arm eabi rather than specifically generating tuned cortex a8 machine code? Recent ubuntu releases (at least maverick and later), come with an arm toolchain available for gnu gcc, see the package "gcc-arm-linux-gnueabi". 

gcc will accept something like "-cpu=cortex-a8" for an arm build to focus it on that cpu if you really need it to but unless you're sure you do, don't :) 

One other toolchain i can think of that i've heard people mention as good is sourcery, though it may well be essentially the same thing, just in a handy big blob
[http://www.codesourcery.com/sgpp/lite/arm/portal/release1592](http://www.codesourcery.com/sgpp/lite/arm/portal/release1592)

I'm not big on arm compilation but hopefully thats at least some help

---

