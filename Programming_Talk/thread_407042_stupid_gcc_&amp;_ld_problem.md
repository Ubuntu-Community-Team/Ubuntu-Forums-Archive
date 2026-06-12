---
title: "stupid gcc &amp; ld problem"
date: 2007-04-11
forum: Programming Talk
---

### Post by odradek on 2007-04-11
```

jimihex@b0x:~/devel/C$ ls
hello.c
jimihex@b0x:~/devel/C$ cat hello.c
#include <stdio.h>
int main () {
        printf("Hello world\n");
        getchar();
        return 0;
}
jimihex@b0x:~/devel/C$ gcc -o hello hello.c
jimihex@b0x:~/devel/C$ ls
hello  hello.c
jimihex@b0x:~/devel/C$ ./hello
Hello world

jimihex@b0x:~/devel/C$ gcc -c -o hello2.o hello.c
jimihex@b0x:~/devel/C$ ld -o hello2 hello2.o
[B]ld: warning: cannot find entry symbol _start; defaulting to 0000000008048094
hello2.o: In function `main':hello.c:(.text+0x24): undefined reference to `puts'
:hello.c:(.text+0x29): undefined reference to `getchar'[/B]
jimihex@b0x:~/devel/C$

```

Help, please...

---

### Post by WW on 2007-04-11
Use gcc again, instead of ld:
```

$ gcc -o hello2 hello2.o

```

---

### Post by phossal on 2007-04-11
GCC is doing much more than most people think on an Ubuntu System. For example, it typically links with ld using something like this:
```

/usr/lib/gcc/i486-linux-gnu/4.1.2/collect2 --eh-frame-hdr -m elf_i386 -dynamic-linker /lib/ld-linux.so.2 -oS /usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/crt1.o /usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/crti.o /usr/lib/gcc/i486-linux-gnu/4.1.2/crtbegin.o -L/usr/lib/gcc/i486-linux-gnu/4.1.2 -L/usr/lib/gcc/i486-linux-gnu/4.1.2 -L/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib -L/lib/../lib -L/usr/lib/../lib [COLOR="Blue"]**S.o **[/COLOR]-lgcc --as-needed -lgcc_s --no-as-needed -lc -lgcc --as-needed -lgcc_s --no-as-needed /usr/lib/gcc/i486-linux-gnu/4.1.2/crtend.o /usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/crtn.o
```
You can always compile using the -v (verbose) flag to see everything gcc is doing to your files. 

Regards.

---

### Post by odradek on 2007-04-11
> **WW said:**
> Use gcc again, instead of ld:
```

$ gcc -o hello2 hello2.o

```

Yes, I know that. I need ld for some other purposes, so I want to know what is going on during the linking.

phossal, thank you a lot, this helped, but I still didn't find with what arguments I should use ld for right linking. Any sugestions ?

---

### Post by DoubleQuadword on 2007-04-11
The following command line should link your program without warnings and/or unresolved references:

```
ld hello2.o -o hello2 **-lc** **--entry main**
```

Note that **-lc** tells the compiler to use the standard C library and **--entry main** tells the compiler to use the address of 'main' as the application's entry point.

Regards.

---

### Post by phossal on 2007-04-11
> **odradek said:**
> Yes, I know that. I need ld for some other purposes, so I want to know what is going on during the linking.

phossal, thank you a lot, this helped, but I still didn't find with **what arguments I should use ld for right linking. Any sugestions ?**

In the example I posted earlier, I highlighted my object file - it's S.o - in blue. Everything else was included by gcc. I had prepared S.o manually using GAS. It was simply a "Hello, World!" program.

DoubleQuadWord may have correctly identified the minimal things necessary for linking, but if that fails, you should be able to substitute your object file in place of S.o and get it to work. 

I'm stuck playing in Windows, so I can't see what does/doesn't work like I normally would. Sorry.

---

### Post by Wybiral on 2007-04-11
I'm curious what you need ld for... ld is just a linker, it doesn't detect C's "main" as the starting point.

As DoubleQuadword showed, you can link to the C library... But if you're linking to the C library, why use ld and not GCC?

---

### Post by odradek on 2007-04-11
> **DoubleQuadword said:**
> The following command line should link your program without warnings and/or unresolved references:

```
ld hello2.o -o hello2 **-lc** **--entry main**
```

Note that **-lc** tells the compiler to use the standard C library and **--entry main** tells the compiler to use the address of 'main' as the application's entry point.

