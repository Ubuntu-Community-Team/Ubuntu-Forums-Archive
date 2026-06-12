---
title: "binutil 2.17 install"
date: 2007-03-26
forum: Programming Talk
---

### Post by k0mpresd on 2007-03-26
can someone help me out here?

the following should explain my problem..thanks :)

> k0mpresd@k0mp:~/Desktop/linux-2.6.20$ **export PATH=$PATH://home/k0mpresd/crosstool-0.43/build/powerpc64-unknown-linux-gnu/gcc-4.1.0-glibc-2.3.6/gcc-core-prefix/bin**
k0mpresd@k0mp:~/Desktop/linux-2.6.20$ alias smake='make ARCH=powerpc CROSS_COMPILE=powerpc64-unknown-linux-gnu-'
k0mpresd@k0mp:~/Desktop/linux-2.6.20$ smake
*** 2.6 kernels no longer build correctly with old versions of binutils.
*** Please upgrade your binutils to 2.12.1 or newer
make: *** [checkbin] Error 1
k0mpresd@k0mp:

i have downloaded and installed binutils-2.17 and installed it like this:
```
./configure
make
sudo make install
```

but i still get the same error?

the binutils readme says this:
> If you have more than one compiler on your system, it is often best to
explicitly set CC in the environment before running configure, and to
also set CC when running make.  For example (assuming sh/bash/ksh):

	CC=gcc ./configure
	make

but i dont know if that applies to me or how to install it correctly if it does

---

### Post by Mr. C. on 2007-03-26
By default, GNU utils will install in /usr/local as PREFIX.

You need to have /usr/local in your path before /bin or /usr/bin in this case:

PATH=/usr/local:$PATH *command*

will do the trick I believe.

MrC

---

### Post by k0mpresd on 2007-03-26
this shouldnt be this hard...i iwish i understood...

> k0mpresd@k0mp:~/Desktop/linux-2.6.20$ export PATH=$PATH://home/k0mpresd/crosstool-0.43/build/powerpc64-unknown-linux-gnu/gcc-4.1.0-glibc-2.3.6/gcc-core-prefix/bin
k0mpresd@k0mp:~/Desktop/linux-2.6.20$ powerpc64-unknown-linux-gnu-gcc
powerpc64-unknown-linux-gnu-gcc: no input files
k0mpresd@k0mp:~/Desktop/linux-2.6.20$ PATH=/usr/local/bin:$PATH
k0mpresd@k0mp:~/Desktop/linux-2.6.20$ powerpc64-unknown-linux-gnu-gcc
powerpc64-unknown-linux-gnu-gcc: no input files
k0mpresd@k0mp:~/Desktop/linux-2.6.20$ alias smake='make ARCH=powerpc CROSS_COMPILE=powerpc64-unknown-linux-gnu-'
k0mpresd@k0mp:~/Desktop/linux-2.6.20$ smake
*** 2.6 kernels no longer build correctly with old versions of binutils.
*** Please upgrade your binutils to 2.12.1 or newer
make: *** [checkbin] Error 1

k0mpresd@k0mp:~/Desktop/linux-2.6.20$ PATH=/usr/local/:$PATH
k0mpresd@k0mp:~/Desktop/linux-2.6.20$ powerpc64-unknown-linux-gnu-gcc
powerpc64-unknown-linux-gnu-gcc: no input files
k0mpresd@k0mp:~/Desktop/linux-2.6.20$ alias smake='make ARCH=powerpc CROSS_COMPILE=powerpc64-unknown-linux-gnu-'
k0mpresd@k0mp:~/Desktop/linux-2.6.20$ smake
*** 2.6 kernels no longer build correctly with old versions of binutils.
*** Please upgrade your binutils to 2.12.1 or newer
make: *** [checkbin] Error 1
k0mpresd@k0mp:~/Desktop/linux-2.6.20$ 

k0mpresd@k0mp:~/Desktop/linux-2.6.20$ powerpc64-unknown-linux-gnu-gcc
powerpc64-unknown-linux-gnu-gcc: no input files
k0mpresd@k0mp:~/Desktop/linux-2.6.20$ PATH=/usr/local/bin:$PATH alias smake='make ARCH=powerpc CROSS_COMPILE=powerpc64-unknown-linux-gnu-'
k0mpresd@k0mp:~/Desktop/linux-2.6.20$ smake
*** 2.6 kernels no longer build correctly with old versions of binutils.
*** Please upgrade your binutils to 2.12.1 or newer
make: *** [checkbin] Error 1
k0mpresd@k0mp:~/Desktop/linux-2.6.20$ 

---

### Post by Mr. C. on 2007-03-27
It isn't that hard, but it is always 10x harder to do something without a little more understanding of the basics.  You've installed a second set of utilities, in /usr/local/bin.  Now you have two versions of the utilities in your system.  You need to tell your shell where to find the new ones.

Its like having two envelopes on your desk - you put Friday's pay check in one, but keep picking up the other empty one and are surprised when you get to the bank and there's no money!   You have to be sure you know which envelope contains the money before you start the car.

