---
title: "wireless not working ubuntu 20.04LTS"
date: 2020-11-01
forum: New to Ubuntu
---

### Post by rfpera on 2020-11-01
My wireless is not working i have tried many options but couldn't get solved 
here is my wireless info script [https://paste.ubuntu.com/p/FrS6nmd8cK/](https://paste.ubuntu.com/p/FrS6nmd8cK/)

---

### Post by grahammechanical on 2020-11-01
Are you using bluetooth to connect to the internet?

If you look at the printout and go to the section called rfkill you will see that bluetooth is listed. It should also list a wireless adapter. Now go to the section called iwconfig. It lists the ethernet adapter and as expected it has no wireless extensions. It should also list a WiFi adapter

Printout from my computer. Notice that my WiFi is listed but I am not actually using it to connect to the internet.

> graham@sdb1-sdb8:~$ rfkill
ID TYPE DEVICE      SOFT      HARD
 0 wlan phy0   unblocked unblocked

graham@sdb1-sdb8:~$ iwconfig
enp2s0    no wireless extensions.

lo        no wireless extensions.

wlx0015af0e9be0  IEEE 802.11  ESSID:  off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr: off   Fragment thr: off
          Power Management:  off
          
enp6s4    no wireless extensions.

Regards

---

### Post by rfpera on 2020-11-01
No i'm not using bluetooth i just installed ubuntu 20.04 to my notebook and i'm struglling to get my wireless to work. I read on some forums that i should install realtek 8723e driver which im tried but also didn't work

---

### Post by ActionParsnip on 2020-11-02
Does this help
[https://askubuntu.com/questions/1180714/realtek-rtl8822ce-is-unable-to-detect-wifi-networks](https://askubuntu.com/questions/1180714/realtek-rtl8822ce-is-unable-to-detect-wifi-networks)

---

### Post by mastablasta on 2020-11-03
for realtek you need to either get newer kernel or patch the current kernel with realtek driver.

to patch a kernel you have to first disable secure boot in UEFI/BIOS.
and to use the correct driver make sure you identify the correct wi-fi chip first.

example how to for rtl8723de: [https://askubuntu.com/questions/1197560/how-to-permanently-install-wifi-driver-realtek-8723de-in-ubuntu-18-04](https://askubuntu.com/questions/1197560/how-to-permanently-install-wifi-driver-realtek-8723de-in-ubuntu-18-04)

---

