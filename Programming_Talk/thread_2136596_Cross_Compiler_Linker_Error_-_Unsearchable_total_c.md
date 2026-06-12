---
title: "Cross Compiler Linker Error - Unsearchable total confusion panic!"
date: 2013-04-18
forum: Programming Talk
---

### Post by jerecb on 2013-04-18
Hi, I am a bit of a Linux beginner - I've used the shell and desktop quite a but never had to set it up! However, I'm now trying to get a compiler working so I can develop some C code on an x86 development machine then cross-compile it to PowerPC code for an embedded system. 

So I have Ubuntu 12.10 running well (in a VirtualBox, if that matters). I've been having a great time writing C with the Code::Blocks IDE. No problems there. 

To get the cross-compiler working, I installed the **gcc-4.7-powerpc-linux-gnu package** with apt-get, along with**libc6-dev-powerpc-cross**.  

This added **powerpc-linux-gnu** and **i686-linux-gnu** to my /usr. 

Code::Blocks seems to be able to compile my code as PowerPC OK, but it fails at the link stage (I think). Here's the output, showing the commands which it is calling. 

```
-------------- Build: PowerPC in HelloWorld (compiler: GNU GCC Compiler for PowerPC)---------------


powerpc-linux-gnu-gcc -Wall  -O2  -Wmain    -c main.c -o obj/PowerPC/main.o
powerpc-linux-gnu-ld  -o bin/PowerPC/HelloWorld obj/PowerPC/main.o   -s  
powerpc-linux-gnu-ld: warning: cannot find entry symbol _start; defaulting to 0000000010000080
obj/PowerPC/main.o: In function `main':
main.c:(.text.startup+0x14): undefined reference to `puts'
Process terminated with status 1 (0 minutes, 0 seconds)
2 errors, 0 warnings (0 minutes, 0 seconds)

```

As you can see, I've set up **powerpc-linux-gnu-gcc** as the C compiler and **powerpc-linux-gnu-ld** as the linker. I'm not even sure this is correct, as there are a number of powerpc-linux-gnu-... binaries available in /usr/bin, and I couldn't find any description of what they are anywhere. These seemed logical. 

The compiler seems OK - it makes a credible main.o. Is the linker missing a library path or something? 

/usr/powerpc-linux-gnu/lib seems to contain the libraries, and I tried adding it to the linker path in Code::Blocks (it adds "-L/usr/powerpc-linux-gnu/lib" to the linker command) but that made no difference. 

Or is this actually far more complex than I think? It looks like it ought to be simple because the compile and link commands used for the normal x86 build are pretty straight-forward, and there are no special options or paths set up in Code::Blocks. 

Any help would be greatly appreciated as I can't find anything useful with internet searches! I'm pulling my hair out because this needs to be done ASAP and I'd really rather be writing code than messing with compiler settings!

---

### Post by dargaud on 2013-04-18
Didn't look in detail, but a much simpler way to cross compile is to use BuildRoot: download tar file, untar, cd, make menuconfig, make, done.

---

### Post by jerecb on 2013-04-18
Thanks! Simple = Good. I'll look into that.

---

### Post by jerecb on 2013-04-18
UPDATE: After more research I realised (I think...) that **powerpc-linux-gnu-gcc** does the linking as well. By using that as the linker I can build OK - but the resulting executable causes an immediate Segmentation Fault on the PowerPC (which is running MicroKnoppix). 

I should post my code for completeness: 

```

#include <stdio.h>
#include <stdlib.h>


int main()
  {
  printf("Hello PowerPC!\n");
  return 0;
  }

```

I agree, "Hello PowerPC" was optimistic. ;)

---

### Post by jerecb on 2013-04-18
SOLVED!

Someone sent me a different version of the GCC compiler, and everything now compiles, links and executes sweetly. So turns out that it WAS pretty simple, with the correct version!

---

