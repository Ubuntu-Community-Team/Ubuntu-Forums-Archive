---
title: "headerfiles_link problem"
date: 2012-05-24
forum: New to Ubuntu
---

### Post by BHASI123 on 2012-05-24
Am having problem with header files.I am not able to understand from where i can get the header files required


I got the following message while trying to compile a cd eject driver.


In file included from /usr/lib/gcc/i686-linux-gnu/4.6.1/include/asm-generic/fcntl.h:4:0,
                 from /usr/lib/gcc/i686-linux-gnu/4.6.1/include/asm/fcntl.h:56,
                 from /usr/lib/gcc/i686-linux-gnu/4.6.1/include/linux/fcntl.h:4,
                 from eject.c:2:
/usr/lib/gcc/i686-linux-gnu/4.6.1/include/linux/types.h:13:2: warning: #warning "Attempt to use kernel headers from user space, see http://kernelnewbies.org/KernelHeaders" [-Wcpp]


How to fix this problem?.

If not user space,from where I have to include the header files.What is the procedure??

Please reply back with complete manual for header file installation 

And also tell me whether I require it to be copied to /usr/include?

If not explain how to handle it so that the program will work without having any problems of header files


I am a beginner to ubuntu.so reply me back with a beginners point of view

---

### Post by anewguy on 2012-05-24
Have you installed the build-essential package?  Have you installed the linux-headers (should be by kernel version, something like "linux-headers-3.2.0-24.38) package?  You can install these right from the package manager.

Dave ;)

---

