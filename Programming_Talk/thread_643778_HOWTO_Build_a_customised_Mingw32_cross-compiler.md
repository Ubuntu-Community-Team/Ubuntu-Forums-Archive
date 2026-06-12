---
title: "HOWTO: Build a customised Mingw32 cross-compiler"
date: 2007-12-18
forum: Programming Talk
---

### Post by samjh on 2007-12-18
Some days ago, I posted a question on getting a Mingw32 cross-compiler for Ada.  Unfortunately that thread was never answered.  So I did some research to find out how to build a Linux-to-Windows cross-compiler and found that the MinGW project has helpfully released an interactive build script to create the MinGW toolchain on Linux from source.

Now, the Mingw32 package in the Ubuntu and Debian repositories only support the C and C++ compilers in the Mingw32 cross-compiler toolchain.  Therefore, cross-compilation for the Win32 platform doesn't exist for other languages in the Mingw32 toolchain, such as Ada, Fortran, Java, Objectve-C, and Pascal.

If you want to build a Mingw32 cross-compiler for any of the above languages not supported by Ubuntu or Debian's Mingw32 package, then do the following:
[list=1]
[*]Download the Cross-Hosted MinGW Build Tool, from MinGW's Sourceforge file repository.  Direct link: [here](http://sourceforge.net/project/showfiles.php?group_id=2435&package_id=12644&release_id=17892).  Do NOT choose the "devel" version, choose the larger, full-release instead.

[*]Extract the downloaded tar.bz2 file in a directory of your choice.

[*]Install the build tool's dependencies: bison, flex, m4, and texinfo.  You obviously also need gcc and make.  In Ubuntu, the following command will install them all:
```
sudo aptitude install bison build-essential flex m4 texinfo
```

[*]Navigate to the directory created when you extracted the tar.bz2 of the build tool.  Give the x86-mingw32-build.sh script permission to be executable.  Invoke the script and also specify the target-spec.  Default target-spec is i386-mingw32 (the mingw32 package in Ubuntu defaults to i586-mingw32msvc).  Example:
```
./x86-mingw32-build.sh i486-pc-mingw32
```

[*]Follow the interactive prompts to specify various options.  You can choose which optional compilers to build and install, the directory for the build process, the install directory, etc., among many others.  Otherwise, edit the x86-mingw32-build.sh.conf file to specify the options explicitly.

If you want the script to install to, or work in, any directory requiring root access, then (re-)run the script using sudo.[/list]

After the build and installation is complete, I highly recommend that you either create symlinks in /usr/bin to point to the mingw32 tools, or else add the mingw32/bin directory to your $PATH.

Take note that the target-spec specified when you ran the build script must prefix the command for any tool you execute.  In other words, if your target spec was i386-mingw32, then to invoke Mingw32's g++ compiler, you must use i386-mingw32-g++ as your command, not just g++.

Happy cross-compiling! :)

---

### Post by aks44 on 2007-12-18
It looks too good & easy to be true... :D

Just a question: can you also choose which GCC version you're going to compile, or is it restricted to the current stable release (currently 3.4.5 :()?

---

### Post by samjh on 2007-12-18
It's slightly more complicated than the simplified steps I've described.  The script is only a tech preview, so there are bound to be problems for some people.

(I still can't get gnat and Ada libs and tools to build, because not only is gnat a special case - requiring an existing gnat installation - but the xgcc compiler doesn't recognise gnat-4.1.2 already installed on my computer.)

I've built the core C and C++ tools (gcc and g++), which work perfectly.  Haven't tried g77, gcj, or gpc.

Yes, you can specify your version by downloading the required packages, placing them all in the one directory, telling the script the package directory, and disabling automatic downloading of packages by the script.

There are alternative scripts available on the MinGW wiki as well, but this one is the most user-friendly I've seen.

---

### Post by qwertymodo on 2008-11-28
It didn't work for me... does this not work for x64 Linux?  I'm running Intrepidx64 and I get the following errors

```
cc1: warnings being treated as errors
../../binutils/bucomm.c: In function ‘make_tempname’:
../../binutils/bucomm.c:426: error: ignoring return value of ‘mktemp’, declared with attribute warn_unused_result
../../binutils/bucomm.c:433: error: ignoring return value of ‘mktemp’, declared with attribute warn_unused_result
make[4]: *** [bucomm.o] Error 1
make[4]: Leaving directory `/home/qwertymodo/tmp/mingw-3.4.5/binutils-2.17.50-20060716-1-src/build/binutils'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/qwertymodo/tmp/mingw-3.4.5/binutils-2.17.50-20060716-1-src/build/binutils'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/qwertymodo/tmp/mingw-3.4.5/binutils-2.17.50-20060716-1-src/build/binutils'
make[1]: *** [all-binutils] Error 2
make[1]: Leaving directory `/home/qwertymodo/tmp/mingw-3.4.5/binutils-2.17.50-20060716-1-src/build'
make: *** [all] Error 2
./x86-mingw32-build.sh: unrecoverable error building binutils

```

---

### Post by samjh on 2008-11-28
I was using 32-bit Ubuntu at the time when I wrote the OP, so I don't know if it works for 64-bits or not.

The process is not for the faint-hearted.  And it might have changed since I wrote the OP - it's been almost a year.

