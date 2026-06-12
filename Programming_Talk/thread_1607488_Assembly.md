---
title: "Assembly"
date: 2010-10-27
forum: Programming Talk
---

### Post by Spirrwell on 2010-10-27
I've learned a lot about C++, C, C# in Windows and I wanted to start using Assembly. I figure that I can handle Assembly, as I've been learning a lot about 3D game development, 3D vectors, etc. It's something that I've been able to really pick up. I installed Ubuntu, (I haven't got a clue why, but I just did) and I wanted to take on Assembly to work on creating a bootloader and a kernel to create my own OS. 

From what I've watched on YouTube! and what I've read, here's what I sum it up to be. You create asm files for whatever purpose in Assembly, and then you use NASM which converts it to a binary file, and then you have put that on a floppy disk or a virtual floppy using QEMU, VMware Player, or something like that, which is the way I have to go as I don't have floppy capabilities with my current system. Is that about right?

If it helps I'm using Ubuntu 10.10, and I think it's 64 bit, I'm not 100% sure it's 64 bit, I burned the CD a while ago. Also if I'm to go this way, would it still be considered a Unix derivative or would it be different depending on the code I use? I'd rather it not be derived from Unix. I want to create something new. One last thing, is there any other way to do this?

Thanks in advance!

---

### Post by snakerdlk on 2010-10-27
Writing assembly is somewhat more difficult from writing in most other high level languages since you have to think differently, because you have to worry about which registers have to hold the values you want to process and where the return value will be stored, and so on.

I'm not knowledgeable in writing kernels or bootloaders but I believe it is not very straightforward.

It should be possible to code a program that is not operating system dependent using NASM and you should be able to test it by specifying it as kernel in grub for example. Or a floppy I think, the program would need to be written at the start of the floppy to be able to be booted.

The code would not be unix derivative since you probably wont use the kernel source code.

To write a kernel of your own, it probably is the only choice, though the linux kernel is written mostly in C but you'll have to start with assembly to get somewhere.

---

### Post by NathanB on 2010-10-27
You will want some good books.  There are only two that I know of that have brand-new editions on the shelf:

Jeff's "Assembly Language Step-By-Step"
[http://www.amazon.com/Assembly-Language-Step-Step-Duntemann/dp/0471578142](http://www.amazon.com/Assembly-Language-Step-Step-Duntemann/dp/0471578142)

Randy's "Art of Assembly Language"
[http://nostarch.com/assembly2.htm](http://nostarch.com/assembly2.htm)

A list of Linux ASM resources can be found here:  
[http://asm.sourceforge.net/](http://asm.sourceforge.net/)

Also, I recommend installing (and building) the latest NASM version ( 2.09.03 ) from source because the one in Ubuntu's repo is likely old and buggy:  [http://www.nasm.us/](http://www.nasm.us/)

If you're really serious about OS development, be sure to study everything obtainable on the community wikis:

[http://aodfaq.wikispaces.com/](http://aodfaq.wikispaces.com/)

[http://wiki.osdev.org/Main_Page](http://wiki.osdev.org/Main_Page)

Lastly, NeHe is the number one go-to site for 3D game development:

[http://nehe.gamedev.net/lesson.asp?index=01](http://nehe.gamedev.net/lesson.asp?index=01)

Hope that helps.

Nathan.

---

### Post by worksofcraft on 2010-10-28
> **Spirrwell said:**
> I wanted to take on Assembly to work on creating a bootloader and a kernel to create my own OS. 


I wrote a kernel once and I learned to avoid assembler. You can do practically EVERYTHING in C++. All you need to do in assembler is have a function to set up stack space, one to access I/O space and to write interrupts service routines (although some C++ compilers have the "interrupt" specifier).

An interrupt service routines can simply push the context on the current stack and jump to your C++ implemented scheduler. The scheduler can do context switches with setjmp/longjmp... oh... you also need a return from interrupt in assembler so that the scheduler can return to interrupted tasks when it finds one.

Mind you, today processors are a lot more complicated and you may have multiple processor cores and virtual memory to contend with. If I were you I would start by looking at the Grub2 source code.

---

### Post by nvteighen on 2010-10-28
Well, ASM is only truly useful if you want/need to go to the lowest possible level of abstraction: kernels, bootloaders, stuff that needs to be highly optimized at the lowest possible level, etc.

But as soon as you go one step up the "abstraction ladder", you may find Assembly to be limiting. AFAIK, the Linux kernel is less than 5% Assembly code whose purpose is to create the basic foundations for the other 95% of C code. Ok, yes, you can write whatever you want in any language you want, but languages have their "niche"; ASM's is pretty specific.

Now, there's a slight "issue" with NASM in particular. Despite being possibly the best ASM out there, gcc insists in using GAS. So, if you're thinking in inlined ASM code in C or C++ code compiled with GCC (remember, GCC = gcc + g++ + gfortran + gobjc + ...), you'll get GAS, which by default uses AT&T syntax (though you can change it to Intel syntax... but it's still not NASM!). To use NASM with GCC compiled code, you'll have to do some linking tricks that are trivial but a bit... uh... cumbersome and hackish... and require you to not use any inlined ASM, but separate ASM modules.

---

### Post by Spirrwell on 2010-10-28
I know that the Assembly language is very low level, and that it isn't portable. I also know that you need a floppy disk, as I mentioned, to be able to boot. That is the stuff that I'm quite familiar with.

As for needing a book, I suppose that I may need those, I managed to learn C\C++\C# without any books, but as has been said, they are mid level programming languages and Assembly is low level.

I've basically heard a bit of the same thing over and over again, you start in Assembly, then you move to C\C++. I've tried to code using MonoDevelop, but it's a little bit different than using Visual Studio 2010, which is what I'm used to. Anyway, thanks I'll keep studying.

---

### Post by nvteighen on 2010-10-29
> **Spirrwell said:**
> I know that the Assembly language is very low level, and that it isn't portable. I also know that you need a floppy disk, as I mentioned, to be able to boot. That is the stuff that I'm quite familiar with.


Well, use a Virtual Machine... it's the best solution, as it allows you to test your stuff in a perfectly safe environment and well... using a dd-created binary file as your floppy or using an ISO file as your CD-ROM or DVD :)

I've only tried Qemu and Bochs, and liked the first better.

---

