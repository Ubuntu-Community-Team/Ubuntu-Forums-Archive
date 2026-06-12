---
title: "develop 64-bit and 32-bit apps on 64-bit ubuntu 12.04"
date: 2012-06-06
forum: Packaging and Compiling Programs
---

### Post by honestann on 2012-06-06
[FONT=Book Antiqua]I've been developing a 3D game/graphics/simulation engine on 64-bit ubuntu 10.04 LTS.  Actually, it is cross platform and compiles and runs as a 32-bit executable on my windoze machine too, but that's not important here.[/FONT]
[FONT=Book Antiqua][/FONT] 
[FONT=Book Antiqua]Recently I switched to 64-bit ubuntu 12.04 LTS, and I'm having trouble getting my application to compile, link, execute.  Actually, I got the 64-bit version to work once I sorta half figured out there were new-and-confusing directories:[/FONT]
[FONT=Book Antiqua][/FONT] 
[FONT=Book Antiqua]/usr/include/x86_64-linux-gnu/[/FONT]
[FONT=Book Antiqua]/usr/lib/x86_64-linux-gnu/[/FONT]
[FONT=Book Antiqua][/FONT] 
[FONT=Book Antiqua]Some library files that (I think) used to be in /usr/lib are now in /usr/lib/x86_64-linux-gnu/ (including cairo, pango, freetype and maybe glib and/or zlib too --- and who knows what else).  [/FONT][FONT=Book Antiqua]I assume that's why adding "/usr/lib/x86_64-linux-gnu" to my linker search path coaxed my codeblocks IDE into successfully compiling and running the 64-bit version.[/FONT]
[FONT=Book Antiqua][/FONT] 
[FONT=Book Antiqua]Unfortunately, the 32-bit version seems further from compiling.  I was compling and executing on 64-bit ubuntu 10.04 LTS until I switched to 64-bit ubuntu 12.04 LTS last week, and I don't know why.[/FONT]
[FONT=Book Antiqua][/FONT] 
[FONT=Book Antiqua]Frankly, I'd really love to understand what is the correct way for software developers to compile, link, execute 32-bit and 64-bit versions of applications.  So that's my question.[/FONT]
[FONT=Book Antiqua][/FONT] 
[FONT=Book Antiqua]Here are some basics of what is my IDE and what's in my applications, in case that matters:[/FONT]
[FONT=Book Antiqua][/FONT] 
[FONT=Book Antiqua]These are installed by the ubuntu software center:[/FONT]
[FONT=Book Antiqua][/FONT] 
[FONT=Book Antiqua]codeblocks IDE[/FONT]
[FONT=Book Antiqua]gcc[/FONT]
[FONT=Book Antiqua]g++[/FONT]
[FONT=Book Antiqua]gdb[/FONT]
[FONT=Book Antiqua]gcc-multilib[/FONT]
[FONT=Book Antiqua]g++-multilib[/FONT]
[FONT=Book Antiqua]libc6-dev[/FONT]
[FONT=Book Antiqua]libc6-dbg[/FONT]
[FONT=Book Antiqua]libc6-i386[/FONT]
[FONT=Book Antiqua]libc6-dev-i386[/FONT]
[FONT=Book Antiqua]build-essential[/FONT]
[FONT=Book Antiqua]libwxgtk2.8-0[/FONT]
[FONT=Book Antiqua]libwxgtk2.8-dev[/FONT]
[FONT=Book Antiqua]libwxgtk2.8-dbg[/FONT]
[FONT=Book Antiqua]wx-common[/FONT]
[FONT=Book Antiqua]wx2.8-doc[/FONT]
[FONT=Book Antiqua]glib (libglib2.0-0 : libglib2.0-bin : libglib2-data : libglib2.0-dev : libglib2.0-doc)[/FONT]
[FONT=Book Antiqua]xlib (libx11-6, libx11-dev, libx11-doc)[/FONT]
[FONT=Book Antiqua]zlib (zlib1g-dev)[/FONT]
[FONT=Book Antiqua]cairo (libcairo2, libcairo2-dev, libcairo2-dbg, libcairo2-doc)[/FONT]
[FONT=Book Antiqua]pango (libpango1.0-0, libpango1.0-dev, libpango1.0-0-dbg, libpango1.0-doc)[/FONT]
[FONT=Book Antiqua]freetype (libfreetype6, libfreetype6-dev)[/FONT]
[FONT=Book Antiqua][FONT=Book Antiqua][/FONT] 
I create the following directories: 
[FONT=Book Antiqua]sudo mkdir /usr/include/GL[/FONT]
[FONT=Book Antiqua]sudo mkdir /usr/include/glew[/FONT]
 
