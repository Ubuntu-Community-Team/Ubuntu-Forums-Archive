---
title: "Airlink 100 Al100ac trouble installing"
date: 2016-04-15
forum: New to Ubuntu
---

### Post by Jan-Cato_Pedersen on 2016-04-15
Hey guys.

I am completely new to Linux in general, but i have read up a lot.

Im having problems installing Jensen of scandinavia's airlink 100 Al100ac.
Everything went fine untill i execute the make command in terminal, then this showed:

> :/home/metcon/Desktop/Al100# make
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.2.0-35-generic/build M=/home/metcon/Desktop/Al100  modules
make[1]: Entering directory `/usr/src/linux-headers-4.2.0-35-generic'
  CC [M]  /home/metcon/Desktop/Al100/core/rtw_cmd.o
  CC [M]  /home/metcon/Desktop/Al100/core/rtw_security.o
  CC [M]  /home/metcon/Desktop/Al100/core/rtw_debug.o
  CC [M]  /home/metcon/Desktop/Al100/core/rtw_io.o
  CC [M]  /home/metcon/Desktop/Al100/core/rtw_ioctl_query.o
  CC [M]  /home/metcon/Desktop/Al100/core/rtw_ioctl_set.o
  CC [M]  /home/metcon/Desktop/Al100/core/rtw_ieee80211.o
  CC [M]  /home/metcon/Desktop/Al100/core/rtw_mlme.o
  CC [M]  /home/metcon/Desktop/Al100/core/rtw_mlme_ext.o
  CC [M]  /home/metcon/Desktop/Al100/core/rtw_wlan_util.o
  CC [M]  /home/metcon/Desktop/Al100/core/rtw_vht.o
  CC [M]  /home/metcon/Desktop/Al100/core/rtw_pwrctrl.o
  CC [M]  /home/metcon/Desktop/Al100/core/rtw_rf.o
  CC [M]  /home/metcon/Desktop/Al100/core/rtw_recv.o
  CC [M]  /home/metcon/Desktop/Al100/core/rtw_sta_mgt.o
  CC [M]  /home/metcon/Desktop/Al100/core/rtw_ap.o
  CC [M]  /home/metcon/Desktop/Al100/core/rtw_xmit.o
  CC [M]  /home/metcon/Desktop/Al100/core/rtw_p2p.o
  CC [M]  /home/metcon/Desktop/Al100/core/rtw_tdls.o
  CC [M]  /home/metcon/Desktop/Al100/core/rtw_br_ext.o
  CC [M]  /home/metcon/Desktop/Al100/core/rtw_iol.o
  CC [M]  /home/metcon/Desktop/Al100/core/rtw_sreset.o
  CC [M]  /home/metcon/Desktop/Al100/core/rtw_btcoex.o
  CC [M]  /home/metcon/Desktop/Al100/core/rtw_beamforming.o
  CC [M]  /home/metcon/Desktop/Al100/core/rtw_odm.o
  CC [M]  /home/metcon/Desktop/Al100/core/efuse/rtw_efuse.o
  CC [M]  /home/metcon/Desktop/Al100/os_dep/osdep_service.o
  CC [M]  /home/metcon/Desktop/Al100/os_dep/linux/os_intfs.o
  CC [M]  /home/metcon/Desktop/Al100/os_dep/linux/usb_intf.o
  CC [M]  /home/metcon/Desktop/Al100/os_dep/linux/usb_ops_linux.o
  CC [M]  /home/metcon/Desktop/Al100/os_dep/linux/ioctl_linux.o
/home/metcon/Desktop/Al100/os_dep/linux/ioctl_linux.c: In function ‘translate_scan’:
/home/metcon/Desktop/Al100/os_dep/linux/ioctl_linux.c:798:1: warning: the frame size of 1204 bytes is larger than 1024 bytes [-Wframe-larger-than=]
 }
 ^
  CC [M]  /home/metcon/Desktop/Al100/os_dep/linux/xmit_linux.o
  CC [M]  /home/metcon/Desktop/Al100/os_dep/linux/mlme_linux.o
  CC [M]  /home/metcon/Desktop/Al100/os_dep/linux/recv_linux.o
  CC [M]  /home/metcon/Desktop/Al100/os_dep/linux/ioctl_cfg80211.o
  CC [M]  /home/metcon/Desktop/Al100/os_dep/linux/wifi_regd.o
  CC [M]  /home/metcon/Desktop/Al100/os_dep/linux/rtw_android.o
/home/metcon/Desktop/Al100/os_dep/linux/rtw_android.c: In function ‘rtw_android_cmdstr_to_num’:
/home/metcon/Desktop/Al100/os_dep/linux/rtw_android.c:345:3: error: implicit declaration of function ‘strnicmp’ [-Werror=implicit-function-declaration]
   if(0 == strnicmp(cmdstr , android_wifi_cmd_str[cmd_num], strlen(android_wifi_cmd_str[cmd_num])) )
   ^
cc1: some warnings being treated as errors
make[2]: *** [/home/metcon/Desktop/Al100/os_dep/linux/rtw_android.o] Error 1
make[1]: *** [_module_/home/metcon/Desktop/Al100] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-4.2.0-35-generic'
make: *** [modules] Error 2


Please tell me what im doing wrong and how to fix if you can. 

Any help is welcome :)

---

