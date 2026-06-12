---
title: "Oregon Scientifc USB WX Stations (wmr100/RMS600A) libhid0 / libhid-dev"
date: 2012-04-02
forum: Packaging and Compiling Programs
---

### Post by rec9140 on 2012-04-02
I am trying to compile the wmr100 software for pulling data from USB Oregon Scientific weather stations like RMS600A, WMR100 etc..

on a previous version Maverick 64bit  I can compile this with libhid0/libhid-dev/python-hid 0.2.15_20060325

For what ever reason libhid0 and libhid-dev and python-hid are no longer in the main repos

I found a PPA with them compiled...BUT its 0.2.16.... 

[https://launchpad.net/~yavdr/+archive/main](https://launchpad.net/~yavdr/+archive/main)

I have done BOTH:

1) Pulled the DEBS from the PPA directory, and then use the DEB installer

2) Added the PPA via apt-add-repository  and then pulling via synaptic

Neither results in a compiled program. Same results regardless of the method of lib install.

If the libhid-dev is not installed, it obviously fails to find it and obvisouly would not compile, hence:

```

x0@x-x:~/barnybug-wmr100-511ecd6$ sudo make
cc  `pkg-config libhid --cflags` -pedantic `pkg-config libhid --libs`  wmr100.c   -o wmr100
Package libhid was not found in the pkg-config search path.
Perhaps you should add the directory containing `libhid.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libhid' found
Package libhid was not found in the pkg-config search path.
Perhaps you should add the directory containing `libhid.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libhid' found
wmr100.c:21:17: fatal error: hid.h: No such file or directory
compilation terminated.
make: *** [wmr100] Error 1
rx@x-x:~/barnybug-wmr100-511ecd6$ 


```

Why do this? I wanted to confirm that libhid-dev was being found... so with it installed and re-attempting the compile:

```

rx@x:~$ cd barnybug-wmr100-511ecd6/
x@rec9140-D525TUD:~/barnybug-wmr100-511ecd6$ sudo make
cc  `pkg-config libhid --cflags` -pedantic `pkg-config libhid --libs`  wmr100.c   -o wmr100
wmr100.c: In function &#8216;wmr_print_state&#8217;:
wmr100.c:146:39: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/tmp/ccdy4Cdm.o: In function `wmr_init':
wmr100.c:(.text+0x119): undefined reference to `hid_init'
wmr100.c:(.text+0x155): undefined reference to `hid_new_HIDInterface'
wmr100.c:(.text+0x1bf): undefined reference to `hid_force_open'
wmr100.c:(.text+0x249): undefined reference to `hid_write_identification'
/tmp/ccdy4Cdm.o: In function `wmr_send_packet_init':
wmr100.c:(.text+0x2cd): undefined reference to `hid_set_output_report'
/tmp/ccdy4Cdm.o: In function `wmr_send_packet_ready':
wmr100.c:(.text+0x32e): undefined reference to `hid_set_output_report'
/tmp/ccdy4Cdm.o: In function `wmr_close':
wmr100.c:(.text+0x3a9): undefined reference to `hid_close'
wmr100.c:(.text+0x3eb): undefined reference to `hid_delete_HIDInterface'
wmr100.c:(.text+0x401): undefined reference to `hid_cleanup'
/tmp/ccdy4Cdm.o: In function `wmr_read_packet':
wmr100.c:(.text+0x4a8): undefined reference to `hid_interrupt_read'
collect2: ld returned 1 exit status
make: *** [wmr100] Error 1
rx@x:~/barnybug-wmr100-511ecd6$ 

```

The cast error is ignorable... as this was written for 32bit and not made 64bit compatible, it will compile and run correctly with this error. I actually have a commit to fix this, but I need to solve this before going any further.

If I compile on the other system it compiles fine, and I can copy the compiled program to the Oneiric system and it does run.. BUT obviously thats not a valid path for the future to continue the program on.

Ok.. try it with DEBS for the 0.2.15 version... same results... no compile, same errors.


This appears to be something related to the make file and getting it to find the hid.h file

I've checked paths v. systems... same paths...

I've checked the symbolic links and the files for this and they are the same....

So the Makefile.....

```

CPPFLAGS += `pkg-config libhid --cflags` -pedantic
LDFLAGS += `pkg-config libhid --libs`

