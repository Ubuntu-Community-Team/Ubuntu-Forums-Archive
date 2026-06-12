---
title: "A simple question"
date: 2005-11-04
forum: Packaging and Compiling Programs
---

### Post by phanboy_iv on 2005-11-04
I am a *budding* programmer(read: ignorant noob), and I have a question.

I have not been able to compile ANYTHING with ubuntu. 

The errors I get always seem to be different, and I don't think this is a library linking problem. I heard about gcc 4.0 not being able to compile some old things.

So, my simple question is, will installing older versions of gcc(eg,3.4 & etc)
solve some of these problems? I know it won't solve all problems, but could it possibly have an effect?

Forgive my ignorance.

---

### Post by rmjokers on 2005-11-04
First of all, make sure you have the package build-essential installed.  Second, what kind of errors are you getting?  A few specific examples might be helpful.  I doubt that using an older compiler would be helpful.

---

### Post by phanboy_iv on 2005-11-08
[QUOTE=rmjokers]First of all, make sure you have the package build-essential installed.  Second, what kind of errors are you getting?  A few specific examples might be helpful.  I doubt that using an older compiler would be helpful.[/QUOTE]

I did that, thanks. While I was at it I took a look at the Readme of the current program I am trying to compile
(it's Gens for Linux, a Sega Genesis&etc emulator) and found a list of packages that it required to compile correctly
(one of those was gcc 2.95, and installing it and using it to compile actually did help). 

That helped, but this program requires the "nasm" x86 assembly compiler package to build correctly. I installed it as previously mentioned, but I got these errors when nasm was called during compilation:
> nasm -D__GCC2 -f elf -O3 vdp_rend.asm -ovdp_rend.o
vdp_rend.asm:2089: error: short jump is out of range
vdp_rend.asm:2112: error: short jump is out of range
vdp_rend.asm:2116: error: short jump is out of range
vdp_rend.asm:2119: error: short jump is out of range
vdp_rend.asm:2126: error: short jump is out of range
vdp_rend.asm:2130: error: short jump is out of range
vdp_rend.asm:2133: error: short jump is out of range
vdp_rend.asm:2155: error: short jump is out of range
vdp_rend.asm:2159: error: short jump is out of range
vdp_rend.asm:2162: error: short jump is out of range
vdp_rend.asm:2169: error: short jump is out of range
vdp_rend.asm:2173: error: short jump is out of range
vdp_rend.asm:2176: error: short jump is out of range
vdp_rend.asm:2195: error: short jump is out of range


......&etc, with this line at the end:
> vdp_rend.asm:2260: error: phase error detected at end of assembly.
make: *** [vdp_rend.o] Error 1

This means nothing to me.
Gens for Linux is a bit buggy still, so this may be a coding error.
If so, forgive me for taking all this forum space up.

---

### Post by zman0900 on 2007-12-07
I too am having the same exact problem compiling gens.  I am using gcc 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2) and nasm 0.98.38.  I was getting other errors such as "'GTK_FILE_SELECTION' was not declared in this scope" and "'gtk_file_selection_get_filename' was not declared in this scope", but I got past that by removing the GTK_DISABLE_DEPRECATED flag from the makefile.  Any help with this would be appreciated since I have been unable to find any other good sega emulator with a gui.

P.S. I'm using ubuntu 7.10

---

