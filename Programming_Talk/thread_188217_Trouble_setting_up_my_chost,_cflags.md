---
title: "Trouble setting up my chost, cflags"
date: 2006-06-03
forum: Programming Talk
---

### Post by sbm on 2006-06-03
Hi

I have the following flags in .bash_profile:

   CHOST="i686-pc-linux-gnu"
   CFLAGS="-Os -march=pentium-m -pipe -fomit-frame-pointer"
   CXXFLAGS=$CFLAGS

   export $CHOST $CFLAGS $CXXFLAGS

But opening bash gives the following errors:

-bash: export: `i686-pc-linux-gnu': not a valid identifier
-bash: export: `-Os': not a valid identifier
-bash: export: `-march=pentium-m': not a valid identifier
-bash: export: `-pipe': not a valid identifier
-bash: export: `-fomit-frame-pointer': not a valid identifier
-bash: export: `-Os': not a valid identifier
-bash: export: `-march=pentium-m': not a valid identifier
-bash: export: `-pipe': not a valid identifier
-bash: export: `-fomit-frame-pointer': not a valid identifier

My CPUINFO is:
(cat /proc/cpuinfo)
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 13
model name      : Intel(R) Pentium(R) M processor 1.80GHz
stepping        : 6
cpu MHz         : 1794.476
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe est tm2
bogomips        : 1196.79


Hope some1 can assist me in correcting my flags :-)

---

### Post by LordHunter317 on 2006-06-03
You give export the name of the variable, not it's subtitution.  Remove the dollar signs.  Setting those globally may be a bad idea, and they may be ignored anyway.

---

### Post by sbm on 2006-06-03
Thx, that did the trick.
Why is it a bad idea to add them globally?
My thought was that adding optimized flags would optimize the software i compile for my system.

---

### Post by Arndt on 2006-06-05
[QUOTE=sbm]Thx, that did the trick.
Why is it a bad idea to add them globally?
My thought was that adding optimized flags would optimize the software i compile for my system.[/QUOTE]

As the previous poster notes, they may not even be recognized. Usually programs are built using 'make', and while there is an option to 'make' to import options from the environment (i.e., variables exported in the shell), it is not always used.

Assuming they are recognized, it is certainly appears reasonable to make sure that the optimizations you want always are made, regardless of what the Makefile says.

There are problems with that, though. One is that some programs may not work if optimized too hard - especially omitting the frame pointer might cause problems. Another is that hard optimization gets in the way of debugging, in which case you will have to change both your environment and the Makefile, instead of only the Makefile. A third problem is that the files on disk alone don't define the compiling environment. If you work with someone else, and he doesn't use the same environment variables, your Makefiles will do different things, which may be a source of confusion.

---