Regards.

Thank you. This works, but, something strange is going on :

```

jimihex@b0x:~/devel/C$ ld -lc --entry main -o hello2 hello2.o
jimihex@b0x:~/devel/C$ ls
hello2  hello2.o  hello.c
jimihex@b0x:~/devel/C$ ./hello2
bash: ./hello2: No such file or directory
jimihex@b0x:~/devel/C$

```

phossal, I saw that too with "-v" (Sorry because of my poor english), but, are all those arguments necessary ?  On Windows, with DJGPP this works fine, without problems. Btw, thanks a lot for helping me. :)

---

### Post by odradek on 2007-04-11
> **Wybiral said:**
> I'm curious what you need ld for... ld is just a linker, it doesn't detect C's "main" as the starting point.

As DoubleQuadword showed, you can link to the C library... But if you're linking to the C library, why use ld and not GCC?

I am working on some small OS development project and I need to link several object files into one flat binary. But, I am using Ubuntu only for a few months, so, it's little hard to adjust.

---

### Post by rplantz on 2007-04-11
> **odradek said:**
> I am working on some small OS development project and I need to link several object files into one flat binary. But, I am using Ubuntu only for a few months, so, it's little hard to adjust.

You can include your object files, assuming they are ELF format, on the same line with your C/C++ files. For example,
```

gcc myProg.c sub1.c sub2.o -o myProg

```
I do this often when I write functions in assembly language. I first assemble them, giving their respective object files. Then I use gcc to compile the main function (which is written in C) and link it with the already assembled object files. gcc is smart enough to know whether it has to compile the function or not. Then it goes on to the ld phase, automatically linking in the required C libraries.

(I do not show various options you may wish to use in my command above.)

---

### Post by Wybiral on 2007-04-12
> **rplantz said:**
> You can include your object files, assuming they are ELF format, on the same line with your C/C++ files. For example,
```

gcc myProg.c sub1.c sub2.o -o myProg

```


That's also pretty standard for C when you're working on something that requires more then one source file. Just compile them all with the "-c" flag (as you seem to already know)...

```

gcc file1.c -c
gcc file2.c -c
gcc file3.c -c

```

Then you link them and whatever libraries you're using...

```

gcc file1.o file2.o file3.o -lSomeLibrary -o program

```

And thats it. I doubt you would want to add the linker to any build system (makefile or whatever) so using GCC to do all of it is usually the way to go.

---

### Post by odradek on 2007-04-12
How can I use ld script in linking with GCC ?

```
ld -T link.ld -o final file1.o file2.o
```

---

### Post by Wybiral on 2007-04-12
What do you need a linker script for?

---

### Post by odradek on 2007-04-12
I was trying to link with "-Xlinker -T link.ld", but, it still doesn't work. I need it because it's not a usualy linking, so I need to define sections and some other parameters by myself. (Once again, I am sorry because of my poor english)

---

### Post by rplantz on 2007-04-12
I have worked with a Motorola 68k single-board computer that had no OS. We developed the code under linux, then loaded it onto the board. We used an ld script to link in our own libraries.

We learned how to do this by reading info for ld.

I don't mean this in the "rtfm" sense, but only you know what you need to do, so it probably makes more sense for you to try to figure it out from info. It's been several years since I have done this, so I would need to consult info myself in order to answer any questions you might have. :)

---

### Post by thornbird on 2010-09-13
> **odradek said:**
> ```

jimihex@b0x:~/devel/C$ ls
hello.c
jimihex@b0x:~/devel/C$ cat hello.c
#include <stdio.h>
int main () {
        printf("Hello world\n");
        getchar();
        return 0;
}
jimihex@b0x:~/devel/C$ gcc -o hello hello.c
jimihex@b0x:~/devel/C$ ls
hello  hello.c
jimihex@b0x:~/devel/C$ ./hello
Hello world
 
jimihex@b0x:~/devel/C$ gcc -c -o hello2.o hello.c
jimihex@b0x:~/devel/C$ ld -o hello2 hello2.o
**ld: warning: cannot find entry symbol _start; defaulting to 0000000008048094**
**hello2.o: In function `main':hello.c:(.text+0x24): undefined reference to `puts'**
**:hello.c:(.text+0x29): undefined reference to `getchar'**
jimihex@b0x:~/devel/C$

```
 
Help, please...
 I also have this problem&#65281;&#65281;do you resolve this question&#65311;if you resolve it&#65292;could you tell me what to do&#65311; thanks~~

