---
title: "[New project] Debian package creator (feature request)"
date: 2007-06-25
forum: Programming Talk
---

### Post by leibowitz on 2007-06-25
Here is a tool to create deb packages easily. It lacks thousand of features, so to have what you need in it rapidly please tell me what you want the most in the Poll. If you want something that is not in it, feel free to propose a new one in this thread.

A screencast of an early version (0.2) if you want to see it in action.
[http://boby.joe.free.fr/dev/debcreator-0.2.ogg](http://boby.joe.free.fr/dev/debcreator-0.2.ogg)

Update (19 July 07): 
Screenshots available at:
[http://boby.joe.free.fr/dev/debcreator/img/](http://boby.joe.free.fr/dev/debcreator/img/)

Last version: 0.3.9.1, Download it at
[http://www.gnomefiles.org/download.php?soft_id=2090&where=http%3A%2F%2Fboby.joe.free.fr%2Fdev%2Fdebcreator%2Ffiles%2F0.3.9.1%2Fdebcreator_0.3.9.1-1_i386.deb](http://www.gnomefiles.org/download.php?soft_id=2090&where=http%3A%2F%2Fboby.joe.free.fr%2Fdev%2Fdebcreator%2Ffiles%2F0.3.9.1%2Fdebcreator_0.3.9.1-1_i386.deb)

You can now build packages from both archives and unpacked source directories. 
Most of the default filed in the control file are editable from the GUI.

Please test this with simple applications and report any problem you have. Please also attach a link to the archive you tried to build with this if it fails.

And please provide all the information you can on your system (distribution, version of libs, version of tools) if you experience any crash on start-up.


Note: this tool can only build software with at least a Makefile or a configure script that will generate the Makefile. It provides best result with GNU packaged software. You can recognize them because the top source directory is often called in the standard format <softwarename>-<version>.tar.gz (or bz2).

---

### Post by Fabioamd87 on 2007-06-25
nice app I'll try it

my vote: Package from archive.tar

---

### Post by Kelimion on 2007-06-25
Interesting project, Leibowitz. I'll be sure and give it a whirl sometime this week and report any feedback I may have.

Nice of you to link here from the [thread=483224]source package thread[/thread], by the looks both projects have lots of potential, even more so if they integrate well.

---

### Post by leibowitz on 2007-06-25
Kelimion you are right. We will learn from both other, I'm sure.

That's why I'm keeping an eye at your project. And I will probably contribute to it.

---

### Post by leibowitz on 2007-07-18
The first message has been updated with the new release.

Feel free to comment/ask features/test it/do what you want with it.

---

### Post by gurpartap on 2007-07-19
> **leibowitz said:**
> The first message has been updated with the new release.

Feel free to comment/ask features/test it/do what you want with it.
hello leibowitz :)

it looks cool enough for most of the basic application installlations! but my first try failed with a "Failed" error, with the progress bar at approximately 50%. Could not find any related information(except this page, and gnomefiles.org)) or any documentation on this, to troubleshoot.

What could possibly be the problem?

---

### Post by gurpartap on 2007-07-19
> **gurpartap said:**
> hello leibowitz :)

it looks cool enough for most of the basic application installlations! but my first try failed with a "Failed" error, with the progress bar at approximately 50%. Could not find any related information(except this page, and gnomefiles.org)) or any documentation on this, to troubleshoot.

What could possibly be the problem?
well, the terminal hints at something and guess now it makes sense what more is needed :D :)

---

### Post by gurpartap on 2007-07-19
You need to change line 407 and 409 in debcreator_dhmake from:

```
/usr/bin/bzip2
```
to:
```
/bin/bzip2
```

/usr/bin/bzip2 isn't the correct path actually. tested to work for tar.bz2 archives after the fix :)

---

### Post by Mickeysofine1972 on 2007-07-19
Lol!

Nice to see I'm not the only one that thinks this is a great idea!

