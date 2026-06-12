---
title: "&quot;Undefined Reference to&quot; using make"
date: 2012-04-28
forum: Packaging and Compiling Programs
---

### Post by enabulator on 2012-04-28
Hi - I was trying to install software (dfu-programmer) from source to fix my arduino:[http://arduino.cc/forum/index.php/topic,92148.msg692355.html#msg692355]("http://arduino.cc/forum/index.php/topic,92148.msg692355.html#msg692355"). It is from source so that I can change it for my 16u2 instead of 8u2.

THE PROBLEM: I think I modified the source OK, but after I ```
./boostrap.sh
``` and ```
./configure
```, and then try to ```
make
``` I get errors:

```

...
...
...
dfu.o: In function `dfu_device_init':
/home/paul/Desktop/dfu-programmer-0.5.4/src/dfu.c:419: undefined reference to `libusb_claim_interface'
/home/paul/Desktop/dfu-programmer-0.5.4/src/dfu.c:436: undefined reference to `libusb_release_interface'
/home/paul/Desktop/dfu-programmer-0.5.4/src/dfu.c:426: undefined reference to `libusb_free_device_list'
dfu.o: In function `dfu_make_idle':
/home/paul/Desktop/dfu-programmer-0.5.4/src/dfu.c:814: undefined reference to `libusb_reset_device'
dfu.o: In function `dfu_device_init':
/home/paul/Desktop/dfu-programmer-0.5.4/src/dfu.c:431: undefined reference to `libusb_free_device_list'
collect2: ld returned 1 exit status
make[2]: *** [dfu-programmer] Error 1
make[2]: Leaving directory `/home/paul/Desktop/dfu-programmer-0.5.4/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/paul/Desktop/dfu-programmer-0.5.4'
make: *** [all] Error 2

```

When searching online for an answer I think it might have something to do with headers or linking or pkg-config. I don't have much experience with C (if it's even the issue- the file extensions in the folder have .c and .h). In case this helps you help me:
```
paul@paul-laptop:~/Desktop/dfu-programmer-0.5.4$ pkg-config --cflags libusb-1.0
-I/usr/include/libusb-1.0  
paul@paul-laptop:~/Desktop/dfu-programmer-0.5.4$ pkg-config --libs libusb-1.0

-lusb-1.0
```


I spent hours try to get my board working yesterday. I even tried using Windows. :) Does anyone know what's going on with the ```
make
```?

Thank you. :|

---

### Post by MadCow108 on 2012-04-28
move -lusb-1.0 from LDFLAGS to LIBS in src/Makefile and it should work

or replace LDFLAGS occurrences in configure.ac with LIBS and running bootstrap again

---

### Post by enabulator on 2012-04-28
Thank you.

I didn't get it to work, though. This is from src/Makefile.in

```
INSTALL_PROGRAM = @INSTALL_PROGRAM@
INSTALL_SCRIPT = @INSTALL_SCRIPT@
INSTALL_STRIP_PROGRAM = @INSTALL_STRIP_PROGRAM@
LDFLAGS = @LDFLAGS@
LIBOBJS = @LIBOBJS@
LIBS = @LIBS@
LIBUSB_1_0_CFLAGS = @LIBUSB_1_0_CFLAGS@
```

I changed @LIBS@ to -lusb-1.0

I also tried changing it in the main folder (not src) Makefile(no file extension)
```
INSTALL_SCRIPT = ${INSTALL}
INSTALL_STRIP_PROGRAM = $(install_sh) -c -s
LDFLAGS =  -lusb-1.0  
LIBOBJS = 
LIBS = <-----THIS IS WHERE I MOVED -LUSB-1.0>
LIBUSB_1_0_CFLAGS = -I/usr/include/libusb-1.0  
LIBUSB_1_0_LIBS = -lusb-1.0  
LTLIBOBJS = 
```

I'll try the "or replace LDFLAGS occurrences in configure.ac with LIBS and running bootstrap again"

---

### Post by enabulator on 2012-04-28
In the main folder (not src)/configure.ac I did a Find and Replace "LDFLAGS" --> "LIBS" in all cases and I think I got it installed.

Thank you for your help MadCow108. :) If you don't mind, I'd appreciate it if you told me what that did or what that fixed. Can you refer me to a subject that it was about? Is it a C program language thing, or a general linux thing?

If it's over my head or would take to long to explain that's fine to.

Thanks again for your help. (hopefully now I can use the software to fix my arduino board)

---

### Post by MadCow108 on 2012-04-28
its a bug in the configure.ac, it uses the LDFLAGS variable to tell the compiler which libraries it should link.
This is wrong, for that the LIBS variable should be used (in this case)
LDFLAGS is for other linker flags (like symbolic-functions, as-needed, no-dt-needed etc.)

the makefile outputs something like this:
gcc $CFLAGS $LDFLAGS $OBJECTS $LIBS

ubuntus gcc/ld requires libraries to be placed behind objects needing else it will ignore them (see man ld, there look for --as-needed).

the configure.ac creates a configure and a Makefile.in after you run bootstrap.
the configure creates a Makefile from the Makefile.in when you run it.
make then executes the Makefile
google autotools/automake/autoconf for more information

---

