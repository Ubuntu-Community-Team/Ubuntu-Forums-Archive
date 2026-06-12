---
title: "problems with g2c.h / C programming"
date: 2008-04-02
forum: Programming Talk
---

### Post by thomasgeo on 2008-04-02
Hi everybody,

I am completely new to C programming and have a problem with the g2c.h file.
When I compile the code I have (not written by me), then I get the following error message:
[code]
**** Build of configuration Debug for project i.spec.unmix ****

make all 
Building file: ../main.c
Invoking: GCC C Compiler
gcc -I/home/thomas/Dokumente/programming/source/grass-6.2.3/include -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"main.d" -MT"main.d" -o"main.o" "../main.c"
In file included from /home/thomas/Dokumente/programming/source/grass-6.2.3/include/la.h:28,
                 from ../global.h:3,
                 from ../main.c:29:
/usr/include/g2c.h:21: error: expected »=«, »,«, »;«, »asm« or »__attribute__« before »integer«{/code]

I found at "Koders Code Search" that this header file is the standard Fortran to C header file, so it looks to me like I have a problem with my g77.

My OS is Ubuntu Gutsy Gibbon.

If you have any idea how I could solve this problem, please let me know.
If you need any further information on this problem, please let me know.

Cheers,
Thomas

---

### Post by WW on 2008-04-02
I don't know what is causing the error, but it looks like you are trying to build grass version 6.2.3.  Version 6.2.2 is in the Ubuntu repositories; the  package name is [grass](http://packages.ubuntu.com/gutsy/grass). Do you need version 6.2.3?

EDIT: Also check out the binary packages at [the grass web site](http://grass.itc.it/download/index.php).  The Ubuntu link appears to give a repository that has version 6.2.3.

---

### Post by thomasgeo on 2008-04-02
No, actually i need a function in GRASS GIS that is not included in the new versions. It is i.spec.unmix, which was implemented by Markus Neteler. The source code is [here]("http://mpa.itc.it/markus/spectral_unmixing/") available. To compile the code you will need the LAPACK and the BLAS package. Those packages are Fortran libraries. Hence i thought i have some problems with the g77. BLAS and LAPACK i got installed, OK, LAPACK gives me an error while testing, but it seems to be ok.

btw. meanwhile there is 6.3 of GRASS released... ;)

Thomas

---

### Post by WW on 2008-04-02
Ah, I see. Good luck!

---

