---
title: "Error compiling kernel 2.6.12 on my Ubuntu 7.04"
date: 2007-07-26
forum: Programming Talk
---

### Post by wayanwolvie on 2007-07-26
Hi everyone,

I got a problem while compiling kernel for my Ubuntu 7.04. For some reasons, I need to use kernel 2.6.12. I followed instructions from this website [http://www.howtoforge.com/kernel_compilation_ubuntu]("http://www.howtoforge.com/kernel_compilation_ubuntu").
But when I did the step 5 and run > make menuconfig I always get errors. Here is the error message
>  HOSTCC  scripts/basic/fixdep
In file included from /usr/include/bits/posix1_lim.h:153,
                 from /usr/include/limits.h:145,
                 from /usr/lib/gcc-lib/i486-linux-gnu/3.3.6/include/limits.h:122,
                 from /usr/lib/gcc-lib/i486-linux-gnu/3.3.6/include/syslimits.h:7,
                 from /usr/lib/gcc-lib/i486-linux-gnu/3.3.6/include/limits.h:11,
                 from scripts/basic/fixdep.c:113:
/usr/include/bits/local_lim.h:36:26: linux/limits.h: No such file or directory
scripts/basic/fixdep.c: In function `use_config':
scripts/basic/fixdep.c:201: error: `PATH_MAX' undeclared (first use in this function)
scripts/basic/fixdep.c:201: error: (Each undeclared identifier is reported only once
scripts/basic/fixdep.c:201: error: for each function it appears in.)
scripts/basic/fixdep.c:201: warning: unused variable `s'
scripts/basic/fixdep.c: In function `parse_dep_file':
scripts/basic/fixdep.c:297: error: `PATH_MAX' undeclared (first use in this function)
scripts/basic/fixdep.c:297: warning: unused variable `s'
make[1]: *** [scripts/basic/fixdep] Error 1
make: *** [scripts_basic] Error 2

This error doesn't appear when I compile kernel 2.6.18 and above.

What's wrong with this? Anything I can do to solve the problem? Do I must change the Ubuntu to the lower version?

---

### Post by slavik on 2007-07-26
looks like you are missing a file ...

---

### Post by wayanwolvie on 2007-07-26
You mean "linux/limits.h" ? I have check it  and the file is present in /usr/src/linux/include/ .
That's why I'm confused

---

### Post by the_unforgiven on 2007-07-26
> **wayanwolvie said:**
> You mean "linux/limits.h" ? I have check it  and the file is present in /usr/src/linux/include/ .
That's why I'm confused
I guess, you have extracted your kernel source tarball in /usr/src/linux.
If that's the case then /usr/src/linux/include/linux/limits.h is a kernel space header; whereas, IIRC, what the fixdep.c code is looking for is a user-space header.
You need to install the [linux-libc-dev]("http://packages.ubuntu.com/feisty/devel/linux-libc-dev") package. Check out the file list of the package from the link.
HTH ;)

---

### Post by wayanwolvie on 2007-07-26
Hi,
I have checked with Synaptic and linux-libc-dev already present in my system. But I still get the same error messages :confused:

---

### Post by Tex-Twil on 2008-06-13
Hello,
it's kinda old topic here but I reopen it cos I have the same problem. Not while compiling a kernel though but yet I have this error msg. I do have also **linux-libc-dev** installed.

Did you solved this issue ?

Regards,
Tex

---

### Post by Joeb454 on 2008-06-13
If the issue was solved, it would say so in the thread title.

May I suggest creating a new thread in the support area's about this issue, as it is unrelated to the original post :)

---

### Post by PmDematagoda on 2008-06-13
This thread is closed.

---

