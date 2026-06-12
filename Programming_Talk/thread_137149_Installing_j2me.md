---
title: "Installing j2me"
date: 2006-02-27
forum: Programming Talk
---

### Post by Grampa on 2006-02-27
Hi,

Sorry if this is question has already been asked, but form my searches i haven't found anything!!

I've been trying to install j2me but this error apears

Checking for Java ME CDC classes to compile ...
Checking for test classes to compile ...
Linking ../../build/linux-x86-suse/bin/cvm
../../build/linux-x86-suse/obj/UNIXProcess_md.o: In function `sigchld_handler':
UNIXProcess_md.c:(.text+0x8f): undefined reference to `__libc_wait'
collect2: ld returned 1 exit status
make: *** [../../build/linux-x86-suse/bin/cvm] Error 1

I've already seen this post:

[http://ubuntuforums.org/printthread.php?t=8903](http://ubuntuforums.org/printthread.php?t=8903)

but it didn't help!!

if anyone could shed some light on this i'd apreciatte it.

---

### Post by Grampa on 2006-03-01
Hi,

Sorry if this is question has already been asked, but form my searches i haven't found anything!!

I've been trying to install j2me but this error apears

Checking for Java ME CDC classes to compile ...
Checking for test classes to compile ...
Linking ../../build/linux-x86-suse/bin/cvm
../../build/linux-x86-suse/obj/UNIXProcess_md.o: In function `sigchld_handler':
UNIXProcess_md.c:(.text+0x8f): undefined reference to `__libc_wait'
collect2: ld returned 1 exit status
make: *** [../../build/linux-x86-suse/bin/cvm] Error 1

I've already seen this post:

[http://ubuntuforums.org/printthread.php?t=8903](http://ubuntuforums.org/printthread.php?t=8903)

but it didn't help!!

if anyone could shed some light on this i'd apreciatte it!
I'm really desperate!!
thanks in advance to any help possible
[B][COLOR="DarkRed"]
UPDATE[/COLOR][/B]

As i was reading this i found that i hadn't provided all the info about my problem, so here it goes

1st - I downloaded Sun Community Source Licensing (SCSL) - CDC - Download
2nd - In the folder /foundation/build/linux-x-suse\ I used the make file
3rd - In order to do the 2nd I needed a java compiler (javac) so I had to install the j2re1.4 and j2sdk1.4 and all the depencies needed (used debfoster)
4th - I linked gcc to cc in order to continue the instalattion and then the error described above apeared

I hope that this additonal info will help 'cause i'm really desperate

Thanks in advance for any help provided

Grampa

---

### Post by blastus on 2006-03-03
You don't actually install the J2ME. You install the J2SE and then you install Sun's Wireless Toolkit (SWT) along with the manufacturer's SDK for the device you are targetting. However, most if not all, manufacturers only provide SDKs for Windows. So chances are you'll be stuck using the generic emulator that comes with the SWT if you are developing on Linux. 

In theory you *may* be able to develop/build device-specific J2ME applications without installing the manufacturers' SDK but you would need figure out a lot of things such as compiling, preverification, packaging, segmentation, signing, and installing. Unfortunately, the J2ME platform is currently fragmented.

What are you trying to do? What device are you targetting?

---

### Post by Grampa on 2006-03-06
Hi, 

First of all i'd like to thank you for the info,  my target is a mobile bot so i intended to have the minimum java there as possible, so I tried to complile the j2me using the makefile as explained bellow:

**[COLOR="DarkRed"]NEW INFO[/COLOR]**

1st - I downloaded Sun Community Source Licensing (SCSL) - CDC - Download
2nd - In the folder /foundation/build/linux-x-suse\ I used the make file
3rd - In order to do the 2nd I needed a java compiler (javac) so I had to install the j2re1.4 and j2sdk1.4 and all the depencies needed (used debfoster)
4th - I linked gcc to cc in order to continue the instalattion and then the error described above apeared

My final intention is to manualy install j2me, in order to reduce the java presence.
I hope that this new  info helps

Thanks in advance

Grampa

---

### Post by blastus on 2006-03-07
Sorry Grampa I've never used SCSL before and I've only worked on CLDC/MIDP devices. Come to think of it maybe the WTK doesn't support CDC devices which is what you really need. I've also never heard of a "mobile bot." I thought maybe you were using a BlackBerry, Nokia, or iDEN phone, but those are CLDC/MIDP devices.

Why not first try installing the SCSL-CDC environment on Windows as it is probably better supported on Windows? Sorry I couldn't help you more, I sure hope you figure it out.

---

