---
title: "connection failed: bad password"
date: 2014-02-15
forum: New to Ubuntu
---

### Post by maor2 on 2014-02-15
Hello,
I have problem with connecting to my home wifi.
I get this error :
[ATTACH=CONFIG]250353[/ATTACH]

After searching the net, I saw that the problem is common
No solution to what I read did not help.
Please help..

---

### Post by deadflowr on 2014-02-15
You seem to have, (from the little info I can see in the screenshot) quite a few connection options.
Are you sure you're trying to connect to the right one?

---

### Post by maor2 on 2014-02-15
> **deadflowr said:**
> You seem to have, (from the little info I can see in the screenshot) quite a few connection options.
Are you sure you're trying to connect to the right one?
Yes!:P

---

### Post by varunendra on 2014-02-16
Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by oldos2er on 2014-02-16
> **maor2 said:**
> After searching the net, I saw that the problem is common
No solution to what I read did not help.
Please help..

Please tell us which OS and version number you're using.

---

### Post by maor2 on 2014-02-16
```



*************** info trace ***************


***** uname -a *****


Linux bt 3.2.6 #1 SMP Fri Feb 17 10:40:05 EST 2012 i686 GNU/Linux


***** lsb_release *****


Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.3 LTS
Release:	10.04
Codename:	lucid


***** lspci *****


02:01.0 Ethernet controller [0200]: Advanced Micro Devices [AMD] 79c970 [PCnet32 LANCE] [1022:2000] (rev 10)
	Kernel driver in use: pcnet32
	Kernel modules: pcnet32
02:02.0 Multimedia audio controller [0401]: Ensoniq ES1371 [AudioPCI-97] [1274:1371] (rev 02)
	Kernel driver in use: snd_ens1371


***** lsusb *****


Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter
Bus 001 Device 005: ID 0781:5567 SanDisk Corp. Cruzer Blade
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


***** PCMCIA Card Info *****




***** iwconfig *****


wlan0     unassociated  Nickname:"rtl_wifi"
          Mode:Managed  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0




***** rfkill *****




***** lsmod *****


r8712u                158277  0 


***** nm-tool *****


***** NetworkManager.state *****


***** NetworkManager.conf *****




***** interfaces *****


auto lo
iface lo inet loopback


auto eth0
iface eth0 inet dhcp


auto eth1
iface eth1 inet dhcp


auto eth2
iface eth2 inet dhcp


auto ath0
iface ath0 inet dhcp


auto wlan0
iface wlan0 inet dhcp




***** iwlist *****


Aquiring of root rights failed.


***** resolv.conf *****


nameserver 192.168.32.2
domain localdomain
search localdomain


***** blacklist *****


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist-bt.conf]
blacklist rt2870sta
blacklist rt2860sta


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist ar9170usb
blacklist r8187
blacklist ath_pci
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


***** modinfo *****


filename:       /lib/modules/3.2.6/kernel/drivers/staging/rtl8712/r8712u.ko
firmware:       rtlwifi/rtl8712u.bin
author:         Larry Finger
description:    rtl871x wireless lan driver
license:        GPL
srcversion:     1D6630D0C1EF297AB671BBC
alias:          usb:v0409p02B6d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7622d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp0051d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp845Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8174d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8174d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3325d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3310d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3341d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3340d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3339d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04F2pAFF6d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04F2pAFF5d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04F2pAFF2d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3302d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3301d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3300d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0064d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p004Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0049d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0058d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019p4901d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED18d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3306d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0015d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v06F8pE031d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9605d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7612d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3303d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3300d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3302d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp815Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3309d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3336d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3335d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3334d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3333d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3342d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3311d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3323d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8172d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0EB0p9061d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8172d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApC512d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v20F4p646Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0752d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp5077d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0154d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0063d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p005Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p005Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p004Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0059d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0045d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0057d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED16d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB28d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0167d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v06F8pE032d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v06F8pE034d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0016d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9603d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7611d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3306d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3306d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp0047d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp945Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1791d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1786d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p8188d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDApC512d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8713d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8712d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8173d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8171d*dc*dsc*dp*ic*isc*ip*
depends:        
staging:        Y
intree:         Y
vermagic:       3.2.6 SMP mod_unload CORE2 
parm:           wifi_test:int
parm:           video_mode:int
parm:           chip_version:int
parm:           rfintfs:int
parm:           lbkmode:int
parm:           hci:int
parm:           network_mode:int
parm:           channel:int
parm:           mp_mode:int
parm:           wmm_enable:int
parm:           vrtl_carrier_sense:int
parm:           vcs_type:int
parm:           busy_thresh:int
parm:           ht_enable:int
parm:           cbw40_enable:int
parm:           ampdu_enable:int
parm:           rf_config:int
parm:           power_mgnt:int
parm:           low_power:int
parm:           ifname: Net interface name, wlan%d=default (string)
parm:           initmac:MAC-Address, default: use FUSE (charp)




***** udev rules *****


# PCI device 0x1022:0x2000 (pcnet32)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# USB device 0x0bda:0x8172 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


***** dmesg *****


[  774.197384] r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[  774.216728] r8712u: DriverVersion: v7_0.20100831
[  774.218650] r8712u: register rtl8712_netdev_ops to netdev_ops
[  774.218993] r8712u: USB_SPEED_HIGH with 4 endpoints
[  774.226664] r8712u: Boot from EFUSE: Autoload OK
[  780.050521] r8712u: CustomerID = 0x0000
[  780.050727] r8712u: MAC Address from efuse = <MAC address removed>
[  780.050816] r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[  781.339449] r8712u: 1 RCR=0x153f00e
[  781.345320] r8712u: 2 RCR=0x553f00e
[  781.491856] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  883.632101] r8712u: DriverVersion: v7_0.20100831
[  883.632134] r8712u: register rtl8712_netdev_ops to netdev_ops
[  883.632140] r8712u: USB_SPEED_HIGH with 4 endpoints
[  883.636723] r8712u: Boot from EFUSE: Autoload OK
[  889.500877] r8712u: CustomerID = 0x0000
[  889.500901] r8712u: MAC Address from efuse = <MAC address removed>
[  889.500907] r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[  890.781113] r8712u: 1 RCR=0x153f00e
[  890.787248] r8712u: 2 RCR=0x553f00e
[  890.929854] ADDRCONF(NETDEV_UP): wlan0: link is not ready


****************** done ******************




```

