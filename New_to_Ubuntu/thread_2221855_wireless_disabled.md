---
title: "wireless disabled"
date: 2014-05-04
forum: New to Ubuntu
---

### Post by naveensimha100 on 2014-05-04
hi, 
    I just tried to install updates , it showed some error in kernel firmware installation but from then wireless is disabled(not being seen )
  could any one pls help me out.

---

### Post by varunendra on 2014-05-04
Welcome to Ubuntu Forums!

Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by naveensimha100 on 2014-05-06
this is the output for that code.....

```


########## wireless info START ##########


##### release #####


Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise


##### kernel #####


Linux NetajiBabuDell 3.2.0-61-generic #92-Ubuntu SMP Mon Mar 31 23:47:59 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


##### lspci #####


01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Dell Device [1028:0597]
    Kernel driver in use: r8169


02:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: Dell Device [1028:020c]


##### lsusb #####


Bus 001 Device 022: ID 0cf3:0036 Atheros Communications, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 005: ID 1bcf:28a2 Sunplus Innovation Technology Inc. 


##### PCMCIA Card Info #####


##### rfkill #####


0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
10: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### iw reg get #####


##### interfaces #####


auto lo
iface lo inet loopback


##### iwconfig #####


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.22.47.254    0.0.0.0         UG    0      0        0 eth0
10.22.44.0      0.0.0.0         255.255.252.0   U     0      0        0 eth0


##### resolv.conf #####


nameserver 10.65.0.3
nameserver 10.65.0.2
nameserver 127.0.0.1
search iitm.ac.in


##### nm-tool #####


NetworkManager Tool


State: connected (global)


- Device: eth0  [iitm lan] -----------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         10.22.44.213
    Prefix:          22 (255.255.252.0)
    Gateway:         10.22.47.254


    DNS:             10.65.0.3
    DNS:             10.65.0.2


##### NetworkManager.state #####


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf #####


[main]
plugins=ifupdown,keyfile
dns=dnsmasq


no-auto-default=<MAC address removed>,


[ifupdown]
managed=false


##### iwlist #####


##### iwlist channel #####


##### lsmod #####


ath3k                  12910  0 
bluetooth             180113  24 bnep,rfcomm,btusb,ath3k


##### modinfo #####


filename:       /lib/modules/3.2.0-61-generic/updates/dkms/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0.1
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     20FBBCFB082574AA82607C8
alias:          usb:v0489pE036d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0489pE03Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0489pE02Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0489pE056d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0489pE04Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3393d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0489pE057d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0930p0219d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3pE004d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3362d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04CAp3008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04CAp3006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04CAp3005d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3375d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p311Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p3004d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p0036d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v03F0p311Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0489pE027d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0489pE03Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0930p0215d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3304d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3pE019d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p3002d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p3000d*dc*dsc*dp*ic*isc*ip*
depends:        bluetooth
vermagic:       3.2.0-61-generic SMP mod_unload modversions 


##### modules #####


lp
rtc
lp
rtc


##### blacklist #####


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
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


##### udev rules #####


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #####


[   20.671305] Bluetooth: Atheros AR30xx firmware driver ver 1.0.1
[ 2756.464783] usb 1-1.1: device firmware changed
[ 4369.625494] usb 1-1.1: device firmware changed
[13259.755894] usb 1-1.1: device firmware changed
[23031.698037] usb 1-1.1: device firmware changed
[30953.719874] usb 1-1.1: device firmware changed
[38244.454018] usb 1-1.1: device firmware changed
[38278.488033] usb 1-1.1: device firmware changed
[39067.561991] usb 1-1.1: device firmware changed


########## wireless info END ############
```

---

### Post by varunendra on 2014-05-06
The driver in your current kernel doesn't have the required support included to drive your wireless card. Please follow the instructions in this post to install a newer driver that supports it : [http://ubuntuforums.org/showpost.php?p=12963298](http://ubuntuforums.org/showpost.php?p=12963298)

---

### Post by naveensimha100 on 2014-05-06
thank you very much....now its working fine........
one more query ..  is there any method to create hotspot that can be used by mobile phones also...
generally it is creating a hotspot that can be used by other computers only.....

---

### Post by varunendra on 2014-05-06
Glad it's working. As mentioned in the linked post, you'll have to compile the driver everytime a kernel upgrade happens. However, you won't have to do that once the kernel is upgraded to version 3.9 or later. You can do that by upgrading your **[Hardware Enablement Stack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")**, or by doing a fresh install of Ubuntu 12.04.4 or 14.04.

About the hotspot question - sorry, I don't have sufficient experience with that to be able to suggest anything useful. Maybe ask the question in a new thread with a relevant title, so that it catches attention of those who may possibly help with that. Good luck in advance! :)

---

### Post by naveensimha100 on 2014-05-07
thanks a lot........

---