wmr100: wmr100.c

clean:
	-rm wmr100


setup_osx:
	sudo cp -r osx/wmr100.kext /System/Library/Extensions/wmr100.kext
	sudo kextload -vt /System/Library/Extensions/wmr100.kext
	sudo touch /System/Library/Extensions

unsetup_osx:
	sudo rm -r -i /System/Library/Extensions/wmr100.kext
	sudo touch /System/Library/Extensions
	echo Please reboot for changes to take effect.

```

I am no c programmer or makefile guru... I've taken over this program since its been abandoned for a year+....

The setup/unsetup stuff do something for os x stuff..... 

I diff'd the hid.h file and there is 2 lines difference [0.2.15 v. 0.2.16] which add 1 function, but the errors are pretty much an inability to find hid.h

Possibly related to default compiler flag(s) changes? [I remember something about that someplace....and it effecting something... not sure if its realted...]

This is for 64bit Oneiric, and I want to resolve this for Precise and the future.....

Any ideas?

---

### Post by oldos2er on 2012-04-02
Moved to Packaging and Compiling Programs.

---

### Post by SevenMachines on 2012-04-03
```
CPPFLAGS += `pkg-config libhid --cflags` -pedantic 
LDFLAGS += `pkg-config libhid --libs`  
wmr100: wmr100.c
```Libs are not LDFLAGS so when make uses its implicit rules to generate a compile command for wmr100.c it puts LDFLAGS (where the libs have wrongly gone) before the object files in the command. As Ubuntu now defaults gcc (ld) to --as-needed for libraries they must now go after the object files, see many, many threads in this forum on this issue :)

As a simple first go I'd try something like...
```
CFLAGS += `pkg-config libhid --cflags` -pedantic
LIBS += `pkg-config libhid --libs`

wmr100: wmr100.c
  cc  ${CFLAGS} -o wmr100 wmr100.c ${LIBS}

```

---

### Post by rec9140 on 2012-04-03
> **SevenMachines said:**
> ```
CPPFLAGS += `pkg-config libhid --cflags` -pedantic 
LDFLAGS += `pkg-config libhid --libs`  
wmr100: wmr100.c
```Libs are not LDFLAGS so when make uses its implicit rules to generate a compile command for wmr100.c it puts LDFLAGS (where the libs have wrongly gone) before the object files in the command. As Ubuntu now defaults gcc (ld) to --as-needed for libraries they must now go after the object files, see many, many threads in this forum on this issue :)


I figured it was related to this...after a bunch of playing...Since I am not into compiling much... I hit a dead end on knowing what to change... 

The original Makefile is from a project long abandoned, but its the only known program for Linux...for OS WX Stations...

Is there one thread, site, HOWTO, wiki or something that outlines this? Reasons, etc... I knew this was going to effect something...  How many other programs pre-change is this going to effect....

> **SevenMachines said:**
> 
As a simple first go I'd try something like...
```
CFLAGS += `pkg-config libhid --cflags` -pedantic
LIBS += `pkg-config libhid --libs`

wmr100: wmr100.c
  cc  ${CFLAGS} -o wmr100 wmr100.c ${LIBS}

```

**THANK YOU**
**THANK YOU****THANK YOU**
**THANK YOU**
**THANK YOU**
**THANK YOU**

RESOLVED!

Now I can work on this abandoned program and others can compile for Oneiric and later...

---

### Post by rec9140 on 2012-04-03
[QUOTE=SevenMachines]Libs are not LDFLAGS so when make uses its implicit rules to generate a compile command for wmr100.c it puts LDFLAGS (where the libs have wrongly gone) before the object files in the command. As Ubuntu now defaults gcc (ld) to --as-needed for libraries they must now go after the object files, see many, many threads in this forum on this issue :)

As a simple first go I'd try something like...
```
CFLAGS += `pkg-config libhid --cflags` -pedantic
LIBS += `pkg-config libhid --libs`

wmr100: wmr100.c
  cc  ${CFLAGS} -o wmr100 wmr100.c ${LIBS}

