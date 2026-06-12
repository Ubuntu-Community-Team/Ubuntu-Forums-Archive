---
title: "trouble compiling wireless driver from source"
date: 2007-09-22
forum: Packaging and Compiling Programs
---

### Post by HokeyFry on 2007-09-22
im having trouble compiling the linux RT2500 wireless usb pen driver. i get this error when running 'make'

```
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/aalber/Desktop/RT/RT25USB-SRC-V2.0.8.0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/aalber/Desktop/RT/RT25USB-SRC-V2.0.8.0/rtusb_main.o
/home/aalber/Desktop/RT/RT25USB-SRC-V2.0.8.0/rtusb_main.c: In function ‘CMDHandler’:
/home/aalber/Desktop/RT/RT25USB-SRC-V2.0.8.0/rtusb_main.c:1079: warning: unused variable ‘pkey’
/home/aalber/Desktop/RT/RT25USB-SRC-V2.0.8.0/rtusb_main.c:1078: warning: unused variable ‘i’
/home/aalber/Desktop/RT/RT25USB-SRC-V2.0.8.0/rtusb_main.c: In function ‘usb_rtusb_probe’:
/home/aalber/Desktop/RT/RT25USB-SRC-V2.0.8.0/rtusb_main.c:1779: error: ‘struct net_device’ has no member named ‘get_wireless_stats’
make[2]: *** [/home/aalber/Desktop/RT/RT25USB-SRC-V2.0.8.0/rtusb_main.o] Error 1
make[1]: *** [_module_/home/aalber/Desktop/RT/RT25USB-SRC-V2.0.8.0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [all] Error 2

```

im not exactly super familiar with compiling from source, so does anyone know what this means?

---

### Post by laurier57 on 2007-09-29
I found this post via Google, looking for help with installing this on FC7, not Ubuntu. I'm replying just in case someone else gets here the same way I did...just connecting the dots :)

So far I have found a team working on a branch of this driver, and this post on their site deals with this build error:

[http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?p=23879&sid=db7e81c26148149951139545d0f75bb1](http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?p=23879&sid=db7e81c26148149951139545d0f75bb1)

They also have HOWTOs for the 2400/2500 devices here:

[http://rt2x00.serialmonkey.com/wiki/index.php?title=HOWTOS](http://rt2x00.serialmonkey.com/wiki/index.php?title=HOWTOS)

I did manage to build the 2500 driver in the HOWTO, and am currently working on configuring it, so I can't say more than the docs at this point.

Good luck!

---

