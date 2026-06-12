---
title: "gcc in makefile with pkg-config doesn't pickup PKG_CONFIG_PATH"
date: 2010-10-27
forum: Packaging and Compiling Programs
---

### Post by macropanther on 2010-10-27
[SIZE=3]Hello,

I am trying to cross compile (for the TI dm365 ARM processor)  a gstreamer program (not gstreamer itself, a program that uses it) on 10.04 using a make file.  

I am running on [/SIZE][SIZE=3]Ubuntu [/SIZE][SIZE=3]10.04 with CodeSourcery toolchain for dm365 located in /opt/arm-2009q1 and included in $PATH.

If I 

[COLOR=Blue]```
export PKG_CONFIG_PATH /home/wmiller/workdir/filesys/opt/gstreamer/lib/pkgconfig
```[/COLOR]

[/SIZE][SIZE=4][SIZE=3](points to the ARM pkg-config files) and issue this make command

[/SIZE][/SIZE][SIZE=3][COLOR=Blue]```
 arm-none-linux-gnueabi-gcc `pkg-config --cflags --libs gstreamer-0.10` gst1.c -o gst1
```[/COLOR][/SIZE][SIZE=4][SIZE=3]

I get [FONT=Courier New][COLOR=Blue]gst1[/COLOR][/FONT] as a binary file.  (Won't execute, but we'll talk about that next post).

Now, if I put my make command into a makefile

[/SIZE][/SIZE][SIZE=3][COLOR=Blue]```
gst1: gst1.c
    arm-none-linux-gnueabi-gcc `pkg-config --cflags --libs gstreamer-0.10`  gst1.c -o gst1
```[/COLOR][/SIZE][SIZE=4][SIZE=3]

and execute [/SIZE][SIZE=3][COLOR=Blue]make[/COLOR][/SIZE][SIZE=3], I get these errors.
[COLOR=Blue]
[/COLOR] [/SIZE][/SIZE][SIZE=3][COLOR=Blue]```

arm-none-linux-gnueabi-gcc `pkg-config --cflags --libs gstreamer-0.10` \
    gst1.c -o gst1
cc1: warning: include location "/usr/include/gstreamer-0.10" is unsafe for cross-compilation
cc1: warning: include location "/usr/include/glib-2.0" is unsafe for cross-compilation
cc1: warning: include location "/usr/include/libxml2" is unsafe for cross-compilation
/opt/arm-2009q1/bin/../lib/gcc/arm-none-linux-gnueabi/4.3.3/../../../../arm-none-linux-gnueabi/bin/ld: cannot find -lgstreamer-0.10
collect2: ld returned 1 exit status
make: *** [gst1] Error 1

```[/COLOR][/SIZE][SIZE=3][COLOR=Blue]
[/COLOR][/SIZE][SIZE=4]
that indicate to me that the make command inside the makefile is completely ignoring the PKG_CONFIG_PATH environment variable.  Yes, I've checked,  It IS set in the environment before I execute[COLOR=Blue] make[/COLOR].

Anyone know why it doesn't work inside the makefile?  And, while we're at it, any ideas why, when it does work from the command line, why the resulting gst1 won't execute?

[/SIZE][SIZE=3][COLOR=Blue]```
$ ./gst1
bash: ./gst1: cannot execute binary file
```[/COLOR][/SIZE][SIZE=4]

Any help will be greatly appreciated,

Wes

[/SIZE]

---

### Post by macropanther on 2010-10-27
:redface:   Well, I get the egg on the face award for my second question.

Of course it won't run under Ubuntu.  It's compiled for ARM-5.  

Duh.

Wes

---

