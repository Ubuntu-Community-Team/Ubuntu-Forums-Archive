---
title: "g++/gcc errors"
date: 2009-10-21
forum: Programming Talk
---

### Post by henkgeb on 2009-10-21
hi,
 
I'm trying to intall my new x-fi xtreme audio soundcard on my ubuntu studio 64 machine.
While compiling, I got some errors like error 1, error 2 and ´size of array ‘type name’ is negative¨. I've already installed all source files of gcc and g++, but it doesn't matter. I compile it exactly the way described in the readme file.
I get the following output:
 
henk@henk-desktop:~/Bureaublad/XFiDrv_Linux_Public_US_1.00$ sudo make
[sudo] password for henk:
make -C /lib/modules/2.6.24-24-rt/build M=/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-24-rt'
  LD      /home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/built-in.o
  CC [M]  /home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/xfi.o
  CC [M]  /home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctatc.o
  CC [M]  /home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctvmem.o
  CC [M]  /home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctpcm.o
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctpcm.c: In function ‘ct_alsa_pcm_create’:
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctpcm.c:462: warning: passing argument 2 of ‘snd_pcm_new’ discards qualifiers from pointer target type
  CC [M]  /home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctmixer.o
  CC [M]  /home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctresource.o
  CC [M]  /home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.o
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function ‘put_src_rsc’:
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.c:569: error: size of array ‘type name’ is negative
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.c:569: warning: comparison of distinct pointer types lacks a cast
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.c:576: error: size of array ‘type name’ is negative
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.c:576: warning: comparison of distinct pointer types lacks a cast
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function ‘put_srcimp_rsc’:
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.c:883: error: size of array ‘type name’ is negative
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.c:883: warning: comparison of distinct pointer types lacks a cast
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.c:887: error: size of array ‘type name’ is negative
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.c:887: warning: comparison of distinct pointer types lacks a cast
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function ‘srcimp_imap_add’:
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.c:916: error: size of array ‘type name’ is negative
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.c:916: warning: comparison of distinct pointer types lacks a cast
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.c:922: error: size of array ‘type name’ is negative
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.c:922: warning: comparison of distinct pointer types lacks a cast
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function ‘srcimp_imap_delete’:
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.c:936: error: size of array ‘type name’ is negative
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.c:936: warning: comparison of distinct pointer types lacks a cast
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.c:942: error: size of array ‘type name’ is negative
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.c:942: warning: comparison of distinct pointer types lacks a cast
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function ‘srcimp_mgr_destroy’:
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.c:1004: error: size of array ‘type name’ is negative
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.c:1004: warning: comparison of distinct pointer types lacks a cast
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.c:1006: error: size of array ‘type name’ is negative
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.c:1006: warning: comparison of distinct pointer types lacks a cast
make[2]: *** [/home/william/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.o] Error 1
make[1]: *** [_module_/home/william/Bureaublad/XFiDrv_Linux_Public_US_1.00] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-24-rt'
make: *** [all] Error 2
henk@henk-desktop:~/Bureaublad/XFiDrv_Linux_Public_US_1.00$
 
Who can tell me what I'm doing wrong? help me, please...
thanks for reading.
 
edit:
my specs: amd athlon x2 4050e,
ubuntu studio 8.04, kernel 2.6.24-24-rt, GNOME 2.22.3

---

### Post by henkgeb on 2009-10-24
nobody? Other files made by myselve won't compile.too.

---

### Post by MadCow108 on 2009-10-24
seems like a problem in the programs source (if you followed the instructions correctly, and ubuntu is a supported platform)
ask the developers of that program whats wrong.

---

### Post by kavon89 on 2009-10-24
Make sure you have build-essential installed. Other than that I think it's a problem with their code.

---

### Post by dwhitney67 on 2009-10-24
> **kavon89 said:**
> Make sure you have build-essential installed. Other than that I think it's a problem with their code.

I second this opinion; it looks like incompatible code for the current version of GCC that you are using.  I've seen similar types of errors with code that I was able to compile under Ubuntu 7.10, but not with later versions.  The version of Ubuntu is not really relevant, but the version of GCC that ships with it is.

Btw, not that it matters significantly, but when you compile a kernel module, you do not need to use 'sudo'.  Only use 'sudo' when you need to install the .ko file in its proper place.

---

### Post by henkgeb on 2009-10-25
all the build essentials are installed. I tried it with other source files too, but received the same errors like I posted.

I have also tried all versions available in the synaptic package manager, but it doesn't make sence. The latest version is 4.2, but the older versions are still installed. Maybe that's the problem?

thanks a lot for the replies.

edit: I've removed the older versions of gcc, and only 4.2 remains. tried again, but no differences.

edit2: also geany won't do the job. seems like a bug or something?

---

### Post by henkgeb on 2009-10-29
all the build essentials are installed. I tried it with other source files too, but received the same errors like I posted.

I have also tried all versions available in the synaptic package manager, but it doesn't make sence. The latest version is 4.2, but the older versions are still installed. Maybe that's the problem?

thanks a lot for the replies.

edit: I've removed the older versions of gcc, and only 4.2 remains. tried again, but no differences.

edit2: also geany won't do the job. seems like a bug or something?

---

### Post by henkgeb on 2009-11-06
help

---

### Post by MadCow108 on 2009-11-06
nobody can help you here
ask the developers

---

### Post by henkgeb on 2009-11-11
I don't think it is an error in the source file. I've tried other source files too, also made by myself, and then I get the same errors. So there is something wrong with gcc of ubuntu I think.

---

### Post by dwhitney67 on 2009-11-11
> **henkgeb said:**
> I don't think it is an error in the source file. I've tried other source files too, also made by myself, and then I get the same errors. So there is something wrong with gcc of ubuntu I think.

Try this program...
```

#include <stdio.h>
int main() {printf("hello world\n");}

```
Report back whether you can compile it using:
```

gcc hello.c

```

---

### Post by MadCow108 on 2009-11-11
> **henkgeb said:**
> I don't think it is an error in the source file. I've tried other source files too, also made by myself, and then I get the same errors. So there is something wrong with gcc of ubuntu I think.

this is very unlikely.
gcc is used by millions of people and  if bugs appear then almost always in very unusual circumstances.
But you can check the known bugs of gcc to see if you find something. I doubt you found a new one.
[http://gcc.gnu.org/bugs/](http://gcc.gnu.org/bugs/)
**but doing this is certainly a waste of time**, I bet you the code (or the instructions to compile) is the problem.

maybe the program just wasn't written for gcc and uses non standard stuff not supported by gcc(aka non-portable)
in that case use the compiler it was written for.

---

### Post by henkgeb on 2009-12-17
sorry for my late reaction. I've upgraded my system to ubuntu 8.10 and the source of dwhitney67 works... thanks dwhitney67!!! So I was hopefull and tried to compile the driver also. And it worked perfect!!! It was the first programme i've compiled since I work with ubuntu. My sound card works very well and I want to thank you all guys. You are great and you're the best community ever!!

If there are other people with this problem, the only thing I did change to make it work was upgrading my OS. The sourcefiles I used before were all OK, but they didn't compile. I dunno why. 

thanks thanks thanks. you're great!!!

---

