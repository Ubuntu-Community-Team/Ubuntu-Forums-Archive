---
title: "Howto: Install and Run Libsafe on a 32bit computer ie: i386"
date: 2008-06-25
forum: Outdated Tutorials &amp; Tips
---

### Post by nowshining on 2008-06-25
KUBUNTU 7.10, KDE ver. 3.5.9 - however it should be universal and shouldn't be dependent on the desktop environment, etc..

WHAT IS LIBSAFE? Libsafe is a security library that gets pre-loaded before every other lib. What it does is tries to protect ones computer beforehand of buffer overflows. When this happens it kills the offending application of which a restart of the application is needed. By doing this it replaces certain libc function calls with it's own. However libc5 & such versions aren't supported:"libc5 linked programs are not supported."

First let's use a test program: sudo apt-get install paxtest

then paxtest blackhat

it should show the following as vulnerable:

strcpy & memcpy & all associated

okay - u can convert the i386 to deb urself using alien and fakeroot or install the one I already converted:

[Download_LibSafe](http://www.4shared.com/file/52515217/500da585/libsafe_20-17_i386.html)

Download the deb first - don't install yet.

first: sudo apt-get install ld.so.preload-manager

second: install the deb.

3rd: sudo /bin/bash or su root

4th: issue the following:

LD_PRELOAD=/lib/libsafe.so.2

then

export LD_PRELOAD

then

echo '/lib/libsafe.so.2' >> /etc/ld.so.preload

5th: paxtest blackhat. --see figure A

5a: If you prelink don't forget to run prelink to prelink the new library u just installed first or after testing.

Figure: A: something like the below should show up now in the paxtest:

```
 
Return to function (strcpy)              : Libsafe version 2.0.16
Detected an attempt to write across stack boundary.
Terminating /home/nowshining/Desktop/paxtest-0.9.7-pre4/rettofunc1.
    uid=1000  euid=1000  pid=17397
Call stack:
    0xa8f81871	/lib/libsafe.so.2.0.16
    0xa8f8197a	/lib/libsafe.so.2.0.16
    0x8048805	/home/nowshining/Desktop/paxtest-0.9.7-pre4/rettofunc1
    0x80489d1	/home/nowshining/Desktop/paxtest-0.9.7-pre4/rettofunc1
    0xa8e3704b	/lib/libc-2.6.1.so
Overflow caused by strcpy()
Killed
Return to function (strcpy, RANDEXEC)    : Libsafe version 2.0.16
Detected an attempt to write across stack boundary.
Terminating /home/nowshining/Desktop/paxtest-0.9.7-pre4/rettofunc1x.
    uid=1000  euid=1000  pid=17400
Call stack:
    0xa4775871	/lib/libsafe.so.2.0.16
    0xa477597a	/lib/libsafe.so.2.0.16
    0x80489c5	/home/nowshining/Desktop/paxtest-0.9.7-pre4/rettofunc1x
    0x8048971	/home/nowshining/Desktop/paxtest-0.9.7-pre4/rettofunc1x
    0xa462b04b	/lib/libc-2.6.1.so
Overflow caused by strcpy()
Killed
Return to function (memcpy)              : Libsafe version 2.0.16
Detected an attempt to write across stack boundary.
Terminating /home/nowshining/Desktop/paxtest-0.9.7-pre4/rettofunc2.
    uid=1000  euid=1000  pid=17403
Call stack:
    0xae444871	/lib/libsafe.so.2.0.16
    0xae444c5d	/lib/libsafe.so.2.0.16
    0x804876c	/home/nowshining/Desktop/paxtest-0.9.7-pre4/rettofunc2
    0x8048911	/home/nowshining/Desktop/paxtest-0.9.7-pre4/rettofunc2
    0xae2fa04b	/lib/libc-2.6.1.so
Overflow caused by memcpy()
Killed
Return to function (memcpy, RANDEXEC)    : Libsafe version 2.0.16
Detected an attempt to write across stack boundary.
Terminating /home/nowshining/Desktop/paxtest-0.9.7-pre4/rettofunc2x.
    uid=1000  euid=1000  pid=17406
Call stack:
    0xb1018871	/lib/libsafe.so.2.0.16
    0xb1018c5d	/lib/libsafe.so.2.0.16
    0x804892c	/home/nowshining/Desktop/paxtest-0.9.7-pre4/rettofunc2x
    0x80488e1	/home/nowshining/Desktop/paxtest-0.9.7-pre4/rettofunc2x
    0xb0ece04b	/lib/libc-2.6.1.so
Overflow caused by memcpy()
Killed

```

Site url w/source: [LibSafe_Main_Site](http://www.research.avayalabs.com/gcm/usa/en-us/initiatives/all/nsr.htm&Filter=ProjectTitle:Libsafe&Wrapper=LabsProjectDetails&View=LabsProjectDetails)

if you see the deb link - it shows an error page on the debian site so..umm..they prob. removed it or changed the url.

If you create a deb file for 64-bit computers or convert the RPM to 64bit, etc.. post and i'll change the title to remove the 32bit part and add ur link in the top post here of where to download the libsafe 64bit deb.

---

### Post by gasull on 2009-11-27
The version in the website is old, so you can just install in Ubuntu 9.10 the old version that was included with Dapper.  I did and it works.

[http://packages.ubuntu.com/dapper/libsafe](http://packages.ubuntu.com/dapper/libsafe)

EDIT: You need to install this package first: [http://packages.ubuntu.com/dapper/ld.so.preload-manager](http://packages.ubuntu.com/dapper/ld.so.preload-manager)

---

### Post by 3rdalbum on 2009-11-27
Do you really need this? Karmic has some extra protection against buffer overflows on 32-bit systems. And 64-bit systems have had this sort of thing for ages. And it's compatible with libc5.

---

### Post by gasull on 2009-11-27
> **3rdalbum said:**
> Do you really need this? Karmic has some extra protection against buffer overflows on 32-bit systems. And 64-bit systems have had this sort of thing for ages. And it's compatible with libc5.

As far as I know that extra protection is added when compiling.  Am I right?  [From Wikipedia]("http://en.wikipedia.org/wiki/Buffer_overrun#Buffer_overflow_protection"):

> Buffer overflow protection is used to detect the most common buffer overflows by checking that the stack has not been altered when a function returns. If it has been altered, the program exits with a segmentation fault. Three such systems are Libsafe,[18] and the StackGuard[19] and ProPolice[20] gcc patches.

What happens if you want to run a program that doesn't come from the Ubuntu repositories?  What happens with programs run under Wine?

To run the program "foo" with libsafe enter this in the terminal:

```
libsafe foo
```

This probably adds some extra protection, but I wouldn't bet anything on it.  The real security comes from knowing what you are doing and running only software that you trust.

---

