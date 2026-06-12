---
title: "Wifi USB Adapter"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by dynastywarrior on 2008-07-21
Hello, can anyone pls. help me...i'm very new to ubuntu and i tried to compile a driver for my USB wifi adapter...i had downloaded the driver from ralink website...did the "untar" thing and when i started to compile i get these:

rey@Machine:~$ cd ralink
rey@Machine:~/ralink$ cd RT25USB-SRC-V2.0.8.0
rey@Machine:~/ralink/RT25USB-SRC-V2.0.8.0$ ./configure
bash: ./configure: No such file or directory
rey@Machine:~/ralink/RT25USB-SRC-V2.0.8.0$ make
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/sweetheartrey/ralink/RT25USB-SRC-V2.0.8.0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/rey/ralink/RT25USB-SRC-V2.0.8.0/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/home/rey/ralink/RT25USB-SRC-V2.0.8.0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [all] Error 2
rey@Machine:~/ralink/RT25USB-SRC-V2.0.8.0$ sudo make install
[sudo] password for rey: 
make -C /lib/modules/2.6.24-19-generic/build \
	INSTALL_MOD_DIR=extra SUBDIRS=/home/rey/ralink/RT25USB-SRC-V2.0.8.0 \
	modules_install 
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  DEPMOD  2.6.24-19-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
Network device directory /etc/sysconfig/network-scripts
Module configuration file /etc/modprobe.conf 
/sbin/depmod -a
rey@Machine:~/ralink/RT25USB-SRC-V2.0.8.0$ 

so what did i do wrong? 

is it this:
"CFLAGS was changed in "/home/rey/ralink/RT25USB-SRC-V2.0.8.0/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/home/rey/ralink/RT25USB-SRC-V2.0.8.0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [all] Error 2"

how can i fix this "Error 2"?

supposed to be when i insert my USB wifi adapter into my computer previously ran on windows OS, it installs automatically...

can anyone help me pls on how to make it work on my ubuntu pc.....

---

### Post by bumanie on 2008-07-21
Have a look for a text file inside the extracted tarball that has installation instructions. That may give you a clue. If you don't understand the instructions, post a copy of the file here and someone will try and help. Also ensure you have build-essetial installed > sudo apt-get install build-essential

---

### Post by scorp123 on 2008-07-21
> **dynastywarrior said:**
>  CFLAGS was changed in "/home/rey/ralink/RT25USB-SRC-V2.0.8.0/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.

how can i fix this "Error 2"? Short version: Do as it says :D

Long version: There was probably a slight change in the syntax between the C-Compiler versions "then" (e.g. when your C-source was written) and "now" (e.g. when GCC 4.2.x which comes with Ubuntu 8.04 was released).

"CFLAGS" was a statement for the C-Compiler which defined extra-options and now this command should be "EXTRA_CFLAGS".

So I'd propose you try again and take note which files it is complaining about. Example:  /home/rey/ralink/RT25USB-SRC-V2.0.8.0/Makefile

I bet when you open that file in a text editor and scan for the word "CFLAGS" you will get plenty of hits. Replace those occurrences with "EXTRA_CFLAGS" (without the quotation marks) just as the error message wants you to and then try again.

---

