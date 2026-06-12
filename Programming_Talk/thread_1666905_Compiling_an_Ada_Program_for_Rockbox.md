---
title: "Compiling an Ada Program for Rockbox"
date: 2011-01-14
forum: Programming Talk
---

### Post by Ad1217 on 2011-01-14
I am trying to build an Ada program for an ARM-based Sandisk Sansa Clip Plus+. The program is William Whitaker's Words, a Latin-English/English-Latin program. Rockbox provides a "rockboxdev.sh" script that builds "arm-elf-eabi-gcc" and some other compilers. I cannot figure out how to build gnat for ARM, though.

---

### Post by ibuclaw on 2011-01-14
What type of host/target are you building gnat on? What have you already tried?

---

### Post by Ad1217 on 2011-01-14
host: ubuntu 10.10 32 bit (I also have 64 bit avalible to me)
target: Sandisk Sansa Clip Plus+
what I've already tried: installing gnat and running the rockboxdev.sh script again, adding ada to the rockboxdev.sh script (as a language to build), I also looked on several sites for an arm ada compiler, but could not figure out if they would work for me

---

### Post by ibuclaw on 2011-01-15
> **Ad1217 said:**
> 
what I've already tried: installing gnat and running the rockboxdev.sh script again, adding ada to the rockboxdev.sh script (as a language to build), I also looked on several sites for an arm ada compiler, but could not figure out if they would work for me

Oh, your using a script? Is this that one?

[http://svn.rockbox.org/viewvc.cgi/trunk/tools/rockboxdev.sh?revision=29051&view=markup](http://svn.rockbox.org/viewvc.cgi/trunk/tools/rockboxdev.sh?revision=29051&view=markup)

Just looking at it, my guess is that you'll need to change two places. First --enable-languages. Something you've already mention. Second remove "-core" from **file="gcc-core-$version.tar.bz2"** to download the right gcc package.

Regards

---

### Post by Ad1217 on 2011-01-17
Yes, that is the script. I am running it with the changes now. Thank you!

---

### Post by Ad1217 on 2011-01-17
after running it for a while, I got this
```
checking for C compiler default output file name... configure: error: in `/tmp/rbdev-build/build-gcc/arm-elf-eabi/libada':
configure: error: C compiler cannot create executables
See `config.log' for more details.
make[1]: *** [configure-target-libada] Error 1
make[1]: Leaving directory `/tmp/rbdev-build/build-gcc'
make: *** [all] Error 2

```

What should I do?

---

### Post by Ad1217 on 2011-01-17
I just ran it again with the exact same results.

---

### Post by Ad1217 on 2011-01-18
if I take C out of enable-languages, will that work?

---

### Post by Ad1217 on 2011-01-18
Never mind, I got the same error when I did that.

---

### Post by Vox754 on 2011-01-18
> **Ad1217 said:**
> I am trying to build an Ada program for an ARM-based Sandisk Sansa Clip Plus+. The program is William Whitaker's Words, a Latin-English/English-Latin program. Rockbox provides a "rockboxdev.sh" script that builds "arm-elf-eabi-gcc" and some other compilers. I cannot figure out how to build gnat for ARM, though.

I can't believe somebody else has heard of "Words"!

Several years before I started using Linux, I used the compiled version of Words in Windows. I believe I tried the compiled Linux executable only once.

Back then I didn't have a clue about programming, now I think, why hasn't this been ported to Python? Could it ever receive promotion and be included in Debian and Ubuntu repos? Will it ever be ported to another language that is not freaking Ada?

Woo... sure brings back memories.

---

### Post by Ad1217 on 2011-01-19
> **Vox754 said:**
>  Will it ever be ported to another language that is not freaking Ada?.

If someone had it in another language that could be compiled for rockbox, that would work to.

---

### Post by ibuclaw on 2011-01-20
Check config.log, see near the bottom where there should be more details on why build is failing. Also, which version of gcc are you building? :)

---

### Post by Ad1217 on 2011-01-20
gcc version is 4.4.4, this is from the rockbox site
config.log is attached from the directory "/tmp/rbdev-build/build-gcc/arm-elf-eabi/libada/"

---

### Post by Vox754 on 2011-01-20
> **Ad1217 said:**
> If someone had it in another language that could be compiled for rockbox, that would work to.

I just took a look at WORDS source code, and it's aweful.

Now, I don't know Ada, so perhaps it's not that bad, it's just that there are so many files there, it's difficult trying to figure out where to start. I would definitely use a subdirectory or two to store all the functions, while keeping the main module (words.adb) in the top directory.

I don't even know if Ada has good library support to perform text, string and character handling, or if everything is mostly low-level, like C. I have the impression the program would be so much manageable in Python.

Rewriting this program would certainly be a monumental task. Perhaps someone finds time for it.

---

### Post by ibuclaw on 2011-01-21
> **Ad1217 said:**
> gcc version is 4.4.4, this is from the rockbox site
config.log is attached from the directory "/tmp/rbdev-build/build-gcc/arm-elf-eabi/libada/"

```

configure:1874: $? = 1
configure:1897: checking for C compiler default output file name
configure:1900: /tmp/rbdev-build/build-gcc/./gcc/xgcc -B/tmp/rbdev-build/build-gcc/./gcc/ -B/usr/local/arm-elf-eabi/bin/ -B/usr/local/arm-elf-eabi/lib/ -isystem /usr/local/arm-elf-eabi/include -isystem /usr/local/arm-elf-eabi/sys-include -g -U_FORTIFY_SOURCE     conftest.c  >&5
/usr/local/arm-elf-eabi/bin/ld: crt0.o: No such file: No such file or directory
collect2: ld returned 1 exit status
configure:1903: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| 
|   ;
|   return 0;
| }
configure:1941: error: in `/tmp/rbdev-build/build-gcc/arm-elf-eabi/libada':
configure:1944: error: C compiler cannot create executables
See `config.log' for more details.

