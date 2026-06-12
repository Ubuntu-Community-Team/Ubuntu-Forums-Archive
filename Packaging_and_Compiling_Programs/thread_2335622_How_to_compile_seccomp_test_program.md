---
title: "How to compile seccomp test program"
date: 2016-08-30
forum: Packaging and Compiling Programs
---

### Post by jongchen on 2016-08-30
I am running 16.04 LTS.

I am trying to compile the seccomp test program that is in the man page for seccomp.  The test program is at the bottom of the man page [http://man7.org/linux/man-pages/man2/seccomp.2.html](http://man7.org/linux/man-pages/man2/seccomp.2.html)

[URL="http://man7.org/linux/man-pages/man2/seccomp.2.html"]
[/URL]When I try to compile the program I get the following error message:

```
chen@consulting-VirtualBox:~/work/seccompTest$ gcc seccompTest.c 
seccompTest.c: In function ‘install_filter’:
seccompTest.c:65:7: warning: implicit declaration of function ‘seccomp’ [-Wimplicit-function-declaration]
   if (seccomp(SECCOMP_SET_MODE_FILTER, 0, &prog)) {
       ^
/tmp/cc5KwI6o.o: In function `install_filter':
seccompTest.c:(.text+0x108): undefined reference to `seccomp'
collect2: error: ld returned 1 exit status
```

If you go and look at the line it complains about it is in the function install_filter and we are trying to make a system call to secomp.

```
  if (seccomp(SECCOMP_SET_MODE_FILTER, 0, &prog)) {
    perror("seccomp");
    return 1;
  }

```

Looking at the error message there are several things going on here
[LIST=1]
[*]It looks like my paths are not setup properly and the compiler cannot find <linux/seccomp.h> 
[*]Due to the inability of finding the header the system call is not being properly made and the compiler thinks that seccomp is a function and not a system call. 
[/LIST]

I tried to fix this problem by downloading the kernel headers and modifying my build line to search for the headers properly.  But this just seems to make the problem worse

```

chen@consulting-VirtualBox:~/work/seccompTest$ gcc -I/usr/src/linux-headers-4.4.0-34/include seccompTest.c 
In file included from /usr/src/linux-headers-4.4.0-34/include/uapi/linux/capability.h:16:0,
                 from /usr/src/linux-headers-4.4.0-34/include/linux/capability.h:15,
                 from /usr/src/linux-headers-4.4.0-34/include/linux/sched.h:15,
                 from /usr/src/linux-headers-4.4.0-34/include/linux/audit.h:26,
                 from seccompTest.c:6:
/usr/src/linux-headers-4.4.0-34/include/linux/types.h:14:26: error: conflicting types for ‘fd_set’
 typedef __kernel_fd_set  fd_set;
                          ^
In file included from /usr/include/x86_64-linux-gnu/sys/types.h:219:0,
                 from /usr/include/stdlib.h:314,
                 from seccompTest.c:4:


```

I can verify that seccomp is installed in the kernel because I can run the program (listed here [https://outflux.net/teach-seccomp/autodetect.html](https://outflux.net/teach-seccomp/autodetect.html)) to detect the version of seccomp that is installed on my machine.

I'm pretty sure that I'm doing something silly wrong here.  Just need some pointers to where to look.

---

### Post by jongchen on 2016-09-02
TL;DR
There is no easy way to allow for this test program to work.

If you want to get into the bowels of Linux system programming here is the issue.

seccomp is a Linux system call.  In order to make a system call you have to use your processors system call instruction.  There is no standard C way to insert a system call instruction so you have to use assembly code.  Given that system calls can change its number between different kernels etc. needless to say this is quite annoying to have to implement different assembly code for each different kernel your software has to run on.  The glibc developers understands this and provides nice wrappers to some of the Linux system calls.  For example you don't have to write assembly wrappers to use the "open" Linux system call.  Unfortunately glibc does not provide wrappers for every possible system call.  seccomp is in the list of system calls without a wrapper.  This is a known issue and is discussed here [https://lwn.net/Articles/655028/](https://lwn.net/Articles/655028/).

Stuff that I have tried and did not work:
I installed (sudo apt-get install libseccomp-dev) and linked against it.  This did not appear to have the required wrapper and I still got undefined errors during link time.

So where does this leave us?

If we have to have this program work then we might have to change the call to seccomp to use the "syscall" C library function.  "syscall" allows you to make indirect system calls for system calls without direct C wrappers.

We can also call seccomp via the prtcl method [https://blog.yadutaf.fr/2014/05/29/introduction-to-seccomp-bpf-linux-syscall-filter/](https://blog.yadutaf.fr/2014/05/29/introduction-to-seccomp-bpf-linux-syscall-filter/)

What I'm really curious about is how the heck did the guys who wrote the seccomp man page get their program to work?

---

