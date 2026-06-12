---
title: "HowTo: How to install DOSBOX 0.70"
date: 2007-04-21
forum: Outdated Tutorials &amp; Tips
---

### Post by Josh1 on 2007-04-21
This is how I got DOSBOX to work with my installation of Ubuntu, and it runs perfectly with no glitches.

[COLOR="Red"]**[SIZE="3"]What is DOSBOX?[/SIZE]**[/COLOR]
[SIZE="1"][I]DOSBox emulates an Intel x86 PC, complete with sound, graphics, mouse, modem, etc., necessary for running many old DOS games that simply cannot be run on modern PCs and operating systems, such as Microsoft Windows 2000, Windows XP, Linux and FreeBSD. However, it is not restricted to running only games. In theory, any DOS application should run in DOSBox, but the emphasis has been on getting DOS games to run smoothly, which means that communication, networking and printer support are still in early developement.

DOSBox also comes with its own DOS-like command prompt. It is still quite rudimentary and lacks many of the features found in MS-DOS, but it is sufficient for installing and running most DOS games.[/I][/SIZE]

Now on to the fun :)

[COLOR="Red"]**[SIZE="3"]1) Downloading DOSBOX.[/SIZE]**[/COLOR]
You can download DOSBOX from their [official site]("http://sourceforge.net/project/downloading.php?groupname=dosbox&filename=dosbox-0.70.tar.gz&use_mirror=optusnet").

2) Installing DOSBOX
In terminal, type in the following commands:
```

cd ~
tar xvf dosbox-0.70.tar.gz
cd dosbox-0.70
./configure
make

```

This will install dosbox, and might take a while depending on your machine! :)

---

### Post by Necreia on 2007-04-23
That's a lot simpler than I had first thought.

Thanks for the write-up!

---

### Post by sebas.rhcp on 2007-04-26
:(

```

checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether make sets $(MAKE)... (cached) yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking for sdl-config... no
checking for SDL - version >= 1.2.0... no
*** The sdl-config script installed by SDL could not be found
*** If SDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the SDL_CONFIG environment variable to the
*** full path to sdl-config.
configure: error: *** SDL version 1.2.0 not found!

```

---

### Post by Perfect Storm on 2007-04-26
Check here for full installation guide of dosbox (with dosbox game launcher): [http://gaming.gwos.org/e107_plugins/content/content.php?content.39](http://gaming.gwos.org/e107_plugins/content/content.php?content.39)



Locking this thread due to incomplete guide.

---

