---
title: "Error in compiling kernel in ubuntu 8.0.4.2!!!"
date: 2009-03-24
forum: Packaging and Compiling Programs
---

### Post by brian1125 on 2009-03-24
hello everybody~
when i use the website method "http://www.howtoforge.com/kernel_compilation_ubuntu", i met a error at build the kernel
as follow:

...
...
/usr/src/linux-2.6.20.21/net/ipv4/af_inet.c:1217: undefined reference to `cpu_possible_map'
net/built-in.o:/usr/src/linux-2.6.20.21/net/ipv4/af_inet.c:1218: more undefined references to `cpu_possible_map' follow
make[1]: *** [.tmp_vmlinux1] Error 1
make[1]: Leaving directory `/usr/src/linux-2.6.20.21'
make: *** [debian/stamp-build-kernel] Error 2
 
(This matter occurs when I add a new system call follow by [http://www.cmpe.boun.edu.tr/courses/cmpe322/fall2008/Tutorials/Kernel%20Compile%20and%20SysCall%20Add%20(Ubuntu%208.04).pdf](http://www.cmpe.boun.edu.tr/courses/cmpe322/fall2008/Tutorials/Kernel%20Compile%20and%20SysCall%20Add%20(Ubuntu%208.04).pdf))


I don't know why can not make the .deb files.
If you know why is what
tell me please.

---

### Post by VMC on 2009-03-25
I'm assuming you installed all the tools. Did it failed on step #6?

---

