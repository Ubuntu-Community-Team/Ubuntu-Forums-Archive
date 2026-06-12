---
title: "x86 Disassembler ?"
date: 2008-11-28
forum: Programming Talk
---

### Post by WitchCraft on 2008-11-28
Hi, anybody knows where I can find a good disassembler for use in my C/C++ program?

I need to disassemble ELF32 & ELF64 files, as well as PE (windows).
I need to have a disassembly of the kind that IDA gives you.

Also, it would be good if I could choose the disassembly length, like the first 20 instructions of a function.

Also, it would be good if I could disassemble Mac UniversialBinary, too.

Also, it would be nice if anybody knew a good PPC disassembler.

Please don't point me to the ******* disassembler, because it has no documentation on how to use it, which is really pointless...

---

### Post by psusi on 2008-11-28
man objdump

---

### Post by WitchCraft on 2008-11-28
> **psusi said:**
> man objdump

I need to disassemble it within a C program, not calling objdump to disassemble.

---

### Post by WitchCraft on 2008-11-28
I think I have PE, just need to correct a few errors in PE dump.

I got a compile error. It compiles fine on IA-32, but i get an error on IA-64:

It used to work on wubi x64, but now on Intrepid, it doesn't anymore, and complained something about a missing stubs-32.h. I took it from 32 bit linux, and copied it to /usr/include/gnu/ to get rid of it.

Now i have a new error:

> 
gcc decoder.o ieee.o main.o pedump.o print.o debug.o -Wall -m32 -O2 -march=i686 -funroll-loops -finline-functions -fno-strict-aliasing -pipe -o disasm
/usr/bin/ld: [COLOR="Red"]skipping incompatible[/COLOR] /usr/lib/gcc/x86_64-linux-gnu/4.3.2/libgcc.a when searching for -lgcc
/usr/bin/ld: [COLOR="Red"]skipping incompatible[/COLOR] /usr/lib/gcc/x86_64-linux-gnu/4.3.2/libgcc.a when searching for -lgcc
/usr/bin/ld: cannot find -lgcc
collect2: ld returned 1 exit status


files attached.

---

### Post by WitchCraft on 2008-11-28
Yehaa, i found the bug:

gcc from the repository is compiled with multilib disabled. 

```

apt-get install gcc-4.3-multilib gcc-multilib lib32gomp1 libc6-dev-i386

```

---

### Post by WitchCraft on 2008-11-29
Really nobody knows a good ELF disassembler for use in a C program?

It should create a disassembler dump, which I can then further analyze in the rest of the program. Need to see string references for offset searching.

---

### Post by NathanB on 2008-11-29
ndisasm (ships with Nasm) gives you coverage of most (if not all) of those platforms you mentioned:

