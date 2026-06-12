---
title: "[SOLVED] &amp;quot;Make&amp;quot; command always gives errors."
date: 2008-11-27
forum: New to Ubuntu
---

### Post by CJ Master on 2008-11-27
No matter what tutorial I use, no matter how I do it, this always happens when I attempt to use the make command...

```
cjmaster@cjmaster-desktop:~/Desktop/SheepShaver-2.3/src/Unix$ make
make: *** No targets specified and no makefile found.  Stop.

```

Any help?:confused:

---

### Post by loell on 2008-11-27
maybe there's **./configur**e if not, first do **./autogen.sh**

---

### Post by Paqman on 2008-11-27
Looks like there's a 32-bit .deb available on [this page]("http://sudan.ubuntuforums.com/showthread.php?t=670336"). Try that instead.

---

### Post by stevek123 on 2008-11-28
This may not be much help, but I'll try... I've successfully compiled source code and 'made' programs. In each case it was necessary to compile all the necessary parts, and configure them, before running the make command. Downloading the code was not enough in and of itself - had to config it. In most of these cases, I was able to get some direction/help from 'readme' and 'install' files that were included in the compile process. I'm not familiar with your prog and cant give more specific help. Good luck!

---

### Post by CJ Master on 2008-11-28
Yes I already did the autogen, and I have no idea how to config manually. Paqman, I can't seem to download that file, it asks me to log in every time, even if i'm already there.

Thanks for all the help!

---