[/FONT][FONT=Book Antiqua]The following are downloaded and installed where I say below:[/FONT]
[FONT=Book Antiqua][/FONT] 
[FONT=Book Antiqua]download latest nvidia driver for 64-bit linux[/FONT]
[FONT=Book Antiqua]  - extract contents into temporary directory[/FONT]
[FONT=Book Antiqua]  - copy files to /usr/include/GL[/FONT]
[FONT=Book Antiqua]    - gl.h : glext.h : glx.h : glxexth[/FONT]
[FONT=Book Antiqua][/FONT] 
[FONT=Book Antiqua]download latest fmodex driver for 64-bit linux[/FONT]
[FONT=Book Antiqua]  - extract contents into temporary directory[/FONT]
[FONT=Book Antiqua]  - copy files to /usr/include/fmodex[/FONT]
[FONT=Book Antiqua]     - all the .h and .hpp files supplied (about 10)[/FONT]
[FONT=Book Antiqua]  - copy files to /usr/lib[/FONT]
[FONT=Book Antiqua]      - libfmodex64-4.40.07.so[/FONT]
[FONT=Book Antiqua]      - libfmodexL64-4.40.07.so[/FONT]
[FONT=Book Antiqua]      - sudo ln -s libfmodex64-4.40.07.so libfmodex.so[/FONT]
[FONT=Book Antiqua]      - sudo ln -s libfmodexL64-4.40.07.so libfmodexL.so[/FONT]
[FONT=Book Antiqua][/FONT] 
[FONT=Book Antiqua]download latest GLEW files to make latest OpenGL functions available[/FONT]
[FONT=Book Antiqua] - the glew .c files are put into my build directory and compiled into my app[/FONT]
[FONT=Book Antiqua]    - glew.c : glewinfo.c : visualinfo.c[/FONT]
[FONT=Book Antiqua] - the glew .h files are put into /usr/include/glew directory.[/FONT]
[FONT=Book Antiqua]    - glew.h :  glxew.h : wglew.h[/FONT]
[FONT=Book Antiqua][/FONT] 
[FONT=Book Antiqua]Anyway, when I try to compile the 32-bit version, it says:[/FONT]
[FONT=Book Antiqua]   cannot find -lGL[/FONT]
[FONT=Book Antiqua]   cannot find -lX11[/FONT]
[FONT=Book Antiqua][/FONT] 
[FONT=Book Antiqua]I have a feeling more problems will arise once those two are resolved, but my REAL question is this:[/FONT]
[FONT=Book Antiqua][/FONT] 
[FONT=Book Antiqua]**What is the correct way to develop 32-bit and 64-bit versions of my applications on 64-bit ubuntu 12.04 linux?**[/FONT]
[FONT=Book Antiqua][/FONT] 
[FONT=Book Antiqua]What 32-bit stuff needs to be downloaded?  Where do their .h files belong?  Where do their .so (link library) files belong?  What are these new /usr/include/x86_64-linux-gnu/ and /usr/lib/x86_64-linux-gnu/ directories all about, and what should be inside them (the /usr/include/ and /usr/lib/ directories still contains lots of files).[/FONT]
[FONT=Book Antiqua][/FONT] 
[FONT=Book Antiqua]Do I need to download 32-bit versions of fmodex?  Of nvidia video drivers?  Of what do I need separate 32-bit versions of, anyway?[/FONT]
[FONT=Book Antiqua][/FONT] 
[FONT=Book Antiqua]I sure would like to understand all this clearly... and do this correctly.  Frankly, I don't know why my 64-bit ubuntu 10.04 LTS compiled, linked and executed 32-bit versions of my applications.  I'm sure I didn't download 32-bit versions of fmodex or nvidia video drivers... or any of those other packages.  Strange!  Straighten me out!  Thanks![/FONT]

