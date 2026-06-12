---
title: "how to add libstdc++ library in configure.ac"
date: 2008-01-22
forum: Programming Talk
---

### Post by bargi on 2008-01-22
Hi ,

Can Anybody tell me how to include libstdc++ in configure.ac file so that my program automatically compile using these libraries.

First of all ,let me know that for compiling C++ files should I need 
libstdc++ libraries....since I am getting following linker error :

tilities.cpp:(.text+0x2c1): undefined reference to `std::allocator<char>::allocator()'
Utilities.cpp:(.text+0x314): undefined reference to `std::allocator<char>::~allocator()'
Utilities.cpp:(.text+0x330): undefined reference to `std::allocator<char>::~allocator()'

I have googled a lot and found that we have to use libstdc++ for removing this error........

Is there any other way so that I can used libstdc++ in my project...?

I am creating makefile from configure.ac and want to compile my cpp files using libstdc++ libraries ......

I have installed libstdc++ and it give following output:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
libstdc++5 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I want that my files automatically compiled with -lstdc++ 

Thanks
Bargi

---

### Post by CptPicard on 2008-01-22
There is no need to explicitly request the linking of the standard library... after all, it's... "standard". :)

You're probably trying to use "gcc" to compile. Use "g++" instead.

---

### Post by bargi on 2008-01-24
Thanks for reply.......

But in my project I have to compile with makefile which r generated from configure.ac file.........

How can I make changes so that it compile with libstdc++ libraries..
Or should I set environment variables for it....

Please give suggestion.........

Thanks a lot

Bargi

---

