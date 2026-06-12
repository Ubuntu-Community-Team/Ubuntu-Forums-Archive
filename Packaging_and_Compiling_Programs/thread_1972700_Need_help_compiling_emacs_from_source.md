---
title: "Need help compiling emacs from source"
date: 2012-05-03
forum: Packaging and Compiling Programs
---

### Post by bonesTdog on 2012-05-03
I am trying to learn how to compile from source and having some trouble figuring it out. Hopefully one of you can help steer me in the right direction. Here is what I have done on my Ubuntu 32 bit 11.04 minimal installation

Downloaded emacs-23.4.tar.gz to ~/home/tod/Compile/ - then from that directory ran the following commands:
tar -zxvf emacs-23.4.tar.gz
./configure
make

Then trouble happened...
The last lines from make were:
make[1]: Entering directory /home/tod/Compile/emacs-23.4/lib-src
make[1]: *** No rule to make target '/usr/lib/crt1.0', needed by 'temacs'. Stop.
make[1]: leaving directory
make: *** [src] Error 2

I have tried a couple of ./configure flags which can be seen below to no avail.[http://www.linuxforums.org/forum/applications/188188-need-help-compiling-emacs-source.html]("http://www.linuxforums.org/forum/applications/188188-need-help-compiling-emacs-source.html")

Any gurus out there that can help with this? I want to try Linux From Scratch and this is the warmup - I don't want to fail the warmup!

---

### Post by 1clue on 2012-05-03
[http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=crt1.o&searchmode=searchfiles&case=insensitive&version=feisty&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=crt1.o&searchmode=searchfiles&case=insensitive&version=feisty&arch=i386)

You're missing libc6-dev.

If you're going to compile a project, you need the header files for the dependencies of that project.  Emacs needs libc6, and you DO have that on your system (can't run a linux box without it) but you don't have the headers for it, which are in the dev package.

I generally start by googling "ubuntu /path/to/file" and it usually leads to a search like the one above, or to some other forum post where they can't find it.

---

### Post by 1clue on 2012-05-03
I haven't really tried compiling on Ubuntu (not C or C++ or other system packages anyway) so I don't know how hard it is to set up the development environment.  I develop on the Java virtual machine, so everything I do is significantly different than what you're going to do.

If you're really interested in starting to build apps, AND if you have a nice quick multicore computer, then you might consider using Gentoo or another source-based distro.  Gentoo is a bit more problematic to get working, but it's DEFINITELY set up for development since every app on it was compiled on your box.

You'll also find the community as a whole is much more knowledgeable about this sort of thing, so you're more likely to have somebody help.

That said, I see a whole lot of names that match on both forums.  It seems quite a few forum members use both distros simultaneously.  As well, any distro has at least a small pool of very capable developers on it, but on a user-friendly distro like Ubuntu I'm guessing those guys are pretty busy working on code and don't get to the forums as much.

---

### Post by oldos2er on 2012-05-03
Moved to Packaging and Compiling Programs.

---

### Post by bonesTdog on 2012-05-04
Thanks. So I guess it would not be as simple as sudo apt-get install libc6-dev?  I will have to re-look at the Linux From Scratch book, but I don't remember it being very particular which distro you run to do the build. Nonetheless, it might be an interesting project to see if I can build a Gentoo system to get started. I tried once before and got stumped, but that was quite a while ago and I think I am further along now...

---

### Post by Bachstelze on 2012-05-05
> **1clue said:**
> 
If you're really interested in starting to build apps, AND if you have a nice quick multicore computer, then you might consider using Gentoo or another source-based distro.

No. Gentoo compilation is just running "sudo emerge something", it's no different from "sudo apt-get install something", it just takes more time. Gentoo definitely has its good sides, but it's not going to tech you how to compile things manually.

---

### Post by 1clue on 2012-05-05
> **Bachstelze said:**
> No. Gentoo compilation is just running "sudo emerge something", it's no different from "sudo apt-get install something", it just takes more time. Gentoo definitely has its good sides, but it's not going to tech you how to compile things manually.

So you always just used genkernel?  What's the point of using a source-based distro if you don't want to play with the compiler?

Gentoo is designed for people who aren't afraid of the compiler, where Ubuntu is designed for end users who don't even want to see a shell script.  There's nothing wrong with that at all, heck I use and like both.

My post was mostly pointing out that the build environment is necessary to install software on the system, therefore if you want to learn how to compile, there's no extra configuration or downloading you need to do.  I don't know that building anything works easily on Ubuntu or not, but I DO know that if you want to build something on Ubuntu or any other "non-source" distro you need to load the dev package for every dependency of the package you want to use.  That step is unnecessary on Gentoo.

FWIW while just installing the system in Gentoo won't teach you how to compile things manually, it teaches you a lot about how software fits together to make an operating system.  By the time you've configured your compiler options, configured and compiled a kernel, chosen a system logger, a shell, picked a dozen other things, then chosen a window manager and desktop options just to get a working system I think you've at least got an idea about dependencies and build options.  As opposed to Ubuntu, where you pretty much just click "next" on a graphical installer.  Ubuntu is easier to install than Windows by a long shot.

---

### Post by lkraemer on 2012-05-05
BonesTdog,
Here you go.....some postings that will give you everything you need.
Google & Search are your friends.................... 


