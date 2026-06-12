---
title: "Compile Windows .exe files in Linux"
date: 2007-11-29
forum: Programming Talk
---

### Post by Warpnow on 2007-11-29
I used to run cygin and I had installed a package which gave me a command like gcc-win which took the code and outputted a .exe file...

Does anyone know of a linux equivalent?

---

### Post by LaRoza on 2007-11-29
Do you mean cygwin? [http://www.cygwin.com/](http://www.cygwin.com/)

If you want to compile C code on Linux:

```

sudo aptitude install build-essential
```

You use gcc to compile.

---

### Post by NathanB on 2007-11-29
In one word:  MinGW

Read the docs on how to install a cross-compiling environment.  It will allow you to generate Windows executables from a Linux box.

[http://www.mingw.org/](http://www.mingw.org/)
[http://www.mingw.org/MinGWiki/](http://www.mingw.org/MinGWiki/)

---

### Post by jespdj on 2007-11-29
Note that it's not really clear what exactly you want, LaRoza and NathanB are interpreting your question differently:

LaRoza thinks you want to compile C programs for Linux. For that, you install the package build-essential and you use gcc to compile your source code to an executable program that runs on Linux.

NathanB thinks you want to compile C programs on Linux, but that you want to run on Windows. Compiling on platform X for platform Y is called cross-compiling. You can use MinGW if you want to do that.

---

### Post by Warpnow on 2007-11-29
I want to cross compile.

It was really easy in cygwin. I had the package installed and I replaced gcc in the makefile with gcc-windows and it spat out a .exe

---

### Post by MicahCarrick on 2007-11-29
You can use cygwin or MinGW to build Linux applications in Windows. Both will output a Windows .exe, however, MinGW does not have the cygwin DLL dependency. Both have a multitude of Linux applications already compiled and available as binaries (such as gcc).

To over-simplify: they emulate a linux environment so that building the applications from Linux build scripts works with little to no modifications but they output Windows binary files (DLL and EXE).

[http://www.cygwin.com/](http://www.cygwin.com/)
[http://www.mingw.org/](http://www.mingw.org/)

---

### Post by MicahCarrick on 2007-11-29
Wait, by "Linux equivalent" do you mean the other way around? Compiling Windows code on Linux?

If so...

The short answer is no. If you find a Visual Studio project you wont' be able to easily compile it on Linux. Furthermore, most Windows software will not have source code available and thus you won't be able to run it as a native Linux binary. However, you can emulate a windows environment and thus run Windows applications in Linux using the open-source wine or the commercial cross over

[http://www.winehq.org/](http://www.winehq.org/)
[http://www.codeweavers.com/](http://www.codeweavers.com/)

---

### Post by Warpnow on 2007-11-29
No, what I mean is compiling linux applications so they work in windows.

The code I am working on is all very simple. A command line program that accepts telnet connections. Actually a text based game if you play them.

I want to compile a .exe that can be ran in windows so players can run their own mini servers for fun on their windows pc. I've done it once in cygwin but now want to update it and no longer use cygwin.

---

### Post by MicahCarrick on 2007-11-29
Then MinGW/MSYS is the way to go.

---

### Post by Vadi on 2007-11-29
Apparently you need to compile your own x-compiler. I tried using a script gave there, but I reveiced an error:

```
gcc -W -Wall -Wstrict-prototypes -Wmissing-prototypes -O2 -fno-exceptions -s -o ar arparse.o arlex.o ar.o not-ranlib.o arsup.o rename.o binemul.o emul_vanilla.o bucomm.o version.o filemode.o  ../bfd/.libs/libbfd.a ../libiberty/libiberty.a
arlex.o: In function `main':
arlex.c:(.text+0x0): multiple definition of `main'
arparse.o:arparse.c:(.text+0x0): first defined here
ar.o: In function `main':
ar.c:(.text+0xd80): multiple definition of `main'
arparse.o:arparse.c:(.text+0x0): first defined here
bucomm.o: In function `make_tempname':
bucomm.c:(.text+0x94): warning: the use of `mktemp' is dangerous, better use `mkstemp' or `mkdtemp'
ar.o: In function `mri_emul':
ar.c:(.text+0x9f2): undefined reference to `yyparse'
collect2: ld returned 1 exit status
```

Tried with the latest version of gcc on that site, same thing...

---

### Post by llonesmiz on 2007-11-30
You can install mingw this way:

```
sudo apt-get install mingw32
```

and then you can simply compile using i586-mingw32msvc-gcc instead of gcc:

```
i586-mingw32msvc-gcc -o test.exe test.c
```

You can also use i586-mingw32msvc-g++ and related tools.

If you use any libraries in your program, you will either need to crosscompile them too or just download the precompiled binaries for windows.

---

### Post by Vadi on 2007-11-30
Hmm.

Okay, I was using mingw on windows too (I used virtualbox). Yeah, I do use other libraries, and they're giving me somewhat of a headache right now. The libraries used are different depending on linux / windows (obviously), and they're included properly with the #if statements. The cheap trick of replacing gcc with that compiler sort of worked, but it went to include the linux libraries, and couldn't find them :/

So I guess I've got some reading to do on how to get this all working.

---

### Post by Vadi on 2007-11-30
Well this is simply giving me a headache. And Google is refusing to cooperate.

I have two makefiles, one for linux, one for windows. The windows one has an FOR_WINDOWS flag defined. So on nearly the first file, I have the following:

```
#if defined( FOR_WINDOWS )
(a bunch of #define stuff here)
#else
# include <arpa/telnet.h>
#endif
```

While, yeah, in this case I can just use the #defines manually for linux too, there are other cases where I can't. And the compiler just starts off with:

> In file included from main.c:82:
header.h:69:26: arpa/telnet.h: No such file or directory

So is it just not finding the library? Or the library isn't compatible with the compiler, and I'd need to find a windows equivalent (well, in this specific case, there is no need for a windows equivalent,, but still).

:?

---

### Post by marylou on 2008-06-24
> **Warpnow said:**
> I used to run cygin and I had installed a package which gave me a command like gcc-win which took the code and outputted a .exe file...

Does anyone know of a linux equivalent?

so uh ... do you recall exactly which cygwin package did this?

i have this program that we have built in linux but i need to convert it to a windows executable. i have NOOOO idea where to start with this. cygwin is not exactly cooperating with me. any ideas/suggestions?

---

