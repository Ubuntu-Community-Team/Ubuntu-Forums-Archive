---
title: "Big Bug: wireless slow down after sidebar appears during flash video"
date: 2012-03-08
forum: New to Ubuntu
---

### Post by dixcuxx on 2012-03-08
This bug always happens when the sidebar appears while a flash video is playing. Then wireless would be like 30% of original speed, hard to play flash video or lage intranal network data tranfer. The only way to solve it would be logout and then login again. This bug easily happen because it is on the left hand side now and easily be touched on that area and then it comes out.

I am using 11.10 always with latest update. 

Any idea how to solve this big bug?

---

### Post by dixcuxx on 2012-03-09
I am surprised that no one talk about this

---

### Post by dixcuxx on 2012-03-11
> **dixcuxx said:**
> I am surprised that no one talk about this

So hard to believe that no one talk about this big bug

---

### Post by wildmanne39 on 2012-03-11
Hi, I doubt it has to do with the sidebar appearing during flash play back please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by dixcuxx on 2012-03-12
> **wildmanne39 said:**
> Hi, I doubt it has to do with the sidebar appearing during flash play back please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

```
:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux b-tp 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:50:54 UTC 2012 i686 i686 i386 GNU/Linux
:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Intel Corporation 82573L Gigabit Ethernet Controller [8086:109a]
	Subsystem: Lenovo ThinkPad T60 [17aa:2001]
	Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4227] (rev 02)
	Subsystem: Intel Corporation Device [8086:1010]
	Kernel driver in use: iwl3945
:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"Core"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: 4C:E6:76:43:06:9F   
          Bit Rate=48 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:14   Missed beacon:0

:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: yes
	Hard blocked: no
```

---

### Post by dixcuxx on 2012-03-12
> **wildmanne39 said:**
> Hi, I doubt it has to do with the sidebar appearing during flash play back please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

ho yeah so I posted the result. Any idea? Yes I agree it should be the sidebar appear during flash play then problem happens. If I logout then login again, it would be fine.

---

### Post by uRock on 2012-03-13
Have you installed a graphics driver via Additional Drivers?

---

### Post by dixcuxx on 2012-03-13
> **uRock said:**
> Have you installed a graphics driver via Additional Drivers?

no, I didn't

---

### Post by wildmanne39 on 2012-03-13
Hi, please run these commands one at a time and do not reboot your computer after you run the commands they are just for one boot and if it helps which I think it will we will need to make it permanent.
```
sudo ifconfig wlan0 down
sudo rmmod -f iwl3945
sudo modprobe iwl3945 11n_disable=1
sudo ifconfig wlan0 up

```
Thanks

---

### Post by dixcuxx on 2012-03-14
> **wildmanne39 said:**
> Hi, please run these commands one at a time and do not reboot your computer after you run the commands they are just for one boot and if it helps which I think it will we will need to make it permanent.
```
sudo ifconfig wlan0 down
sudo rmmod -f iwl3945
sudo modprobe iwl3945 11n_disable=1
sudo ifconfig wlan0 up

```
Thanks

What does these commands really do? Let me try it out after I get out of office.

---

### Post by wildmanne39 on 2012-03-14
They temporarily disable the N speed because it does not work right with intel cards and it should increase your speed considerably.
Thanks

---

### Post by dixcuxx on 2012-03-16
> **wildmanne39 said:**
> They temporarily disable the N speed because it does not work right with intel cards and it should increase your speed considerably.
Thanks

I should say thanks! Well it doesn't work, I tried and here is the result:

:~$ sudo ifconfig wlan0 down
[sudo] password for bencarcar: 
:~$ sudo rmmod -f iwl3945
:~$ sudo modprobe iwl3945 lln_disable=1
FATAL: Error inserting iwl3945 (/lib/modules/3.0.0-16-generic/kernel/drivers/net/wireless/iwlegacy/iwl3945.ko): Unknown symbol in module, or unknown parameter (see dmesg)
:~$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
:~$ 

