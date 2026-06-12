---
title: "Installing Snack"
date: 2012-05-09
forum: Packaging and Compiling Programs
---

### Post by jjoysingh on 2012-05-09
I have a similar problem... help me out please.... 
I untar'ed the file ... and went into the /unix folder and typed ... 

 *./configure --prefix=/usr/local --exec-prefix=/usr/local --with-tcl=/usr/local/lib --with-tk=/usr/local/lib --enable-alsa*

That seems to work fine .. 
But when i type... 
[I]
make [/I]

it shows an error... 
as follows ... 

[I]gcc -c -O -fPIC -DUSE_TCL_STUBS -DUSE_TK_STUBS -DALSA  -I/usr/local/include -I/home/joys/speechproject/HTS/tcl8.4.19/generic -I/home/joys/speechproject/HTS/tk8.4.19/generic   -DTCL_81_API -I./../generic -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1  ./../generic/sound.c
In file included from ./../generic/snack.h:34,
                 from ./../generic/sound.c:24:
./../generic/jkAudIO.h:105: fatal error: alsa/asoundlib.h: No such file or directory
compilation terminated.
make: *** [sound.o] Error 1[/I]


if i type make install without make... 
i get this following error...

[I]cp -f libsound.so /lib/snack2.2/
cp: cannot stat `libsound.so': No such file or directory
make: *** [install] Error 1
[/I]
Please please help me out.. been struggling with this for the past two days.....

---

### Post by oldos2er on 2012-05-09
Moved to Packaging and Compiling Programs.

---

### Post by steeldriver on 2012-05-09
I don't know anything about what you're trying to build, but

```
In file included from ./../generic/snack.h:34,
                 from ./../generic/sound.c:24:
./../generic/jkAudIO.h:105: fatal error: alsa/asoundlib.h: No such file or directory
```suggests you are missing the alsa development library (libasound2-dev) package?

---

