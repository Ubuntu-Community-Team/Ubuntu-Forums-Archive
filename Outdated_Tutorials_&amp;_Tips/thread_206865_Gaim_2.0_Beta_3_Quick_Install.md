---
title: "Gaim 2.0 Beta 3 Quick Install"
date: 2006-06-30
forum: Outdated Tutorials &amp; Tips
---

### Post by daverab on 2006-06-30
This is my first submission of a howto guide. Feedback apreciated.

The actual guide is here and is aplicable for a new 6.06 LTS system:

[https://help.ubuntu.com/community/Gaim_2.0_Beta_3_Quick_Install](https://help.ubuntu.com/community/Gaim_2.0_Beta_3_Quick_Install)

(hey, they did say to put it on the wiki too)

Anyways, hope this helps for those of you who want a quick reference to get gaim2.0  beta3 running on a new Ubuntu setup.

---

### Post by fate on 2006-07-01
Your walkthrough is great! One minor thing if I may however. :)

Under 'Packages required for Base Gaim compilation', I didn't have the libxml-parser-perl package installed with my base Ubuntu 6.06 install. When I tried to install your recommended package, I noticed it was 'libxml-**par*c*er**-xml instead of 'parser'.

One minor typo there, but everything seems to work great.

Thanks.

---

### Post by dom02 on 2006-07-02
nice how to.  thanx.  I had completly forgotten about checkinstall.

---

### Post by 13121982 on 2006-07-02
libxml-parcer-perl???
libxml-parser-perl!!!

---

### Post by betawind on 2006-07-02
Fantastic information!  Thank you so much!

---

### Post by Jeconais on 2006-07-02
Thanks for the guide - nice and easy.

For all those complaining about the parcer->parser typo - it's a wiki, it only takes two seconds to login and fix it yourself (which I've done).

---

### Post by lotheac on 2006-07-02
I'd like to point out someone's made debs of gaim2 beta3 and has a repository. Just add these to your sources.list:
```
deb http://people.ubuntu.com/~seb128/deb ./
deb-src http://people.ubuntu.com/~seb128/deb ./
```

The repository also has a newer rhythmbox.

---

### Post by Muty on 2006-07-02
Hi,

is there a way to have ALSA support in this GAIM Beta 3?

Regards,
Muty.

---

### Post by Patskumaster on 2006-07-03
I install Gaim with this guide...
How i run Gaim?

---

### Post by Downtown on 2006-07-03
Used the repositories lotheac posted, package manager detected the update after a sudo apt-get update.  Thx.

---

### Post by daverab on 2006-07-04
Thanks for the Sources list lotheac, I've added it to the wiki page. Thanks for the typo fix as well. I've also added the page to the Documentation Category. Maybe then it'll get cleaned up a bit faster (apropriate links being added for certain steps mentioned as short sentances).

---

### Post by Epperly on 2006-07-11
Can anyone help me? I keep getting this error and Idk what to do, I can't get beta 3 installed...
[http://img.photobucket.com/albums/v92/k20importtuner/Screenshot-sammy.png](http://img.photobucket.com/albums/v92/k20importtuner/Screenshot-sammy.png)
and then "cd /gaim-2.0.0beta3" isn't a directory.

---

### Post by ericesque on 2006-07-12
I may be wrong, but I thought the fast (and easy) way of installing Gaim 2.0 Beta 3 was to use Automatix.

---

### Post by fakie_flip on 2006-08-28
I'm not able to login to yahoo chat rooms from gaim anymore. Maybe it is the version that I'm using. I get these messages everytime "Failed to join the chat Maybe the room is full" even if the chat room has only one person in it. Is there anyway I can go to yahoo chat rooms from gaim? Can someone else try to go to a yahoo chat room and tell me if his or her version of gaim allows it? Thanks. I am using Gaim beta3.

---

### Post by dmizer on 2006-09-09
> **lotheac said:**
> I'd like to point out someone's made debs of gaim2 beta3 and has a repository. Just add these to your sources.list:
```
deb http://people.ubuntu.com/~seb128/deb ./
deb-src http://people.ubuntu.com/~seb128/deb ./
```

The repository also has a newer rhythmbox.

these repos are no longer working.

---

### Post by m0rfin on 2006-09-09
Thanks

---

### Post by aie on 2006-09-09
> **Epperly said:**
> Can anyone help me? I keep getting this error and Idk what to do, I can't get beta 3 installed...
"cd /gaim-2.0.0beta3" isn't a directory.

I am getting the same error.. 
Any light ?

---

### Post by stalefries on 2006-09-09
For one, can you please post the error here? The image you linked to doesn't exist anymore. Also, "cd /gaim-2.0.0beta3" won't work because there is no "/gaim2.0.0beta3" directory. It's like saying C:/gaim2.0.0beta3. What you want (and what the howto whould have) is just gaim2.0.0beta3, without the /.

---

### Post by aie on 2006-09-09
ok. here is more clarity:

You were right, I took away the / before the folder name and it went ok.

However, after configure

ai@ai-desktop:~$ cd gaim-2.0.0beta3
ai@ai-desktop:~/gaim-2.0.0beta3$ sudo ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for sed... /bin/sed
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc static flag  works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
appending configuration tag "F77" to libtool
checking for a BSD-compatible install... /usr/bin/install -c
checking for perl... /usr/bin/perl
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool
--------------------------------------------------------------------
and after make:

ai@ai-desktop:~/gaim-2.0.0beta3$ sudo make
make: *** No targets specified and no makefile found.  Stop.


Thank you for your feedback

---

### Post by e2k on 2006-09-10
> **aie said:**
> checking for perl... /usr/bin/perl
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool
I've got the same problem.. Any thoughts?

EDIT: Apparently I had to install libxml-parser-perl :)

---

### Post by aie on 2006-09-10
> **e2k said:**
> I've got the same problem.. Any thoughts?

EDIT: Apparently I had to install libxml-parser-perl :)


--------------------------------------------------------------------
:D Thanks for the tip, it worked for me too.

---

### Post by lamego on 2006-09-11
I have built .deb packages for Dapper, they were build using the Edgy version and fixing a few dependencies so they should work better than the checkinstall based ones:
[http://www.getdeb.net/getdeb.php?file=gaim-data_2.0.0%2Bbeta3.1-1ubuntu4_all.deb](http://www.getdeb.net/getdeb.php?file=gaim-data_2.0.0%2Bbeta3.1-1ubuntu4_all.deb)
[http://www.getdeb.net/getdeb.php?file=gaim_2.0.0%2Bbeta3.1-1ubuntu4_i386.deb](http://www.getdeb.net/getdeb.php?file=gaim_2.0.0%2Bbeta3.1-1ubuntu4_i386.deb)

---

### Post by VortaX on 2006-09-15
Nice work lamego :D

---

### Post by fakie_flip on 2007-03-13
I still can't join yahoo chat rooms using gaim. Are other people able to or having the same problem as me? In the picture is the error I get for every yahoo chatroom I try to join no matter how many people are in it.

---

