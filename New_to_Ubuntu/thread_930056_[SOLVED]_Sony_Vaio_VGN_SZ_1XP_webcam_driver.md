---
title: "[SOLVED] Sony Vaio VGN SZ 1XP webcam driver"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by Harisz750 on 2008-09-25
hi!! i just installed ubuntu 8.04 in Sony Vaio VGN SZ 1XP and i cannot make VGN-VCC2 webcam to work. my kernel is 2.6.24-19-generic and i have downloaded r5u870-0.10.0 driver in order to compile it. i have done update and upgrade and installed build-essentials. i extracted the file in home folder and the readme file says:

 To build/install this driver, you must have a set of configuration and
interface headers, or the complete build directory, for your running kernel,
or the target kernel for which the driver is to be built.  This should
include most files in the include/linux directory, and specifically
include/linux/autoconf.h and include/linux/version.h.

The required interface headers are usually located at or symlinked from:
/lib/modules/<version>/build

Your kernel must be 2.6.17 or newer.
INSTALLATION

make

To build against a specific kernel:

make **KDIR=/path/to/kernel**

To install the modules to the appropriate location:

make install

-or-

make install KDIR=/path/to/kernel


1) how can i find the path/to/kernel??? 
2) i type the following commands in terminal ```
cd r5u870-0.10.0
```
```
make
```  and the output is make -C /lib/modules/2.6.24-19-generic/build M=/home/marios/r5u870-0.10.0 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/marios/r5u870-0.10.0/r5u870_md.o
In file included from /home/marios/r5u870-0.10.0/r5u870_md.c:55:
/home/marios/r5u870-0.10.0/usbcam.h:36:29: error: media/video-buf.h: No such file or directory
make[2]: *** [/home/marios/r5u870-0.10.0/r5u870_md.o] Error 1
make[1]: *** [_module_/home/marios/r5u870-0.10.0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [all] Error 2

3) i type ```
sudo make install
```  and it returns  :  make -C /lib/modules/2.6.24-19-generic/build M=/home/marios/r5u870-0.10.0 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/marios/r5u870-0.10.0/r5u870_md.o
In file included from /home/marios/r5u870-0.10.0/r5u870_md.c:55:
/home/marios/r5u870-0.10.0/usbcam.h:36:29: error: media/video-buf.h: No such file or directory
make[2]: *** [/home/marios/r5u870-0.10.0/r5u870_md.o] Error 1
make[1]: *** [_module_/home/marios/r5u870-0.10.0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [all] Error 2
marios@marios:~/r5u870-0.10.0$ 

what am i doing wrong?

---

### Post by Harisz750 on 2008-09-26
no one???????????????

---

### Post by Nepherte on 2008-09-26
I recall having installed those drivers by:
[LIST=1]
[*] Be sure you have the necessary build tools:
```
sudo apt-get install build-essential
```
[*]Untarring the archive file.
[*]Navigate to the dir:
```
cd r5u870-0.10.0
```
[*]run the make command:
```
make
```
[*]Run the make install command:
```
sudo make install
```
[*] insert the correct module:
```
sudo modprobe r5u870
```
and add them to /etc/modules.
[/LIST]

---

### Post by Harisz750 on 2008-09-26
i have done all these... if you see my first post, i have some error messages in make and sudo make install. more help????  please????

---

### Post by Harisz750 on 2008-09-27
solved.. i downloaded a newer driver and worked like charm. here is the download page  [http://wiki.mediati.org/Installation](http://wiki.mediati.org/Installation)

---

