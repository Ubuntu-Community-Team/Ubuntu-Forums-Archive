---
title: "Rt61 Driver"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by coubury on 2008-05-31
Im installing this now had trouble with it before

root@coubury-desktop:/home/coubury# wget [http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz)
--02:10:08--  [http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz)
           => `rt61-cvs-daily.tar.gz.3'
Resolving rt2x00.serialmonkey.com... 
208.100.15.174
Connecting to rt2x00.serialmonkey.com|208.100.15.174|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 333,645 (326K) [application/x-gzip]

100%[===========================>] 333,645       42.59K/s    ETA 00:00

02:10:22 (40.18 KB/s) - `rt61-cvs-daily.tar.gz.3' saved [333645/333645]

root@coubury-desktop:/home/coubury# tar xvfz rt61-cvs-daily.tar.gz
rt61-cvs-2008053116/
rt61-cvs-2008053116/FAQ
rt61-cvs-2008053116/THANKS
rt61-cvs-2008053116/CHANGELOG
rt61-cvs-2008053116/CVS/
rt61-cvs-2008053116/CVS/Root
rt61-cvs-2008053116/CVS/Repository
rt61-cvs-2008053116/CVS/Entries.Log
rt61-cvs-2008053116/CVS/Entries
rt61-cvs-2008053116/WPA_Supplicant/
rt61-cvs-2008053116/WPA_Supplicant/drivers.c
rt61-cvs-2008053116/WPA_Supplicant/CVS/
rt61-cvs-2008053116/WPA_Supplicant/CVS/Root
rt61-cvs-2008053116/WPA_Supplicant/CVS/Repository
rt61-cvs-2008053116/WPA_Supplicant/CVS/Entries
rt61-cvs-2008053116/WPA_Supplicant/driver_ralink.c
rt61-cvs-2008053116/WPA_Supplicant/wpa_supplicant_example.conf
rt61-cvs-2008053116/WPA_Supplicant/readme
rt61-cvs-2008053116/WPA_Supplicant/defconfig
rt61-cvs-2008053116/WPA_Supplicant/driver_ralink.h
rt61-cvs-2008053116/WPA_Supplicant/Makefile
rt61-cvs-2008053116/LICENSE
rt61-cvs-2008053116/Module/
rt61-cvs-2008053116/Module/auth.c
rt61-cvs-2008053116/Module/rt2561.bin
rt61-cvs-2008053116/Module/rt2x00debug.h
rt61-cvs-2008053116/Module/md5.c
rt61-cvs-2008053116/Module/rtmp_main.c
rt61-cvs-2008053116/Module/rt_config.h
rt61-cvs-2008053116/Module/assoc.c
rt61-cvs-2008053116/Module/CVS/
rt61-cvs-2008053116/Module/CVS/Root
rt61-cvs-2008053116/Module/CVS/Repository
rt61-cvs-2008053116/Module/CVS/Entries
rt61-cvs-2008053116/Module/STA_iwpriv_ATE_usage.txt
rt61-cvs-2008053116/Module/wpa.c
rt61-cvs-2008053116/Module/rt2561s.bin
rt61-cvs-2008053116/Module/sync.c
rt61-cvs-2008053116/Module/rtmp_data.c
rt61-cvs-2008053116/Module/rtmp_info.c
rt61-cvs-2008053116/Module/iwpriv_usage.txt
rt61-cvs-2008053116/Module/mlme.h
rt61-cvs-2008053116/Module/connect.c
rt61-cvs-2008053116/Module/rtmp_tkip.c
rt61-cvs-2008053116/Module/rt2661.bin
rt61-cvs-2008053116/Module/auth_rsp.c
rt61-cvs-2008053116/Module/oid.h
rt61-cvs-2008053116/Module/rt2661.h
rt61-cvs-2008053116/Module/rtmp_init.c
rt61-cvs-2008053116/Module/TESTING
rt61-cvs-2008053116/Module/rtmp.h
rt61-cvs-2008053116/Module/mlme.c
rt61-cvs-2008053116/Module/md5.h
rt61-cvs-2008053116/Module/wpa.h
rt61-cvs-2008053116/Module/eeprom.c
rt61-cvs-2008053116/Module/rtmp_wep.c
rt61-cvs-2008053116/Module/README
rt61-cvs-2008053116/Module/rtmp_def.h
rt61-cvs-2008053116/Module/Makefile
rt61-cvs-2008053116/Module/rtmp_type.h
rt61-cvs-2008053116/Module/rt2x00debug.c
rt61-cvs-2008053116/Module/ReleaseNote
rt61-cvs-2008053116/Module/sanity.c
root@coubury-desktop:/home/coubury# cd rt61-cvs-*
root@coubury-desktop:/home/coubury/rt61-cvs-2008053116# cd Module
root@coubury-desktop:/home/coubury/rt61-cvs-2008053116/Module# make
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
!!! WARNING: Module file much too big (>1MB)
!!! Check your kernel settings or use 'strip'
*** Module rt61.ko built successfully
root@coubury-desktop:/home/coubury/rt61-cvs-2008053116/Module# make install
*** Install module in /lib/modules/2.6.22-14-generic/extra ...
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  INSTALL /home/coubury/rt61-cvs-2008053116/Module/rt61.ko
  DEPMOD  2.6.22-14-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
/sbin/depmod -a
*** Update /etc/modprobe.d/ralink alias for wlan*
*** Install firmware in /lib/firmware ...
*** Check old config ...
!!!
!!! WARNING: DEPRECATED CONFIG FOUND !
!!!
!!! -> Update your config and remove /etc/Wireless/RT61STA
root@coubury-desktop:/home/coubury/rt61-cvs-2008053116/Module# modprobe rt61


see above Update /etc/modprobe.d/ralink alias for wlan* i did i changed it to wlan0

now how do i delate etc/Wireless/RT61STA? i tried sudo gedit /etc/Wireless/RT61STA but it says its a directory 

also when i type iwconfig my wireless card still isnt recognized 


root@coubury-desktop:/home/coubury# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ppp0      no wireless extensions.

root@coubury-desktop:/home/coubury# 



any ideas?

---