### Post by stevek123 on 2008-11-28
for the config, if I remember right, in terminal you open the folder with the compiled code and run ./configure - might need to sudo... With 2 diff progs I do remember failures in the config but the errors it gave were enough info to help me add the necessary progs/files (sometimes it was an entire prog build :( and in another case it was to use Synaptic to add the assoc -dev files.... you DO need the proper library and development files to configure and make code...

---

### Post by adult swim on 2008-11-28
try this link for the deb.  its at the bottom of the first post
[http://ubuntuforums.org/showthread.php?p=6042005](http://ubuntuforums.org/showthread.php?p=6042005)

---

### Post by jamesrl on 2008-11-28
What's the output from ./autogen.sh ?
Also what are the contents of the src/Unix directory?  

This autogen (configure) step is likely failing, which doesn't produce a Makefile, which the command make is complaining about.  Usually the autogen/configure failing, tells you need some packages to install (usually the -dev versions).

---

### Post by Keen101 on 2008-11-28
[http://ubuntuforums.org/attachment.php?attachmentid=56717&d=1200586675](http://ubuntuforums.org/attachment.php?attachmentid=56717&d=1200586675)

---

### Post by CJ Master on 2008-11-28
Well I finally installed the deb, but I want to figure out how I'd make anyways, for the future reference. Heres the output:

```
cjmaster@cjmaster-desktop:~/Desktop/SheepShaver-2.3/src/Unix$ ./autogen.sh
 + Running aclocal: configure.ac:267: warning: macro `AM_PATH_GTK' not found in library
done.
 + Running autoheader: done.
 + Running autoconf: configure.ac:121: error: possibly undefined macro: AC_MSG_WARN
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.ac:267: error: possibly undefined macro: AM_PATH_GTK
done.
 + Running 'configure ':
   ** If you wish to pass arguments to ./configure, please
   ** specify them on the command line.
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking whether make sets $(MAKE)... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for file... /usr/bin/file
checking for perl... /usr/bin/perl
checking for PowerPC target CPU... no
checking for mon... no
configure: WARNING: Could not find mon, ignoring --with-mon.
checking for sem_init in -lposix4... no
checking for cos in -lm... yes
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for pthread_create in -lpthread... yes
checking for pthread_cancel... yes
checking for pthread_cond_init... yes
checking for pthread_testcancel... yes
checking for pthread_mutexattr_setprotocol... yes
checking for pthread_mutexattr_settype... yes
checking for pthread_mutexattr_setpshared... yes
checking for sem_init... yes
checking linux/fb.h usability... yes
checking linux/fb.h presence... yes
checking for linux/fb.h... yes
checking for XF86DGAQueryExtension in -lXxf86dga... no
configure: WARNING: Could not find XFree86 DGA extension, ignoring --enable-xf86-dga.
checking for XF86VidModeQueryExtension in -lXxf86vm... no
configure: WARNING: Could not find XFree86 VidMode extension, ignoring --enable-xf86-vidmode.
checking for pkg-config... /usr/bin/pkg-config
checking for GTK+ - version >= 1.3.15... yes (version 2.14.4)
./configure: line 7919: syntax error near unexpected token `1.2.0,'
./configure: line 7919: `  AM_PATH_GTK(1.2.0,'
cjmaster@cjmaster-desktop:~/Desktop/SheepShaver-2.3/src/Unix$ make
make: *** No targets specified and no makefile found.  Stop.
cjmaster@cjmaster-desktop:~/Desktop/SheepShaver-2.3/src/Unix$ sudo checkinstall

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

*** No known documentation files were found. The new package 
*** won't include a documentation directory.

Please write a description for the package.
End your description with an empty line or EOF.
>> Emulator for Mac
>> EOF
>> 

*****************************************
**** Debian package creation selected ***
*****************************************

*** Warning: The package name "Unix" contains upper case
*** Warning: letters. dpkg might not like that so I changed
*** Warning: them to lower case.

This package will be built according to these values: 

0 -  Maintainer: [ root@cjmaster-desktop ]
1 -  Summary: [ Emulator for Mac ]
2 -  Name:    [ unix ]
3 -  Version: [  ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ Unix ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]
11 - Provides: [ unix ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
make: *** No rule to make target `install'.  Stop.

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

cjmaster@cjmaster-desktop:~/Desktop/SheepShaver-2.3/src/Unix$ 

```

---

### Post by adult swim on 2008-11-28
anytime that ./configure fails the file will not make because no makefile was made.  see what it says after you ran make, make: *** No targets specified and no makefile found.  Stop., the error that ./configure presents is that there is a syntax error in line 7919 of the ./configure script.  im no compiling/building guru but that seems to be the place you need to explore.

---

### Post by CJ Master on 2008-11-28
> **adult swim said:**
> anytime that ./configure fails the file will not make because no makefile was made.  see what it says after you ran make, make: *** No targets specified and no makefile found.  Stop., the error that ./configure presents is that there is a syntax error in line 7919 of the ./configure script.  im no compiling/building guru but that seems to be the place you need to explore.

Well it came straight from their site lol, maybe I'm missing some files?

---

### Post by mc4man on 2008-11-28
In this case i'd do this
cd to src/Unix and then run your ./configure or first maybe ./configure --help 
So your at the Unix$ prompt  
Ex.  doug@doug-desktop:~/Desktop/SheepShaver-2.3/src/Unix$ ./configure

A 'straight ./configure produced this
> ...................................clipped
SheepShaver configuration summary:

SDL support ...................... : none
FBDev DGA support ................ : yes
XFree86 DGA support .............. : yes
XFree86 VidMode support .......... : yes
Using PowerPC emulator ........... : yes
Enable JIT compiler .............. : yes
Enable video on SEGV signals ..... : yes
ESD sound support ................ : yes
GTK user interface ............... : gtk2
mon debugger support ............. : no
Addressing mode .................. : real
Bad memory access recovery type .. : siginfo

Configuration done. Now type "make".

It's always good to ck. configure --help, running a 'straight' ./configure isn't always optimal

Edit : I went ahead and built, ran from build folderand it opened fine (don't have a max Os so can't use per se

To test run after a make (with out installing you'd do this

Ex.
doug@doug-desktop:~/Desktop/SheepShaver-2.3/src/Unix$ ./SheepShaver
SheepShaver V2.3-Pre (Nov 28 2008) by Christian Bauer and Mar"c" Hellwig

---

### Post by stevek123 on 2008-11-28
I played this game of making a tough prog just to get the experience also :) - and it was tough -the code was very incomplete - a college project I think.... anyway, yes, as these others have added, the config did not compile. and then it wouldnt make. Looking at the stuff you posted from the terminal output, I'd guess you're still missing a * - dev file and assoc libraries (AM_PATH_GTK) that need to be found thru synaptic (or similar). Generally when looking at the outputs, warnings can be ignored, but errors are the thing to fix....

---

### Post by CJ Master on 2008-11-28
Yea, yours is tiny, but look at what my straight config is spitting out.

```
cjmaster@cjmaster-desktop:~/Desktop/SheepShaver-2.3/src/Unix$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking whether make sets $(MAKE)... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for file... /usr/bin/file
checking for perl... /usr/bin/perl
checking for PowerPC target CPU... no
checking for mon... no
configure: WARNING: Could not find mon, ignoring --with-mon.
checking for sem_init in -lposix4... no
checking for cos in -lm... yes
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for pthread_create in -lpthread... yes
checking for pthread_cancel... yes
checking for pthread_cond_init... yes
checking for pthread_testcancel... yes
checking for pthread_mutexattr_setprotocol... yes
checking for pthread_mutexattr_settype... yes
checking for pthread_mutexattr_setpshared... yes
checking for sem_init... yes
checking linux/fb.h usability... yes
checking linux/fb.h presence... yes
checking for linux/fb.h... yes
checking for XF86DGAQueryExtension in -lXxf86dga... no
configure: WARNING: Could not find XFree86 DGA extension, ignoring --enable-xf86-dga.
checking for XF86VidModeQueryExtension in -lXxf86vm... no
configure: WARNING: Could not find XFree86 VidMode extension, ignoring --enable-xf86-vidmode.
checking for pkg-config... /usr/bin/pkg-config
checking for GTK+ - version >= 1.3.15... yes (version 2.14.4)
./configure: line 7919: syntax error near unexpected token `1.2.0,'
./configure: line 7919: `  AM_PATH_GTK(1.2.0,'

```

If I don't run a straight configure what would i run?

---

### Post by loell on 2008-11-28
**checking for GTK+ - version >= 1.3.15**

the software is old :( needs a component upgrade , or you need to downgrade. ;)

---

### Post by CJ Master on 2008-11-28
Well, striking out the downgrade option, how do I upgrade it?

---

### Post by stevek123 on 2008-11-28
in my 'tough build', I had a similar 'downgrade' issue too that I had to deal with ... I was able to just add the older version in addition to the newer thru synaptic and the prog then found what it was looking for - and I didnt have to uninstall the newer ver that it didnt like.....

---

### Post by mc4man on 2008-11-28
> Yea, yours is tiny
> ...................................clipped

I removed the whole configure, just showed the results
> 
If I don't run a straight configure what would i run? 

Well I have no use for this app or have ever used, running ./configure --help will show you what's enabled by default and what's disabled by default.

When 'things' are enabled and you don't have the proper packages installed your configure can fail

Ex.

> configure: WARNING: Could not find XFree86 DGA extension, ignoring --enable-xf86-dga.
checking for XF86VidModeQueryExtension in -lXxf86vm... no

you'd need to install libXxf86dga-dev, libXxf86vm-dev (look in synaptic

It's basically a process of working your way thru.

If something was enabled by default and not necessary you'd add to your configure   ./configure --disable-<whatever>

(or however the syntax is shown in ./configure --help

Most sources install to /usr/local, you may wish to install to /usr (where most apps install, then again adding to 
./configure --prefix=/usr --disable-<whatever>  ect.ect.

(not saying that's the case here.

---

### Post by loell on 2008-11-28
> **CJ Master said:**
> Well, striking out the downgrade option, how do I upgrade it?

oh.. uhmm.. how do break this up to you? :D

not only you have to edit the configure file( configure.am / configure.ac ?) which is relatively easy, should just be a one liner. you'll have to rewrite all the gtk stuff in the program that has been deprecated in gtk + 2.0 .

although, if someone built a deb then it may be possible to compile, still the question remains if he built it in an ubuntu box.

---

### Post by CJ Master on 2008-11-28
Well I think I got my answer, thanks everybody! I got the program working via deb anyways, but ya'll were helpfull in case of future problems.

Case Solved. ;)

---

### Post by stevek123 on 2008-11-28
CJ - I just had another thought/memory on this. One build I tried required that i open up the config file I was using and edited it to look for that 'newer' version that I had installed. I ran 'make clean' first, edited and  saved my config file and reran config & make with good results. It then looked for the newer version instead of the older one originally listed....

---

### Post by mc4man on 2008-11-28
one little final thing, when you see "Gtk" it's referring to libgtk and in this case to libgtk2.0 and libgtk2.0-dev (the -dev must be installed to build.
If it's not installed you'll error.

In 8.10 there's a package that should be install to 'help' with compiling which can fail otherwise for no good reason
'ccache' I believe is the name, will have to boot into 8.10 to ck.name

---

