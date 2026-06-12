---
title: "Updating mingw gcc compiler"
date: 2014-05-04
forum: Packaging and Compiling Programs
---

### Post by SamBam77 on 2014-05-04
**Long story short:**
I need to help updating the gcc compiler that mingw uses to compile for windows within my linux build environment.  When I installed the mingw version available by default in the Ubuntu repositories (3.0), I get an old version of the gcc compiler (4.6.3).  However, I need at least version 4.7 for what I am trying to compile.  I have installed a more recent version of mingw (3.5.8) that contains gcc version 2.8.2, but I have been unable to use it since the previous version of mingw is still taking precedent over it. 


**More context to my question:**
I have been struggling for a while now trying to cross-compile some code, which already works in linux, for Windows.  When done correctly, my code should compile to a Windows DLL file to be used in conjunction with a larger software package,which already works in Windows.


I have already set up mingw to cross-compile c code written in linux into windows EXEs.  That works fine as long as the programs are simple.  But for what I really want to do, I need to include more complicated elements and build the project with ./configure, make, make install.  To do this, I know that I need to use a command something like this:
```
./configure --host=x86_64-w64-mingw32--build=x86_64-w64-mingw32 –with-dest=$PWD/_install
```
To configure it for the cross-compilation.  However, when I “make,” I get an error saying,
```
x86_64-w64-mingw32-gcc: error:unrecognized option '-pthread'
```
which I have learned means that I am using a gcc compiler that is too out of date.

Of course I have more up-to-date gcc compilers on my system, but they are for linux target systems.  The one that came with mingw, by default, is too old.  So to do this, I [installed a more recent version]("http://ffmpeg.zeranoe.com/blog/?p=269#more-269") of mingw from source, which compiled a newer version of gcc.  Great.  Except that I cannot figure out how to use it.

When I try ./configure, it is still targeting the old installation of mingw, and its out-of-date gcc.


How can I specify the new mingw (and/or new gcc) for configuring, make, install?
And/or, make my new version of mingw the default?

---

### Post by qyot27 on 2014-05-04
> **SamBam77 said:**
> **Long story short:**
I need to help updating the gcc compiler that mingw uses to compile for windows within my linux build environment.  When I installed the mingw version available by default in the Ubuntu repositories (3.0), I get an old version of the gcc compiler (4.6.3).  However, I need at least version 4.7 for what I am trying to compile.  I have installed a more recent version of mingw (3.5.8) that contains gcc version 2.8.2, but I have been unable to use it since the previous version of mingw is still taking precedent over it.
If you were using 14.04 instead of 13.10, this would be a moot point: the MinGW-w64 GCC in Trusty's repos is 4.8.2.

3.5.8 is not the MinGW-w64 version, it's the version number of Zeranoe's build script.  The MinGW-w64 version it pulls in is either 3.1.0 or an SVN checkout.


> Of course I have more up-to-date gcc compilers on my system, but they are for linux target systems.  The one that came with mingw, by default, is too old.  So to do this, I [installed a more recent version]("http://ffmpeg.zeranoe.com/blog/?p=269#more-269") of mingw from source, which compiled a newer version of gcc.  Great.  Except that I cannot figure out how to use it.

When I try ./configure, it is still targeting the old installation of mingw, and its out-of-date gcc.


How can I specify the new mingw (and/or new gcc) for configuring, make, install?
And/or, make my new version of mingw the default?
The instructions that Zeranoe's build script gives tells the user to add the install directory for the toolchain to your PATH variable.  Let's say it installed to $HOME/mingw-build/mingw-w64-x86_64.  It's going to be something like:
```
export PATH=$HOME/mingw-build/mingw-w64-x86_64/bin:$PATH
```
which inserts the bin path for the GCC install into the PATH before the rest of the entries.  Unless you add that to your user profile, you'll have to do that PATH insertion every time you need to build something.  Just to make extra-sure, you probably should purge the existing MinGW packages so that it *can't* get confused by two of them existing in the PATH (this being why the new chain is specified before the $PATH in the insertion, but I generally don't like multiple versions of a program existing on the PATH as a matter of principle).

The build script doesn't install the toolchain to the system, which is why this all is required.  To wit, the way it creates the directory hierarchy in the install location ceased to be compatible with system installs a few versions ago (prior to that, it still didn't install to the system, but the user could take the output and install it there themselves).  It's why I switched the cross-compilation guide I maintain for FFmpeg and mpv and their dependencies from using the build script to also guiding the user through installing the toolchain just like everything else in the guide (based, admittedly, on what Zeranoe's build script *used* to do, just with more updated components).  I haven't fleshed out instructions for Win64-targeted toolchains, though - it might be as simple as changing the --host= commands, it might not.



Also, if you're using --build= and setting it to the MinGW-w64 target, you need to make sure you have Wine installed.  --host= is normally all that's needed (I have encountered some that more or less *make* you use --build= too, but usually the only reason to specify both --build and --host is to try and fool configure into thinking it's being executed on Windows itself, which is why you need Wine).

---

### Post by SamBam77 on 2014-05-04
> **qyot27 said:**
> 
```
export PATH=$HOME/mingw-build/mingw-w64-x86_64/bin:$PATH
```
which inserts the bin path for the GCC install into the PATH before the rest of the entries. 
Haha, of course the problem is so simple.
I did add those directories to my PATH, but I added them to the end of the existing path and not in front of it. 

I purged the old version of mingw and ensure that the path was in the correct order.  Now it is using the correct version of mingw and gcc.
I still get errors, but I think they are caused by something else.  Thanks.

---

