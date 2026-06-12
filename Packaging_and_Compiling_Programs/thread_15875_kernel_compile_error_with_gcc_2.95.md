---
title: "kernel compile error with gcc 2.95"
date: 2005-02-17
forum: Packaging and Compiling Programs
---

### Post by mondave on 2005-02-17
Hi,

    I'm getting a compile failure when I try to compile the kernel with gcc 2.95 .  With gcc 3.3.4 things work fine.

Here's the commands that I am using to do the build:

apt-get install linux-source-2.6.8.1
tar xvfj linux-source-2.6.8.1.tar.bz2
cd linux-source-2.6.8.1
cp /boot/config-2.6.8.1-3-686 .config
make-kpkg clean
MAKEFLAGS="CC=gcc-2.95" make-kpkg --initrd --append-to-version=-e kernel_image


With these commands, I eventually get the following compile error:

  CC [M]  drivers/isdn/hardware/mISDN/layer2.o
  CC [M]  drivers/isdn/hardware/mISDN/tei.o
  CC [M]  drivers/isdn/hardware/mISDN/x25_dte.o
  CC [M]  drivers/isdn/hardware/mISDN/x25_l3.o
  CC [M]  drivers/isdn/hardware/mISDN/sedl_fax.o
  CC [M]  drivers/isdn/hardware/mISDN/isar.o
drivers/isdn/hardware/mISDN/isar.c: In function `isar_down':
drivers/isdn/hardware/mISDN/isar.c:1655: parse error before `)'
make[5]: *** [drivers/isdn/hardware/mISDN/isar.o] Error 1
make[4]: *** [drivers/isdn/hardware/mISDN] Error 2
make[3]: *** [drivers/isdn/hardware] Error 2
make[2]: *** [drivers/isdn] Error 2
make[1]: *** [drivers] Error 2


If I start over, but change the compiler version as follows :

make-kpkg --initrd --append-to-version=-g kernel_image

Then I get no errors.


I'm not sure if this is a problem or not.  The linux source documentation says to use gcc 2.95.X ( X >= 3 ) but I see lots of comments that indicate that gcc 3.3 or higher should work as well.

My questions are:

What are the risks/concerns of using gcc 3.3 ( or other ) compiler?
What am I doing wrong that causes me to run into this compile error?


Thanks

- Dave


Here is the output from gcc -v and gcc-2.95 -v :


Reading specs from /usr/lib/gcc-lib/i486-linux/3.3.4/specs
Configured with: ../src/configure -v --enable-languages=c,c++,java,f77,pascal,objc,ada,treelang --prefix=/usr --mandir=/usr/share/man --infodir=/usr/share/info --with-gxx-include-dir=/usr/include/c++/3.3 --enable-shared --with-system-zlib --enable-nls --without-included-gettext --enable-__cxa_atexit --enable-clocale=gnu --enable-debug --enable-java-gc=boehm --enable-java-awt=xlib --enable-objc-gc i486-linux
Thread model: posix
gcc version 3.3.4 (Debian 1:3.3.4-9ubuntu5)

root@ruby:/usr/src # gcc-2.95 -v
Reading specs from /usr/lib/gcc-lib/i386-linux/2.95.4/specs
gcc version 2.95.4 20011002 (Debian prerelease)

---

### Post by az on 2005-03-08
Isn't it that you should use gcc >2.95?

Is there a reason to use a version of gcc any older than the current one?  Your distribution kernel was compiled with that, so if you want binary compatibility, you need gcc 3.3 (or whatever Hoary is using)

---

### Post by mondave on 2005-03-16
Thank you for responding.

[B]
Isn't it that you should use gcc >2.95?[/B]

I'm using 2.95 because the kernel documentation says to do so.

This is from the file Documentation/Changes that is included as part of the kernel source:

[I]The recommended compiler for the kernel is gcc 2.95.x (x >= 3), and it
should be used when you need absolute stability. You may use gcc 3.0.x
instead if you wish, although it may cause problems. Later versions of gcc
have not received much testing for Linux kernel compilation, and there are
almost certainly bugs (mainly, but not exclusively, in the kernel) that
will need to be fixed in order to use these compilers. [/I]


**Is there a reason to use a version of gcc any older than the current one? Your distribution kernel was compiled with that, so if you want binary compatibility, you need gcc 3.3 (or whatever Hoary is using)**

How do you know which gcc the kernel was compiled with?  Having seen the above note in the Docuementation/Changes file, my guess has been that the distribution kernel was compiled with the "recommended compiler" (i.e. 2.95).  I've always wondered if there's a way to positively confirm this.  

If my distribution ( warty ) kernel was compiled with gcc 3.3, then I don't mind using it to compile my own kernel.  It would be nice to know for sure that this is the case and also to know why the recommendation in "Documentation/Changes" is not being followed.

Please correct me if I'm wrong but regarding binary compatibility, there should be no problem  as long as the *entire* kernel ( including kernel modules ) is compiled with the same compiler and header files ( 2.95,  3.3, whatever ).    User space applications should not need to be compiled with the same gcc as the kernel ( again, let me know if I'm wrong ).

- Dave

---

### Post by hans yperman on 2005-03-21
You can see the gcc version for the running kernel with:

cat /proc/version

For me on a hoary system, this says:

hans@bruudruuster:~ $ cat /proc/version
Linux version 2.6.8.1-3-386 (buildd@terranova) (gcc version 3.3.4 (Debian 1:3.3.4-9ubuntu5)) #1 Tue Oct 12 12:41:57 BST 2004

---

### Post by az on 2005-03-21
"Please correct me if I'm wrong but regarding binary compatibility, there should be no problem as long as the *entire* kernel ( including kernel modules ) is compiled with the same compiler and header files ( 2.95, 3.3, whatever ). User space applications should not need to be compiled with the same gcc as the kernel ( again, let me know if I'm wrong )."

Yes, and yes (meaning correct).

---

