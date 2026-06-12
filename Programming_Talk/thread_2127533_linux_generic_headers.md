---
title: "linux generic headers?"
date: 2013-03-20
forum: Programming Talk
---

### Post by thedardanius on 2013-03-20
I have updated my kernel headers, what does that mean for the kernel?
I heard that generic headers/kernels are NOT the "real" linux kernel. I currently have the 3.5.0-generic linux, but my father said I shouldnt have chosen this one because its a development headers and potentially unstable (which I experienced it with some versions of it).
He said I should get the 3.2.0-headers/kernel. How should I get these, what are generic headers, and are there real differences between "normal" and generic headers?
Or are generic headers standard linux kernel code?
I dont get it any more...

---

### Post by slickymaster on 2013-03-21
They are sets of files that define all the application programming interface (API) for a program.
To compile a program that uses what's called a function library (or just library), you need the header files for that library so your compiler can check your code for syntax problems. You don't need the entire source code for the library in order to use the functions - thus saving a lot of space because header files are very small compared to the source files.
The reason the header files are not generally included by default is because these days most distributions provide you with binary (pre-compiled) packages for your system. Since you don't have to do any compiling, you don't need to look up any function definitions by their headers, you can simply run your software which has already been verified against the headers when it was compiled and it uses the pre-compiled function libraries (lib*.so) on your system.
If you have the wrong version of a function library on your system, then the pre-compiled binary usually breaks with a segmentation fault or something like that and you either need to get the right library version installed or re-compile the program from source using the library version (and its headers) that you have so it is now referencing the correct API.

---

### Post by thedardanius on 2013-03-21
thank you.
Then what are generic kernels?
Are there other type of linux kernels then?

---

### Post by schragge on 2013-03-21
See [uwiki]Kernel/Dev/Flavours[/uwiki]

---

### Post by slickymaster on 2013-03-21
> **thedardanius said:**
> thank you.
Then what are generic kernels?
Are there other type of linux kernels then?


Header files define interfaces to functions as well as structures used by programs.
In the case of the kernel header files, these functions and structures are within the kernel itself. The kernel header packages range in name from 'linux-headers' to 'kernel-headers' and other variations that end in '-headers'. However, most other packages keep their headers in a *-devel[op] or *-dev package.

---

