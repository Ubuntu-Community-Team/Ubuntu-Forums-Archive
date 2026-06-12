---
title: "Ubuntu 11.10 and Asus USB-N13"
date: 2011-12-04
forum: New to Ubuntu
---

### Post by pfriesen on 2011-12-04
I am a total newbie at linux and Ubuntu and am looking at help install my wireless adapter.
I have tried numerous things but am stuck getting it to work.


```
perry@perry-Dimension-3000:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0b05:1784 ASUSTek Computer, Inc. USB-N13 802.11n Network Adapter [Ralink RT2870]
Bus 001 Device 005: ID 1e3d:2093  
Bus 002 Device 002: ID 045e:00a4 Microsoft Corp. 
Bus 003 Device 002: ID 413c:1003 Dell Computer Corp. Keyboard Hub
Bus 003 Device 003: ID 413c:2010 Dell Computer Corp. Keyboard
```

Any ideas? Anyone?
Thanks in advance.

---

### Post by pfriesen on 2011-12-05
Anyone able to help?

---

### Post by chili555 on 2011-12-06
Please define "stuck getting it to work." Is a wireless interface created?```
iwconfig
```Does it scan and see networks?```
sudo iwlist wlan0 scan
```Does it try to connect? Are you challenged for an encryption key?

Please show us:```
dmesg | grep rt2
```Thanks.

---

### Post by pfriesen on 2011-12-06
Sorry I am not even sure what you are asking, but I am right at the beginning, trying to install driver but it didn't seem to work.


```
perry@perry-Dimension-3000:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```

---

### Post by chili555 on 2011-12-06
What have you done to try to install the driver? In Ubuntu 11.10, the driver rt2800usb is already installed. Is there any change if you do:```
sudo modprobe rt2800usb
dmesg | grep rt2
iwconfig
```Please run each command in turn and post the result.

---

### Post by pfriesen on 2011-12-07
I've been trying to follow the instructions in 

[http://ubuntuforums.org/showthread.php?t=1419504]("http://ubuntuforums.org/showthread.php?t=1419504")

and when I "make" I get the following error:

```
perry@perry-Dimension-3000:~/Desktop/RT3070$ make
make -C tools
make[1]: Entering directory `/home/perry/Desktop/RT3070/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/perry/Desktop/RT3070/tools'
/home/perry/Desktop/RT3070/tools/bin2h
cp -f os/linux/Makefile.6 /home/perry/Desktop/RT3070/os/linux/Makefile
make  -C  /lib/modules/3.0.0-13-generic/build SUBDIRS=/home/perry/Desktop/RT3070/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-13-generic'
  CC [M]  /home/perry/Desktop/RT3070/os/linux/../../common/crypt_md5.o
  CC [M]  /home/perry/Desktop/RT3070/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/perry/Desktop/RT3070/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/perry/Desktop/RT3070/os/linux/../../common/mlme.o
/home/perry/Desktop/RT3070/os/linux/../../common/mlme.c: In function ‘BssTableSetEntry’:
/home/perry/Desktop/RT3070/os/linux/../../common/mlme.c:4002:39: warning: operation on ‘Tab->BssOverlapNr’ may be undefined [-Wsequence-point]
/home/perry/Desktop/RT3070/os/linux/../../common/mlme.c: In function ‘BssTableSortByRssi’:
/home/perry/Desktop/RT3070/os/linux/../../common/mlme.c:4406:1: warning: the frame size of 1572 bytes is larger than 1024 bytes [-Wframe-larger-than=]
  CC [M]  /home/perry/Desktop/RT3070/os/linux/../../common/cmm_wep.o
  CC [M]  /home/perry/Desktop/RT3070/os/linux/../../common/action.o
  CC [M]  /home/perry/Desktop/RT3070/os/linux/../../common/cmm_data.o
  CC [M]  /home/perry/Desktop/RT3070/os/linux/../../common/rtmp_init.o
/home/perry/Desktop/RT3070/os/linux/../../common/rtmp_init.c: In function ‘RtmpRaDevCtrlInit’:
/home/perry/Desktop/RT3070/os/linux/../../common/rtmp_init.c:3709:2: error: implicit declaration of function ‘init_MUTEX’ [-Werror=implicit-function-declaration]
/home/perry/Desktop/RT3070/os/linux/../../common/rtmp_init.c:3710:2: warning: passing argument 2 of ‘os_alloc_mem’ from incompatible pointer type [enabled by default]
/home/perry/Desktop/RT3070/include/rtmp.h:5704:13: note: expected ‘UCHAR **’ but argument is of type ‘UCHAR *’
cc1: some warnings being treated as errors

make[2]: *** [/home/perry/Desktop/RT3070/os/linux/../../common/rtmp_init.o] Error 1
make[1]: *** [_module_/home/perry/Desktop/RT3070/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-13-generic'
make: *** [LINUX] Error 2
```

Thanks again for your help!!

---

### Post by pfriesen on 2011-12-07
> **chili555 said:**
>  Is there any change if you do:```
sudo modprobe rt2800usb
dmesg | grep rt2
iwconfig
```Please run each command in turn and post the result.

This is what I got:


```
perry@perry-Dimension-3000:~$ sudo modprobe rt2800usb
[sudo] password for perry: 
perry@perry-Dimension-3000:~$ dmesg |grep rt2
[ 4627.094647] Registered led device: rt2800usb-phy0::radio
[ 4627.094683] Registered led device: rt2800usb-phy0::assoc
[ 4627.094715] Registered led device: rt2800usb-phy0::quality
[ 4627.097790] usbcore: registered new interface driver rt2800usb
perry@perry-Dimension-3000:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
```

---

### Post by pfriesen on 2011-12-07
Restarted my machine and now I get:


```
perry@perry-Dimension-3000:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```

---

### Post by chili555 on 2011-12-07
> error: implicit declaration of function ‘init_MUTEX’ [-Werror=implicit-function-declaration]That's a sure sign that the package was written for a much earlier kernel, and, probably gcc version than your shiny new 3.0.0-13 kernel. 

Why is this wlan***1***? Do you have an internal card that's not working; likely wlan0? Wouldn't we be wiser to troubleshoot it first? Please let us see:```
lspci -nn | grep 0280
rfkill list all
```Thanks.

---

### Post by pfriesen on 2011-12-07
Sorry, but I don't get anything with those commands.

Thanks for helping.

---

### Post by pfriesen on 2011-12-10
I reinstalled 11.10 and it is now working.
Thanks Chili555 for your help. :P

---

