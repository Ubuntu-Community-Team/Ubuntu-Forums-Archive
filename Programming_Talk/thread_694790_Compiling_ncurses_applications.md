---
title: "Compiling ncurses applications"
date: 2008-02-12
forum: Programming Talk
---

### Post by tom66 on 2008-02-12
What arguments should be passed to G++ or GCC to compile an ncurses application?

Thanks,
Tom

---

### Post by lnostdal on 2008-02-13
```

root@ibmr52:~# aptitude search ncurses | grep dev
p   lib64ncurses5-dev               - Developer's libraries for ncurses (64-bit)
p   libcunit1-ncurses-dev           - Unit Testing Library for C (ncurses) -- de
p   libkaya-ncurses-dev             - Ncurses binding for kaya                  
v   libncurses-dev                  -                                           
i   libncurses5-dev                 - Developer's libraries and docs for ncurses
p   libncursesw5-dev                - Developer's libraries for ncursesw        
v   ncurses-dev                     -                                           

```

ok, so i got the development files for ncurses installed already .. (the *i* infront of *libncurses5-dev* signifies this)

```

root@ibmr52:~# dpkg -L libncurses5-dev | grep .so$
/usr/lib/libncurses.so
/usr/lib/libform.so
/usr/lib/libmenu.so
/usr/lib/libpanel.so
/usr/lib/libcurses.so
/usr/lib/libtermcap.so

```

which means:

```

gcc -g -Wall -l ncurses -o hello hello.c

```

(remove the "lib" and the "-dev" part)

the linker will by default already look in the */usr/lib* directory for *.so* files so you do not need to specify where it is to look

---

### Post by tom66 on 2008-02-13
Thanks! I'll try that.

Tom

---

### Post by tom66 on 2008-02-13
Unfortunately it didn't work :(.

I got only one error trying to compile the demo app, better than 350 or so, I suppose...

internal.h:39:25: error: ncurses_cfg.h: No such file or directory

Thanks for your help anyway though!

---

### Post by aks44 on 2008-02-13
Are you sure you correctly installed the -dev package? Or that you did specify the include path?

[http://ubuntuforums.org/showthread.php?t=691451](http://ubuntuforums.org/showthread.php?t=691451)

---

### Post by tom66 on 2008-02-14
Do you know what include path I should use?

Thanks,
Tom

---

### Post by RIchard James13 on 2008-02-14
You don't need to specify a include path for ncurses.h because it is already in the compilers include path.

I just compiled a game I wrote in ncurses at the command line by typing this
gcc -o ascii-attack -l ncurses *.c

If ncurses is not installed then you will get many error messages compiling a ncurses app. But you seem to have only one error message which makes me think it is not related to ncurses being installed or include paths.
instead of 
#include ncurses_cfg.h
just try
#include ncurses.h

I have never heard of ncurses_cfg.h

---

### Post by tom66 on 2008-02-15
Thanks for your help, but it didn't work. It brought up many thousands of errors, all sort of like:

```

/tmp/ccKXm0Vz.o:(.rodata._ZTI13Integer_Field[typeinfo for Integer_Field]+0x0): undefined reference to `vtable for __cxxabiv1::__si_class_type_info'
/tmp/ccKXm0Vz.o:(.rodata._ZTI17Enumeration_Field[typeinfo for Enumeration_Field]+0x0): undefined reference to `vtable for __cxxabiv1::__si_class_type_info'
/tmp/ccKXm0Vz.o:(.rodata._ZTI5Label[typeinfo for Label]+0x0): undefined reference to `vtable for __cxxabiv1::__si_class_type_info'
/tmp/ccKXm0Vz.o:(.rodata._ZTI5Label[typeinfo for Label]+0x8): undefined reference to `typeinfo for NCursesFormField'
/tmp/ccKXm0Vz.o:(.rodata._ZTI9PadAction[typeinfo for PadAction]+0x0): undefined reference to `vtable for __cxxabiv1::__si_class_type_info'
/tmp/ccKXm0Vz.o:(.rodata._ZTI9PadAction[typeinfo for PadAction]+0x8): undefined reference to `typeinfo for NCursesMenuItem'
/tmp/ccKXm0Vz.o:(.rodata._ZTI10ScanAction[typeinfo for ScanAction]+0x0): undefined reference to `vtable for __cxxabiv1::__si_class_type_info'
/tmp/ccKXm0Vz.o:(.rodata._ZTI10ScanAction[typeinfo for ScanAction]+0x8): undefined reference to `typeinfo for NCursesMenuItem'
/tmp/ccKXm0Vz.o:(.rodata._ZTI8QuitItem[typeinfo for QuitItem]+0x0): undefined reference to `vtable for __cxxabiv1::__si_class_type_info'
/tmp/ccKXm0Vz.o:(.rodata._ZTI8QuitItem[typeinfo for QuitItem]+0x8): undefined reference to `typeinfo for NCursesMenuItem'
/tmp/ccKXm0Vz.o:(.eh_frame+0x12): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status

```

Thanks anyway!

---

### Post by aks44 on 2008-02-15
> **tom66 said:**
> Thanks for your help, but it didn't work. It brought up many thousands of errors

It worked: you got past the compiling stage, now the linker is whining (which is a very good progression).

Now all you need to do is to link to the relevant library (-l [lowercase L] command line switch, and optionally -L). See lnostdal's post and/or the link I gave you earlier.

---

### Post by tom66 on 2008-02-15
I did use the lowercase l with 'ncurses', the same as before for the other one which threw one error. Any idea what parameter should be used for the -L switch? 

Thanks,
Tom

---

### Post by aks44 on 2008-02-15
Hmm *if* the compiler couldn't find libncurses.so you'd get an error message along the lines of
**/usr/bin/ld: cannot find -lncurses**

Looks like your problem is a bit more complex. Your compiler spits out errors about vtables and typeinfos, from the top of my head I'd say it has to do with RTTI but if this is the case I don't know (yet) how to handle that on Linux. :(

---

### Post by tom66 on 2008-02-15
What's RTTI? And can it solve my problem?

(Sorry, I haven't programmed with C++ that much, I'm best at PHP)

Thanks,
Tom

---

### Post by aks44 on 2008-02-15
Run Time Type Information.

It is some kind of "meta-data" about classes and types that the compiler adds to the compiled binaries.

It is usually not needed unless dynamic_cast is used (most likely) or typeid (quite unlikely).


As a *wild* guess I'd say that the ncurses binary (libncurses.so) was not compiled with RTTI, but you somehow call (inlined?) functions that make use of it under the hood.

Again: I have very little experience with the GCC compiler, and I never ever used ncurses. I'm just using a "generic troubleshooting" approach here, so I may well be off the tracks... ;)

---