I tried to start a similar project a few months ago but got shot down in flames so I gave up . ([http://ubuntu-utils.wikispaces.com](http://ubuntu-utils.wikispaces.com)) 

The Python code is still there if there is anything you might like to take from it, (doubt it though as your project seems far more advanced than mine ever did lol)

WTG dude keep up the good work. I cant help out at the moment unfortunately as I'm involved with the iTeam game project but I dont mind helping by testing.

Mike

---

### Post by leibowitz on 2007-07-19
gurpartap: thanks a lot.

I changed the way it finds bzip2/gzip/822-date tools. Also there was some bugs with dash in feisty. 

The first post has been updated to 0.3.9.1.

---

### Post by gurpartap on 2007-07-19
Tried to package debcreator's source tarball and got this:

```
dpkg-buildpackage: source package is debcreator
dpkg-buildpackage: source version is 0.3.9.1-1
dpkg-buildpackage: source changed by Gurpartap Singh <gurpartap__@g_mail.com>
dpkg-buildpackage: host architecture i386
dpkg-buildpackage: source version without epoch 0.3.9.1-1
dpkg-checkbuilddeps: error: syntax error in control file debian/control at line 14: continued value line not in field
dpkg-buildpackage: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: (Use -d flag to override.)
```

---

### Post by leibowitz on 2007-07-19
That is an error related to the "Description:" field. What did you put in there ?

Also, what version of ubuntu are you using ?

I need all the info you can give me so I can reproduce the bug.

---

### Post by gurpartap on 2007-07-19
Ubuntu 7.04 Feisty Fawn

The description field had the desc. as at [http://www.gnomefiles.org/app.php/Deb_Creator](http://www.gnomefiles.org/app.php/Deb_Creator)
and now tried with "test" in description field and it worked upto  building process with some problems :guitar: : ```
checking for GTK... configure: error: Package requirements (gtk+-2.0 >= 2.8.0) were not met:

No package 'gtk+-2.0' found
``` That might be gtk version? (but ubuntu is up to date, if gtk had any updates).

And we really need 2.8.0? after all debcreator is already running :p

Anyways, is the first error, a character/word length related problem?

---

### Post by leibowitz on 2007-07-19
I figured it out. Thanks to the information you gave.

That's because the description text has a line with a blank space. Just below the "synopsis". See the "<- here" in the text.

> GTK wizard tool to build deb packages easily
 <- here
This software is based upon debhelper, dpkg-buildpackage, and
other well tested tools. You can try to build simple package from
source archive with some GNU-packaged software containing at
least a Makefile and a configure script.

In the future this application will be able to perform advanced
operation.

Note: you don't need any particular package building knowledge
to use this.


If you copy pasted this instead, you should not have found this bug.

> This software is based upon debhelper, dpkg-buildpackage, and
other well tested tools. You can try to build simple package from
source archive with some GNU-packaged software containing at
least a Makefile and a configure script.

In the future this application will be able to perform advanced
operation.

Note: you don't need any particular package building knowledge
to use this.

Thanks for your time, and the luck you had in finding this. 

Update: it's already fixed in the next version (0.3.9.2). But I won't release it now. I want to add more features to this release concerning archive packages. You will have to wait sorry for this.

Edit: I forgot to add, for your GTK+ problem:

> That might be gtk version? (but ubuntu is up to date, if gtk had any updates).

And we really need 2.8.0? after all debcreator is already running

Yep but to build it from sources you need the gtk development libs, and headers. Which are in libgtk2.0-dev package. That's why you have to install many things when trying to build a software from source.

Creating a binary deb package is no exception.

---

### Post by kosmo on 2007-07-19
I created with your nice program another debcreator packet for Ubuntu Dapper and people may check is this good packet for it. For me it works!
 P.S. Well, i think, it's OK now? Does debcreator really depend on libcairo2?

---

### Post by kosmo on 2007-07-20
Debcreator in action seem to have problem with permissions, for example with these sources:
 
 [http://fy.chalmers.se/~appro/linux/DVD+RW/tools/dvd+rw-tools-7.0.tar.gz](http://fy.chalmers.se/~appro/linux/DVD+RW/tools/dvd+rw-tools-7.0.tar.gz)
 [http://prdownload.berlios.de/hardinfo/hardinfo-0.4.2.2.tar.bz2](http://prdownload.berlios.de/hardinfo/hardinfo-0.4.2.2.tar.bz2)

 Logs:

---

### Post by leibowitz on 2007-07-20
Good ! I'm interested in these problems. Let me just tell you that it's more than a permission problem.

As you can see, it's trying to put things in your /usr/local/bin ... and other directories where it can't write anything unless being root (or using sudo)

That's why it can't do this. Also that's why you should never run this application with administrator privileges.

This is wrong from the point of view of the installer. It should not access any /usr/bin directory (that's the whole purpose of using fakeroot)

> /usr/bin/make install prefix=/home/milan/.debcreator/hardinfo/hardinfo-0.4.2.2/debian/hardinfo/usr

You can see the "prefix=/" which point to a user directory where there is a "/" hierarchy. This should be respected. I suppose the Makefile of this project is not respecting default options? I need to verify this though.

> cp hardinfo.desktop /usr/share/applications
cp: cannot create regular file `/usr/share/applications/hardinfo.desktop': Permission denied

That's normal :-) 


For your own information this is more a package specific problem, which I really want to handle. That's the whole purpose of this software.

Thanks for your time trying to build those software. 

Update: some notes about dvd+rw-tools first.

This can be found in Makefile.m4:
>  install:        dvd+rw-tools
        /usr/sbin/install -o -f /usr/local/bin  $(CHAIN)
       /usr/sbin/install -o -f /usr/local/man/man1 growisofs.1

Hard coded path are not the way to go for a Makefile. So this won't be tackled at the moment. It's out-of-scope for current release. More work need to be done on stabilisation than experimentation. Because it's only supporting GNU packaged software currently. That has been said before.

Also I must say I don't know how to fix this at the moment.


About hardinfo: there seems to be a "DESTDIR" variable which needs to be set (this is kind of prefix). I don't know if it needs to be set by hand before calling the "make install" or is build from configure. That's also some kind of non-standard configure/make scripts.

I hope I can tackle hardinfo at least after the next version (>0.3.9.2) but I would not bet on it.

---

### Post by kosmo on 2007-07-20
Thanks for your explanation. Sorry for my bad english (i'm not native speaker), because of that i need more time to scrapped thats sentences:confused:. For now (with 0.3.9.1) i have also some weird 'bugs':
 1. Debcreator doesn't created icon-theme.cache and mimeinfo.cache in some debs that he does create (gnomebaker, soundconverter, gelemental, etc), with checkinstall or make install it's OK and in some debs that doesn't have it (like isomaster) icons in menu, because of that?, happily appears. 
 2. Big number of debs not goes to the right sections. I check that in Synaptic and in most case it goes to checkinstall section, no matter what i specified in debcreator's section dialog.
 
 Is there any way to debug debcreator when it say failed on prebuild checking window, when it's not a tipo mistake in package meta-data? Some old sources with Debian folder in it failed to go with it (can you fix that?). Example: [http://pitchtune.sourceforge.net/](http://pitchtune.sourceforge.net/)

---

### Post by leibowitz on 2007-07-21
About the prebuild checks, yep you can see more infos by calling debcreator from a terminal with

```
debcreator --debug
```

You will see that it calls "debcreator_dhmake" and that's where it hangs if there is a debian folder already present.

That's because dhmake doesn't overwrite any existing control file. The only way to fix this for you is to extract the archive to a folder and delete the debian folder in it.

But I checked the source folder of pitchtune, there is more to do... You have to edit the Makefile.am file and delete the "debian" in line 4.

Then go to the configure.in file and delete the line  51 containing "  debian/Makefile \"

Then execute "./autogen.sh" in the top source folder.

And now you can start debcreator only to see that the Makefile does not contain any make all target. Then this need more than just deleting the debian folder... Hey and I spotted a bug during trying this :-)

For icon-theme.cache and mimeinfo.cache I don't know what you are talking about so I will need to check that with more attention.

Thanks again for your great work and good error reporting.

Edit: about the "section", I need to know, what did you put in there ?

Try with one of those: "admin", "base", "devel", "games", "gnome", "kde", "text", "sound", "x11", "unknown"

---

### Post by kosmo on 2007-07-21
Super it can debug! I was not figured out that debcreator created build log in source dir, that is very useful for you & everyone. Pitchtune on the way: i deleted Debian folder, edited Makefile.am, configure.in, and execute in the top of source folder ./autogen.sh which created config.guess and config.sub links with root permissons (plain ./configure in console don't produce this), and... after that in log.
 For mimeinfo.cache i can't momentary find out in which debs that miss, but for icon-theme.cache i attached logs for lucky created debs (soundconverter & gelemental) which could be more expressive on that thing then i with my weird english speak.:)
 For section, in most cases, i just leave that it goes with unknown (don't touch anything) or put in it some of your suggests, in gdebi details it's unknown or whatever i specified, but in Synaptic it's in checkinstall section (only exeption is gelemental that goes strait to Unknown). I try to put Unknown (with big "U"), because Synaptic have that section, but this don't make any sense.

---

### Post by leibowitz on 2007-07-21
Note for the section field.

Someone sent me a patch with all the possible section available, that's taken from Synaptic and will be included in the next release (v0.3.9.2). AFAIK it's the only application that does print something more valuable than the raw section field (I'm talking about Synapic).

That's why you see "Unknown" with a big "U" in Synaptic and not in gdebi. 

Synaptic does translate this field with something more comprehensible.

For example, if you put "base" in the section field, you should see "Base System" in Synaptic.

If you have something else, than you need to check your Synaptic installation. 

Alternatively you can use "dpkg -f packagename.deb" to get all the meta-data information set on a package.


PS: I don't know why you did mention checkinstall sometimes, since debcreator does not use checkinstall. Am I missing something ?

---

### Post by kosmo on 2007-07-21
I know that debcreator doesn't use checkinstall, but kosmo use it and when i install it (checkinstall.deb from Ubuntu repo), and create deb with him, then he create it's own section beside all standard section in Synaptic. Debcreator's debs allways move to that (checkinstall) section and change it (see picture-that debcreator created with debcreator with unknown section, but...)(weird thing is that has been one exception -gelemental). All others repo-debs goes to the right section! Gdebi or dpkg -f is OK (what i wrote in debcreator-exactly that they listed). Maybe it is some badly connection within synaptic-checkinstall and i will remove all checkistaled debs (what, in my case, bad thing), checkinstall.deb , and try again.:)

---

### Post by leibowitz on 2007-07-21
I don't have this problem here.

That's probably related to checkinstall. And I don't know why yet.

You may want to try with the new version. That's not a public release though. 

[http://boby.joe.free.fr/dev/debcreator/files/0.3.9.2/debcreator_0.3.9.2-1_i386.deb](http://boby.joe.free.fr/dev/debcreator/files/0.3.9.2/debcreator_0.3.9.2-1_i386.deb)



Keep the old version too in case you want to rollback.

[http://boby.joe.free.fr/dev/debcreator/files/0.3.9.1/debcreator_0.3.9.1-1_i386.deb](http://boby.joe.free.fr/dev/debcreator/files/0.3.9.1/debcreator_0.3.9.1-1_i386.deb)

---

### Post by kosmo on 2007-07-21
As i said, i removed all this checkinstalled debs (and stuck down from Xorg 7.2 to 7.0, that i need to recompile again after test), tried mine and debcreator.deb (and v0.3.9.2) that you provided, debcreating some debs...but without success. It's always goes to checkinstall section, although checkinstall.deb is not instaled. OK, maybe it's a checkinstall related problem, so may leave it for now. 
 I'm impressed how things goes for new version and i don't have a suggestion for this, because i liked it's small GUI window and hope that you can't get more huge when present some other option, but don't now your opinion about that, is it be huge in the future?  
 
 Some lucky testing today::)
 -supertux-0.1.3 (it goes like hell)
 -gxmame-0.35beta2 ( in source it has Debian folder, removed it, without editing anything, and voila)
 -wine-0.9.41 (produce lot of debug output, some warnings, but created and work well)

---

### Post by kosmo on 2007-07-22
Well, i think i find what cause that all debcreated debs go to the checkinstall section. All debs which i debcreated has been previously installed with checkinstall. Same name of the package is a problem with checkinstall which has been ones installed previously. I rename source folder from debcreator-0.3.9.1 to debcreators-0.3.9.1, debcreated it, install it and this does work (deb goes to the right (devel) section), but i think that is not good solution for this problem. Hope, i'm helpfull to you with my amater explaination.:)

---

### Post by leibowitz on 2007-07-22
I will need to check this problem on another computer. But sure, I will be investigating checkinstall and see why it's doing this.

> is it be huge in the future?

I don't understand what you mean by huge. Is it big in the sense of user interface with too much option ? Because that's exactly what I feel. That's why I won't publicly release this last version (0.3.9.2). I need to think again how to present things in the interface.

---

### Post by kosmo on 2007-07-22
When i wrote 'huge' i meaning about main window by default (and dimensions), because of "next-next-finish" nature of program and tabbed windows on those steps doesn't need to become more complicated in future, all that in question of userfriendlyness, not in question of more and more sophisticated options that you (and i wish to see that too) wish to implement.
 
 Some lucky info: today i try (0.3.9.1) at my neighbour's computer with preinstalled Linux Mint 3.0 (Cassandra) which is compatibile with Feisty to compile and debcreating debcreator, and it works, but i'm not have to much time to test another softer on it. One more success of debcreator!:guitar:

---

### Post by leibowitz on 2007-07-22
I tried myself on Debian 4.0 stable and I was quite astonished that it worked well.

Now I need to add more complexity because it cannot compile anything more than a single binary deb at the moment.

That's quite frustrating me. More than you can think of. 

So that's quite a bit of mission impossible for me to add more functionality without adding any more complexity. Because I suck at creating user interface. I'm quite a beginner and that's it.

I think I will keep adding functionality and wait for someone who cares about user interface to rethink the interface later. I cannot do anything else.

---

### Post by kosmo on 2007-07-23
Thank you for your answer i think understand you on your state of programming skills or your visons on GUI side, but beside the GUI you made good work that can make simple packages without console and i must say another thank you for that. Debcreator is, within this state, very respectable app for me.:KS 
 You are programmer and i'm just a simple user that want to test your program in whatever state it is and whatever ways you think it can be helpful to you. You can add complexity how much you think want to in GUI and beside it and i'm always be happy to test it.:)

---

### Post by Kreuger on 2007-07-23
When I tried to build Pidgin from source, I got an error:

> dpkg-buildpackage: source package is pidgin
dpkg-buildpackage: source version is 2.0.2-1
dpkg-buildpackage: source changed by Kreuger Burns <kreugerburns@gmail.com>
dpkg-buildpackage: host architecture i386
dpkg-buildpackage: source version without epoch 2.0.2-1
 fakeroot debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp 
# Add here commands to clean up after the build process.
/usr/bin/make distclean
make[1]: Entering directory `/home/kreuger/.debcreator/pidgin/pidgin-2.0.2'
make[1]: *** No rule to make target `distclean'.  Stop.
make[1]: Leaving directory `/home/kreuger/.debcreator/pidgin/pidgin-2.0.2'
make: [clean] Error 2 (ignored)
cp -f /usr/share/misc/config.sub config.sub
cp -f /usr/share/misc/config.guess config.guess
dh_clean 
 dpkg-source -b pidgin-2.0.2
dpkg-source: building pidgin in pidgin_2.0.2.orig.tar.gz
dpkg-source: building pidgin in pidgin_2.0.2-1.diff.gz
dpkg-source: building pidgin in pidgin_2.0.2-1.dsc
 debian/rules build
dh_testdir
# Add here commands to configure the package.
CFLAGS="-Wall -g -O2 -Wl,-z,defs" ./configure --host=i486-linux-gnu --build=i486-linux-gnu --prefix=/usr --mandir=\${prefix}/share/man --infodir=\${prefix}/share/info
checking build system type... i486-pc-linux-gnu
checking host system type... i486-pc-linux-gnu
checking target system type... i486-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for sed... /bin/sed
checking for i486-linux-gnu-gcc... i486-linux-gnu-gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether i486-linux-gnu-gcc accepts -g... yes
checking for i486-linux-gnu-gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of i486-linux-gnu-gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by i486-linux-gnu-gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... i486-linux-gnu-gcc -E
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
checking for i486-linux-gnu-g++... i486-linux-gnu-g++
checking whether we are using the GNU C++ compiler... yes
checking whether i486-linux-gnu-g++ accepts -g... yes
checking dependency style of i486-linux-gnu-g++... gcc3
checking how to run the C++ preprocessor... i486-linux-gnu-g++ -E
checking for i486-linux-gnu-g77... no
checking for i486-linux-gnu-f77... no
checking for i486-linux-gnu-xlf... no
checking for i486-linux-gnu-frt... no
checking for i486-linux-gnu-pgf77... no
checking for i486-linux-gnu-fort77... no
checking for i486-linux-gnu-fl32... no
checking for i486-linux-gnu-af77... no
checking for i486-linux-gnu-f90... no
checking for i486-linux-gnu-xlf90... no
checking for i486-linux-gnu-pgf90... no
checking for i486-linux-gnu-epcf90... no
checking for i486-linux-gnu-f95... no
checking for i486-linux-gnu-fort... no
checking for i486-linux-gnu-xlf95... no
checking for i486-linux-gnu-ifc... no
checking for i486-linux-gnu-efc... no
checking for i486-linux-gnu-pgf95... no
checking for i486-linux-gnu-lf95... no
checking for i486-linux-gnu-gfortran... no
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
checking command to parse /usr/bin/nm -B output from i486-linux-gnu-gcc object... ok
checking for objdir... .libs
checking for i486-linux-gnu-ar... no
checking for ar... ar
checking for i486-linux-gnu-ranlib... no
checking for ranlib... ranlib
checking for i486-linux-gnu-strip... no
checking for strip... strip
checking if i486-linux-gnu-gcc supports -fno-rtti -fno-exceptions... no
checking for i486-linux-gnu-gcc option to produce PIC... -fPIC
checking if i486-linux-gnu-gcc PIC flag -fPIC works... yes
checking if i486-linux-gnu-gcc static flag -static works... yes
checking if i486-linux-gnu-gcc supports -c -o file.o... yes
checking whether the i486-linux-gnu-gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by i486-linux-gnu-g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the i486-linux-gnu-g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for i486-linux-gnu-g++ option to produce PIC... -fPIC
checking if i486-linux-gnu-g++ PIC flag -fPIC works... yes
checking if i486-linux-gnu-g++ static flag -static works... yes
checking if i486-linux-gnu-g++ supports -c -o file.o... yes
checking whether the i486-linux-gnu-g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for a BSD-compatible install... /usr/bin/install -c
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... /usr/bin/msgfmt
checking for msgmerge... /usr/bin/msgmerge
checking for xgettext... /usr/bin/xgettext
checking for i486-linux-gnu-pkg-config... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for catalogs to be installed...  af am ar az bg bn bs ca ca@valencia cs da de dz el en_AU en_CA en_GB eo es et eu fa fi fr gl gu he hi hu id it ja ka kn ko ku lt mk my_MM nb ne nl nn pa pl pt_BR pt ps ro ru sk sl sq sr sr@Latn sv ta te th tr uk vi xh zh_CN zh_HK zh_TW
checking for ANSI C header files... (cached) yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking arpa/nameser_compat.h usability... yes
checking arpa/nameser_compat.h presence... yes
checking for arpa/nameser_compat.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking for locale.h... (cached) yes
checking signal.h usability... yes
checking signal.h presence... yes
checking for signal.h... yes
checking for stdint.h... (cached) yes
checking regex.h usability... yes
checking regex.h presence... yes
checking for regex.h... yes
checking for an ANSI C-conforming const... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for time_t... yes
checking size of time_t... 4
checking whether byte ordering is bigendian... no
checking return type of signal handlers... void
checking for strftime... yes
checking for strdup... yes
checking for strstr... yes
checking for atexit... yes
checking for setlocale... yes
checking for getopt_long... yes
checking for inet_aton... yes
checking for __res_query in -lresolv... yes
checking for gethostent in -lnsl... yes
checking for socket... yes
checking for getaddrinfo... yes
checking for socklen_t... yes
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for _LARGE_FILES value needed for large files... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking for the %z format string in strftime()... yes
checking for GLIB... yes
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for GTK... yes
checking for pango... yes
checking for XScreenSaverRegister in -lXext... no
checking for XScreenSaverRegister in -lXss... no
checking for SmcSaveYourselfDone in -lSM... yes
checking X11/SM/SMlib.h usability... yes
checking X11/SM/SMlib.h presence... yes
checking for X11/SM/SMlib.h... yes
checking for STARTUP_NOTIFICATION... no
no
checking for GTKSPELL... no
no
checking for EVOLUTION_ADDRESSBOOK... no
yes
checking for EVOLUTION_ADDRESSBOOK... no
yes
checking for SQLITE3... no
no
checking for initscr in -lncursesw... no
checking for update_panels in -lpanelw... no
checking for initscr in -lncurses... yes
checking for update_panels in -lpanel... yes
checking for X11... yes
checking for LIBXML... yes
checking for gconftool-2... /usr/bin/gconftool-2
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
checking for GSTREAMER... yes
checking for MEANWHILE... no
no
checking for HOWL... no
no
checking for HOWL... no
no
checking howl.h usability... no
checking howl.h presence... no
checking for howl.h... no
checking for sw_discovery_init in -lhowl... no
checking for SILC... no
no
checking for SILC... no
no
checking for SILC... no
no
checking for GADU... no
no
checking sys/utsname.h usability... yes
checking sys/utsname.h presence... yes
checking for sys/utsname.h... yes
checking for uname... yes
checking for -Waggregate-return option to gcc... yes
checking for -Wcast-align option to gcc... yes
checking for -Wdeclaration-after-statement option to gcc... yes
checking for -Wendif-labels option to gcc... yes
checking for -Werror-implicit-function-declaration option to gcc... yes
checking for -Wextra -Wno-sign-compare -Wno-unused-parameter option to gcc... yes
checking for -Winit-self option to gcc... yes
checking for -Wmissing-declarations option to gcc... yes
checking for -Wmissing-noreturn option to gcc... yes
checking for -Wmissing-prototypes option to gcc... yes
checking for -Wnested-externs option to gcc... yes
checking for -Wpointer-arith option to gcc... yes
checking for -Wundef option to gcc... yes
checking for FORTIFY_SOURCE support... yes
checking for pidgin... /usr/local/bin/pidgin
checking for dbus-binding-tool... yes
checking for DBUS... yes
checking for python... /usr/bin/python
checking location of the D-Bus services directory... ${prefix}/share/dbus-1/services
Building with D-Bus support
checking for perl... /usr/bin/perl
checking for Perl compile flags... ok
checking for libperl... checking for perl_run... no
checking EXTERN.h usability... yes
checking EXTERN.h presence... yes
checking for EXTERN.h... yes
checking for perl.h... yes
checking for GnuTLS includes... ""
checking gnutls/gnutls.h usability... yes
checking gnutls/gnutls.h presence... yes
checking for gnutls/gnutls.h... yes
checking for GnuTLS libraries... yes
checking for NSS... yes
checking for tclConfig.sh... yes (/usr/lib/tcl8.4/tclConfig.sh)
checking Tcl version compatability... ok, 8.4
checking for Tcl linkability... yes
checking for tkConfig.sh... no
checking for snprintf... yes
checking for connect... (cached) yes
checking for me pot o' gold... no
checking for gethostid... yes
checking for lrand48... yes
checking for memcpy... yes
checking for memmove... yes
checking for random... yes
checking for strchr... yes
checking for strerror... yes
checking for vprintf... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking paths.h usability... yes
checking paths.h presence... yes
checking for paths.h... yes
checking sgtty.h usability... yes
checking sgtty.h presence... yes
checking for sgtty.h... yes
checking stdarg.h usability... yes
checking stdarg.h presence... yes
checking for stdarg.h... yes
checking sys/cdefs.h usability... yes
checking sys/cdefs.h presence... yes
checking for sys/cdefs.h... yes
checking sys/file.h usability... yes
checking sys/file.h presence... yes
checking for sys/file.h... yes
checking sys/filio.h usability... no
checking sys/filio.h presence... no
checking for sys/filio.h... no
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/msgbuf.h usability... no
checking sys/msgbuf.h presence... no
checking for sys/msgbuf.h... no
checking sys/select.h usability... yes
checking sys/select.h presence... yes
checking for sys/select.h... yes
checking sys/uio.h usability... yes
checking sys/uio.h presence... yes
checking for sys/uio.h... yes
checking for sys/utsname.h... (cached) yes
checking for sys/wait.h... (cached) yes
checking termios.h usability... yes
checking termios.h presence... yes
checking for termios.h... yes
checking sys/sysctl.h usability... yes
checking sys/sysctl.h presence... yes
checking for sys/sysctl.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking for struct tm.tm_zone... yes
checking for timezone external... yes
checking for altzone external... no
checking for daylight external... yes
checking for tm_gmtoff in struct tm... yes
checking for CHECK... no
checking for check - version >= 0.8.2... no
*** Could not run check test program, checking why...
*** The test program failed to compile or link. See the file config.log for
*** the exact error that occured.
checking for doxygen... true
checking for dot... false
configure: WARNING: *** GraphViz dot not found, docs will not have graphs
configure: creating ./config.status
config.status: creating Makefile
config.status: creating Doxyfile
config.status: creating doc/Makefile
config.status: creating doc/pidgin.1
config.status: creating doc/finch.1
config.status: creating m4macros/Makefile
config.status: creating pidgin.apspec
config.status: creating pidgin/Makefile
config.status: creating pidgin/pidgin.pc
config.status: creating pidgin/pidgin-uninstalled.pc
config.status: creating pidgin/pixmaps/Makefile
config.status: creating pidgin/pixmaps/animations/Makefile
config.status: creating pidgin/pixmaps/animations/16/Makefile
config.status: creating pidgin/pixmaps/buddy_icons/Makefile
config.status: creating pidgin/pixmaps/buddy_icons/qq/Makefile
config.status: creating pidgin/pixmaps/dialogs/Makefile
config.status: creating pidgin/pixmaps/dialogs/16/Makefile
config.status: creating pidgin/pixmaps/dialogs/16/scalable/Makefile
config.status: creating pidgin/pixmaps/dialogs/64/Makefile
config.status: creating pidgin/pixmaps/dialogs/64/scalable/Makefile
config.status: creating pidgin/pixmaps/emblems/Makefile
config.status: creating pidgin/pixmaps/emblems/16/Makefile
config.status: creating pidgin/pixmaps/emblems/16/scalable/Makefile
config.status: creating pidgin/pixmaps/emotes/Makefile
config.status: creating pidgin/pixmaps/emotes/default/Makefile
config.status: creating pidgin/pixmaps/emotes/default/22/Makefile
config.status: creating pidgin/pixmaps/emotes/default/22/scalable/Makefile
config.status: creating pidgin/pixmaps/emotes/none/Makefile
config.status: creating pidgin/pixmaps/icons/Makefile
config.status: creating pidgin/pixmaps/icons/16/Makefile
config.status: creating pidgin/pixmaps/icons/16/scalable/Makefile
config.status: creating pidgin/pixmaps/icons/24/Makefile
config.status: creating pidgin/pixmaps/icons/24/scalable/Makefile
config.status: creating pidgin/pixmaps/icons/32/Makefile
config.status: creating pidgin/pixmaps/icons/32/scalable/Makefile
config.status: creating pidgin/pixmaps/icons/48/Makefile
config.status: creating pidgin/pixmaps/icons/48/scalable/Makefile
config.status: creating pidgin/pixmaps/protocols/Makefile
config.status: creating pidgin/pixmaps/protocols/16/Makefile
config.status: creating pidgin/pixmaps/protocols/16/scalable/Makefile
config.status: creating pidgin/pixmaps/protocols/22/Makefile
config.status: creating pidgin/pixmaps/protocols/22/scalable/Makefile
config.status: creating pidgin/pixmaps/protocols/48/Makefile
config.status: creating pidgin/pixmaps/protocols/48/scalable/Makefile
config.status: creating pidgin/pixmaps/status/Makefile
config.status: creating pidgin/pixmaps/status/16/Makefile
config.status: creating pidgin/pixmaps/status/16/rtl/Makefile
config.status: creating pidgin/pixmaps/status/16/scalable/Makefile
config.status: creating pidgin/pixmaps/status/22/Makefile
config.status: creating pidgin/pixmaps/status/22/rtl/Makefile
config.status: creating pidgin/pixmaps/status/22/scalable/Makefile
config.status: creating pidgin/pixmaps/status/32/Makefile
config.status: creating pidgin/pixmaps/status/32/rtl/Makefile
config.status: creating pidgin/pixmaps/status/32/scalable/Makefile
config.status: creating pidgin/pixmaps/status/48/Makefile
config.status: creating pidgin/pixmaps/status/48/rtl/Makefile
config.status: creating pidgin/pixmaps/toolbar/Makefile
config.status: creating pidgin/pixmaps/toolbar/16/Makefile
config.status: creating pidgin/pixmaps/toolbar/16/scalable/Makefile
config.status: creating pidgin/pixmaps/toolbar/22/Makefile
config.status: creating pidgin/pixmaps/toolbar/22/scalable/Makefile
config.status: creating pidgin/pixmaps/tray/Makefile
config.status: creating pidgin/pixmaps/tray/16/Makefile
config.status: creating pidgin/pixmaps/tray/16/scalable/Makefile
config.status: creating pidgin/pixmaps/tray/22/Makefile
config.status: creating pidgin/pixmaps/tray/22/scalable/Makefile
config.status: creating pidgin/pixmaps/tray/32/Makefile
config.status: creating pidgin/pixmaps/tray/48/Makefile
config.status: creating pidgin/plugins/Makefile
config.status: creating pidgin/plugins/cap/Makefile
config.status: creating pidgin/plugins/gestures/Makefile
config.status: creating pidgin/plugins/gevolution/Makefile
config.status: creating pidgin/plugins/musicmessaging/Makefile
config.status: creating pidgin/plugins/perl/Makefile
config.status: creating pidgin/plugins/perl/common/Makefile.PL
config.status: creating pidgin/plugins/ticker/Makefile
config.status: creating pidgin/sounds/Makefile
config.status: creating libpurple/example/Makefile
config.status: creating libpurple/gconf/Makefile
config.status: creating libpurple/purple.pc
config.status: creating libpurple/purple-uninstalled.pc
config.status: creating libpurple/plugins/Makefile
config.status: creating libpurple/plugins/mono/Makefile
config.status: creating libpurple/plugins/mono/api/Makefile
config.status: creating libpurple/plugins/mono/loader/Makefile
config.status: creating libpurple/plugins/perl/Makefile
config.status: creating libpurple/plugins/perl/common/Makefile.PL
config.status: creating libpurple/plugins/ssl/Makefile
config.status: creating libpurple/plugins/tcl/Makefile
config.status: creating libpurple/Makefile
config.status: creating libpurple/protocols/Makefile
config.status: creating libpurple/protocols/bonjour/Makefile
config.status: creating libpurple/protocols/gg/Makefile
config.status: creating libpurple/protocols/irc/Makefile
config.status: creating libpurple/protocols/jabber/Makefile
config.status: creating libpurple/protocols/msn/Makefile
config.status: creating libpurple/protocols/novell/Makefile
config.status: creating libpurple/protocols/null/Makefile
config.status: creating libpurple/protocols/oscar/Makefile
config.status: creating libpurple/protocols/qq/Makefile
config.status: creating libpurple/protocols/sametime/Makefile
config.status: creating libpurple/protocols/silc/Makefile
config.status: creating libpurple/protocols/silc10/Makefile
config.status: creating libpurple/protocols/simple/Makefile
config.status: creating libpurple/protocols/toc/Makefile
config.status: creating libpurple/protocols/yahoo/Makefile
config.status: creating libpurple/protocols/zephyr/Makefile
config.status: creating libpurple/tests/Makefile
config.status: creating libpurple/version.h
config.status: creating finch/Makefile
config.status: creating finch/libgnt/Makefile
config.status: creating finch/libgnt/gnt.pc
config.status: creating finch/libgnt/wms/Makefile
config.status: creating finch/plugins/Makefile
config.status: creating po/Makefile.in
config.status: creating pidgin.spec
config.status: creating config.h
config.status: executing depfiles commands
config.status: executing intltool commands
config.status: executing default-1 commands
config.status: executing po/stamp-it commands

pidgin 2.0.2

Build GTK+ 2.x UI............. : yes
Build console UI.............. : yes

Protocols to build dynamically : gg irc jabber msn novell oscar qq simple yahoo zephyr
Protocols to link statically.. :

Build with GStreamer support.. : yes
Build with D-Bus support...... : yes
D-Bus services directory...... : /usr/share/dbus-1/services
Build with NetworkManager..... : no
SSL Library/Libraries......... : Mozilla NSS and GnuTLS
Build with Cyrus SASL support. : no
Use kerberos 4 with zephyr.... : no
Use external libzephyr........ : no
Has you....................... : yes

Use XScreenSaver Extension.... : no
Use X Session Management...... : yes
Use startup notification...... : no
Build with GtkSpell support... : no

Build with plugin support..... : yes
Build with Mono support....... : no
Build with Perl support....... : no
Build with Tcl support........ : yes
Build with Tk support......... : no

Print debugging messages...... : no

Pidgin will be installed in /usr/bin.
Warning: You have an old copy of Pidgin at /usr/local/bin/pidgin.

configure complete, now type 'make'

dh_testdir
# Add here commands to compile the package.
/usr/bin/make
make[1]: Entering directory `/home/kreuger/.debcreator/pidgin/pidgin-2.0.2'
/usr/bin/make  all-recursive
make[2]: Entering directory `/home/kreuger/.debcreator/pidgin/pidgin-2.0.2'
Making all in libpurple
make[3]: Entering directory `/home/kreuger/.debcreator/pidgin/pidgin-2.0.2/libpurple'
/usr/bin/make  all-recursive
make[4]: Entering directory `/home/kreuger/.debcreator/pidgin/pidgin-2.0.2/libpurple'
Making all in gconf
make[5]: Entering directory `/home/kreuger/.debcreator/pidgin/pidgin-2.0.2/libpurple/gconf'
LC_ALL=C ../../intltool-merge -s -u -c ../../po/.intltool-merge-cache ../../po purple.schemas.in purple.schemas
Generating and caching the translation database
NOTICE: ../../po/nb.po is not in UTF-8 but ISO-8859-1, converting...
NOTICE: ../../po/id.po is not in UTF-8 but iso-8859-1, converting...
NOTICE: ../../po/th.po is not in UTF-8 but tis-620, converting...
Merging translations into purple.schemas.
make[5]: Leaving directory `/home/kreuger/.debcreator/pidgin/pidgin-2.0.2/libpurple/gconf'
Making all in plugins
make[5]: Entering directory `/home/kreuger/.debcreator/pidgin/pidgin-2.0.2/libpurple/plugins'
Making all in ssl
make[6]: Entering directory `/home/kreuger/.debcreator/pidgin/pidgin-2.0.2/libpurple/plugins/ssl'
if /bin/bash ../../../libtool --silent --tag=CC --mode=compile i486-linux-gnu-gcc -DHAVE_CONFIG_H -I. -I. -I../../..  -DDATADIR=\"/usr/share\" -DLIBDIR=\"/usr/lib/libpurple\" -I../../../libpurple -I../../../libpurple -Wall  -Waggregate-return -Wcast-align -Wdeclaration-after-statement -Wendif-labels -Werror-implicit-function-declaration -Wextra -Wno-sign-compare -Wno-unused-parameter -Winit-self -Wmissing-declarations -Wmissing-noreturn -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wundef -Wp,-D_FORTIFY_SOURCE=2 -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include      -g  -g -O2 -Wl,-z,defs -MT ssl.lo -MD -MP -MF ".deps/ssl.Tpo" -c -o ssl.lo ssl.c; \
	then mv -f ".deps/ssl.Tpo" ".deps/ssl.Plo"; else rm -f ".deps/ssl.Tpo"; exit 1; fi
i486-linux-gnu-gcc: -z: linker input file unused because linking not done
i486-linux-gnu-gcc: defs: linker input file unused because linking not done
/bin/bash ../../../libtool --silent --tag=CC --mode=link i486-linux-gnu-gcc  -g  -g -O2 -Wl,-z,defs   -o ssl.la -rpath /usr/lib/purple-2 -module -avoid-version ssl.lo -Wl,--export-dynamic -pthread -lgobject-2.0 -lgmodule-2.0 -ldl -lgthread-2.0 -lrt -lglib-2.0   -lnsl -lresolv 
.libs/ssl.o: In function `purple_init_plugin':
/home/kreuger/.debcreator/pidgin/pidgin-2.0.2/libpurple/plugins/ssl/ssl.c:124: undefined reference to `purple_plugin_register'
.libs/ssl.o: In function `plugin_unload':
/home/kreuger/.debcreator/pidgin/pidgin-2.0.2/libpurple/plugins/ssl/ssl.c:71: undefined reference to `purple_plugins_get_loaded'
/home/kreuger/.debcreator/pidgin/pidgin-2.0.2/libpurple/plugins/ssl/ssl.c:74: undefined reference to `purple_plugin_unload'
.libs/ssl.o: In function `probe_ssl_plugins':
/home/kreuger/.debcreator/pidgin/pidgin-2.0.2/libpurple/plugins/ssl/ssl.c:40: undefined reference to `purple_plugins_get_all'
/home/kreuger/.debcreator/pidgin/pidgin-2.0.2/libpurple/plugins/ssl/ssl.c:50: undefined reference to `purple_plugin_is_loaded'
/home/kreuger/.debcreator/pidgin/pidgin-2.0.2/libpurple/plugins/ssl/ssl.c:50: undefined reference to `purple_plugin_load'
collect2: ld returned 1 exit status
make[6]: *** [ssl.la] Error 1
make[6]: Leaving directory `/home/kreuger/.debcreator/pidgin/pidgin-2.0.2/libpurple/plugins/ssl'
make[5]: *** [all-recursive] Error 1
make[5]: Leaving directory `/home/kreuger/.debcreator/pidgin/pidgin-2.0.2/libpurple/plugins'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/kreuger/.debcreator/pidgin/pidgin-2.0.2/libpurple'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/kreuger/.debcreator/pidgin/pidgin-2.0.2/libpurple'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/kreuger/.debcreator/pidgin/pidgin-2.0.2'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/kreuger/.debcreator/pidgin/pidgin-2.0.2'
make: *** [build-stamp] Error 2
 I'm sure I have everything installed as I built the source before to install it myself. Now I just want to create a deb of it.

---

### Post by abhijeetmaharana on 2007-07-23
I am getting the same error.

---

### Post by leibowitz on 2007-07-23
I can confirm this.

It's probably related to the libpurple thing, it needs to be compiled first so some changes may be done in the dh_make rules file. But I don't know what at the moment.

I will be investigating this.

PS: I have registered the project at launchpad.net



Feel free to report any bug or failed build
[https://bugs.launchpad.net/debcreator/](https://bugs.launchpad.net/debcreator/)

---

### Post by Kreuger on 2007-07-23
Also, when trying to build a deb package for amsn it just fails without showing any errors. Is there any way to get it to output an error so we can see whats going on? I ran it from a terminal and it didnt show anythin

---

### Post by leibowitz on 2007-07-23
You need to add --debug to the command line. I presume it's a pre-check failing issue. Otherwise it won't help you.

---

### Post by leibowitz on 2007-07-23
Some update about pidgin.

I figured out that this seems to be an architecture related problem. As when you compile it by hand gcc has no build-arch option, but when you build it with debcreator it has --host=i486-linux-gnu --build=i486-linux-gnu

Both options are defined in the debian/rules file created by dh_make script. It's in ~/.debcreator/pidgin/pidgin-<version>/debian/rules

You can check your build arch with dpkg-architecture too.



To compile this, I've stopped the wizard just before the building process (the last step) and edited the rules files mentionned before.

In this file I commented out line 15 to 25 included.

Then removed parts of the line 30.

CFLAGS="$(CFLAGS) -Wl,-z,defs" 
--host=$(DEB_HOST_GNU_TYPE) --build=$(DEB_BUILD_GNU_TYPE)

Both parts have been removed.

This is the complete line after removing those parts:

./configure --prefix=/usr --mandir=\$${prefix}/share/man --infodir=\$${prefix}/share/info


Saved the file, and clicked next to build the package. But this still fails at the end. So I probably did something wrong.

---

### Post by kosmo on 2007-07-23
I try to make deb for gxine-0.5.10 and it make it, but when i start gxine it gives me segfault error.
 For brasero-0.4.4: it couldn't make it, because of 'mime' thing.

 Chestnut-dialer as well as soundconverter (both works) are a python programs. For these debcreator doesn't generate dependencies, but i think it is normal (for now) with them?

---

### Post by Kreuger on 2007-07-23
So is there anyway to fix the pidgin problem or would I have to do that every time I want to build it?

I tried it and got:
> dpkg-buildpackage: source package is pidgin
dpkg-buildpackage: source version is 2.0.2-1
dpkg-buildpackage: source changed by Kreuger Burns <kreugerburns@gmail.com>
dpkg-buildpackage: host architecture i386
dpkg-buildpackage: source version without epoch 2.0.2-1
 fakeroot debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp 
# Add here commands to clean up after the build process.
/usr/bin/make distclean
make[1]: Entering directory `/home/kreuger/.debcreator/pidgin/pidgin-2.0.2'
make[1]: *** No rule to make target `distclean'.  Stop.
make[1]: Leaving directory `/home/kreuger/.debcreator/pidgin/pidgin-2.0.2'
make: [clean] Error 2 (ignored)
cp -f /usr/share/misc/config.sub config.sub
cp -f /usr/share/misc/config.guess config.guess
dh_clean 
 dpkg-source -b pidgin-2.0.2
dpkg-source: building pidgin in pidgin_2.0.2.orig.tar.gz
dpkg-source: building pidgin in pidgin_2.0.2-1.diff.gz
dpkg-source: building pidgin in pidgin_2.0.2-1.dsc
 debian/rules build
dh_testdir
# Add here commands to configure the package.
dh_testdir
# Add here commands to compile the package.
/usr/bin/make
make[1]: Entering directory `/home/kreuger/.debcreator/pidgin/pidgin-2.0.2'
make[1]: *** No targets specified and no makefile found.  Stop.
make[1]: Leaving directory `/home/kreuger/.debcreator/pidgin/pidgin-2.0.2'
make: *** [build-stamp] Error 2

For amsn, the output I got was
> mkdir /home/kreuger/.debcreator/amsn
check directories
cmd: cp -r /home/kreuger/Downloads/Updates/msn /home/kreuger/.debcreator/amsn/amsn-svn-20070723 [0]
check files
dhmake
cmd: cd /home/kreuger/.debcreator/amsn/amsn-svn-20070723 && DEBEMAIL="kreugerburns@gmail.com" DEBFULLNAME="Kreuger Burns" /usr/bin/debcreator_dhmake --single -c GPL 1> /dev/null
failed

---

### Post by kosmo on 2007-07-24
OK, i found what disturbing debcreator to make brasero's deb and others who have cache option enabled by default. In configure script it has this option:

 --enable-cache Run update-* to update mime, desktop and icon caches when installing [default = yes]

 I can't find better way (i'm not programmer) to disable cache and i change it to this:

```
if test x"$enable_caches" = "xyes"; then
  UPDATE_CACHES_TRUE='#'
  UPDATE_CACHES_FALSE=
 else
  UPDATE_CACHES_TRUE=
  UPDATE_CACHES_FALSE='#'
 fi
``` 

 And voila!:) Or in rule file i must add at the end of configure --disable-cache. I don't know why this cache doesn't work with debcreator, but maybe you can now handle this mime-icon-desktop cache thing, i hope, in some better way.
 P.S. Better way? There it is!:guitar: Inside debhelper package (/usr/share/debhelper/autoscripts) exists all those autoscripts that you must call or borrow and implement in your code. Hope this helps.

---

### Post by leibowitz on 2007-07-24
Kreuger: No there's no way to compile pidgin at the moment. I did find a way to pass the first error (things about undefined reference to purple_* function in ssl.c)

What you did is useless, and you did it wrong. 

> make[1]: *** No targets specified and no makefile found. Stop.

You probably removed completly the ./configure line I was talking about in an earlier post.

By the way, even if you did it correctly, it would just have failed after the compilation and no package would have been build.


For amsn, you can either type this in a terminal:
```
cd /home/kreuger/.debcreator/amsn/amsn-svn-20070723 && DEBEMAIL="kreugerburns@gmail.com" DEBFULLNAME="Kreuger Burns" /usr/bin/debcreator_dhmake --single -c GPL
```

Or download the last version of debcreator (v0.3.9.2) and call it with --debug

---

### Post by Kreuger on 2007-07-24
I'm sure left ./configure line in with what you had. I know it would've failed again anyway but I wanted to see if I could get that far. Maybe we can contact the pidgin devels and they might have an idea of what to do.. I have v0.3.9.1 but I'll get v0.3.9.2. I got that error using the --debug with the version I have now though.

Edit: Now for amsnI just grabbed the svn source off their site and tried it, it shows:
> mkdir /home/kreuger/.debcreator/msn
check directories
cmd: cp -r /home/kreuger/Downloads/Updates/msn /home/kreuger/.debcreator/msn/msn-0.0.20070724 [0]
check files
dhmake
cmd: cd /home/kreuger/.debcreator/msn/msn-0.0.20070724 && DEBEMAIL="kreugerburns@gmail.com" DEBFULLNAME="Kreuger Burns" /usr/bin/debcreator_dhmake --single  -c gpl
You already have a debian/ subdirectory in the source tree.
dh_make will not try to overwrite anything.
failed So I just deleted that directory and it worked

Edit 2: Now it's giving me a problem installing: (this was using GDebi)
> Selecting previously deselected package msn.
(Reading database ... 199001 files and directories currently installed.)
Unpacking msn (from .../amsn0.97RC1+svn20070724.deb) ...
dpkg: error processing /home/kreuger/Downloads/Updates/amsn0.97RC1+svn20070724.deb (--install):
 trying to overwrite `/usr/share/amsn/abook.tcl', which is also in package amsn
dpkg-deb: subprocess paste killed by signal (Broken pipe)
(Reading database ... 199001 files and directories currently installed.)
Unpacking msn (from .../amsn0.97RC1+svn20070724.deb) ...
dpkg: error processing /home/kreuger/Downloads/Updates/amsn0.97RC1+svn20070724.deb (--install):
 trying to overwrite `/usr/share/amsn/abook.tcl', which is also in package amsn
dpkg-deb: subprocess paste killed by signal (Broken pipe)

---

### Post by leibowitz on 2007-07-24
> Trying to overwrite `/usr/share/amsn/abook.tcl', which is also in package amsn

Apparently the package you created has some files that are present in the package called "amsn". I don't know how to fix this, but I would try to add "amsn" in one of the dependencies field ("Replaces" seems a good one)

Though the last error could still be an issue.

> dpkg-deb: subprocess paste killed by signal (Broken pipe)

---

### Post by Kreuger on 2007-07-24
I don't see a replaces field.

---

### Post by leibowitz on 2007-07-25
You need to use the last version, which is 0.3.9.2. This has a replaces field

Otherwise you could still try to edit the debian/control file generated during pre-checks, and add a "Replaces: amsn" line under the "Package: " one.

Though this need to be done by hand, in a terminal, like was explained earlier for other tasks.

---

### Post by kosmo on 2007-07-25
And I can confirm this. There is no 'Replaces' field on the Package-meta-data/Optional window
in 0.3.9.2 version.
 P.S. I add this in main.c and now it have Replaces field. Is this OK?

 ```
interface_attach_entrylabel_totable(widg->table_depend,
			widg->label_depreplaces, 
			widg->entry_depreplaces, 11);
```

  @Kreuger
  You can, for now, first try to fix that broken package. Synaptic/Edit/Fix Broken Packages.
And then install debcreator's amsn package with gdebi or gdebi-gtk or with dpkg -i

 Instead of this, you can also try (but with caution) with:

 ```
sudo dpkg -i --force-overwrite amsn0.97RC1+svn20070724.deb
```

---

### Post by leibowitz on 2007-07-25
You are right there is no replaces filed. I just found out I forgot to attach the replaces field. Sorry for having misinformed you. I really thought it was there ...

kosmo: don't forget to edit the line 494 
> 
widg->table_depend = gtk_table_new(11, 2, FALSE);

And put 12 in place of 11.

---

### Post by kosmo on 2007-07-25
Thank you, i will put that, but i put also "debcreator" in place of "unknown" in line 446.
Then change sections_trans.h to something more comprehensible:). I remove "alien" and "unknown" section because maintainers and users doesn't need this sections and add "debcreator", because sections must have proper names and debcreator's name is a name of fame:KS, add "non-free/utils", because it exist in Ubuntu and finally align all sections from A to Z. Thats much more i liked and maybe you will.:guitar:

---

### Post by Kreuger on 2007-07-25
> Instead of this, you can also try (but with caution) with:

sudo dpkg -i --force-overwrite amsn0.97RC1+svn20070724.deb Yeah that's how I got it to work but I'd rather if I shared this with anyone they need not have to do that. I was told it's because it's not trying to upgrade, rather install along side it (at least thats my understanding) so I'm sur ethe replaces will fix it. Where in the main.c file do I add the replaces code? I see a thing for replaces already there..
> 		interface_create_labelentry(&widg->label_depreplaces,
			"Replaces:",
			&widg->entry_depreplaces,
			NULL); it's just above the line > widg->table_depend = gtk_table_new(11, 2, FALSE);

 By the way I was wondering if we can somehow create templates to use so we don't have to add all the info all the time just open the template and add in the new info for the updated version?

---

### Post by leibowitz on 2007-07-25
**kosmo:** great. Thanks for your contribution.

By the way I'm unsure of the sections name for "non-free", "main", and "contrib". 

As far I understand, "main" should never be present. Because everything under main should be presented as "section". But for the non-free and contrib, it should be specified like this: "non-free/section"

Source: [http://www.debian.org/doc/debian-policy/ch-archive.html#s-subsections](http://www.debian.org/doc/debian-policy/ch-archive.html#s-subsections)

I need some clarification/confirmation on this.


**Kreuger: **the widgets are already created and the code is done around it. You just need to add what kosmo said after they have been created (after what you quoted).

This is what need to be added :
> interface_attach_entrylabel_totable(widg->table_depend,
			widg->label_depreplaces, 
			widg->entry_depreplaces, 11);

This is what need to be changed:
> widg->table_depend = gtk_table_new(11, 2, FALSE);

Should become 12 instead of 11.

Or you could wait the next version.

PS: all modification are in the "src/main.c" file

---

### Post by Kreuger on 2007-07-25
Just to be sure, you mean it goes between Replaces and Architecture right? Like this:
> 		interface_create_labelentry(&widg->label_depreplaces,
			"Replaces:",
			&widg->entry_depreplaces,
			NULL);
		interface_attach_entrylabel_totable(widg->table_depend,
		widg->label_depreplaces,
		widg->entry_depreplaces, 11);

		interface_create_labelentry(&widg->label_pkgarch,
			"Architecture:",
			&widg->entry_pkgarch,
			"any"); I tried that and there was still no replaces. When are you planning on releasing the next one? And is there anything we can do for templatest like I previously said?

---

### Post by leibowitz on 2007-07-25
> When are you planning on releasing the next one? 

I have a problem to fix, that is probably more important than anything else. I need to found out what causing this first.

> And is there anything we can do for templatest like I previously said?

Of course. I have my idea on this. Probably being able to load all the fields from a file would be enough. Though that is _not_ coming soon.

---

### Post by kosmo on 2007-07-26
Because of all these, little to say, weird sections related problem with Synaptic...

```
                              gdebi or dpkg -f   Synaptic

zsnes                         contrib/otherosfs  checkinstall    
unrar                         non-free/utils     Utilities (non free)
drdsl                         non-free/comm      Base System (restricted)
linux-restricted-modules-386  restricted/base    Base System (restricted)
nvidia-kernel-common          contrib/x11        Miscellaneous  - Graphical (restricted)
nvidia-glx                    restricted/misc    Miscellaneous  - Graphical (restricted)
avm-fritz-firmware            restricted         Miscellaneous  - Text Based (restricted)
gtk2-engines-clearlooks       gnome              GNOME Desktop Environment
gtk2-engines-crux             gnome              Graphics
gtk2-engines-mist             gnome              Miscellaneous  - Graphical
```

   ...i think that we can ignored it and have one proposal that may simplify and clarify problem with sections:

 First remove that sections patch, it is useless and will produce only misunderstandings and headaches in future. Then create 'Sections' field with empty box, like all others in 'Optional', where user can put in it whatever section he want to be (Why it can't be contrib/otherosfs when i can simply write that in box?:)) and if users don't want to write anything in that empty box then it goes with debcreator section and that is it. 

P.S. How users knows what to put in it? Later, you can make balloon with short description.:)

---

### Post by Kreuger on 2007-07-26
**leibowitz** - what's the current problem. I'd like to try and help. Also, did I get the code right for the replaces?

**kosmo** - I usually just use older debs to see what section they show up as (using GDebi) and use that one. I dont bother worrying about synaptic (although maybe I should?)

---

### Post by leibowitz on 2007-07-26
The problem is related to a crash. I don't know why it's crashing on some user system.

For the code part, just wait that it is published on the bazaar launchpad mirror. You need to see a "Revision 2". It is already pushed, but it will take times before it's mirrored.

[http://codebrowse.launchpad.net/~gianni.net/debcreator/debcreator/changes](http://codebrowse.launchpad.net/~gianni.net/debcreator/debcreator/changes)

When you finally see rev. 2, you can download the main.c file.

Edit: it's updated, you can download the file from the following link.

[http://codebrowse.launchpad.net/~gianni.net/debcreator/debcreator/download/bobyjoe0%40yahoo.fr-20070726173038-eu24rc3mtgiol3hd/main.c-20070723225524-y7jhojhwz3t1cv6d-10/main.c](http://codebrowse.launchpad.net/~gianni.net/debcreator/debcreator/download/bobyjoe0%40yahoo.fr-20070726173038-eu24rc3mtgiol3hd/main.c-20070723225524-y7jhojhwz3t1cv6d-10/main.c)

---

### Post by kosmo on 2007-07-26
@Kreuger
   No, users shouldn't worry about sections in Synaptic, they will alredy be badly show in it
when install some local debs with gdebi or dpkg -i and all that because of APT nature + GPG
signature of CD/DVD and repos on net.:) I just mention that exists these differences between
Synaptic-gdebi-dpkg in sections and functionality point of view and because of that i have
crucial proposal for properly handle sections in debcreator.

---

### Post by Kreuger on 2007-07-27
> Edit: it's updated, you can download the file from the following link. Thanks I'll give 'er a go

Edit: Still not showing. Should I redownload the source?

Edit 2: Apparently the source installed it to /usr/local/bin

Edit 3: Even with using replaces field to have it replace amsn I got the error.

---

### Post by leibowitz on 2007-07-27
What if you uninstall amsn first?

---

### Post by Kreuger on 2007-07-27
Thats possible. But something else went wrong  because after I installed it and tried to start amsn it wouldnt work. So I went into my binaries and it was gone. I had to remove and reinstall it using an alternate deb

---

### Post by kosmo on 2007-07-28
I see that "weird" bug on launchpad (but i shouldn't agitate there) and must say that satkata
probably running session as root and that is much more weird then segfault.:popcorn:

 What's your opinion about sessinon thing? I think that the best way to nameing sections like Debian Policy Manual- section 2.4 provide + some Ubuntu specific sections and no Synaptic's, but don't know what you think about it. And for my proposal, what do you think about that?

 Some warnings from debcreator-build.log, when i try to make debcreator.deb: 

 ```
action.c: In function ‘update_textview_filelist’:
action.c:44: warning: implicit declaration of function ‘set_textview_text’
action.c: In function ‘copy_from_to’:
action.c:175: warning: implicit declaration of function ‘g_printf’
action.c:190: warning: implicit declaration of function ‘g_mkdir’

callback.c: In function ‘create_tmpdir’:
callback.c:219: warning: implicit declaration of function ‘g_mkdir’
callback.c: In function ‘operation_call_first’:
callback.c:761: warning: implicit declaration of function ‘do_next_operation’
callback.c:759: warning: unused variable ‘widg’
callback.c: In function ‘do_next_operation’:
callback.c:773: warning: unused variable ‘progress_status’
callback.c: In function ‘setdir’:
callback.c:1029: warning: unused variable ‘exist’
callback.c: In function ‘start_nautilus’:
callback.c:59: warning: ‘cmd’ may be used uninitialized in this function
```

 I don't know what these warnings try to tell me? Maybe you can explain it?

 P.S. These 3 screenshots is taken in about 1 second when i start debcreator. Little time, but perceptible.:)

---

### Post by leibowitz on 2007-07-28
> **kosmo said:**
>  What's your opinion about sessinon thing? I think that the best way to nameing sections like Debian Policy Manual- section 2.4 provide + some Ubuntu specific sections and no Synaptic's, but don't know what you think about it. And for my proposal, what do you think about that?

I don't know much. I don't have a really good opinion on that, and I lack the experience to say what it should be. So I will probably ask where it is appropriate to have more opinion on that before doing anything else.


>  Some warnings from debcreator-build.log, when i try to make debcreator.deb [...]
 I don't know what these warnings try to tell me? Maybe you can explain it? 

Don't know. What are you trying to compile anyway (source tar, bazaar branch ?)

> P.S. These 3 screenshots is taken in about 1 second when i start debcreator. Little time, but perceptible.:)

I know. But what do you propose I do for that? I don't even know if it's caused by some wrong programmation from me or if it's normal behavior. In other words have you any idea how to improve this? I don't.

PS: I'm sure the crash is caused by some wrong programmation, at least I think so. I'm not sure but it could be. It's so weird..

---

### Post by kosmo on 2007-07-29
```
I don't know much. I don't have a really good opinion on that, and I lack the experience to say what it should be. So I will probably ask where it is appropriate to have more opinion on that before doing anything else.
```

 OK, there is my conclusion. I must say this is nothing that we carry about so much, but
there are linda and lintian programs and thay said what isn't orderly and properly from maintainer to put in it. If (s)he want to put in it whatever section who isn't in Debian Policy Manual- section 2.4 [http://www.debian.org/doc/debian-policy/ch-archive.html#s-subsections](http://www.debian.org/doc/debian-policy/ch-archive.html#s-subsections) , than (s)he break that statute and therefore that packet is incorrect. Ubuntu has some sections like 'restricted' and for these packets there is no way to come into use in Debian distribution, but...  Apt (Synaptic use it) use lists from /var/lib/apt/lists and these lists are cached from CD/DVD media or from repositorium. You can see that sections for some packages in main and restricted lists isn't correct with what gdebi or dpkg -f says (if you have installed some with them see /var/lib/dpkg) and for some with what they really are if not. For example, nvidia-kernel-common (that isn't installed with dpkg or gdebi, but...) If you try to see what section he belong in /var/lib/apt/lists/...something_restricted_binary, you will see restricted/x11, but if you look from it on CD/DVD or repo and check this with gdebi or dpkg -f, there it is ... contrib/x11 (Debian Policy Manual- section 2.4) and because of that Ubuntu choose right way for it. Only difference on Ubuntu is his restricted sections and for remains it just rename these sections in his apt lists in order to avoid it.

 ```
Don't know. What are you trying to compile anyway (source tar, bazaar branch ?)
```

 tar.gz

 ```
I know. But what do you propose I do for that? I don't even know if it's caused by some wrong programmation from me or if it's normal behavior. In other words have you any idea how to improve this? I don't.
```

 That's not normal behavior, i think, because i didn't see that before.:) No, i'm not programmer to propose some clean way to improve this, but maybe i can find reasons, who knows?

 ```
PS: I'm sure the crash is caused by some wrong programmation, at least I think so. I'm not sure but it could be. It's so weird..
```

 Segfaults, that are only few isolated cases! OO, Blender, GIMP... all these big programs has it, but in 99% cases generally isn't prior to them.

---

### Post by Kreuger on 2007-07-29
Its definitely not normal behavior mine is fine. I'd think it's probably a video driver issue.

---

### Post by leibowitz on 2007-07-29
I checked Evolution account druid (same kind of gnome_druid than debcreator).

And it seems to just "pop-up".

Debcreator is different. It shows the druid first, empty, then fill in the widgets and get bigger.

So it's definitely a programming issue. Again I don't know how to improve this. Have no idea.

---

### Post by kosmo on 2007-07-30
OK, i'm find something that works. So, if we can't improve it, why just can't hide the druid.:)

  In line 110 put this:

  ```
gtk_widget_hide(widg->window);
```

  And voila, druid is invisible to user.:)

 P.S. If you also want to windows always be on center of screen, put this in new 112 line.

  ```
gtk_window_set_position(GTK_WINDOW(widg->window),
			GTK_WIN_POS_CENTER_ALWAYS);
```

  I think this is nice.:guitar:

---

### Post by Kreuger on 2007-08-02
I created a ticket about the problem compiling pidgin and apparently it's because debcreator is using certain flags it shouldn't be and that's causing the problem (they are -Wl,-z,defs).

---

### Post by kosmo on 2007-08-02
Interesting! For some program i need to change --prefix=/usr/local in rules file. For example gxine 5.10. Install is OK, but when i run it... Segfault. With /usr/local it run just fine.
 
 Belooted is very funny game:guitar: (i'm stuck with it for hours) and of course, it was succesfully debcreated. Thanks!!!

---

### Post by Kreuger on 2007-08-05
Nevermind this post. I found the problem myself.

---

### Post by Kreuger on 2007-08-11
There seems to be a problem with amsn packages built with debcreater. For some reason, amsn wont load from my menu in fluxbox and when I run ./amsn from the terminal (in my /usr/bin) it says no such file or directory. However doing an > ls | grep amsn shows > amsn, amsn-remote, amsn-remote-CLI. When I used a file manager, the files showed by they hard these little arrows which I thought meant it was a shortcut. However, I can't seem to edit the files and right clicking does nothing at all. I'm not sure if this is fault of debcreator or amsn. It builds and installs with the resulting deb fine. But when you exit amsn and try to reopen it later, it wont work.

---

### Post by Kreuger on 2007-08-19
Any ideas?

---

### Post by leibowitz on 2007-08-21
Sorry, I'm pretty much busy all the time now on something not related to gnome/ubuntu nor linux at all... 

Oh, and I have no idea what's causing your problem.

You may try some commands in a terminal though, like "which", "type", and "file"

---

### Post by Kreuger on 2007-08-23
That's alright. It's not all that important. I can just always build the sources for myself :p

---

### Post by nanotube on 2007-08-23
why not just use epm ([http://www.easysw.com/epm/](http://www.easysw.com/epm/))
it seems to already have the features... 
you might save yourself effort and start from the epm code base...

---

### Post by leibowitz on 2007-08-23
It's not exactly the same purpose, is it?

Could you explain a little bit why you propose a cross-platform installer to use as a debian package creator ?

---

### Post by nanotube on 2007-08-23
> **leibowitz said:**
> It's not exactly the same purpose, is it?

Could you explain a little bit why you propose a cross-platform installer to use as a debian package creator ?

epm is not an "installer" it is a "package creator". and among the package types that it supports, is our favorite .deb. :) see the epm manual for more info ([http://www.easysw.com/epm/epm-book.html](http://www.easysw.com/epm/epm-book.html))

in fact, i use it to create .debs for the [ubuntuzilla]("http://ubuntuzilla.sourceforge.net/") releases. it works just fine, and way easier than the "standard" deb packaging tools.

---

### Post by nanotube on 2007-08-23
> **Kreuger said:**
> There seems to be a problem with amsn packages built with debcreater. For some reason, amsn wont load from my menu in fluxbox and when I run ./amsn from the terminal (in my /usr/bin) it says no such file or directory. However doing an  shows . When I used a file manager, the files showed by they hard these little arrows which I thought meant it was a shortcut. However, I can't seem to edit the files and right clicking does nothing at all. I'm not sure if this is fault of debcreator or amsn. It builds and installs with the resulting deb fine. But when you exit amsn and try to reopen it later, it wont work.

whats your output for 
```
ls -al /usr/bin/amsn
```

---

### Post by Kreuger on 2007-08-24
> why not just use epm That's confusing as hell, I couldn't even figure out how ot get the GUI.

> whats your output for 
kreuger@kreuger-desktop:~$ ls -al /usr/bin/amsn
lrwxrwxrwx 1 root root 87 2007-08-24 18:44 /usr/bin/amsn -> /home/kreuger/.debcreator/amsn/amsn-0.97RC1+svn20070824/debian/amsn/usr/share/amsn/amsn

I guess that means it installed to /usr/share/amsn?

---

### Post by leibowitz on 2007-08-24
It means the install process of amsn do some things wrong. It should not symlink to the binary on the builded directory.

That's not common behavior. You should edit some makefile/rules to fix this, I suppose.

Edit: or fakeroot is not installed correctly. If other softwares are builded fine then it's not related to fakeroot.

---

### Post by Kreuger on 2007-08-26
yeah others seem fine. Doesn't debcreator make the deb the rules file? Im pretty sure it always complains at me because amsn already has a debian folder that I have to delete so I assume it makes the file (it's in there isn't it?)

---

### Post by nanotube on 2007-08-26
> **Kreuger said:**
> That's confusing as hell, I couldn't even figure out how ot get the GUI.


kreuger@kreuger-desktop:~$ ls -al /usr/bin/amsn
lrwxrwxrwx 1 root root 87 2007-08-24 18:44 /usr/bin/amsn -> /home/kreuger/.debcreator/amsn/amsn-0.97RC1+svn20070824/debian/amsn/usr/share/amsn/amsn

I guess that means it installed to /usr/share/amsn?

ehrm, nooo, it means it installed a symlink into /usr/bin that points to 
/home/kreuger/.debcreator/amsn/amsn-0.97RC1+svn20070824/debian/amsn/usr/share/amsn/amsn

since it says "no such file or directory" when you run /usr/bin/amsn, my guess is that that file with a fancy long path doesn't actually exists.

which in turn means something went wrong with your package creation process.

no clue how you'd actually fix it though. :)

---

### Post by nanotube on 2007-08-26
> **Kreuger said:**
> That's confusing as hell, I couldn't even figure out how ot get the GUI.


kreuger@kreuger-desktop:~$ ls -al /usr/bin/amsn
lrwxrwxrwx 1 root root 87 2007-08-24 18:44 /usr/bin/amsn -> /home/kreuger/.debcreator/amsn/amsn-0.97RC1+svn20070824/debian/amsn/usr/share/amsn/amsn

I guess that means it installed to /usr/share/amsn?

epm is in the repositories.
sudo apt-get install epm.

also, i don't know about the gui, i just use epm in commandline mode. create the .list file, and run epm with some options...

edit: so, leibowitz, what do you think about epm? does it do what you want your package creator to do?

---

### Post by leibowitz on 2007-08-26
kreuger: I was not talking about debian/rules file, but Makefile related rules. That's what you put on configure.{ac,in} and Makefile.{am,in}

But I suppose amsn does some non-standard things. I should check before saying this, but I have not much free time at the moment.


nanotube: not exactly. I think it does much more than what I wanted to do. My first goal was to have an Ubuntu .deb package creator, to build third-application .deb, with just one package.

Now I want (but will probably never achieve) to do a full debian package creator for debian package maintainer. But I need to do some packaging first, or talk with packagers, to know how to do this carefully.

That's why I probably will never achieve this. That's too much time and effort, and I hope I will not drop the project before doing all this.

So epm is kind of out of my goal right now. And I don't think it will change in the future.

---

### Post by Kreuger on 2007-09-08
I found out I can easily build a package for amsn using ```
./configure && make deb
``` so I'll be using that from now on or at least until you get it straightened away

---

