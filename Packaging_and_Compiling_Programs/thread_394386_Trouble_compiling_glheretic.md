---
title: "Trouble compiling glheretic"
date: 2007-03-26
forum: Packaging and Compiling Programs
---

### Post by mrbiggles on 2007-03-26
I trying to compile glheretic from source, which i got here: [http://heretic.linuxgames.com/homepage3.html]("http://heretic.linuxgames.com/homepage3.html")

When I try to compile using make glheretic, I get this error:
w_wad.c:37:24: error: asm/system.h: No such file or directory
make: *** [depsdlogl] Error 1

What packages do I have to download to fix this problem?

---

### Post by will_in_wi on 2007-03-26
linux-headers-generic should be the package

---

### Post by mrbiggles on 2007-03-27
It still doesn't work.  Any other suggestions?

---

### Post by hod139 on 2007-03-27
Have you installed the package build-essential?

---

### Post by mrbiggles on 2007-03-27
Yes I have.

---

### Post by hod139 on 2007-03-28
Does the file 
/usr/include/asm/system.h 
exist on your system.  I thought that file was installed by the build-essential package.

---

### Post by mrbiggles on 2007-03-29
No, system.h is not in that folder.  The contents of it are:
```
a.out.h       ioctl.h    mtrr.h         shmparam.h      timex.h
atomic.h      ioctls.h   page.h         sigcontext32.h  types.h
auxvec.h      io.h       param.h        sigcontext.h    ucontext.h
boot.h        ipcbuf.h   poll.h         siginfo.h       unistd.h
bootsetup.h   irq.h      posix_types.h  signal.h        user.h
byteorder.h   ldt.h      prctl.h        socket.h        vm86.h
cpufeature.h  linkage.h  ptrace.h       sockios.h       vsyscall32.h
debugreg.h    mce.h      resource.h     statfs.h        vsyscall.h
elf.h         mman.h     sembuf.h       stat.h
errno.h       msgbuf.h   setup.h        termbits.h
fcntl.h       msr.h      shmbuf.h       termios.h

```

---

### Post by hod139 on 2007-03-29
Are you running edgy?  I'm guessing yes.  I looks like asm/system.h exists in dapper,  but not in edgy.  This must mean that asm/system.h was deprecated, and glheretic never updated.  

Maybe someone else can help you more, I don't think I can do anything else.

---

### Post by Abu Yoav on 2007-03-31
I'm having exactly the same problem. I'm trying to compile picprg ([http://cole.homedns.org/picprg.php)](http://cole.homedns.org/picprg.php)).

> **hod139 said:**
> This must mean that asm/system.h was deprecated, and glheretic never updated.


If so, could someone please post how the source should be updated and/or how I can hack my system so that the above files do compile?

Abu Yoav

---

### Post by nbeyer on 2007-04-14
I've run into this issue on Feisty Fawn 7.04 (beta) as well. I've logged a bug about it [1].

I've tried installing "linux-headers-generic" and any variation I could think of, but nothing seemed to setup the linux headers correctly.

[1] [https://launchpad.net/bugs/104561](https://launchpad.net/bugs/104561)

---

### Post by Corin-EU on 2008-10-06
To get glheretic 1.2 to successfully compile on Ubuntu Hardy Heron you need to make two changes to the source code.

First, remove the line

#include <asm/system.h>

from w_wad.c

If you read the comments in the source code, you will see that this was included as a work around for a problem in the Linux 2.2.14 kernel.  The kernel version has moved on somewhat since then.

Secondly, in the musserv directory, in the file musserver.h, remove the following lines

/* Seems AWE began to work on 2.1.64 */
#  if (LINUX_VERSION_CODE > 131392)
#    define ENABLE_AWE
#    include <linux/awe_voice.h>
#  endif

The seperate AWE functionality was part of OSS, and awe_voice.h is not part of the ALSA library.  The sound server will still function without this.  And you probably do not have an IDE SB AWE card in your PC anyway.

Additionally, to remove a warning message, in the Makefile for the line

COPT.x86 = -O2 -fomit-frame-pointer -mcpu=i586 -march=i586 -D__32BIT__ \

remove the -mcpu=i586 option, and if your CPU is better than a pentium, you should change -march=i586 to -march=i686

When everything is built, you will need to ensure that the following files are present in your destination directory

+++++++ Path is /usr/local/games/heretic

total 5612
   4 drwxr-sr-x 2 root sys    4096 2008-10-06 06:02 ./
   4 drwxr-sr-x 3 root sys    4096 2008-10-06 05:44 ../
  12 -r--r--r-- 1 root sys   12288 1999-08-09 10:14 blood1.raw
  12 -r--r--r-- 1 root sys   12288 1999-08-09 10:15 blood2.raw
   4 -r--r--r-- 1 root sys    3072 1999-08-09 10:17 blood3.raw
   4 -r--r--r-- 1 root sys    3072 1999-08-09 10:19 blood4.raw
   4 -r--r--r-- 1 root sys    3072 1999-08-09 10:21 blood5.raw
   4 -r--r--r-- 1 root sys    3072 1999-08-09 10:22 blood6.raw
   4 -r--r--r-- 1 root sys    3072 1999-08-10 12:42 bullet1.raw
 448 -r-xr-xr-x 1 root sys  454652 2008-10-06 05:41 glheretic*
  16 -r--r--r-- 1 root sys   16384 1999-06-01 13:06 haze.raw
5016 -r--r--r-- 1 root sys 5120920 1999-06-30 14:39 heretic_share.wad
  24 -r-xr-xr-x 1 root sys   22624 2008-10-06 05:41 musserver*
  24 -r-xr-xr-x 1 root sys   20952 2008-10-06 05:41 sndserver*
  32 -r-xr-xr-x 1 root sys   31658 2003-12-09 00:21 XHeretic-launch*

As a simple shell script to fire up glheretic, you could use something akin to

#! /bin/sh

#*****************************************************************************#
#|
#|  file : ${SH}/quake
#|
#*---------------------------------------------------------------------------*#

HERETICHOME="/usr/local/games/heretic"
export HERETICHOME

cd ${HERETICHOME}

${HERETICHOME}/glheretic

exit 0

#*****************************************************************************#


If you want to use the fancy XHeretic-launch script you will need to edit that and replace
the three lines at the top of the file from

#!/bin/sh
# the next line restarts using wish \
exec wish8.0 "$0" "$@"

to simply

#! /usr/bin/wish

and to also change the line

if [catch {open "|xheretic $options |& cat" r+} input] {


to

if [catch {open "|glheretic $options |& cat" r+} input] {


In order for this script to work properly you will need to cd to the directory to invoke it, or have a similar shell script to the above,
with

${HERETICHOME}/glheretic

replaced with

${HERETICHOME}/XHeretic-launch


I hope this is of help to you.

---

### Post by RickKnight on 2008-11-23
Great HOWTO. I have just one problem. When I try to use XHeretic-launch to start GLHeretic-1.2 and make my selections and then press Start I get an error message in the XHereticLog box...

/usr/local/games/glheretic-1.2/musserver: error reading msg. pipe

The came works fin if I start it from the command line. Any idea how to fix the error?

Thanks,
Rick

---

### Post by Outlit on 2008-11-25
Are you interested in making absolutely free money?

Nothing better then Bux.to!

Click here and join today -----V

[[IMG]http://i423.photobucket.com/albums/pp318/Outlit/banner.png[/IMG]]("http://bux.to/?r=Outlit")

---

### Post by badrianiulian on 2009-06-12
> **RickKnight said:**
> Great HOWTO. I have just one problem. When I try to use XHeretic-launch to start GLHeretic-1.2 and make my selections and then press Start I get an error message in the XHereticLog box...

/usr/local/games/glheretic-1.2/musserver: error reading msg. pipe

The came works fin if I start it from the command line. Any idea how to fix the error?

Thanks,
Rick

With the full version (heretic.wad) there are no such errors. I bought the game ages ago. :P
It crashes when trying to play the demo in background form the shareware version.

Tested with Hardy with the 'padsp' wrapper (onboard soundcard, hardware mixing not supported). Worked also by killing pulseaudio and artsd.

Also needed to modify the script:

```
#! /bin/sh

#************************************************* ****************************#
#|
#| file : ${SH}/quake
#|
#*---------------------------------------------------------------------------*#

HERETICHOME="/usr/local/games/heretic"
export PATH=${HERETICHOME}

cd ${HERETICHOME}

${HERETICHOME}/glheretic

exit 0

#************************************************* ****************************#
```

Without this modification the errors were:
```
sh: musserver: command not found
sh: sndserver: command not found
```

Also by compiling the binaries on an older version of linux (mine was a SUSE 8.0 Pro at work), you could get rid of a lot of warnings. After that just copy the binaries to your instalation folder on your ubuntu distro (worked on Hardy)

---