```[/QUOTE]

One question...if the Makefile for the project is updated... and Jane User comes along pulls this... and compiles on PRE Onereic based systems... what effect? Still compile or the gcc defaults there will cause other issues and there needs to be Makefiles PRE THIS CHANGE, and Makefile POST THIS CHANGE?

---

### Post by SevenMachines on 2012-04-03
It'll work on both, as-needed allows the linker to drop libraries which it believes it doesn't need the symbols from, without it they'll still be linked in to the binary anyway. Order *can* effect linking in general but its much more essential to pay attention when using as-needed.
[http://www.gentoo.org/proj/en/qa/asneeded.xml](http://www.gentoo.org/proj/en/qa/asneeded.xml)
is a decent explanation

---

### Post by rec9140 on 2012-04-06
> **SevenMachines said:**
> It'll work on both, as-needed allows the linker to drop libraries which it believes it doesn't need the symbols from, without it they'll still be linked in to the binary anyway. Order *can* effect linking in general but its much more essential to pay attention when using as-needed.
[http://www.gentoo.org/proj/en/qa/asneeded.xml](http://www.gentoo.org/proj/en/qa/asneeded.xml)
is a decent explanation

I guess I am still not convinced of the need for this change... other than it seems to appeal to a faction Linux which seems to feel that having the smallest compiled program is some metric of honor or something...

Quite honestly, *I* could care less..maybe if I was developing for the 1K of ROM or something in a 68HC11 or some thing fine... but then I would not use C either...I would be using native assembler for it.. been there done it as part of the senior EE project.

This change seems to be in my view a way to really break things to meet some specious "geeky" metric.

I looked at gcc -dumpspecs... and tried to find the default specs file that gcc is using as I think it will best to revert this change to retain that of the norm, but the way this has been built will require specs files to replace this...

I think this change really needs some re-consideration from those OUTSIDE the c and gcc inner circle.

---

### Post by oretovalley on 2012-07-11
> **SevenMachines said:**
> ```
CPPFLAGS += `pkg-config libhid --cflags` -pedantic 
LDFLAGS += `pkg-config libhid --libs`  
wmr100: wmr100.c
```Libs are not LDFLAGS so when make uses its implicit rules to generate a compile command for wmr100.c it puts LDFLAGS (where the libs have wrongly gone) before the object files in the command. As Ubuntu now defaults gcc (ld) to --as-needed for libraries they must now go after the object files, see many, many threads in this forum on this issue :)

As a simple first go I'd try something like...
```
CFLAGS += `pkg-config libhid --cflags` -pedantic
LIBS += `pkg-config libhid --libs`

wmr100: wmr100.c
  cc  ${CFLAGS} -o wmr100 wmr100.c ${LIBS}

```

I can not fill, I modified the makefile as indicated, but I get this error:

```
giuseppe@giuseppe-HP-Mini-110-3100:~/Scaricati/barnybug-wmr100-511ecd6$ make
Makefile:5: *** separatore  mancante.  Arresto."

```

If you do not edit the makefile, the build fails:

```

giuseppe@giuseppe-HP-Mini-110-3100:~/Scaricati/barnybug-wmr100-511ecd6$ make
cc  `pkg-config libhid --cflags` -pedantic `pkg-config libhid --libs`  wmr100.c   -o wmr100
/tmp/cc9xr8qp.o: In function `wmr_init':
wmr100.c:(.text+0xeb): undefined reference to `hid_init'
wmr100.c:(.text+0x120): undefined reference to `hid_new_HIDInterface'
wmr100.c:(.text+0x190): undefined reference to `hid_force_open'
wmr100.c:(.text+0x21b): undefined reference to `hid_write_identification'
/tmp/cc9xr8qp.o: In function `wmr_send_packet_init':
wmr100.c:(.text+0x29f): undefined reference to `hid_set_output_report'
/tmp/cc9xr8qp.o: In function `wmr_send_packet_ready':
wmr100.c:(.text+0x302): undefined reference to `hid_set_output_report'
/tmp/cc9xr8qp.o: In function `wmr_close':
wmr100.c:(.text+0x369): undefined reference to `hid_close'
wmr100.c:(.text+0x3a4): undefined reference to `hid_delete_HIDInterface'
wmr100.c:(.text+0x3b3): undefined reference to `hid_cleanup'
/tmp/cc9xr8qp.o: In function `wmr_read_packet':
wmr100.c:(.text+0x44e): undefined reference to `hid_interrupt_read'
collect2: ld returned 1 exit status
make: *** [wmr100] Errore 1

```

---