**Dependencies:**
Versions of packages emacs23 depends on:
 emacs23-bin-common      23.3+1-1         The GNU Emacs editor's shared, arc
 libasound2              1.0.23-4         shared library for ALSA applicatio
 libatk1.0-0             2.0.0-1          The ATK accessibility toolkit
 libc6                   2.13-5           Embedded GNU C Library: Shared lib
 libcairo2               1.10.2-6         The Cairo 2D vector graphics libra
 libdbus-1-3             1.4.10-2         simple interprocess messaging syst
 libfontconfig1          2.8.0-2.2        generic font configuration library
 libfreetype6            2.4.2-2.1        FreeType 2 font engine, shared lib
 libgconf2-4             2.32.3-2         GNOME configuration database syste
 libgdk-pixbuf2.0-0      2.23.3-3         GDK Pixbuf library
 libgif4                 4.1.6-9          library for GIF images (library)
 libglib2.0-0            2.28.6-1         The GLib library of C routines
 libgpm2                 1.20.4-3.4       General Purpose Mouse - shared lib
 libgtk2.0-0             2.24.4-3         The GTK+ graphical user interface 
 libice6                 2:1.0.7-1        X11 Inter-Client Exchange library
 libjpeg62               6b1-1            The Independent JPEG Group's JPEG 
 libm17n-0               1.6.2-3          a multilingual text processing lib
 libncurses5             5.9-1            shared libraries for terminal hand
 libotf0                 0.9.12-1         A Library for handling OpenType Fo
 libpango1.0-0           1.28.3-6         Layout and rendering of internatio
 libpng12-0              1.2.44-2         PNG library - runtime
 librsvg2-2              2.34.0-1         SAX-based renderer library for SVG
 libsm6                  2:1.2.0-1        X11 Session Management library
 libtiff4                3.9.5-1          Tag Image File Format (TIFF) libra
 libx11-6                2:1.4.3-1        X11 client-side library
 libxft2                 2.2.0-2          FreeType-based font drawing librar
 libxpm4                 1:3.5.9-1        X11 pixmap library
 libxrender1             1:0.9.6-1        X Rendering Extension client libra
 zlib1g                  1:1.2.3.4.dfsg-3 compression library - runtime


**Prerequisites:**
Typically you need to install build-essential, and the headers for the
kernel you are running, if you are going to compile code.
```

uname -r

```
will tell you the kernel you are currently running.
```

sudo apt-get install build-essential linux-headers-$(uname -r)

```
will install the software needed to compile your code.


**TYPICAL COMPILE STEPS: (from within your source directory)**
```

cd /path/to/source
tar xvf packagename.tar.gz
cd /folder/of/extracted/source
./configure
make clean
make
sudo make install

```
"make clean" won't remove anything on the first compile, but will clean up
on a successive compile.

You can also use checkinstall to build a deb file.

REF:
[http://ubuntuguide.org/wiki/Ubuntu:Lucid](http://ubuntuguide.org/wiki/Ubuntu:Lucid)


**Extra Info:**
[http://ubuntuforums.org/showthread.php?t=1908852&highlight=build-essential](http://ubuntuforums.org/showthread.php?t=1908852&highlight=build-essential)


**If you get error messages about missing dependencies................**
[http://ubuntuforums.org/showthread.php?t=1949937&highlight=build-essential](http://ubuntuforums.org/showthread.php?t=1949937&highlight=build-essential)


**Setting your PATHS correctly so the Compiler or Linker finds the correct LIBS (Libraries).**
[http://ubuntuforums.org/showthread.php?t=1901733&highlight=build-essential](http://ubuntuforums.org/showthread.php?t=1901733&highlight=build-essential)
Start at Posting #8 


**IDE's:**
Eclipse with CDT
Monodevelop
Geany
Emacs
Codeblocks

[http://penguininside.blogspot.com/2009/08/top-10-multi-language-ides-for-linux.html](http://penguininside.blogspot.com/2009/08/top-10-multi-language-ides-for-linux.html)


One other point should be mentioned.......If you can't compile a small test program, and make it run (execute) you will never be able to compile a source distro.......


lk

---

### Post by pbrane on 2012-05-05
One more thing you can do that is sometimes helpful
```

sudo apt-get build-dep emacs

```
That should install the basic dependencies for emacs. Of course if a newer version of emacs requires something the current version does not then this probably won't help.

---

### Post by 1clue on 2012-05-06
> **pbrane said:**
> One more thing you can do that is sometimes helpful
```

sudo apt-get build-dep emacs

```
That should install the basic dependencies for emacs. Of course if a newer version of emacs requires something the current version does not then this probably won't help.

That's really cool!

---

### Post by Bachstelze on 2012-05-06
> **pbrane said:**
> One more thing you can do that is sometimes helpful
```

sudo apt-get build-dep emacs

```
That should install the basic dependencies for emacs. Of course if a newer version of emacs requires something the current version does not then this probably won't help.

Also, this pulls the dependencies that are required to compile the Ubuntu package. If there is some option that you want but was disabled in the Ubuntu package, and requires an additional dependency, you will need to install it separately. Likewise if you want to disable some option that the Ubuntu package was compiled with: if the dependenvy is present, it may be auto-enabled, so you will have to disable it manually at the configuration step.

---

