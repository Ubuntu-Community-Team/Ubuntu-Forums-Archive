---
title: "I need mipsel-linux-gcc - where is it?"
date: 2007-01-17
forum: Programming Talk
---

### Post by zerhacke on 2007-01-17
I need mipsel-linux-gcc to build a PlayStation 1 Linux kernel.  Yes, that's right, Linux in a Playstation 1.  I found some source on a Russian website and it compiles just right up to the actual making of the kernel.  I get the following error in the terminal:

make: mipsel-linux-gcc: Command not found
make: *** [init/main.o] Error 127
jason@diabolical:~/Playstation_Linux/PSXLinux$ 

Does anyone know where I can get mipsel-linux-gcc?

---

### Post by adewale on 2007-01-17
i also have an old ps x at home. please could you give an how to i tried googling 4 it but yielded no result thanks

---

### Post by zerhacke on 2007-01-17
I found out that mipsel-linux-gcc is part of the mipsel-linux package alluded to across the internet but not actually offered for download at any place I have found.  The process involves patching binutils and gcc, which I have not yet done.  I will get on this soon, within the next two days or so... first I gotta find the download, then read the instructions, then get back to compiling this kernel.

Even if/when I compile this kernel I still need to figure out how to build a bootable CD out of it.  I'm of the mind that using Windows (easiest way I can think of it) to use Nero, put a PS1 CD in the drive, and tell it to copy the bootloader off of that CD.  Then I simply replace the file the bootloader hands off to with the kernel and it should boot.  Just gotta fire up a hex editor and read the boot sector to see what it is that it hands off to.

Yay for reverse engieering!

adewale, the howto* will be located in the how to section of the forum when I am done.  Give me a couple days.  I will PM you in particular and anyone else who wants a PM when I have finished.

*Those of you in the know, please respond in this thread to tell me if putting a Generic Linux - Non Ubuntu Linux howto is allowed.

---

### Post by adewale on 2007-01-17
thanks

---

