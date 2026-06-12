---
title: "Error when trying to install a program using &quot;make&quot;"
date: 2012-05-18
forum: Packaging and Compiling Programs
---

### Post by andaryfaysal on 2012-05-18
I am not sure if this is the correct section of the forum to post in, so please guide me if I'm wrong.
Anyways, I am trying to install this program that would allow me to use my smart phone as a remote control for my laptop over bluetooth. The program came in a tarball, and I went thru the readme file and installed all the prerequisites which were:
       bluez
       bluez-utils
       libbluetooth
       build-essentials (sometimes named build-essential)
       libbluetooth-dev
       x11proto-core-dev
       libxtst-dev        
       libimlib2
       libimlib2-dev
       giblib1
       giblib-dev

After that I ran the usual "./configure", "make" and "make install" commands.

The configure went well I presume, and the Makefile was created, but once I issue the "make" command, I get the following output:

$ make
Making all in src
make[1]: Entering directory `/media/disk/Setups/Freemoted/freemoted-1.3.3/src'
make  all-am
make[2]: Entering directory `/media/disk/Setups/Freemoted/freemoted-1.3.3/src'
/bin/bash ../libtool --tag=CC   --mode=link gcc -DSYSCONFDIR=/usr/local/etc -g -O2   -o freemoted freemoted-main.o freemoted-screen.o freemoted-threadutil.o freemoted-lockutil.o  -lgiblib -lXtst -lX11 -lbluetooth -lpthread 
libtool: link: gcc -DSYSCONFDIR=/usr/local/etc -g -O2 -o freemoted freemoted-main.o freemoted-screen.o freemoted-threadutil.o freemoted-lockutil.o  -lgiblib -lXtst -lX11 -lbluetooth -lpthread
/usr/bin/ld: freemoted-main.o: undefined reference to symbol 'imlib_context_set_operation'
/usr/bin/ld: note: 'imlib_context_set_operation' is defined in DSO /usr/lib/libImlib2.so.1 so try adding it to the linker command line
/usr/lib/libImlib2.so.1: could not read symbols: Invalid operation
collect2: ld returned 1 exit status
make[2]: *** [freemoted] Error 1
make[2]: Leaving directory `/media/disk/Setups/Freemoted/freemoted-1.3.3/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/media/disk/Setups/Freemoted/freemoted-1.3.3/src'
make: *** [all-recursive] Error 1

The installation cannot be completed due to this error. Does anybody have suggestions?
Thank you.

---

### Post by oldos2er on 2012-05-18
Moved to Packaging and Compiling Programs.

---

### Post by steeldriver on 2012-05-20
I had a look in the configure script and it does not appear to mention libImlib2 at all - I suspect it's an oversight by the package maintainer

If you feel like trying a bit of hackery you could do exactly what 'make' suggests i.e. edit the src/Makefile and add

```
-lImlib2
```somewhere on the LIBS line (try right at the front, before -lgiblib)

Regardless it would probably be polite to contact the maintainer to let them know

---

### Post by andaryfaysal on 2012-05-21
Thank you, it worked :-)

---

