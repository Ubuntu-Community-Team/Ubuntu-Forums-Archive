---
title: "How to add .o file in the Linux Kernel"
date: 2012-07-16
forum: Programming Talk
---

### Post by geewhan on 2012-07-16
I would like to know how would you enable the Congestion Control Algorithm correctly (lets call it Tcp_quic or quic).

My code is almost exactly like the tcp_veno.c file. Just the algorithm in the tcp_veno_cong_avoid() function changed.
I would like to attached the code on here, but I got an upload error. I would post it as well, but it is pretty long.

I have successfully compile the Linux Kernel with the C file (in the directory linux-3.4-rc7\net\ipv4\tcp_quic.c)
I just need to enable it, so I can use my algorithm and add it to the Kernel. 

I realize that in the Linux Kernel folder(kernel\linux-3.3.6\net\ipv4), where I added the tcp_quic.c file, does not have .mod.o or .o file. With means that the tcp_quic.c did not compile successfully, right? However why did the compile in the terminal compile successfully? I read on one forum that may be I need to change something in the MAKEFILE to have .o file, is this true? I am not sure how I would do this if it is so.

I know that most people said that you should not mess with the Kernel, but it is something I would like to try.

The code below is how I want to enable the Congestion Control Algorithm.

```
echo quic > /proc/sys/net/ipv4/tcp_congestion_control
```

Also this is how I compile the Linux Kernel:

```
make-kpkg clean

fakeroot make-kpkg --initrd --append-to-version=-geekernel kernel_image kernel_headers
(this takes about 2 hours to compile)
```

---

### Post by the_unforgiven on 2012-07-17
Yes, you'd need to modify the Makefile in net/ipv4/.
In there, just look for tcp_veno.o - how it's getting used.

More precisely, check these:
[http://lxr.linux.no/linux+*/net/ipv4/Makefile#L46](http://lxr.linux.no/linux+*/net/ipv4/Makefile#L46)
[http://lxr.linux.no/linux+*/net/ipv4/Kconfig#L530](http://lxr.linux.no/linux+*/net/ipv4/Kconfig#L530)

You'd need to add something similar for your files.
If you want to compile it as a module, use the following command while compiling the kernel:
```

fakeroot CONFIG_TCP_CONG_WHATEVER=m make-kpkg --initrd --append-to-version=-geekernel kernel_image kernel_headers
```
where you add the following line in the Makefile:
```
obj-$(CONFIG_TCP_CONG_WHATEVER) += tcp_<your_file>.o
```

---

### Post by geewhan on 2012-07-17
the_unforgiven,

Thank you for the reply.

So far I have done that steps on editing the MAKEFILE and the Kconfig file. Where I see veno, I copy and paste another line(s) of code and replace it with the word "quic".
What I put in the MAKEFILE is
```
obj-$(CONFIG_TCP_CONG_QUIC) += tcp_quic.o
```

What I put in the Kconfig file is:
(there is a lot of editing in this one I wont list them because I basically search for "vegas/veno" to copy and paste a new one for "quic"


I did get an error when I try using the code you have recommended, but I got an Error

```
fakeroot CONFIG_TCP_CONG_QUIC=m make-kpkg --initrd --append-to-version=-geekernel kernel_image kernel_headers
```

This is the error

> /usr/bin/fakeroot: line 176: CONFIG_TCP_QUIC=m: command not found

Here is the code in the fakeroot file around line 176:

```
export FAKEROOT_FD_BASE

if test -z "$*"; then
  FAKEROOTKEY=$FAKEROOTKEY LD_LIBRARY_PATH="$PATHS"  LD_PRELOAD="$LIB" ${SHELL:-/bin/sh}
  RESULT=$?
else
(LINE 176)  FAKEROOTKEY=$FAKEROOTKEY LD_LIBRARY_PATH="$PATHS"  LD_PRELOAD="$LIB" "$@"
  RESULT=$?
fi

exit $RESULT
```

Did I miss something when I edit in the MAKEFILE or Kconfig file?

Thanks

---

### Post by the_unforgiven on 2012-07-18
OK, I guess, fakeroot is trying to interpret "CONFIG_TCP_CONG_QUIC=.." as a command - which is wrong.

Instead, what you could do is edit the .config file.
At the end of kernel configuration, "make (x|menu|whatever)config" generates a .config file which is built using all the Kconfig segments.

You can simply edit .config and add CONFIG_TC_CONG_QUIC=m to it. Then reconfigure using "make oldconfig" and then build the kernel using your regular "make-kpkg ..." command.

HTH ;)

---

### Post by geewhan on 2012-07-19
the_unforgiven,

I believe what you wrote is really important, but I am having a hard time understanding or locating the files that you recommended. 

When you mean the .config file are you referring to kconfig file?
I ask because I do not know what you mean by here.
> At the end of kernel configuration, "make (x|menu|whatever)config" generates a .config file which is built using all the Kconfig segments.


When you mention this part:
> You can simply edit .config and add CONFIG_TCP_CONG_QUIC=m to it. Then reconfigure using "make oldconfig" and then build the kernel using your regular "make-kpkg ..." command.

Are you talking about the kconfig file the lines around here

```
	config DEFAULT_CUBIC
		bool "Cubic" if TCP_CONG_CUBIC=y

	config DEFAULT_HTCP
		bool "Htcp" if TCP_CONG_HTCP=y

	config DEFAULT_HYBLA
		bool "Hybla" if TCP_CONG_HYBLA=y

	config DEFAULT_VEGAS
		bool "Vegas" if TCP_CONG_VEGAS=y
        config DEFAULT_VENO
		bool "Veno" if TCP_CONG_VENO=y

        config DEFAULT_QUIC
		bool "Quic" if TCP_CONG_QUIC=m
```

Thanks

---

### Post by the_unforgiven on 2012-07-24
What I meant was that before compiling the kernel, it needs to be configured for the type of system on which it will run - this is what the various "make config" commands do. For details, check this:
[http://lxr.linux.no/linux+*/README#L153](http://lxr.linux.no/linux+*/README#L153)

This is true for almost all operating system kernels - linux, *BSD, solaris (I don't know about Windows) - that you need to configure the kernel before compiling it.

During this configuration process, you decide what all features to include in the kernel - some of them can be built into the kernel binary, while others can be compiled as loadable kernel modules (drivers).

At the end of this configuration process, there is a .config file written in the same directory as README/MAINTAINERS files in the kernel sources - it's a simple text file that you can examine using any text editor.

This file is used during the compilation process to different options in various parts of the kernel - CONFIG_TCP_CONG_QUIC being one of them.
"CONFIG_*=m" says that it should be built as a module - whereas, "CONFIG_*=y" means that it should be built into the kernel binary directly.

Most modern linux distros include the configuration with which the kernel was built under /boot/config-<KERNEL_VERSION>. This can be quite helpful as a starting point.
You can just copy this file to .config in your kernel sources and edit it to your liking (for example, add "CONFIG_TCP_CONG_QUIC=m" in the .config file which is copied from /boot/config-<KERNEL_VERSION>).

make-kpkg tries to automate the kernel build process by bundling predefined configuration templates.

I've never used make-kpkg - so, don't know what should be the ideal way. But, ubuntu uses a similar process. In there, there is a directory debian.master/configs/ (or something similar) which stores the configuration templates.

I hope this helps in understanding the basics of kernel build process ;)

---

### Post by shraddhapatelganapat on 2012-11-29
how to add new congstion control like tcp_hybla.c in linux kernel...

step to recompile kernel
step to add new .c file and required changes in kernel...

---