---

### Post by MadCow108 on 2012-06-06
ubuntu 12.04 now features the so called "multi-arch" to allow better cross compiling and coinstallation of multiple architectures on one system.
it among other things replaces the unmaintainable ia32-libs package which previously provided a bunch of 32 bit libraries.

libraries are supposed to go into /usr/lib/<arch-triplet>
where arch-triplet is e.g. x86_64-linux-gnu for standard 64 bit or i386-linux-gnu for standard 32 bit. There are many more triplets for all kind of architectures and abi's.

the toolchain knows about these paths, there is no need to ever explicitly refer to them.

To cross compile you now only need to install all required libraries for the target and a cross compiler
for 32/64 bit you need gcc-multilib and the i386 variant of all libraries.
To install a foreign architectures just add :i386 to the package.
e.g. apt-get install libx11-6:i386
it will automatically install all i386 dependencies for you.


in some cases the -dev packages are not coinstallable (e.g. libxml2-dev) in that case you have to change the installation on each target compile.
Also not all libraries are multiarched yet, if one is missing you are stuck with the old pbuilder/chroot approach.

---

### Post by honestann on 2012-06-07
> **MadCow108 said:**
> ubuntu 12.04 now features the so called "multi-arch" to allow better cross compiling and coinstallation of multiple architectures on one system. It among other things replaces the unmaintainable ia32-libs package which previously provided a bunch of 32 bit libraries.
 
libraries are supposed to go into /usr/lib/<arch-triplet>
where arch-triplet is e.g. x86_64-linux-gnu for standard 64 bit or i386-linux-gnu for standard 32 bit. There are many more triplets for all kind of architectures and abi's.
 
the toolchain knows about these paths, there is no need to ever explicitly refer to them.
 
To cross compile you now only need to install all required libraries for the target and a cross compiler. For 32/64 bit you need gcc-multilib and the i386 variant of all libraries.
 
To install a foreign architectures just add :i386 to the package.
e.g. apt-get install libx11-6:i386
It will automatically install all i386 dependencies for you.
 
In some cases the -dev packages are not coinstallable (e.g. libxml2-dev) in that case you have to change the installation on each target compile.
 
Also not all libraries are multiarched yet, if one is missing you are stuck with the old pbuilder/chroot approach.
 
Let me see if I understand this.
 
#1: I should remove the ia32-libs package.
 
#2: There should be no library files in /usr/lib any more.
 
#3: There should be many 64-bit library files in /usr/lib/x86_64-linux-gnu.
 
#4: There should be many 32-bit library files in /usr/lib/i386-linux-gnu.
 
#5: To compile 32-bit and 64-bit versions of my applications, I must find-or-download and install 32-bit and 64-bit versions of... which packages?
- zlib?
- glib? // install libglib2.0-0:i386? install libglib2.0-dev:i386?
- xlib? // is this libx11-6:i386? what is libx11-dev:i386 (separate headers?)
- cairo2?
- pango?
- freetype?
- fmodex?
- GL/GLX? // where would these libraries come from?
 
NOTE: I went to install libglib2.0-dev:i386 and a dialog appeared that said this: "If you install libglib2.0-dev:i386, future updates will not include new items in the Ubuntu desktop system set. Are you sure you want to continue?' The list was about 200 items long and included fundamental packages, including:
- install packages using the apt protocol - gtk+ frontend
- install packages using the apt protocol - common data
- build-essentials
- deja-dup
- g++
- g++-multilib
- gcc
- gcc-multilib
- gdb
- gedit
- gimp
- ... and literally 100~200 more items !!!
- Of course I said "cancel", cuz it looks like it would destroy my system. WTF ???
 
- I got a similar egregious warning on zlib1g-dev:i386 and canceled out.
- I got a similar egregious warning on libcairo2-dev:i386 and canceled out.
- I got a similar egregious warning on libpango1.0-dev:i386 and canceled out.
- I got a similar egregious warning on libfreetype6-dev:i386 and canceled out.
- Are all the above examples of "incompatible" as you called it? If so, what do I do?
 
