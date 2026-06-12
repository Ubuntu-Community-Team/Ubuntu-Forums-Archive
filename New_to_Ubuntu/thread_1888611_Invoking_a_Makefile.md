---
title: "Invoking a Makefile?"
date: 2011-11-29
forum: New to Ubuntu
---

### Post by pakopako on 2011-11-29
Was trying to compile bSNES in Ubuntu 11.04 (WUBI if it makes any difference). On the bSNES [help file]("http://byuu.org/bsnes/compilation-guide") the commands were listed as:

```
sudo apt-get install build-essential gcc-4.5 g++-4.5 libgtk2.0-dev libqt4-dev libsdl1.2-dev
sudo apt-get install libpulse-dev libopenal-dev libao-dev libxv-dev
make
sudo make install
```So far I've:
[LIST]
[*]Downloaded the [source file]("http://code.google.com/p/bsnes/downloads/list?can=1")
[*]Unpacked it using File-Roller into **Downloads/bsnes_v084-source**
[*]Entered the terminal and changed directory to ~/Dowloads//bsnes_v084-source
[*]Installed all the possible packages
[*]Ran *make*
[/LIST]


At that point I looked up and saw the *bsnes_v084-source* directory was empty and panicked. :confused:
Not very proud of that one. So I tried snooping around and saw that the bsnes sub-directory under "bsnes_v084-source" had its own Makefile. I presumed that was the "main" file to look at.

> And now you can compile the bsnes source code **by invoking its Makefile**. You can also optionally choose to install the application.I liked the sound of that! Except running it from Nautilus does nothing. If I type "Makefile" in the terminal, it won't recognize it as an executable text. If I entered the bsnes sub-directory and tried to continue with ***make*** I get an error 127:
> 
g++-4.6 -std=gnu++0x -O3 -fomit-frame-pointer -I. -fno-tree-vectorize -DPROFILE_ACCURACY -c ui/main.cpp -o obj/ui-main.o
make: g++-4.6: Command not found
make: *** [obj/ui-main.o] Error 127Really feel like a PEBKAC is going on here as this is edition of the package was released earlier this month and no one else seems to have issues compiling it (or they're using the Windows release).

Bottomline -- how do I invoke a Makefile... or choose to install this program from Nautilus or terminal?

---

### Post by 3Miro on 2011-11-29
To evoke a Makefile, you need to either go to the directory and type "make" or type:
```
make -f filename
```
where filename is the name of the Makefile (by default make looks for a file called Makefile).

You installed gcc-4.5 on your system. The program is trying to compile using gcc-4.6. You should try to install gcc-4.6 and see if this works. Otherwise you may have to edit the makefile and change the version of gcc that is being used.

---

### Post by 3Miro on 2011-11-29
To change the compiler you can go to: bsnes/nall and open Makefile with Nautilus. You are looking for:
```
ifeq ($(compiler),)
  ifeq ($(platform),win)
    compiler := gcc
  else ifeq ($(platform),osx)
    compiler := gcc-mp-4.6
  else
    compiler := gcc-4.6
  endif
endif
```
You can change that to:
```
ifeq ($(compiler),)
  ifeq ($(platform),win)
    compiler := gcc
  else ifeq ($(platform),osx)
    compiler := gcc-mp-4.5
  else
    compiler := gcc-4.5
  endif
endif
```

You should first try to install 4.6 as programs sometimes require a specific version of gcc and wouldn't compile with another one.

---

### Post by pakopako on 2011-11-29
> **3Miro said:**
> You installed gcc-4.5 on your system. The program is trying to compile using gcc-4.6. You should try to install gcc-4.6 and see if this works. Otherwise you may have to edit the makefile and change the version of gcc that is being used.
Hm. This makes sense, but I thought I had gcc-4.6 installed already. I can't quite 
```
 sudo apt-get install build-essential gcc-4.6 g++-4.6
```I was skimming over the various Makefiles in the subdirectories of bsnes and few make referenecs to 4.6; Search came up with a hit, but it was in a hashed/comment line.
>   # tree vectorization causes code generation errors with Linux/GCC 4.6.1> **3Miro said:**
> You should first try to install 4.6 as programs  sometimes require a specific version of gcc and wouldn't compile with  another one.
Worth a shot, but you're right, I need to figure out how to get gc-4.6 installed because tricking bsnes/nall/Makefile into sing 4.5 spews a lot of *nullptr not declared* errors.

---

### Post by pakopako on 2011-11-30
I think I hit a stumbling block when installing GCC-4.6  I followed the instructions [here]("http://buildall.wordpress.com/2011/05/03/installing-gcc-4-6-in-the-ubuntu-11-04-natty-narwhal/") to install GCC 4.6 on Ubuntu 11.04... except I ran out of space part-way through MAKE.  So this time I've extracted the [package]("http://gcc.parentingamerica.com/snapshots/LATEST-4.6/") onto a USB flashdrive, putting *build* and *gcc-4.6-20111125* in the root of the 4GB drive. That leaves me with a full 1.0 GB on sda6. (Maximum size: 5GB. Despite resting on its own partition, it's a WUBI install; there's 2.5 more GB, but I believe they are taken up by the WUBI boot image.)  Except now I can't run the configure script included. Regardless of what I add, the end result is a **Permission denied**. From the build folder: ```
../gcc-4.6-20111125/configure --disable-checking --enable-languages=c,c++ --enable-multiarch --enable-shared --enable-threads=posix --program-suffix=-4.6 --with-gmp=/usr/local/lib --with-mpc=/usr/lib --with-mpfr=/usr/lib --without-included-gettext --with-system-zlib --with-tune=generic
``` End result is always **bash: ../gcc-4.6-20111125/configure: Permission denied**   Any reason it's doing that? My Ubuntu Software Center still lists my GCC as 4.5.2-1ubuntu3 so I guess I didn't screw up my 4.5 configuration. Is 4.6 just outside of my reach?

---

