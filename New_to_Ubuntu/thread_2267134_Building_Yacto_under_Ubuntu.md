---
title: "Building Yacto under Ubuntu"
date: 2015-02-27
forum: New to Ubuntu
---

### Post by Elli_Kahn on 2015-02-27
Dear All,
I am new to ubentu and linux, would like to increase my knowledge about linux in general. I am building a test image by using yacto, it seems that i run in build failure after while
the following message come: Install SDL development, needed,  can you please guide me how to address the following error, I downloaded many pacjages to address the SDL issue
but sometime messages come as some packages are held.
Please provide direction, thanks

k/i686-linux/qemu-native/2.1.0-r0/temp/log.do_configure.24568)
ERROR: Logfile of failure stored in: /poky/build/tmp/work/i686-linux/qemu-native/2.1.0-r0/temp/log.do_configure.24568
Log data follows:
| DEBUG: Executing python function sysroot_cleansstate
| DEBUG: Python function sysroot_cleansstate finished
| DEBUG: Executing shell function autotools_preconfigure
| DEBUG: Shell function autotools_preconfigure finished
| DEBUG: Executing python function autotools_copy_aclocals
| DEBUG: Python function autotools_copy_aclocals finished
| DEBUG: Executing shell function do_configure
| 
| ERROR: User requested feature sdl
|        configure was not able to find it.
|        Install SDL devel
|

---

### Post by ajgreeny on 2015-02-27
I have no idea what **yacto** is, nor what it's used for, but it is very likely if you are having trouble compiling, building and making for installation that you need the package **build-essential** which adds many of the compiling/building packages that are needed but missing from a default Ubuntu installation.

---

### Post by tgalati4 on 2015-02-27
Welcome to the forums.

[Yocto]("https://www.yoctoproject.org/") is an embedded linux environment.  What tutorial did you follow?

Some necessary packages required:  [http://www.yoctoproject.org/docs/1.7.1/ref-manual/ref-manual.html#detailed-supported-distros](http://www.yoctoproject.org/docs/1.7.1/ref-manual/ref-manual.html#detailed-supported-distros)

10.5 hours youtube video of SCaLE13X embedded linux session including yocto history and build setup:  [https://www.youtube.com/watch?v=rzKI0ASB_Js](https://www.youtube.com/watch?v=rzKI0ASB_Js)

---

