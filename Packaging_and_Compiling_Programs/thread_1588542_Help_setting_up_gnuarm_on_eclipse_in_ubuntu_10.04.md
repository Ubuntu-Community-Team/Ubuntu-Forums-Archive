---
title: "Help setting up gnuarm on eclipse in ubuntu 10.04"
date: 2010-10-05
forum: Packaging and Compiling Programs
---

### Post by krish2487 on 2010-10-05
Hello all..
I am basically a newbie who wants to shift from windows to linux.
I installed ubuntu 10.04, desktop version on my netbook. 
I work on embedded systems so after googling around i was able to understand that i would need to compile the toolchain for my PC.

I took the most popular option eclipse and gnuarm.

I downloaded a precompiled/ prebuilt package from gnuarms website.
My netbook has a 32 bit processor so i downloaded the package for x86 systems.
The instructions said all i had to do was to decompress the zip file to a location and add the bin directory for the decompressed folder to my path.

I did accordingly and added the bin directory to my $PATH
i included the change in my .bashrc file too.

I then downloaded eclipse helios and installed the gnuarm eclipse plugin on it.

Now when i tried to compile a simple code that is given below.

```

/*
 * hello.c
 *
 *  Created on: 04-Oct-2010
 *      Author: krishi
 */

#include<stdio.h>

int main()
{
    printf("Hello World");
}

```

it gives me a make error error 127

the exact error message it gives is

```

**** Build of configuration Debug for project hello ****

make -k all 
/bin/sh: arm-elf-gcc: not found
Building file: ../hello.c
Invoking: ARM Linux GCC C Compiler
make: *** [hello.o] Error 127
arm-elf-gcc -O0 -Wall -Wa,-adhlns="hello.o.lst" -c -fmessage-length=0 -MMD -MP -MF"hello.d" -MT"hello.d" -mcpu=arm7tdmi -mthumb -mthumb-interwork -g3 -gdwarf-2 -o"hello.o" "../hello.c"
make: Target `all' not remade because of errors.

```

Now i did do my homework and google for the popular reasons to see this message and tried all the fixes/workarounds that were suggested
sadly none of them worked for me.

I did try compiling the code from command prompt in the workspace directory and it compiled just fine with all the arguments that were passed in eclipse.
I simply copied the commands that eclipse invoked and pasted them in the command prompt.
It compiled just fine.

Then i saw that eclipse invoked the arm-elf-gcc through the sh shell and repeated the exercise from sh shell rather than bourne and that too worked.

However the project refuses to compile in eclipse
And i dont think it is a path issue nor any package dependancy nor installing the gnuarm toolchain.
These are/were the most obvious/popular problems. and i dont think this is the problem which i am facing.
Am i overlooking an obvious step, owing to the lack of my experience, preventing the toolchain from compiling?

Thanks in advance.

---

