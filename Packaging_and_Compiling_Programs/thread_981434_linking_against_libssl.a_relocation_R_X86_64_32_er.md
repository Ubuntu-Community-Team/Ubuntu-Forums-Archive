---
title: "linking against libssl.a: relocation R_X86_64_32 error"
date: 2008-11-13
forum: Packaging and Compiling Programs
---

### Post by cytoplasm on 2008-11-13
I am attempting to link a shared library to libssl.a and get this:

```
# Building liballkeyrtv.so.1.1.1
gcc  -shared -Wl,-O1 -Wl,-soname,liballkeyrtv.so.1 -static-libgcc -o liballkeyrtv.so.1.1.1 allkeyrtv.o parseini.o tksc.o TkscTls.o TkscSockets.o skeys.o writelogs.o tThreads.o /usr/lib/libssl.a /usr/lib/libcrypto.a /usr/lib/libz.a /usr/lib/libc.a
/usr/bin/ld: /usr/lib/libssl.a(t1_clnt.o): relocation R_X86_64_32 against `a local symbol' can not be used when making a shared object; recompile with -fPIC
/usr/lib/libssl.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make: *** [liballkeyrtv.so.1.1.1] Error 1
```

Is this happening because openssl (t1_clnt.o specifically) was compiled without '-fPIC'? How can I resolve this? 


--Shawn

---

### Post by ejaz.sayyed@gmail.com on 2009-03-10
I am also getting the same error while trying to 
sudo make" the TORCS game on my system

g++ -shared -o libclient.so entry.o mainmenu.o splash.o exitmenu.o optionmenu.o -L/home/momin/Games/TORCS/torcs-1.3.1/export/lib  -lalut -L/usr/lib  -lplibssg -lplibsg -lplibul 
/usr/bin/ld: /usr/lib/libplibssg.a(ssg.o): relocation R_X86_64_32 against `a local symbol' can not be used when making a shared object; recompile with -fPIC
/usr/lib/libplibssg.a: could not read symbols: Bad value
collect2: ld returned 1 exit status



PLease help.

Regards,
- Ejaz

---

### Post by omer.qadir on 2010-04-21
in case you're still interested:
you need to install plib from the repository rather than compiling the source.

[http://forums.fedoraforum.org/showthread.php?t=203208](http://forums.fedoraforum.org/showthread.php?t=203208)

---

### Post by FerroPower on 2011-08-26
Thanks I also ran into similar error while trying to compile Torcs

---