- I got a less egregious warning on libglib2.0-bin:i386 and canceled out.
 
- I got no warnings installing libcairo2:i386
- I got no warnings installing libpango1.0-0:i386
- I got no warnings installing libglib2.0-0:i386
- I got no warnings installing libx11-dev:i386
- I got no warnings installing libx11-6:i386
 
#6: There are no separate .h files (same files for 32-bit and 64-bit with #ifdefs?).
 
#7: In fact, /usr/lib and /usr/lib32 contain lots of files.
 
#8: Should I be putting downloaded 64-bit libraries like "fmodex64.so" and "fmodexL64.so" into /usr/lib or /usr/lib/x86_64-linux-gnu? And likewise, should I be putting downloaded 32-bit libraries like "fmodex32.so" and "fmodexL32.so" into /usr/lib32 or /usr/lib/i386-linux-gnu?
 
What a complicated mess! Or maybe it just seems that way at this point.
 
NOTE:  I got most of the 32-bit version of my 3D engine to compile, but still get the following error:
 
warning:  libXext.so.6, needed by /usr/lib32/nvidia-current-updates/libGL.so, not found (try using -rpath or -rpath-link)
following by 6 lines like the following:
/usr/lib32/nvidia-current-updates/libGL.so   undefined reference to 'XextCreateExtension'
 
I note that the only libXext.so is inside the /usr/lib/x86_64-linux-gnu directory.

---

### Post by MadCow108 on 2012-06-07
> **honestann said:**
> Let me see if I understand this.
 
#1: I should remove the ia32-libs package.

in 12.04 its just a transitional package pulling lots of multiarch ones
you can keep if thats more convinient for you than installing whats needed.
 
> 
#2: There should be no library files in /usr/lib any more.

no, there are lots of libraries not multiarched yet, in the far future it maybe empty, but not yet.

> #5: To compile 32-bit and 64-bit versions of my applications, I must find-or-download and install 32-bit and 64-bit versions of... which packages?
- zlib?
- glib? // install libglib2.0-0:i386? install libglib2.0-dev:i386?
- xlib? // is this libx11-6:i386? what is libx11-dev:i386 (separate headers?)
- cairo2?
- pango?
- freetype?
- fmodex?
- GL/GLX? // where would these libraries come from?
you install what you needed
zlib1g-dev:i386
libglib2.0-dev:i386
libx11-dev:i386
libcairo2-dev:i386
libpango1.0-dev:i386
libfreetype6-dev:i386
libgl1-mesa-dev:i386
libglu1-mesa-dev:i386

> NOTE: I went to install libglib2.0-dev:i386 and a dialog appeared that said this: "If you install libglib2.0-dev:i386, future updates will not include new items in the Ubuntu desktop system set. Are you sure you want to continue?' The list was about 200 items long and included fundamental packages, including:

I have never seen this, what did you use to install?
indeed glib2.0-dev does not seem fully coinstallable so you have to juggle the installation for each compile
also you must make sure to not install the recommends python:i386 or you break your system:
apt-get install libglib2.0-dev:i386 --no-install-recommends
 
> #6: There are no separate .h files (same files for 32-bit and 64-bit with #ifdefs?).
in most cases the headers are the same and shared via reference counting between the packages.

 
> #8: Should I be putting downloaded 64-bit libraries like "fmodex64.so" and "fmodexL64.so" into /usr/lib or /usr/lib/x86_64-linux-gnu? And likewise, should I be putting downloaded 32-bit libraries like "fmodex32.so" and "fmodexL32.so" into /usr/lib32 or /usr/lib/i386-linux-gnu?
no user files don't go directly into /usr, /usr/local is a common place to put them
where you put them there is up to you, just don't put them in package manager territory or they might get overwritten on upgrades.
 
> What a complicated mess! Or maybe it just seems that way at this point.

