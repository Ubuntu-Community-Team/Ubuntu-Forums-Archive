---
title: "C++ debugger"
date: 2010-02-22
forum: Packaging and Compiling Programs
---

### Post by whatifwe on 2010-02-22
I am Microsoft/Windows based software engineer  with the need to develop C++ programs in 32-bit Ubuntu 9.04 and 64-bit Ubuntu 9.10.   I have found that the debugger is difficult to use.  Is there a more user-friendly debugger defined by a .deb file that can be installed on these two operating systems.

I would appreciate any recommendations

Thank You

Robert Adams

---

### Post by SevenMachines on 2010-02-23
I take it you mean the gdb debugger? I have to admit, I usually use IDE's which have gdb use integrated in. But if your looking to use gdb as a stand alone debugger while avoiding the command line you might want to try out the 'ddd' package, basically a gui front end for gdb and others

---

### Post by Simian Man on 2010-02-23
Sadly, there is no GUI debugger that's even close to the one in Visual Studio on Linux.

I use the one in Eclipse when I'm using it and ddd when I'm not.  Both suck in different ways :(.

---

### Post by whatifwe on 2010-02-23
> **SevenMachines said:**
> I take it you mean the gdb debugger? I have to admit, I usually use IDE's which have gdb use integrated in. But if your looking to use gdb as a stand alone debugger while avoiding the command line you might want to try out the 'ddd' package, basically a gui front end for gdb and others


Thank You -- What IDE's are you referring to? I am developing command line software.  Can they be installed easily with a .deb file?

Robert Adams

---

### Post by SevenMachines on 2010-02-23
theres quite a few, i'm sure everyone has their preferences. These are some that i know are in the main repositories.
Personally I use eclipse with CDT plugin for c++.
Netbeans also has c++ plugins, both of those definitely have win32 versions if you need that sort of cross platform thing.

Others i've heard about but rarely have used.
codelite, codeblocks, both look pretty good.
anjuta, kdevelop.

you might want to try some of them out, theres probably quite a few more too
also try the [programming forum]("http://ubuntuforums.org/forumdisplay.php?f=39"), they probably have a sticky on ide comparison as i know it crops up a lot

---