And im using Ubuntu 2.30.2

---

### Post by Yellow Pasque on 2014-02-16
Backtrack is not supported on these forums, and you seem to be running an ancient version of it based off Ubuntu 10.04 (which is EOL itself). Please use the forums provided by Backtrack.

```
r8712u: module is from the staging directory, the quality is unknown, you have been warned.
wlan0: link is not ready
```

---

### Post by deadflowr on 2014-02-16
Quick note, 10.04 is end of life on the desktop.
Don't know what you mean by Ubuntu 2.30.2.

Edit: +1 to post#7

---

### Post by varunendra on 2014-02-16
> **maor2 said:**
> After searching the net, I saw that the problem is common

Yes the problem is common, and seeing your current version of the kernel/os, I must say the suggestion is common too - "Upgrade your OS to a version that offers the newer and better driver(s)".

Your current version is not worth putting too much efforts in troubleshooting.

---

### Post by oldos2er on 2014-02-16
> **maor2 said:**
> And im using Ubuntu 2.30.2

There's no such thing. If you're using Backtrack or Kali, you need to get help from their forums.

[http://www.backtrack-linux.org/forums/forum.php](http://www.backtrack-linux.org/forums/forum.php)

[http://forums.kali.org/](http://forums.kali.org/)

---

### Post by Yellow Pasque on 2014-02-16
2.30.2 = GNOME version

---