---

### Post by spjackson on 2010-09-13
> **thornbird said:**
> 
```

jimihex@b0x:~/devel/C$ ld -o hello2 hello2.o
**ld: warning: cannot find entry symbol _start; defaulting to 0000000008048094**[B]
hello2.o: In function `main':hello.c:(.text+0x24): undefined reference to 
`puts'[/B]**:hello.c:(.text+0x29): undefined reference to `getchar'**

```I also have this problem&#65281;&#65281;do you resolve this question&#65311;if you resolve it&#65292;could you tell me what to do&#65311; thanks~~
Why are you linking by calling ld directly? Please explain why you need to do this. Linking by using gcc will do the right thing.
```
jimihex@b0x:~/devel/C$ gcc -o hello2 hello2.o
```If you must use ld directly then you will have to explicitly include the C runtime library.

---

### Post by van7hu on 2010-10-28
> **odradek said:**
> Thank you. This works, but, something strange is going on :

```

jimihex@b0x:~/devel/C$ ld -lc --entry main -o hello2 hello2.o
jimihex@b0x:~/devel/C$ ls
hello2  hello2.o  hello.c
jimihex@b0x:~/devel/C$ ./hello2
bash: ./hello2: No such file or directory
jimihex@b0x:~/devel/C$

```phossal, I saw that too with "-v" (Sorry because of my poor english), but, are all those arguments necessary ?  On Windows, with DJGPP this works fine, without problems. Btw, thanks a lot for helping me. :)

Has anyone solved this problem ?

---

### Post by NathanB on 2010-10-28
> **van7hu said:**
> Has anyone solved this problem ?

Yes.  Some versions of 'ld' look for the wrong version of stdlib, so you must tell it to use "/lib/ld-linux.so.2" instead.

---

### Post by van7hu on 2011-07-02
> **NathanB said:**
> Yes.  Some versions of 'ld' look for the wrong version of stdlib, so you must tell it to use "/lib/ld-linux.so.2" instead.

What did you really do?

and more, 
> 
van7hu@van7hu-laptop:~/C$ ldd main
    linux-gate.so.1 =>  (0x00776000)
    libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0x00d29000)
    /usr/lib/libc.so.1 => /lib/ld-linux.so.2 (0x00689000)
van7hu@van7hu-laptop:~/C$ whereis libc
libc: /usr/lib/libc.so /usr/lib/libc.a /usr/share/man/man7/libc.7.gz


---

### Post by RintheGreat on 2012-05-01
Hi everyone,
My gcc can not compile any file even the simplest hello.c one.
It worked just fine one Ubuntu 11.10 but when I've upgraded to 12.04 it cannot compile anything.
It said something about: 

/usr/local/bin/ld: this linker was not configured to use sysroots
collect2: ld returned 1 exit status

Can anyone show me how to fix this problem???

---

### Post by Zugzwang on 2012-05-02
> **RintheGreat said:**
> Hi everyone,
/usr/local/bin/ld: this linker was not configured to use sysroots
collect2: ld returned 1 exit status


First of all, check that you have the package "build-essential" installed. Then, you appear to have installed a custom version of the linker into "/usr/local/bin". Would you mind telling us why? Of course, you could just wipe everything from /usr/local, and this problem would go away, but there is probably a reason why you installed the custom linker there in the first place, so just removing stuff from "/usr/local" would surely break something else on the machine.

---

### Post by RintheGreat on 2012-05-02
I don't for sure. But the system worked just fine before I upgraded it. And I did not install anything strange after upgrading.

I search on the Internet I saw that this problem relates to many compilers but there is no result that relates to gcc.

---

### Post by Zugzwang on 2012-05-03
> **RintheGreat said:**
> I don't for sure. But the system worked just fine before I upgraded it. And I did not install anything strange after upgrading.

The point is that you installed some stuff bypassing the package manager **before** you eventually upgraded. After the upgrade, the old stuff is no longer compatible. It's like with a car: if you installed some tweak to your car, and then change the car, but keep the tweak, it isn't guaranteed to still work.

---

### Post by mprat on 2013-04-05
I find this entire thread a little bit sad - nowhere is a mention of a fix to the original problem and there is only ad-hominem on the original poster. 

If /usr/local/bin is the custom linker path that is installed, how do you change it back to the default linker path?

---

### Post by codemaniac on 2013-04-05
Really really old thread. Closed.

Please feel free to start afresh.

---

