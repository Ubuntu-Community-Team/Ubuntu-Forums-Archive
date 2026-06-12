---
title: "avr-ranlib: Command not found"
date: 2008-01-12
forum: Programming Talk
---

### Post by oguzhana on 2008-01-12
hi,
I am trying to install avr gcc compiler, I could install the binutils 2.15 first but I am stuck at gcc. I am going through the following document :
[http://www.tuxgraphics.org/electronics/200411/article352.shtml](http://www.tuxgraphics.org/electronics/200411/article352.shtml)

I can run make without any trouble I guess, it reaches to the end but while running make install I got following error:
[I]
avr-ranlib /usr/local/avr/lib/gcc/avr/3.4.2/libgcc.a
make[2]: avr-ranlib: Command not found
make[2]: *** [install] Error 127
make[2]: Leaving directory `/home/oguzhan/Desktop/Oguzhan/gcc-3.4.2/obj-avr/gcc'
make[1]: *** [install-multilib] Error 2
make[1]: Leaving directory `/home/oguzhan/Desktop/Oguzhan/gcc-3.4.2/obj-avr/gcc'
make: *** [install-gcc] Error 2[/I]

avr-ranlib in my path under directory /usr/local/avr/bin and it is executable. What might be the problem with it? I can supply any info related, could you help me to fix?

---

### Post by geraldm on 2008-01-12
The most likely problem is that you did not execute (as root user) "ldconfig" after building the library.  The tutorial does not do a good job of emphasizing   that this command must be executed whenever libraries are built, and whenever binaries are installed.  The reason is that linux works out of a cache for purposes of speedy execution, and after a "make install" it still is working with the older, obsoleted cache.  Executing "ldconfig' updates the cache.  
There are other ways around the cache problem:
1. Use full-path filename to the executable.
2. Use relative-path beginning from the current directory "./../bin/avr-ranlib"
3.  Reboot the system, which builds a fresh cache.

Gerald

---

### Post by oguzhana on 2008-01-12
I executed ldconfig by typing "/sbin/ldconfig". It just worked and did not show any report or something. Should I had sent some parameters to it? I rebooted the system as well. It does not work. Should I do something to clear the mess left from a half installation?

---

### Post by geraldm on 2008-01-12
/sbin/ldconfig is normally run without any parameters.
I suggest putting a link in /usr/local/bin pointing to avr-ranlib
You might check your package documentation to see if there were any environment variables that needed to be set.
A system reboot always builds a fresh cache, so if it does not work after the reboot, then some tweaks, links, or mv instructions may need to be done.

Gerald

---

