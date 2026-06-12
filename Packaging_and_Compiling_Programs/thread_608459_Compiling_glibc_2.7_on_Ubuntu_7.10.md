---
title: "Compiling glibc 2.7 on Ubuntu 7.10"
date: 2007-11-10
forum: Packaging and Compiling Programs
---

### Post by sriram.venkataramani on 2007-11-10
I'm trying to compile glibc 2.7 on Ubuntu 7.10 (Kernel Version 2.6.22-14). So here's what I've done till now -

1. Downloaded and extracted the glibc source from [http://ftp.gnu.org/pub/gnu/glibc/glibc-2.7.tar.gz](http://ftp.gnu.org/pub/gnu/glibc/glibc-2.7.tar.gz)
2. Made a separate glibc-build directory from which I did a configure. 

../libidn/configure --prefix=/usr     --disable-profile --enable-add-ons     --enable-kernel=2.6.22 --libexecdir=/usr/lib/glibc

3, This generated the Makefile and I did a make at which point it fails with the following error.

/home/vsriram/Desktop/glibc-build/elf/librtld.os: In function `print_statistics':
/home/vsriram/Desktop/libidn/elf/rtld.c:2800: undefined reference to `__stack_chk_fail_local'
/home/vsriram/Desktop/glibc-build/elf/librtld.os: In function `process_dl_debug':
/home/vsriram/Desktop/libidn/elf/rtld.c:2436: undefined reference to `__stack_chk_fail_local'
/home/vsriram/Desktop/glibc-build/elf/librtld.os: In function `process_envvars':
/home/vsriram/Desktop/libidn/elf/rtld.c:2695: undefined reference to `__stack_chk_fail_local'
/home/vsriram/Desktop/glibc-build/elf/librtld.os: In function `dl_main':
/home/vsriram/Desktop/libidn/elf/rtld.c:2316: undefined reference to `__stack_chk_fail_local'
/home/vsriram/Desktop/glibc-build/elf/librtld.os: In function `print_search_path':
/home/vsriram/Desktop/libidn/elf/dl-load.c:1567: undefined reference to `__stack_chk_fail_local'
/home/vsriram/Desktop/glibc-build/elf/librtld.os:/home/vsriram/Desktop/libidn/elf/dl-load.c:1787: more undefined references to `__stack_chk_fail_local' follow
collect2: ld returned 1 exit status
make[2]: *** [/home/vsriram/Desktop/glibc-build/elf/ld.so] Error 1
make[2]: Leaving directory `/home/vsriram/Desktop/libidn/elf'
make[1]: *** [elf/subdir_lib] Error 2
make[1]: Leaving directory `/home/vsriram/Desktop/libidn'
make: *** [all] Error 2

Now I googled "__stack_chk_fail_local" and found that it had to with the stack protection that Ubuntu provides and it can be disabled by setting the CFLAGS with -fno-stack-protector. Now I did this using  export CFLAGS=" -fno-stack-protector -fno-stack-protector-all" and that still gives me the above error.

Couple of notable things:

a. I set the CFLAGS to  export " -fno-stack-protector -fno-stack-protector-all" before doing the ./configure and I get the following error:

checking whether ln -s works... yes
checking for gcc... gcc
[B]checking for suffix of object files... configure: error: cannot compute suffix of object files: cannot compile
[/B]See `config.log' for more details.

If I unset CFLAGS configure works fine again.

b. I tried compiling glibc 2.6.1 and get the exact same error. 

What is going on? How can I fix this?

Thanks!

---

### Post by mlind on 2007-11-10
why exactly you want to compile newer glibc?

---

### Post by sriram.venkataramani on 2007-11-10
I am working on this checkpointing software and it fails only in Ubuntu (6.10+). I believe it is a problem with whatever changes Ubuntu people might have made to glibc and want to compile a vanilla glibc and check if the checkpointing software works using the same.

---

### Post by elmasto on 2008-03-06
I am getting the same error. Any ideas? Thanks.

---

### Post by Partyboi2 on 2008-04-29
> **elmasto said:**
> I am getting the same error. Any ideas? Thanks.
Did you find a way around this error? I have run into the same problem.

---

### Post by khalidsafwat on 2008-06-02
what gcc version are you using ?

---

### Post by Partyboi2 on 2008-06-02
I was using glibc 2.5 but I have got it compiled successfully now. Thanks

---

### Post by rahuldhur on 2008-06-17
Hello venkat.....

could you please tell me how u resolved ur problem.....
..
Thanks in advance....

---

### Post by sriram.venkataramani on 2008-07-24
We did get a solution to this problem. The issue was with the Stack Smashing protection that Ubuntu's glibc has. We fixed the issue by adding -fno-stack-protection in the Makefile. A more detailed solution is available [here]("https://wiki.ccs.neu.edu/display/CSG280/MTCP+on+Ubuntu") and [here]("http://perilsofdecadence.blogspot.com/2008/07/glibc-on-ubuntu.html").

---

### Post by StoneSledge on 2008-07-25
Hi Sriram, thanks for the input. I've managed to extract the build params they used for building glibc-2.7 for the Hardy release, see [COLOR="Blue"]**[http://ubuntuforums.org/showthread.php?t=867674](http://ubuntuforums.org/showthread.php?t=867674)**.[/COLOR]
--

Regards,
Lars.

---

### Post by dougalg on 2011-02-17
I've run into the same problem. I tried adding

```
export CFLAGS="-fno-stack-protection"
```

in the makefile but it doesn't help. I am still getting the stack_chk_fail_local error.

Any ideas what might be causing this?

---

