---
title: "makefiles"
date: 2013-05-25
forum: Programming Talk
---

### Post by thedardanius on 2013-05-25
I have issues with linking to 3rd part libs. I use libbass (with a .so) and xpm lib (which should be standardly available on xlib sys?)
How do makefiles work? Are they used for this? How do I use them with gcc and codeblocks, can they help me with linking to .so files and stuff like that?

---

### Post by MG&amp;TL on 2013-05-25
> **thedardanius said:**
> I have issues with linking to 3rd part libs. I use libbass (with a .so) and xpm lib (which should be standardly available on xlib sys?)
How do makefiles work? Are they used for this? How do I use them with gcc and codeblocks, can they help me with linking to .so files and stuff like that?

*Make* and the associated files it uses, conventionally called *makefiles*, are just a way of automatically building things via set rules that you use. I'd recommend the GNU make manual ([http://www.gnu.org/software/make/manual/make.html](http://www.gnu.org/software/make/manual/make.html)) if you're interested. Yes, they can help with linking, but *GCC* can do this on its own. *Make* simply executes *GCC* in a predefined pattern.

As for your 'issues': what specifically is the problem? How do you want to build your project? What are you doing currently?

---

### Post by thedardanius on 2013-05-25
I have an opengl engine project, written in C/C++, xlib etc. I try to challenge me to use the least possible 3rd party libs, and implement things myself. I use codeblocks and gcc or g++. The linker can link to libxpm (but I dont know if its standard). my command line gcc execution has -l libxpm (works), but then I downloaded bass dev set, (BASS API), and I must provide the bass.so on my own. I put it in the directory of the executable, but it doesn't find it? Only if I specify the absolue path, which will make it only work on my computer. if i put -l libbass, it cant find it (its not in the usr lib folders, and it shouldn't be). Mind you, Im using a standalone structre, so I cant install the libs and stuff, which normal apps do. I namely have no idea how to code an installer on windows, let alone on linux.

---

### Post by MG&amp;TL on 2013-05-25
> **thedardanius said:**
> I have an opengl engine project, written in C/C++, xlib etc. I try to challenge me to use the least possible 3rd party libs, and implement things myself. I use codeblocks and gcc or g++. The linker can link to libxpm (but I dont know if its standard). my command line gcc execution has -l libxpm (works), but then I downloaded bass dev set, (BASS API), and I must provide the bass.so on my own. I put it in the directory of the executable, but it doesn't find it? Only if I specify the absolue path, which will make it only work on my computer. if i put -l libbass, it cant find it (its not in the usr lib folders, and it shouldn't be). Mind you, Im using a standalone structre, so I cant install the libs and stuff, which normal apps do. I namely have no idea how to code an installer on windows, let alone on linux.

Standalone structures don't really work well on linux. That said, you could have a look at static libraries (more info: [http://www.yolinux.com/TUTORIALS/LibraryArchives-StaticAndDynamic.html](http://www.yolinux.com/TUTORIALS/LibraryArchives-StaticAndDynamic.html) ) -see if the libraries you want to use provide a .a version of their library.

As a side note: why do you want a standalone structure? If you're already dependent upon *libstdc++, libc, libX11, libGL,* and their dependencies  (yes, you are), why make it hard for yourself by providing your own libraries for certain parts?

---

### Post by thedardanius on 2013-05-25
ok, so cna you tell me how to create a proper installer for installing, instead of a standalone?
Because that might be a solution as well.
And why is it hard? Cant an application find so files "near" himself, like in windows, a app will automatically link to dll near him if 3rd party.

---

### Post by steeldriver on 2013-05-25
Well if you've ever had to deal with Windows 'dll hell' you'd probably be thankful that *nix doesn't do things that way ;)

Really the idea behind shared object (.so) libraries is exactly that - they should be common libraries that live in standard locations and can be loaded by any application that needs them. Anything needed by just your code is better statically linked (as .o object code or as a .a archive library). The exception would be if you need to run a non-standard version of a standard library, or for testing purposes before you commit your library into a standard location - in which case you can use the LD_PRELOAD or LD_LIBRARY_PATH environment variables to tell the dynamic linker where to find 'your' .so library at runtime - it's hard to give you specifics because you haven't posted exactly what the error is (in particular whether it's a link-time error or a runtime error).

---

### Post by MG&amp;TL on 2013-05-25
Steeldriver answered your other question excellently, but:

> **thedardanius said:**
> ok, so cna you tell me how to create a proper installer for installing, instead of a standalone?
Because that might be a solution as well.


It's not especially easy, but Debian-based derivatives (Ubuntu included) use debian packages as their 'installers'. There's several packaging-related guides here: [http://developer.ubuntu.com/packaging/html/](http://developer.ubuntu.com/packaging/html/)

---

