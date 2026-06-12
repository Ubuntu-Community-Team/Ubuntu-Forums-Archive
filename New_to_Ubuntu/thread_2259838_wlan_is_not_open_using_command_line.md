---
title: "wlan is not open using command line"
date: 2015-01-07
forum: New to Ubuntu
---

### Post by Hasan55 on 2015-01-07
guys my laptop wlan is not opening by command line untill trip the power button of wlan. i used these commands.....


```
hasan@mx1:~
$ sudo su -
[sudo] password for hasan: 
root@mx1:~# iwconfig
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
lo        no wireless extensions.

eth0      no wireless extensions.

usb0      no wireless extensions.

root@mx1:~# ifconfig wlan0 up
SIOCSIFFLAGS: Operation not possible due to RF-kill
root@mx1:~# 
```





plz help me giving me some suggestion   what is worng here...thanks

---

### Post by wildmanne39 on 2015-01-07
Please do not create duplicate posts it dilutes community effort.
Thanks

---

