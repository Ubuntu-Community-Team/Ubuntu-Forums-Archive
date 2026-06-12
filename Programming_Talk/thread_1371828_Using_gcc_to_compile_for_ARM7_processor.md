---
title: "Using gcc to compile for ARM7 processor"
date: 2010-01-03
forum: Programming Talk
---

### Post by bhargava470 on 2010-01-03
Hi all,

I'm trying to compile a program for ARM processor. Lets say the hello world program. What should be the -march option for the arm7 processor.

```
gcc hello.c -o hello -march=armv7
hello.c:1: error: bad value (armv7) for -march= switch
hello.c:1: error: bad value (armv7) for -mtune= switch
```

I found [here]("http://gcc.gnu.org/onlinedocs/gcc/ARM-Options.html") , it has armv7 option. Why is this giving errors.

Thanks

---

### Post by not_a_phd on 2010-01-03
It is unclear to me from your posting, so I will ask: 

Have you compiled the version of gcc (and glibc) that you are using with the -march switch? I am pretty sure that you cannot use the stock gcc supplied with Ubuntu to go off and cross compile for any architecture. 

If not, I would highly recommend [http://www.kegel.com/crosstool/](http://www.kegel.com/crosstool/) as a starting point for putting together the toolchain you need for crosscompiling to the arm processor.

Regards.

---

### Post by MindSz on 2010-01-04
I work with ARM processors a lot and, even tho I don't use the -march option, I do have to compile my programs using an ARM compiler, provided by the same people that creates the boards.

---

### Post by iharrold on 2010-01-05
I have always had to compile my crosscompiler for the specific platform.  It will use the local machine's instruction set to compile the code to the target machine's instruction set.  

Once the cross compiler is built then you can use the "-mtune" etc... switches (though usually they are set by default).  

Here are some quick google links that might help you:
[http://www.quickembeddedtips.com/arm7-gcc-toolchains-ide-and-debug-support-beginners-12](http://www.quickembeddedtips.com/arm7-gcc-toolchains-ide-and-debug-support-beginners-12)
[http://wiki.lochraster.org/wiki/ARM7_GNU_Toolchain](http://wiki.lochraster.org/wiki/ARM7_GNU_Toolchain)

---

### Post by bhargava470 on 2010-01-06
> **not_a_phd said:**
> Have you compiled the version of gcc (and glibc) that you are using with the -march switch? I am pretty sure that you cannot use the stock gcc supplied with Ubuntu to go off and cross compile for any architecture. 

Sorry I was just using the compiler which was installed by default and assumed it would have been compiled already.
Thanks.

---

### Post by not_a_phd on 2010-01-08
> **bhargava470 said:**
> Sorry I was just using the compiler which was installed by default and assumed it would have been compiled already.
Thanks.

Welcome to the wonderfully confusing world of cross compilation. So, as you put it - the compiler which was installed by default is in fact compiled already. However, it has likely been compiled on an x86 platform to generate instructions for an x86 target. By default, it will *not* spit out programs that will run on an ARM processor, even though it looks like it should accept a flag that tells it to do so.

What you must do is get the source code for the gcc compiler, and compile it (using your default compiler) with the flags set to enable it to output ARM instructions. Unfortunately, it is not even as easy as that, as you will also need libraries built for the ARM while you are building gcc. Thus, you will have to build a bootstrap compiler (and assembler, and linker) with limited capabilities, to build the libraries, to build the compiler (and assembler, and linker) that you will end up using.

Complicated enough yet? Fortunately, Dan Kegel has automated this whole process with a set of scripts that do all of this for you, ultimately producing a non-default version of gcc that will compile applications (and Linux kernels) to run on your ARM processor.

Good Luck!

---

