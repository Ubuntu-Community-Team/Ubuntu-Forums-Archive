---
title: "Installing wireless driver"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by coubury on 2008-09-08
m trying to install my drivers again for my RT61 chipset

I get it off here [http://www.aircrack-ng.org/doku.php?id=rt61](http://www.aircrack-ng.org/doku.php?id=rt61)

when i try to install it i get errors
Quote:

a-desktop:~$ wget [http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz)
--20:33:29-- [http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz)
=> `rt61-cvs-daily.tar.gz.1'
Resolving rt2x00.serialmonkey.com... 208.100.15.174
Connecting to rt2x00.serialmonkey.com|208.100.15.174|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 334,162 (326K) [application/x-gzip]

100%[====================================>] 334,162 122.43K/s

20:33:32 (122.00 KB/s) - `rt61-cvs-daily.tar.gz.1' saved [334162/334162]

laura@laura-desktop:~$ tar xvfz rt61-cvs-daily.tar.gz
rt61-cvs-2008090813/
rt61-cvs-2008090813/FAQ
rt61-cvs-2008090813/THANKS
rt61-cvs-2008090813/CHANGELOG
rt61-cvs-2008090813/CVS/
rt61-cvs-2008090813/CVS/Root
rt61-cvs-2008090813/CVS/Repository
rt61-cvs-2008090813/CVS/Entries.Log
rt61-cvs-2008090813/CVS/Entries
rt61-cvs-2008090813/WPA_Supplicant/
rt61-cvs-2008090813/WPA_Supplicant/drivers.c
rt61-cvs-2008090813/WPA_Supplicant/CVS/
rt61-cvs-2008090813/WPA_Supplicant/CVS/Root
rt61-cvs-2008090813/WPA_Supplicant/CVS/Repository
rt61-cvs-2008090813/WPA_Supplicant/CVS/Entries
rt61-cvs-2008090813/WPA_Supplicant/driver_ralink.c
rt61-cvs-2008090813/WPA_Supplicant/wpa_supplicant_example.conf
rt61-cvs-2008090813/WPA_Supplicant/readme
rt61-cvs-2008090813/WPA_Supplicant/defconfig
rt61-cvs-2008090813/WPA_Supplicant/driver_ralink.h
rt61-cvs-2008090813/WPA_Supplicant/Makefile
rt61-cvs-2008090813/LICENSE
rt61-cvs-2008090813/Module/
rt61-cvs-2008090813/Module/auth.c
rt61-cvs-2008090813/Module/rt2561.bin
rt61-cvs-2008090813/Module/rt2x00debug.h
rt61-cvs-2008090813/Module/md5.c
rt61-cvs-2008090813/Module/rtmp_main.c
rt61-cvs-2008090813/Module/rt_config.h
rt61-cvs-2008090813/Module/assoc.c
rt61-cvs-2008090813/Module/CVS/
rt61-cvs-2008090813/Module/CVS/Root
rt61-cvs-2008090813/Module/CVS/Repository
rt61-cvs-2008090813/Module/CVS/Entries
rt61-cvs-2008090813/Module/STA_iwpriv_ATE_usage.txt
rt61-cvs-2008090813/Module/wpa.c
rt61-cvs-2008090813/Module/rt2561s.bin
rt61-cvs-2008090813/Module/sync.c
rt61-cvs-2008090813/Module/rtmp_data.c
rt61-cvs-2008090813/Module/rtmp_info.c
rt61-cvs-2008090813/Module/iwpriv_usage.txt
rt61-cvs-2008090813/Module/mlme.h
rt61-cvs-2008090813/Module/connect.c
rt61-cvs-2008090813/Module/rtmp_tkip.c
rt61-cvs-2008090813/Module/rt2661.bin
rt61-cvs-2008090813/Module/auth_rsp.c
rt61-cvs-2008090813/Module/oid.h
rt61-cvs-2008090813/Module/rt2661.h
rt61-cvs-2008090813/Module/rtmp_init.c
rt61-cvs-2008090813/Module/TESTING
rt61-cvs-2008090813/Module/rtmp.h
rt61-cvs-2008090813/Module/mlme.c
rt61-cvs-2008090813/Module/md5.h
rt61-cvs-2008090813/Module/wpa.h
rt61-cvs-2008090813/Module/eeprom.c
rt61-cvs-2008090813/Module/rtmp_wep.c
rt61-cvs-2008090813/Module/README
rt61-cvs-2008090813/Module/rtmp_def.h
rt61-cvs-2008090813/Module/Makefile
rt61-cvs-2008090813/Module/rtmp_type.h
rt61-cvs-2008090813/Module/rt2x00debug.c
rt61-cvs-2008090813/Module/ReleaseNote
rt61-cvs-2008090813/Module/sanity.c
laura@laura-desktop:~$ cd rt61-cvs-*
laura@laura-desktop:~/rt61-cvs-2008090813$ cd Module
laura@laura-desktop:~/rt61-cvs-2008090813/Module$ make
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
Building modules, stage 2.
MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
!!! WARNING: Module file much too big (>1MB)
!!! Check your kernel settings or use 'strip'
*** Module rt61.ko built successfully
laura@laura-desktop:~/rt61-cvs-2008090813/Module$
laura@laura-desktop:~/rt61-cvs-2008090813/Module$ make install
*** Install module in /lib/modules/2.6.24-19-generic/extra ...
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
mkdir: cannot create directory `/lib/modules/2.6.24-19-generic/extra': Permission denied
make[1]: *** [_emodinst_] Error 1
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [modules_install] Error 2
laura@laura-desktop:~/rt61-cvs-2008090813/Module$ rmmod rt61pci 2>/dev/null
laura@laura-desktop:~/rt61-cvs-2008090813/Module$ modprobe rt61
FATAL: Module rt61 not found.
laura@laura-desktop:~/rt61-cvs-2008090813/Module$

any ideas?


Do i need to install a package are something first?

Like ssql etc?

---

### Post by knix on 2008-09-08
try using sudo before everything but wget. Or just type sudo bash to become root. These will resolve the permission denied problem, which will fix the not found problem.

Edit: I just use the bt3 usb version since I use ndiswrapper on my ubuntu. They may include your driver (they have mine).

---