---

### Post by Anunnaki on 2009-01-22
> **qwertymodo said:**
> It didn't work for me... does this not work for x64 Linux?  I'm running Intrepidx64 and I get the following errors

```
cc1: warnings being treated as errors
../../binutils/bucomm.c: In function ‘make_tempname’:
../../binutils/bucomm.c:426: error: ignoring return value of ‘mktemp’, declared with attribute warn_unused_result
../../binutils/bucomm.c:433: error: ignoring return value of ‘mktemp’, declared with attribute warn_unused_result
make[4]: *** [bucomm.o] Error 1
make[4]: Leaving directory `/home/qwertymodo/tmp/mingw-3.4.5/binutils-2.17.50-20060716-1-src/build/binutils'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/qwertymodo/tmp/mingw-3.4.5/binutils-2.17.50-20060716-1-src/build/binutils'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/qwertymodo/tmp/mingw-3.4.5/binutils-2.17.50-20060716-1-src/build/binutils'
make[1]: *** [all-binutils] Error 2
make[1]: Leaving directory `/home/qwertymodo/tmp/mingw-3.4.5/binutils-2.17.50-20060716-1-src/build'
make: *** [all] Error 2
./x86-mingw32-build.sh: unrecoverable error building binutils

```

I'm getting this same error, and can't find any solutions online. Does anyone know what this error means?

---

### Post by jmarsden on 2009-02-28
> **Anunnaki said:**
> I'm getting this same error, and can't find any solutions online. Does anyone know what this error means?

It means that the standard library headers on your machine define the mktemp function as generating a warning if it is ever used in such a way that the returned result is thrown away.  "Warn Unused Result".  This is a relatively new thing in the gcc world, and was not there in Ubuntu 8.04 Hardy, but is present in Ubuntu 8.10 Intrepid.

The problem is made worse because this part of the cross compiler build process uses -Werror, turning all warnings into errors... so the build stops when it encounters this warning message from your (Linux native) gcc.

If you look in the file /usr/include/stdlib.h you will see the macro __wur on the line that declares the mktemp function (line 583 on my Ubuntu 8.10 x64 system).

UGLY WORKAROUND: You can edit that line of /usr/include/stdlib.h to remove the __wur from that line.  Just remember to put it back when you are done building your cross compiler :)

You can also just do your cross-compiling in a Hardy 8.04 VM.

Conclusion: This issue the result of using some very old (2006) source code with a very new gcc and libc6-dev.

Hoping this helps,

Jonathan

---

### Post by jmarsden on 2009-02-28
A bit more digging into this issue leads to:

(a) Some of these issues with old code are already fixed in the mingw cvs version of this script, which uses a newer ( 2008 ) version of the binutils sources.

(b) Not quite all of this kind of thing is fixed in that version of binutils, unfortunately.

Here's my script mingw-builder.sh that deals with this by downloading the mingw build script from cvs, patching it, and downloading current binutils sources (2.19.1) from the FSF, and using those.  

Works for me on Ubuntu Intrepid 8.10 64bit.  You may want to edit the SFMIRROR= line to use an SF mirror that is close to you, but other than that it should "just work".

Jonathan

---

### Post by SneakyWho_am_i on 2009-04-03
> **jmarsden said:**
> Here's my script mingw-builder.sh

Oh man, wow! All I had to do was run it! That is so much better than the stupid downloading and running and cursing that I was doing before! Can I move in with you?

After editing ~/.bashrc:
```
export PATH=~/mingw32/bin:"${PATH}"
```

And starting a new terminal window:
```
sneaky@gsc2:~/tmp$ vi hello.cpp # Sorry RMS
sneaky@gsc2:~/tmp$ g++ hello.cpp
sneaky@gsc2:~/tmp$ ls
a.out  hello.cpp
sneaky@gsc2:~/tmp$ a.out
bash: a.out: command not found
sneaky@gsc2:~/tmp$ ./a.out
Hello, world!
sneaky@gsc2:~/tmp$ i386-mingw32-c++ hello.cpp
sneaky@gsc2:~/tmp$ ls
a.exe  a.out  hello.cpp
sneaky@gsc2:~/tmp$ wine a.exe
Hello, world!
```

It works, it works! Now I'm going to try compiling Qt under it. Maybe the Code Gods will smile down upon me and do all my work for me again there :D ... yeah dreams are for free, right?

Thanks, JMarsden.

Tested on (wow, I have to look this up, I don't even know which version I'm running) Hardy? :
> Thank you for your interest in Ubuntu 8.04
                - the Hardy Heron - released in April 2008.
From the about window.
At any rate, the earlier script wouldn't work out for me, and doing it by hand was just too much work, but this rocked my socks.

---

### Post by Ferralll on 2009-07-14
I think I am love with you! 
Thankyou sooo much.  Now I do not have to learn C++ so that I can cross compile things.  I can stick to my ol' fashion f77.

It worked perfectly.  Thanks again!

---

### Post by Fatman_UK on 2009-10-20
> **jmarsden said:**
> Here's my script mingw-builder.sh

Thanks dude. You made my first cross-compile so easy.

I nominate jmarsden for cross-compiling president of ubuntuforums. Second?

---