Before you start the build process, you have to ensure that the shell knows where to find your new binutils programs.  They are likely in /usr/local/bin.  Have you verified this (eg. looked in the envelope to see if the money is there) ?  If not, you need to find out where they were installed.  If so, then you need to be sure your shell commands use the correct programs.  Your PATH variable tells the shell where to look (for relative paths).  This will do what you want:

```
$ alias smake='make ARCH=powerpc CROSS_COMPILE=powerpc64-unknown-linux-gnu-'
$ PATH=/usr/local/bin:$PATH   # you only need to do this once for this shell
$ smake

```

Read a little about shells in Week 5's notes in the Coursework section: [http://cis68a.mikecappella.com/](http://cis68a.mikecappella.com/)

MrC

---

### Post by k0mpresd on 2007-03-27
ohhhh.....ok...wow...haha..yea..that is really simple...i get it now though

and yes, it did install to usr/local/bin

thank you for the help and your time :)

i feel like such a n00b :lolflag:

---

### Post by winch on 2007-03-27
Binutils is a collection of tools that handle program binaries, like gcc they target a specific architecture.

Run configure with no arguments and it will build the tools so they target the hosts architecture. You need to pass configure the correct arguments so it targets powerpc64 instead of your host system.
Something along the lines of
./configure --target=powerpc64

I'm not sure if you can take a tool chain then just swap in a newer version of binutils. Binutils contains low level tools like the assembler (as) and linker (ld) that are used by gcc. I'm not really sure how it all works together but I think it might be better to scrap your existing tool chain and start from scratch using the version of binutils you require.

I'd look into why crosstool doesn't use a newer version of binutils and if it can be made to. Building just a compiler without crosstool is usually pretty easy. Building a compiler that will also build the kernel and glibc can be a nightmare which crosstool or at least the patches it uses can make much easier.

What system/project are you trying to use? They might have instructions for building a working toochain.

---

### Post by mac.ryan on 2007-03-27
> **k0mpresd said:**
> i feel like such a n00b

Noob here as well. What I am doing to get a grasp on how linux is working is to build my own linux from scratch ([http://www.linuxfromscratch.org/)]("http://www.linuxfromscratch.org/%29"). It is time consuming and so dense of information that you won't probably retain it all (I am not, for sure), but you really get to know well the toolchain, how it works, what parameters you need to use, etc... besides other concepts like cross-compilation, booting, package management, etc...

"Beyond Linux From Scratch" goes... beyond. But I haven't reached that point yet, so I can't comment on that.

If you have some spare hours and some patience, I warmly recommend the experience! :)

---

### Post by k0mpresd on 2007-03-27
> **winch said:**
> I'd look into why crosstool doesn't use a newer version of binutils and if it can be made to. Building just a compiler without crosstool is usually pretty easy. Building a compiler that will also build the kernel and glibc can be a nightmare which crosstool or at least the patches it uses can make much easier.

What system/project are you trying to use? They might have instructions for building a working toochain.
crosstool came w/ a binutils-2.16 install package..i didnt know about this until after i had already downloaded the 2.17 version

i am trying to compile a patched linux kernel to be booted by an xbox360

reference page for what im trying to do ~> [http://mydedibox.homelinux.com/modules/smartsection/item.php?itemid=3](http://mydedibox.homelinux.com/modules/smartsection/item.php?itemid=3)

there is also a thread on xboxhacker.net w/ more information, it is located under software/technical.."writing C programs for xbox360 possible" is the thread title

any input is more than welcome :)

---

### Post by k0mpresd on 2007-03-27
i hate my computer

> k0mpresd@k0mp:~$ cd Desktop/linux-2.6.20
k0mpresd@k0mp:~/Desktop/linux-2.6.20$ export PATH=$PATH://home/k0mpresd/crosstool-0.43/build/powerpc64-unknown-linux-gnu/gcc-4.1.0-glibc-2.3.6/gcc-core-prefix/bin
k0mpresd@k0mp:~/Desktop/linux-2.6.20$ alias smake='make ARCH=powerpc CROSS_COMPILE=powerpc64-unknown-linux-gnu-'
k0mpresd@k0mp:~/Desktop/linux-2.6.20$ PATH=/usr/local/bin:$PATH
k0mpresd@k0mp:~/Desktop/linux-2.6.20$ smake
*** 2.6 kernels no longer build correctly with old versions of binutils.
*** Please upgrade your binutils to 2.12.1 or newer
make: *** [checkbin] Error 1
k0mpresd@k0mp:~/Desktop/linux-2.6.20$ 

---

### Post by k0mpresd on 2007-03-27
i finally got it :) :)

but not i have a new problem :(

oh well..atleast i solved this one

here was the solution:
> k0mpresd@k0mp:~/Desktop/linux-2.6.20$ alias smake='make ARCH=powerpc CROSS_COMPILE=powerpc64-unknown-linux-gnu-'
k0mpresd@k0mp:~/Desktop/linux-2.6.20$ PATH=/opt/crosstool/gcc-4.1.0-glibc-2.3.6/powerpc64-unknown-linux-gnu/bin:$PATH
k0mpresd@k0mp:~/Desktop/linux-2.6.20$ smake


---

