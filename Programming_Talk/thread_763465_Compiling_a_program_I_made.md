---
title: "Compiling a program I made"
date: 2008-04-23
forum: Programming Talk
---

### Post by jsatubnutufroums on 2008-04-23
Hi,
I write a simple program:
```
#include <stdio.h>
#include <linux/init.h>
#include <linux/timer.h>

int main()
{
        return 0;
}
```
And I compile it by 'gcc -o test test.c' and get the error message:
```
test.c:2:24: error: linux/init.h: No such file or directory
test.c:3:25: error: linux/timer.h: No such file or directory
```
I already install linux-kernel-devel and linux-headers by the following instructions:
```
apt-get install linux-kernel-devel
apt-get install linux-headers-`uname-r'
```
Someone tells me to try to re-build a kernel module. I follow this article '[Kernel/Compile]("https://help.ubuntu.com/community/Kernel/Compile")'.
[LIST=1]
[*]sudo apt-get install linux-kernel-devel fakeroot build-essential
[*]sudo apt-get build-dep linux-source
[*]apt-get source linux-source
[*]sudo apt-get install linux-source
[*]mkdir ~/src
[*]cd ~/src
[*]tar xjvf /usr/src/linux-source-<version-number-here>.tar.bz2
[*]cd linux-source-<version-number-here>
[*]cp -vi /boot/config-`uname -r` .config
[*]sudo apt-get install qt3-dev-tools libqt3-mt-dev # if you plan to use 'make xconfig'
[*]sudo apt-get install libncurses5 # if you plan to use 'make menuconfig'
[*]make menuconfig # or "make xconfig" if you prefer
[*]make-kpkg clean # only needed if you want to do a "clean" build
[*]fakeroot make-kpkg --initrd --append-to-version=-some-string-here kernel-image kernel-headers
[*]sudo dpkg -i linux-image-2.6.20-16-2be-k7_2.6.20-16_i386.deb
[*]sudo dpkg -i linux-headers-2.6.20-16-2be-k7_2.6.20-16_i386.deb
[/LIST]
After I reboot the OS, I compile the test.c program and stiil get the same error message. What should I do? :confused:
Thank you.

---

### Post by justleen on 2008-04-23
the libraries you are tryin to include are not found. No need to rebuild a kernel for that...if you are sure the libraries are installed and available try including them without the linux/ in front of them

---

### Post by jsatubnutufroums on 2008-04-23
This is my original post:
[http://ubuntuforums.org/showthread.php?p=4769464#post4769464](http://ubuntuforums.org/showthread.php?p=4769464#post4769464)
Someone tells me to try to rebuild the kernel.

---

### Post by justleen on 2008-04-23
try copying the timer.h to the actual dir your working.. adjust the include path to reflect this

PS: nobody in that post tells you to rebuild your kernel... Someone asks wether you are building a kernel module.. that something quite different..
You are assuming you should rebuild your kernel.. thats not the case. 
You are asked wehter you are trying to build a kernel module.. im guessing thats not the case either..

---

### Post by jsatubnutufroums on 2008-04-23
I have already specified the include path, like this:
```
gcc -o test -I/lib/modules/2.6.20.3-ubuntu1/build/include/ test.c
```
But it still gets some error messages.

---

### Post by PmDematagoda on 2008-04-23
I have moved this thread to Programming Talk since this really does belong in Programming Talk.

---

