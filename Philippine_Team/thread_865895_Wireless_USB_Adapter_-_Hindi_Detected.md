---
title: "Wireless USB Adapter - Hindi Detected"
date: 2008-07-21
forum: Philippine Team
---

### Post by ysNoi on 2008-07-21
mga brods, patulong naman po..!
Nag-install ako ng Ubuntu in one of the PC's here sa Company pero hindi madetect yung Wireless USB Driver to have internet access...!

Meron namang driver pero hindi ko alam paano install...!

Here is the device: IEEE 802.11g Wireless USB Adapter :)

Any inputs is highly appreciated..! TYIA :guitar:

---

### Post by loell on 2008-07-21
can you do a ```
lsusb
``` after plugging the device?

---

### Post by dynastywarrior on 2008-07-21
Sir loell, 

i have the same problem...i tried compiling for the driver but this is what i've got:


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

thanks in advance sir loell....

---

### Post by ysNoi on 2008-07-21
> **loell said:**
> can you do a ```
lsusb
``` after plugging the device?

heRe siR :

louie@louie-desktop:~$ lsusb
Bus 005 Device 002: ID 0bda:8189 Realtek Semiconductor Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
louie@louie-desktop:~$

sorry for the laTe reply..!
Thanks anyway...! :guitar:

---

### Post by perbiu on 2008-07-21
Buti pa yung Hawking Technology USB Wifi plug and play.

---

### Post by loell on 2008-07-21
with this wireless usb, you need [ndiswrapper]("apt:ndiswrapper-common")

you can just follow this guide

[http://ubuntuforums.org/showthread.php?t=529090]("http://ubuntuforums.org/showthread.php?t=529090")


or..
maybe you could install the native driver

[ftp://210.51.181.211/cn/wlan/rtl8185_linux_26%5B1%5D.1027.0823.2007.tar.gz]("ftp://210.51.181.211/cn/wlan/rtl8185_linux_26%5B1%5D.1027.0823.2007.tar.gz")

---

### Post by ysNoi on 2008-07-22
Thanks for the help bro...!

I've been reading these since yesterday but since I'm super busy kahapon sa company, hindi ko natapos gawin..! But I'll be very soon to solve my problem..!

Post ko agad dito pag OK na bro..! Thanks talaga ng marami..!:guitar:

---