[http://www.nasm.us/](http://www.nasm.us/)

---

### Post by WitchCraft on 2009-01-22
> **NathanB said:**
> ndisasm (ships with Nasm) gives you coverage of most (if not all) of those platforms you mentioned:

[http://www.nasm.us/](http://www.nasm.us/)

NDISASM is not what i want.

---

### Post by PCHome on 2009-01-22
I don't know how good it is since I can't figure out how to install in on 8.10 but Biew keeps coming up in my searches.

---

### Post by WitchCraft on 2009-02-07
BVIEW = CRAP

In the mean time I have started writing my own disassembler...
Already fully decodes 386+ & 3Dnow instruction set flawlessly, but I'm still fighting with SSE and x64

But int he meantime, I was pointed to [http://www.agner.org/optimize/#objconv](http://www.agner.org/optimize/#objconv)
And, OMG, a fantastic tool!!! 
It works! I've stolen the macho.c to get mac support for my disassembler.

And I like the opcode map. This is almost identical to what I was doing, unlike gdb's and diStorms table.

And I like the idea of converting the file format, never thougt of it before, but it's a very interesting idea.

In case anybody is interested:
[http://www.c-jump.com/CIS77/CPU/x86/index.html](http://www.c-jump.com/CIS77/CPU/x86/index.html) 		                   		  		  		 		 			 				__________________

---

### Post by asm_Coty on 2009-05-08
> **WitchCraft said:**
> Yehaa, i found the bug:

gcc from the repository is compiled with multilib disabled. 

```

apt-get install gcc-4.3-multilib gcc-multilib lib32gomp1 libc6-dev-i386

```
that worked well, but after installing, how do I launch it?

---

### Post by PCHome on 2009-05-08
Command gives an error:

sudo apt-get install gcc-4.3-multilib gcc-multilib lib32gomp1 libc6-dev-i386
[sudo] password for user:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package lib32gomp1

---

### Post by WitchCraft on 2009-06-28
> **PCHome said:**
> Command gives an error:

sudo apt-get install gcc-4.3-multilib gcc-multilib lib32gomp1 libc6-dev-i386
[sudo] password for user:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package lib32gomp1

```

root@ST-LAPTOP:~# apt-cache search lib32gomp*
lib32gomp1 - GCC OpenMP (GOMP) support library (32bit)
lib32gomp1-dbg - GCC OpenMP (GOMP) support library (32 bit debug symbols)


root@ST-LAPTOP:~# apt-cache search gomp*
bovo - gomoku board game for KDE 4
lib32gomp1 - GCC OpenMP (GOMP) support library (32bit)
lib32gomp1-dbg - GCC OpenMP (GOMP) support library (32 bit debug symbols)
libgomp1 - GCC OpenMP (GOMP) support library
libgomp1-dbg - GCC OpenMP (GOMP) support library (debug symbols)
libpangomm-1.4-1 - C++ Wrapper for pango (shared libraries)
libpangomm-1.4-dbg - C++ Wrapper for pango (debugging symbols)
libpangomm-1.4-dev - C++ Wrapper for pango (development files)
libpangomm-1.4-doc - C++ Wrapper for pango (documentation)
libtommath-dev - multiple-precision integer library [development files]
libtommath-docs - multiple-precision integer library [documentation]
libtommath0 - multiple-precision integer library [runtime]
bsdgames - a collection of classic textual unix games
gom - Command line and interactive ncurses-based OSS audio mixer
gomoku.app - Extended TicTacToe game for GNUstep
gridlock.app - A collection of grid-based board games for GNUstep
libcomplearn-gomp-dev - CompLearn library, OpenMP version development files
libcomplearn-gomp1 - machine-learning core library runtime files with OpenMP (libgomp)
libqsearch-gomp-dev - CompLearn library, OpenMP version development files
libqsearch-gomp1 - machine-learning core library runtime files with OpenMP (libgomp)
sysinfo - display computer and system information
root@ST-LAPTOP:~# 


```

---

### Post by leblancmeneses on 2009-06-28
for PE reader writer
microsoft released: 
[http://ccimetadata.codeplex.com/](http://ccimetadata.codeplex.com/)
there is also:
[http://evain.net/blog/articles/2009/04/27/pdb2mdb-and-mono-cecil-pdb](http://evain.net/blog/articles/2009/04/27/pdb2mdb-and-mono-cecil-pdb)


Since you want to programmatically access all of these formats in a common language c/c++ (basically you want the raw AST.. is this correct?)
you may need to write the parsers yourself as you mentioned.


check this tool i'm building:
[http://www.robusthaven.com/Products.aspx?type=products&name=peg](http://www.robusthaven.com/Products.aspx?type=products&name=peg)

I support C/C# export parsers of peg rules and as you build your rules you can provide input to test. Actually this week we were going start working on the c++ export version of the library (C was going be the most difficult to support [we still have a couple of fixes but it is ready for use] ... the oop languages should take half the time < 1 month).   

This could be a real world test of the project.  
I would be willing to provide the ide, and export of the project into your perfered language for your needs as long as we could work together to build these rules and publish them public.

let me know if you are interested.

lm

---

### Post by directhex on 2009-06-28
> **leblancmeneses said:**
> for PE reader writer
microsoft released: 
[http://ccimetadata.codeplex.com/](http://ccimetadata.codeplex.com/)
there is also:
[http://evain.net/blog/articles/2009/04/27/pdb2mdb-and-mono-cecil-pdb](http://evain.net/blog/articles/2009/04/27/pdb2mdb-and-mono-cecil-pdb)

Ehm..... No, not helpful. cecil is for CLI assemblies only, not PE executables

---

