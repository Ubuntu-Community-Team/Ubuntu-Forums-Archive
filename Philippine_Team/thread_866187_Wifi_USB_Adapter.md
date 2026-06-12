---
title: "Wifi USB Adapter"
date: 2008-07-21
forum: Philippine Team
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

### Post by echo2knight on 2008-07-21
> **dynastywarrior said:**
> Hello, can anyone pls. help me...i'm very new to ubuntu and i tried to compile a driver for my USB wifi adapter...i had downloaded the driver from ralink website...did the "untar" thing and when i started to compile i get these:

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

Brod, anong model ng ub wifi mo? Ano sabi ng "dmesg" pagnainsert mo na sya sa usb?

---

### Post by dynastywarrior on 2008-07-21
thanks echo2knight for prompt reply.....

anyways, it's a Buffalo WLI-U2-KG54-A1 USB adapter. the driver is from ralink...

what is "dmesg"? i'm sorry i'm really a noob.........

when i insert my USB adapter, nothing happens.......

so what's the problem with my compile? and what to do next? have you encountered the same problem before?

---

### Post by echo2knight on 2008-07-22
> **dynastywarrior said:**
> thanks echo2knight for prompt reply.....

anyways, it's a Buffalo WLI-U2-KG54-A1 USB adapter. the driver is from ralink...

what is "dmesg"? i'm sorry i'm really a noob.........

when i insert my USB adapter, nothing happens.......

so what's the problem with my compile? and what to do next? have you encountered the same problem before?

Sorry pare. Built-in ang wifi ko sa lappy. Try opening a terminal then enter the "dmesg" command, it should give you a clue as to what is happening in your system. Kung detected nya ba to o hindi.

---

### Post by daxumaming on 2008-07-26
if you're on Hardy, NetworkManager should've installed the drivers for you. i have TP-Link TL-WN321G that uses Ralink's RT73 and I had to compile its driver when I was on Gutsy. Imagine my surprise when it worked out of the box after clean upgrading to Hardy. It even supported WPA2.

---