cross compiling is always complicated, but with multiarch its simpler now (in the general case)

 
> warning:  libXext.so.6, needed by /usr/lib32/nvidia-current-updates/libGL.so, not found (try using -rpath or -rpath-link)
following by 6 lines like the following:
/usr/lib32/nvidia-current-updates/libGL.so   undefined reference to 'XextCreateExtension'

install libxext-dev:i386

---

### Post by honestann on 2012-06-07
> **MadCow108 said:**
>  
you install what you needed
zlib1g-dev:i386
libglib2.0-dev:i386
libx11-dev:i386
libcairo2-dev:i386
libpango1.0-dev:i386
libfreetype6-dev:i386
libgl1-mesa-dev:i386
libglu1-mesa-dev:i386
 
I have never seen this, what did you use to install?

 
On ALL the following packages, when I went to install them with the **ubuntu software center**, a dialog appeared that said the following:
 
**#####  the packages that generated the warning dialog**:
 - libglib2.0-dev:i386
 - zlib1g-dev:i386
 - libcairo2-dev:i386
 - libpango1.0-dev:i386
 - libfreetype6-dev:i386

**#####  the warning dialog that appeared said this**:
*If you install libglib2.0-dev:i386, future updates will not include new items in the Ubuntu desktop system set. Are you sure you want to continue?*
 
The list was about 200 items long and included fundamental packages, including:
[I]- install packages using the apt protocol - gtk+ frontend
- install packages using the apt protocol - common data
- build-essentials
- deja-dup
- g++
- g++-multilib
- gcc
- gcc-multilib
- gdb
- gedit
- gimp
- ... and literally 100~200 more packages !!![/I]
 
**#####  my reaction and actions**:
Of course I said "cancel" in the warning dialog for all these packages, because it looks like it would destroy my system.  Specifically, it seems to remove all support for 64-bit libraries !!!

> No, user files don't go directly into /usr, /usr/local is a common place to put them where you put them there is up to you, just don't put them in package manager territory or they might get overwritten on upgrades.
 
I'm not sure what this means.  What qualifies as a "user file"?
 
For example, I need to download and install the fmodex sound library so my 3D graphics application can call functions to play sounds.  Where should the *.so shared libraries in that downloaded package get put?
 - /usr/lib
 - /usr/lib/x86_64-linux-gnu
 - somewhere else

---

### Post by MadCow108 on 2012-06-08
for libglib2.0-dev:i386 you must not install the recommended packages, it will pull in python:i386 which will break your system
```
sudo apt-get install libglib2.0-dev:i386 --no-install-recommends
```

> I'm not sure what this means. What qualifies as a "user file"?
anything that doesn't belong to the package manager.
everything in /usr except /usr/local is package manager country

---

### Post by honestann on 2012-06-08
An update.  Apparently I caused myself a lot of trouble by NOT installing the ia32-libs package.  Once I "gave up" and installed that package, most of my problems vanished.  Oh, I still had to create a pile of softlinks to the hyper-verbose, fully-versioned filenames of the installed shared libraries, but otherwise that solved much of my problem.
 
I did find it wacko that I had to put a 64-bit search-path in my 32-bit application so it could get to certain glib headers, namely:
    /usr/lib/x86_64-linux-gnu/glib-2.0/include
 
I guess "multiarch" and "multilib" won't save us from needing the ia32-libs package for several more years, at least.  Huh?

---

### Post by MadCow108 on 2012-06-09
ia32-libs is an empty transitional package, it does nothing more than install other packages, so effectively its already gone:
contents in 12.04:
```
apt-file list ia32-libs
ia32-libs: /usr/share/doc/ia32-libs/NEWS.Debian.gz
ia32-libs: /usr/share/doc/ia32-libs/changelog.gz
ia32-libs: /usr/share/doc/ia32-libs/copyright

```
and now compare that to what it was in natty 11.04:
[http://packages.ubuntu.com/natty/amd64/ia32-libs/filelist](http://packages.ubuntu.com/natty/amd64/ia32-libs/filelist)

the glib-2.0-dev non-coinstallability is an issue but in future that will be handled too.
symlinking the arches might work for your case, but probably not in the general case. The headers are not the same across architectures else the problem would not exist.

---