```
It's expecting to find a linker that simply isn't there (possibly because the script may presume you already have some sort of cross-compiling binutils already installed on the system). Last time I checked, Ubuntu x86/x86_64 platforms have an ARM EABI cross compiler toolset there in the repository for you to install. Using it may help...

---

### Post by Ad1217 on 2011-01-21
I installed both the 4.4 and 4.5 versions of the arm-linux-gcc packages, but both returned the same thing about ada not being installed as the script-created files did. I then tried running the script, but that did not work either, giving the same error as before.

---

### Post by gmargo on 2011-01-23
Hi, I've been following this discussion since it's an interesting cross-compiling question.  Interesting even I know nothing of Ada or Latin :D

Here's a patch that gets around the problem you've encountered.  Some of the other libraries (like libgcc) are configured better for cross-compiling, so this patch adds one part of that for libada.

However, this does not solve the entire problem.  The compile goes further but still dies from an error.  Perhaps you can help with that.

Attached is the patch to gcc-4.4.4.tar.bz2.  Apply after the rockbox patch.

---

### Post by Ad1217 on 2011-01-23
When and how should I apply this? Should I add it to the script?

---

### Post by Ad1217 on 2011-01-25
I tried adding it to the script (and probably did it completely wrong)... it did not work.

---

### Post by gmargo on 2011-01-26
You can't use the script as written. It handles only a single patch per package. You have to compile manually.

Use the script to compile the binutils package.  Here are the basic steps for compiling gcc manually:
```

$ mkdir rbdev-build
$ cd rbdev-build
$ tar xjf ../rbdev-dl/gcc-4.4.4.tar.bz2
$ cd gcc-4.4.4
$ patch -p1 < ../../rbdev-dl/rockbox-multilibs-noexceptions-arm-elf-eabi-gcc-4.4.2_1.diff
$ tar xjf ../../rbdev-dl/gmp-4.3.2.tar.bz2 
$ ln -s gmp-4.3.2 gmp
$ tar xjf ../../rbdev-dl/mpfr-2.4.2.tar.bz2 
$ ln -s mpfr-2.4.2 mpfr

# At this point the gcc-4.4.4 directory is patched as the script does it.
# You could make a copy of it now to avoid repeating the above.

# Apply experimental ada patch:
$ patch -p1 < ../../rbdev-dl/ada-patch1.diff

# Create build directory
$ mkdir ../build-gcc
$ cd ../build-gcc

# Ready to configure (substitute your preferred prefix):
$ CFLAGS=-U_FORTIFY_SOURCE ../gcc-4.4.4/configure --target=arm-elf-eabi --prefix=/usr/local --enable-languages=c,ada --disable-libssp --disable-docs

# Ready to compile:
$ make

```

---

### Post by Ad1217 on 2011-01-26
In the "ready to configure" bit, should I add "--enable-languages=ada"?

---

### Post by gmargo on 2011-01-27
> **Ad1217 said:**
> In the "ready to configure" bit, should I add "--enable-languages=ada"?

It has a complete command line there - be sure to scroll sideways.

Here is the configure command again, but without CODE tags so that it wraps:

CFLAGS=-U_FORTIFY_SOURCE ../gcc-4.4.4/configure --target=arm-elf-eabi --prefix=/usr/local --enable-languages=c,ada --disable-libssp --disable-docs

---

### Post by Ad1217 on 2011-01-27
oh... sorry, didn't see that. How should I > Use the script to compile the binutils package  without having it compile gcc?

---