then even logout doesn't make my wireless work again. I restart and then I get back to internet.

---

### Post by wildmanne39 on 2012-03-16
Hi, after you rebooted your computer those commands were reset so there is no lasting effects.

Please post the output of:
```
modinfo iwl3945
```
also it looks like you have a typo in the command please copy and paste all commands for accuracy.
thanks

---

### Post by dixcuxx on 2012-03-18
> **wildmanne39 said:**
> Hi, after you rebooted your computer those commands were reset so there is no lasting effects.

Please post the output of:
```
modinfo iwl3945
```
also it looks like you have a typo in the command please copy and paste all commands for accuracy.
thanks

I just copy and paste what I did...

I just tried:
:~$ modinfo iwl3945
filename:       /lib/modules/3.0.0-16-generic/kernel/drivers/net/wireless/iwlegacy/iwl3945.ko
firmware:       iwlwifi-3945-2.ucode
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:s
description:    Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
srcversion:     C44CD48BCAE08938796D099
alias:          pci:v00008086d00004227sv*sd*bc*sc*i*
alias:          pci:v00008086d00004222sv*sd*bc*sc*i*
alias:          pci:v00008086d00004227sv*sd00001014bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001044bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001034bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001005bc*sc*i*
depends:        iwl-legacy,cfg80211,mac80211
vermagic:       3.0.0-16-generic SMP mod_unload modversions 686 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           swcrypto:using software crypto (default 1 [software]) (int)
parm:           disable_hw_scan:disable hardware scanning (default 1) (int)
parm:           fw_restart:restart firmware in case of error (int)

---

### Post by wildmanne39 on 2012-03-18
Hi, lets try this:
```
sudo ifconfig wlan0 down
sudo rmmod -f iwl3945
sudo modprobe iwl3945 swcrypto=0
sudo ifconfig wlan0 up
```
again do not reboot.
thanks

---

### Post by dixcuxx on 2012-03-22
> **wildmanne39 said:**
> Hi, lets try this:
```
sudo ifconfig wlan0 down
sudo rmmod -f iwl3945
sudo modprobe iwl3945 swcrypto=0
sudo ifconfig wlan0 up
```
again do not reboot.
thanks

I just try:

:~$ sudo ifconfig wlan0 down
[sudo] password for : 
:~$ sudo rmmod -f iwl3945
:~$ sudo modprobe iwl3945 swcrpto=0
FATAL: Error inserting iwl3945 (/lib/modules/3.0.0-16-generic/kernel/drivers/net/wireless/iwlegacy/iwl3945.ko): Unknown symbol in module, or unknown parameter (see dmesg)
:~$ sudo modprobe iwl3945 swcrpto=0
FATAL: Error inserting iwl3945 (/lib/modules/3.0.0-16-generic/kernel/drivers/net/wireless/iwlegacy/iwl3945.ko): Unknown symbol in module, or unknown parameter (see dmesg)
:~$ sudo modprobe iwl3945 swcrpto=0
FATAL: Error inserting iwl3945 (/lib/modules/3.0.0-16-generic/kernel/drivers/net/wireless/iwlegacy/iwl3945.ko): Unknown symbol in module, or unknown parameter (see dmesg)
:~$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
:~$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
:~$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device

---

### Post by wildmanne39 on 2012-03-22
Hi, try this then please:
```
sudo ifconfig wlan0 down
sudo rmmod -f iwl3945
sudo modprobe iwl3945 disable_hw_scan=0
sudo ifconfig wlan0 up
```
Thanks

---

### Post by dixcuxx on 2012-03-26
> **wildmanne39 said:**
> Hi, try this then please:
```
sudo ifconfig wlan0 down
sudo rmmod -f iwl3945
sudo modprobe iwl3945 disable_hw_scan=0
sudo ifconfig wlan0 up
```
Thanks

wireless can reconnect after thes commands but still laggy.

---

### Post by wildmanne39 on 2012-03-26
Hi, also set your setting to match these screenshots please.
Thanks

---

