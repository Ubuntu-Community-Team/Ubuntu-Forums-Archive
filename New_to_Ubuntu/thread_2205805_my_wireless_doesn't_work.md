---
title: "my wireless doesn't work"
date: 2014-02-16
forum: New to Ubuntu
---

### Post by show2 on 2014-02-16
computer:HP Pavilion dv4-5a02
I installed ubuntu 12.04 yesterday. But the wireless didn't work. 
And anything do right in my Windows 7 system.
I have tried many ways that I get from Google. 

There is Broadcom STA wireless driver in Additional Drivers. And it says" This driver is activated but not currently in use".

I have tried to use ndiswrapper. I installed the driver but got an error "Module ndiswrapper not found". But after that I can still see the driver was installed.

I am new one here. Please help me! Thanks!

---

### Post by varunendra on 2014-02-16
Welcome to the forums show2 !

Please open a terminal (Ctrl-Alt-T) and post back the outputs of the following commands -
```
lspci -nnk | grep -iA2 net
lsmod | egrep 'b43|wl|brcm|ssb|ndis'
```

Ndiswrapper is and should be last resort, when it is confirmed that there is no supporting native linux driver for your card.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by show2 on 2014-02-16
Thanks.Here is the result.

The first command return:
```
08:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)	Subsystem: Hewlett-Packard Company Device [103c:1795]
	Kernel modules: wl, bcma
0a:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Hewlett-Packard Company Device [103c:18f4]
	Kernel driver in use: r8169



```
And the second one return nothing.

---

### Post by varunendra on 2014-02-16
> **show2 said:**
> ...And the second one return nothing.

Which, if the command was run correctly, means trouble.

Please try -
```
sudo apt-get purge bcmwl-kernel-source
sudo modprobe -rv ndiswrapper
sudo apt-get purge ndisgtk ndiswrapper*
sudo rm /etc/modprobe.d/ndis*
sudo rm -r /etc/ndiswrapper
```
If Ndiswrapper was not installed, you only need the first command. If not sure, run all of them anyway. Reboot after this and check -
```
lsmod | egrep 'wl|brcm|ndis'
```
You should see only **brcmsmac** and its supporting drivers. If still can't connect, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

---

### Post by show2 on 2014-02-16
I have tried your code and reboot my computer, but it seems don't work.
here is the wireless-info.txt
```



*************** info trace ***************


***** uname -a *****


Linux show5-HP-Pavilion-dv4-Notebook-PC 3.11.0-15-generic #25~precise1-Ubuntu SMP Thu Jan 30 17:42:40 UTC 2014 i686 i686 i386 GNU/Linux


***** lsb_release *****


Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.4 LTS
Release:	12.04
Codename:	precise


***** lspci *****


08:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:1795]
	Kernel driver in use: bcma-pci-bridge
--
0a:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Hewlett-Packard Company Device [103c:18f4]
	Kernel driver in use: r8169


***** lsusb *****


Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 05c8:033a Cheng Uei Precision Industry Co., Ltd (Foxlink) 


***** PCMCIA Card Info *****




***** iwconfig *****


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


***** rfkill *****


1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
2: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
3: hp-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: yes


***** lsmod *****


brcmsmac              534235  0 
mac80211              534884  1 brcmsmac
brcmutil               15066  1 brcmsmac
cfg80211              416271  2 brcmsmac,mac80211
cordic                 12518  1 brcmsmac
bcma                   41297  2 brcmsmac


***** nm-tool *****


NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
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
    Address:         192.168.0.103
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             192.168.1.1




- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 






***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


***** NetworkManager.conf *****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq


[ifupdown]
managed=false


***** interfaces *****


auto lo
iface lo inet loopback




***** iwlist *****




***** resolv.conf *****


nameserver 127.0.0.1


***** blacklist *****


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
blacklist b43
blacklist ssb 
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


***** modinfo *****


filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     DB4E5CDF31AA9B12B2BA2C0
alias:          bcma:m04BFid0812rev18cl*
alias:          bcma:m04BFid0812rev17cl*
alias:          bcma:m04BFid0812rev11cl*
depends:        mac80211,bcma,brcmutil,cfg80211,cordic
intree:         Y
vermagic:       3.11.0-15-generic SMP mod_unload modversions 686 


filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     E81EE4CBB6A7A689150D93D
depends:        
intree:         Y
vermagic:       3.11.0-15-generic SMP mod_unload modversions 686 


filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     67ADEA6E309FDB9FC19CBCF
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004365sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004359sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004358sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004331sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A8D8sv*sd*bc*sc*i*
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.11.0-15-generic SMP mod_unload modversions 686 




***** udev rules *****


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.5/0000:0a:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:08:00.0/bcma0:0 (bcma-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:08:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


***** dmesg *****


[    8.443118] bcma: bus0: Found chip with id 0x4313, rev 0x01 and package 0x08
[    8.443152] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x24, class 0x0)
[    8.443179] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x18, class 0x0)
[    8.443233] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x11, class 0x0)
[    8.455820] bcma: bus0: Bus registered
[    9.301751] Bluetooth: can't load firmware, may not work correctly
[    9.947640] brcmsmac bcma0:0: mfg 4bf core 812 rev 24 class 0 irq 17
[   10.171915] ieee80211 phy0: registered radio enabled led device: brcmsmac-phy0:radio gpio: 243
[   14.193055] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   14.193066] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[   14.193685] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.193971] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.845931] wlan0: authenticate with <MAC address removed>
[   16.849858] wlan0: send auth to <MAC address removed> (try 1/3)
[   16.851431] wlan0: authenticated
[   16.853396] wlan0: associate with <MAC address removed> (try 1/3)
[   16.856984] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=7)
[   16.857691] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[   16.857694] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[   16.857699] wlan0: associated
[   16.857706] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   26.881213] wlan0: disassociating from <MAC address removed> by local choice (reason=3)
[   26.882368] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[   26.882375] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   26.883244] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   27.718145] wlan0: authenticate with <MAC address removed>
[   27.720039] wlan0: send auth to <MAC address removed> (try 1/3)
[   27.742082] wlan0: authenticated
[   27.745817] wlan0: associate with <MAC address removed> (try 1/3)
[   27.748866] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=7)
[   27.749550] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[   27.749554] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[   27.749564] wlan0: associated
[   35.816470] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[   35.854691] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[   35.854697] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   36.788426] wlan0: authenticate with <MAC address removed>
[   36.790378] wlan0: send auth to <MAC address removed> (try 1/3)
[   36.812088] wlan0: authenticated
[   36.816202] wlan0: associate with <MAC address removed> (try 1/3)
[   36.820205] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=7)
[   36.820833] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[   36.820836] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[   36.820842] wlan0: associated
[   40.794508] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   40.795468] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[   40.795474] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)


****************** done ******************



```

---

### Post by varunendra on 2014-02-16
The driver seems to have been correctly loaded now. However, the wireless seems to be turned off by the hardware switch -
> **show2 said:**
> ```

***** rfkill *****


1: **phy0: Wireless LAN**
	Soft blocked: no
	**Hard blocked: [COLOR="#FF0000"]yes[/COLOR]**
2: **hp-wifi: Wireless LAN**
	Soft blocked: no
	**Hard blocked: [COLOR="#FF0000"]yes[/COLOR]**
3: hp-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: yes

```

Please try the switch or key combination that is used to toggle the wireless on/off. It may be dodgy sometimes, especially in HP laptops.

If the switch doesn't seem to be working, and if this is not a UEFI based system dualbooting with windows, try resetting your BIOS to enable the hardware switch.

---

### Post by show2 on 2014-02-16
The wireless disconnected after I turn on the switch. But I find the computer can connected to my mobile phone's hotspot.
Maybe there is something wrong with my wireless router. I need to have a check.

Thanks for your help!!

---

### Post by varunendra on 2014-02-16
Check the outputs of -
```
rfkill list all
sudo iwlist scan
```
Does the first command show phy0 and hp-wifi as both soft/hard unblocked?
If yes, does the second command show any scan results?

If the wireless is unblocked now, but still can't scan or connect to available networks, run the wireless_script again and post back its fresh report.

---

### Post by show2 on 2014-02-16
The first one shows they were unblocked.
 And the second one got:```

wlan0     Scan completed :
          Cell 01 - Address: C8:3A:35:2A:AD:00
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"Tenda_2AAD00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000009a1d327b6
                    Extra: Last beacon: 20ms ago
                    IE: Unknown: 000C54656E64615F324141443030
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7E181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B0F0400000000000000000000000000000000000000
                    IE: Unknown: DD090010180202F02C0000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00


lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.



```



And I run the script again, I got

```



*************** info trace ***************


***** uname -a *****


Linux show5-HP-Pavilion-dv4-Notebook-PC 3.11.0-15-generic #25~precise1-Ubuntu SMP Thu Jan 30 17:42:40 UTC 2014 i686 i686 i386 GNU/Linux


***** lsb_release *****


Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.4 LTS
Release:	12.04
Codename:	precise


***** lspci *****


08:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:1795]
	Kernel driver in use: bcma-pci-bridge
--
0a:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Hewlett-Packard Company Device [103c:18f4]
	Kernel driver in use: r8169


***** lsusb *****


Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 05c8:033a Cheng Uei Precision Industry Co., Ltd (Foxlink) 


***** PCMCIA Card Info *****




***** iwconfig *****


wlan0     IEEE 802.11bgn  ESSID:"Tenda_2AAD00"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC address removed>   
          Bit Rate=6.5 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=39/70  Signal level=-71 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:6  Invalid misc:0   Missed beacon:0




***** rfkill *****


1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: hp-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no


***** lsmod *****


brcmsmac              534235  0 
mac80211              534884  1 brcmsmac
brcmutil               15066  1 brcmsmac
cfg80211              416271  2 brcmsmac,mac80211
cordic                 12518  1 brcmsmac
bcma                   41297  2 brcmsmac


***** nm-tool *****


NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
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
    Address:         192.168.0.103
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             192.168.1.1




- Device: wlan0  [Tenda_2AAD00] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             connecting (configuring)
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 
    Tenda_2AAD00:    Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA






***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


***** NetworkManager.conf *****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq


[ifupdown]
managed=false


***** interfaces *****


auto lo
iface lo inet loopback




***** iwlist *****


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"Tenda_2AAD00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000009994a6ab3
                    Extra: Last beacon: 40ms ago
                    IE: Unknown: 000C54656E64615F324141443030
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7E181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B0F0400000000000000000000000000000000000000
                    IE: Unknown: DD090010180204F02C0000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00




***** resolv.conf *****


nameserver 127.0.0.1


***** blacklist *****


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
blacklist b43
blacklist ssb 
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


***** modinfo *****


filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     DB4E5CDF31AA9B12B2BA2C0
alias:          bcma:m04BFid0812rev18cl*
alias:          bcma:m04BFid0812rev17cl*
alias:          bcma:m04BFid0812rev11cl*
depends:        mac80211,bcma,brcmutil,cfg80211,cordic
intree:         Y
vermagic:       3.11.0-15-generic SMP mod_unload modversions 686 


filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     E81EE4CBB6A7A689150D93D
depends:        
intree:         Y
vermagic:       3.11.0-15-generic SMP mod_unload modversions 686 


filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     67ADEA6E309FDB9FC19CBCF
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004365sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004359sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004358sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004331sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A8D8sv*sd*bc*sc*i*
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.11.0-15-generic SMP mod_unload modversions 686 




***** udev rules *****


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.5/0000:0a:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:08:00.0/bcma0:0 (bcma-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:08:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


***** dmesg *****


[   10.171915] ieee80211 phy0: registered radio enabled led device: brcmsmac-phy0:radio gpio: 243
[   14.193055] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   14.193066] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[   14.193685] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.193971] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.845931] wlan0: authenticate with <MAC address removed>
[   16.849858] wlan0: send auth to <MAC address removed> (try 1/3)
[   16.851431] wlan0: authenticated
[   16.853396] wlan0: associate with <MAC address removed> (try 1/3)
[   16.856984] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=7)
[   16.857691] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[   16.857694] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[   16.857699] wlan0: associated
[   16.857706] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   26.881213] wlan0: disassociating from <MAC address removed> by local choice (reason=3)
[   26.882368] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[   26.882375] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   26.883244] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   27.718145] wlan0: authenticate with <MAC address removed>
[   27.720039] wlan0: send auth to <MAC address removed> (try 1/3)
[   27.742082] wlan0: authenticated
[   27.745817] wlan0: associate with <MAC address removed> (try 1/3)
[   27.748866] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=7)
[   27.749550] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[   27.749554] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[   27.749564] wlan0: associated
[   35.816470] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[   35.854691] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[   35.854697] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   36.788426] wlan0: authenticate with <MAC address removed>
[   36.790378] wlan0: send auth to <MAC address removed> (try 1/3)
[   36.812088] wlan0: authenticated
[   36.816202] wlan0: associate with <MAC address removed> (try 1/3)
[   36.820205] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=7)
[   36.820833] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[   36.820836] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[   36.820842] wlan0: associated
[   40.794508] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   40.795468] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[   40.795474] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1463.918807] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1463.918816] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[ 1463.919435] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1466.230909] wlan0: authenticate with <MAC address removed>
[ 1466.232291] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1466.235340] wlan0: authenticated
[ 1466.237949] wlan0: associate with <MAC address removed> (try 1/3)
[ 1466.262780] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 1466.263237] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1466.263245] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1466.263262] wlan0: associated
[ 1466.263280] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1466.809901] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1466.810913] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1466.810923] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1476.768766] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1476.768775] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[ 1476.769405] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1479.047135] wlan0: authenticate with <MAC address removed>
[ 1479.048528] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1479.050188] wlan0: authenticated
[ 1479.054202] wlan0: associate with <MAC address removed> (try 1/3)
[ 1479.057332] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 1479.057933] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1479.057940] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1479.057956] wlan0: associated
[ 1479.057973] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1487.071539] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 1487.083533] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1487.083549] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1488.016952] wlan0: authenticate with <MAC address removed>
[ 1488.018330] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1488.019997] wlan0: authenticated
[ 1488.023954] wlan0: associate with <MAC address removed> (try 1/3)
[ 1488.027120] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 1488.027720] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1488.027726] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1488.027741] wlan0: associated
[ 1496.062134] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 1496.073316] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1496.073332] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1497.006333] wlan0: authenticate with <MAC address removed>
[ 1497.007997] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1497.009584] wlan0: authenticated
[ 1497.013684] wlan0: associate with <MAC address removed> (try 1/3)
[ 1497.017098] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 1497.018611] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1497.018623] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1497.018636] wlan0: associated
[ 1505.052983] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 1505.062985] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1505.062998] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1505.996534] wlan0: authenticate with <MAC address removed>
[ 1505.997847] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1505.999526] wlan0: authenticated
[ 1506.003520] wlan0: associate with <MAC address removed> (try 1/3)
[ 1506.010582] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 1506.011142] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1506.011148] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1506.011164] wlan0: associated
[ 1512.185388] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1512.186453] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1512.186459] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1517.803062] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1517.803078] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[ 1517.803739] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1524.799409] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1524.799425] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[ 1524.800103] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1527.098135] wlan0: authenticate with <MAC address removed>
[ 1527.099449] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1527.101041] wlan0: authenticated
[ 1527.105046] wlan0: associate with <MAC address removed> (try 1/3)
[ 1527.108408] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 1527.109025] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1527.109037] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1527.109055] wlan0: associated
[ 1527.109106] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1537.401807] wlan0: deauthenticated from <MAC address removed> (Reason: 16)
[ 1537.429671] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1537.429684] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1538.365220] wlan0: authenticate with <MAC address removed>
[ 1538.366640] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1538.368282] wlan0: authenticated
[ 1538.372290] wlan0: associate with <MAC address removed> (try 1/3)
[ 1538.375461] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 1538.376046] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1538.376053] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1538.376068] wlan0: associated
[ 1553.591175] wlan0: deauthenticated from <MAC address removed> (Reason: 16)
[ 1553.614593] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1553.614610] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1554.547778] wlan0: authenticate with <MAC address removed>
[ 1554.549072] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1554.550693] wlan0: authenticated
[ 1554.554679] wlan0: associate with <MAC address removed> (try 1/3)
[ 1554.557849] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 1554.558465] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1554.558472] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1554.558488] wlan0: associated
[ 1574.983151] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1574.984983] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1574.984990] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1578.631086] wlan0: authenticate with <MAC address removed>
[ 1578.632499] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1578.634170] wlan0: authenticated
[ 1578.638136] wlan0: associate with <MAC address removed> (try 1/3)
[ 1578.641363] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 1578.641964] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1578.641970] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1578.641986] wlan0: associated
[ 1586.650714] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 1586.666039] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1586.666054] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1587.600777] wlan0: authenticate with <MAC address removed>
[ 1587.602232] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1587.603865] wlan0: authenticated
[ 1587.607894] wlan0: associate with <MAC address removed> (try 1/3)
[ 1587.618053] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 1587.618489] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1587.618495] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1587.618512] wlan0: associated
[ 1634.025219] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1634.026281] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1634.026288] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1637.677188] wlan0: authenticate with <MAC address removed>
[ 1637.678428] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1637.679994] wlan0: authenticated
[ 1637.684067] wlan0: associate with <MAC address removed> (try 1/3)
[ 1637.687219] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 1637.687846] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1637.687852] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1637.687867] wlan0: associated
[ 1645.771393] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 1645.785374] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1645.785390] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1646.718277] wlan0: authenticate with <MAC address removed>
[ 1646.720092] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1646.724013] wlan0: authenticated
[ 1646.725841] wlan0: associate with <MAC address removed> (try 1/3)
[ 1646.734004] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 1646.734669] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1646.734672] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1646.734680] wlan0: associated
[ 1654.822798] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 1654.832172] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1654.832186] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1655.768359] wlan0: authenticate with <MAC address removed>
[ 1655.770094] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1655.771759] wlan0: authenticated
[ 1655.775710] wlan0: associate with <MAC address removed> (try 1/3)
[ 1655.778903] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 1655.779815] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1655.779824] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1655.779842] wlan0: associated
[ 1663.792967] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 1663.801142] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1663.801154] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1664.735268] wlan0: authenticate with <MAC address removed>
[ 1664.736779] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1664.738397] wlan0: authenticated
[ 1664.742359] wlan0: associate with <MAC address removed> (try 1/3)
[ 1664.745550] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 1664.746138] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1664.746144] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1664.746160] wlan0: associated
[ 1716.100093] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1716.101110] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1716.101118] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1719.761576] wlan0: authenticate with <MAC address removed>
[ 1719.763406] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1719.764991] wlan0: authenticated
[ 1719.769118] wlan0: associate with <MAC address removed> (try 1/3)
[ 1719.774172] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=16)
[ 1719.774771] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1719.774777] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1719.774793] wlan0: associated
[ 1727.789894] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 1727.794504] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1727.794520] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1728.728236] wlan0: authenticate with <MAC address removed>
[ 1728.729674] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1728.731705] wlan0: authenticated
[ 1728.735367] wlan0: associate with <MAC address removed> (try 1/3)
[ 1728.738551] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=16)
[ 1728.739151] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1728.739158] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1728.739173] wlan0: associated
[ 1736.770492] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 1736.785234] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1736.785249] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1737.722253] wlan0: authenticate with <MAC address removed>
[ 1737.723927] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1737.725580] wlan0: authenticated
[ 1737.729630] wlan0: associate with <MAC address removed> (try 1/3)
[ 1737.739616] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 1737.740267] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1737.740274] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1737.740287] wlan0: associated
[ 1745.771217] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 1745.785961] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1745.785977] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1746.721005] wlan0: authenticate with <MAC address removed>
[ 1746.722427] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1746.724015] wlan0: authenticated
[ 1746.727919] wlan0: associate with <MAC address removed> (try 1/3)
[ 1746.731100] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 1746.731699] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1746.731705] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1746.731721] wlan0: associated
[ 1754.938672] wlan0: deauthenticated from <MAC address removed> (Reason: 7)
[ 1754.949446] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1754.949458] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1755.882995] wlan0: authenticate with <MAC address removed>
[ 1755.884698] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1755.886368] wlan0: authenticated
[ 1755.890394] wlan0: associate with <MAC address removed> (try 1/3)
[ 1755.893510] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 1755.894191] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1755.894197] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1755.894213] wlan0: associated
[ 1763.933040] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 1763.943749] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1763.943766] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1764.877496] wlan0: authenticate with <MAC address removed>
[ 1764.879009] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1764.880836] wlan0: authenticated
[ 1764.884643] wlan0: associate with <MAC address removed> (try 1/3)
[ 1764.888068] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 1764.888704] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1764.888710] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1764.888725] wlan0: associated
[ 1772.913805] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 1772.926040] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1772.926054] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1773.859482] wlan0: authenticate with <MAC address removed>
[ 1773.861187] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1773.862812] wlan0: authenticated
[ 1773.866881] wlan0: associate with <MAC address removed> (try 1/3)
[ 1773.869997] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 1773.870687] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1773.870690] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1773.870697] wlan0: associated
[ 1778.966209] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1778.967404] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1778.967420] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1794.591190] wlan0: authenticate with <MAC address removed>
[ 1794.592869] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1794.698661] wlan0: send auth to <MAC address removed> (try 2/3)
[ 1794.700250] wlan0: authenticated
[ 1794.702723] wlan0: associate with <MAC address removed> (try 1/3)
[ 1794.705966] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 1794.706579] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1794.706587] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1794.706604] wlan0: associated
[ 1802.719486] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 1802.728044] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1802.728060] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1803.661560] wlan0: authenticate with <MAC address removed>
[ 1803.663349] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1803.664932] wlan0: authenticated
[ 1803.668946] wlan0: associate with <MAC address removed> (try 1/3)
[ 1803.672101] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 1803.672741] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1803.672747] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1803.672762] wlan0: associated
[ 1811.690156] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 1811.702397] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1811.702411] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1812.636320] wlan0: authenticate with <MAC address removed>
[ 1812.637694] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1812.639317] wlan0: authenticated
[ 1812.643213] wlan0: associate with <MAC address removed> (try 1/3)
[ 1812.646587] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 1812.647214] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1812.647223] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1812.647240] wlan0: associated
[ 1820.660814] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 1820.672820] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1820.672834] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1821.606513] wlan0: authenticate with <MAC address removed>
[ 1821.607911] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1821.609524] wlan0: authenticated
[ 1821.613415] wlan0: associate with <MAC address removed> (try 1/3)
[ 1821.619090] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 1821.619677] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1821.619683] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1821.619699] wlan0: associated
[ 1829.631545] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 1829.643337] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1829.643353] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1830.580716] wlan0: authenticate with <MAC address removed>
[ 1830.582092] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1830.583766] wlan0: authenticated
[ 1830.587667] wlan0: associate with <MAC address removed> (try 1/3)
[ 1830.596882] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 1830.598260] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1830.598266] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1830.598283] wlan0: associated
[ 1838.602230] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 1838.617107] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1838.617126] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1839.550614] wlan0: authenticate with <MAC address removed>
[ 1839.552369] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1839.553986] wlan0: authenticated
[ 1839.557895] wlan0: associate with <MAC address removed> (try 1/3)
[ 1839.561068] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 1839.561666] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1839.561672] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1839.561688] wlan0: associated
[ 1847.572999] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 1847.587302] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1847.587317] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1848.521242] wlan0: authenticate with <MAC address removed>
[ 1848.522485] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1848.524177] wlan0: authenticated
[ 1848.528162] wlan0: associate with <MAC address removed> (try 1/3)
[ 1848.535262] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 1848.535835] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1848.535841] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1848.535857] wlan0: associated
[ 1854.053111] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1854.054207] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1854.054221] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1866.216767] wlan0: authenticate with <MAC address removed>
[ 1866.218619] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1866.220296] wlan0: authenticated
[ 1866.224361] wlan0: associate with <MAC address removed> (try 1/3)
[ 1866.227547] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 1866.228160] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1866.228166] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1866.228182] wlan0: associated
[ 1874.264800] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 1874.286525] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1874.286539] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1875.223521] wlan0: authenticate with <MAC address removed>
[ 1875.224931] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1875.226535] wlan0: authenticated
[ 1875.230622] wlan0: associate with <MAC address removed> (try 1/3)
[ 1875.233953] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 1875.234565] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1875.234572] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1875.234636] wlan0: associated
[ 1883.245682] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 1883.255971] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1883.256124] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1884.189793] wlan0: authenticate with <MAC address removed>
[ 1884.191370] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1884.194334] wlan0: authenticated
[ 1884.196876] wlan0: associate with <MAC address removed> (try 1/3)
[ 1884.200013] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 1884.200655] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1884.200665] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1884.200687] wlan0: associated
[ 1892.216512] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 1892.233458] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1892.233473] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1893.168216] wlan0: authenticate with <MAC address removed>
[ 1893.169644] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1893.174667] wlan0: authenticated
[ 1893.175134] wlan0: associate with <MAC address removed> (try 1/3)
[ 1893.178413] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=13)
[ 1893.178999] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1893.179006] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1893.179021] wlan0: associated
[ 1901.227153] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 1901.242825] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1901.242841] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1902.177933] wlan0: authenticate with <MAC address removed>
[ 1902.179740] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1902.181388] wlan0: authenticated
[ 1902.185446] wlan0: associate with <MAC address removed> (try 1/3)
[ 1902.190681] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=13)
[ 1902.191270] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1902.191279] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1902.191297] wlan0: associated
[ 1910.227852] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 1910.254770] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1910.254784] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1911.188611] wlan0: authenticate with <MAC address removed>
[ 1911.190096] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1911.191754] wlan0: authenticated
[ 1911.195710] wlan0: associate with <MAC address removed> (try 1/3)
[ 1911.198903] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=13)
[ 1911.199489] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1911.199495] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1911.199510] wlan0: associated
[ 1919.228699] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 1919.268248] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1919.268263] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1920.206604] wlan0: authenticate with <MAC address removed>
[ 1920.208285] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1920.209943] wlan0: authenticated
[ 1920.214009] wlan0: associate with <MAC address removed> (try 1/3)
[ 1920.217184] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=13)
[ 1920.217756] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1920.217763] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1920.217778] wlan0: associated
[ 1926.135991] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1926.137486] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1926.137500] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1957.245433] wlan0: authenticate with <MAC address removed>
[ 1957.246664] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1957.248314] wlan0: authenticated
[ 1957.252287] wlan0: associate with <MAC address removed> (try 1/3)
[ 1957.255487] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=13)
[ 1957.256117] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1957.256124] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1957.256140] wlan0: associated
[ 1965.304633] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 1965.325656] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1965.325671] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1966.259454] wlan0: authenticate with <MAC address removed>
[ 1966.260927] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1966.262653] wlan0: authenticated
[ 1966.266584] wlan0: associate with <MAC address removed> (try 1/3)
[ 1966.269768] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=13)
[ 1966.270368] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1966.270374] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1966.270390] wlan0: associated
[ 1974.284772] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 1974.311918] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1974.311933] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1975.245472] wlan0: authenticate with <MAC address removed>
[ 1975.247138] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1975.248814] wlan0: authenticated
[ 1975.252803] wlan0: associate with <MAC address removed> (try 1/3)
[ 1975.255915] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=13)
[ 1975.256568] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1975.256574] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1975.256590] wlan0: associated
[ 1983.265386] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 1983.296119] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1983.296137] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1984.232047] wlan0: authenticate with <MAC address removed>
[ 1984.233423] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1984.235140] wlan0: authenticated
[ 1984.239109] wlan0: associate with <MAC address removed> (try 1/3)
[ 1984.242318] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=13)
[ 1984.242918] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1984.242924] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1984.242940] wlan0: associated
[ 1992.286246] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 1992.292532] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1992.292545] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1993.226169] wlan0: authenticate with <MAC address removed>
[ 1993.227696] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1993.229345] wlan0: authenticated
[ 1993.233342] wlan0: associate with <MAC address removed> (try 1/3)
[ 1993.236499] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=13)
[ 1993.237112] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1993.237118] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1993.237134] wlan0: associated
[ 2001.287006] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 2001.306354] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2001.306369] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2002.240255] wlan0: authenticate with <MAC address removed>
[ 2002.241911] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2002.245581] wlan0: authenticated
[ 2002.247678] wlan0: associate with <MAC address removed> (try 1/3)
[ 2002.252413] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=13)
[ 2002.255324] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2002.255330] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2002.255348] wlan0: associated
[ 2010.307779] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 2010.316945] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2010.316951] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2011.250457] wlan0: authenticate with <MAC address removed>
[ 2011.252215] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2011.253969] wlan0: authenticated
[ 2011.257981] wlan0: associate with <MAC address removed> (try 1/3)
[ 2011.261178] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=13)
[ 2011.261779] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2011.261785] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2011.261801] wlan0: associated
[ 2016.237732] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2016.240793] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2016.240808] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2047.648411] wlan0: authenticate with <MAC address removed>
[ 2047.649807] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2047.651447] wlan0: authenticated
[ 2047.655505] wlan0: associate with <MAC address removed> (try 1/3)
[ 2047.658696] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=16)
[ 2047.659298] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2047.659309] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2047.659333] wlan0: associated
[ 2055.699155] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 2055.711135] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2055.711151] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2056.646864] wlan0: authenticate with <MAC address removed>
[ 2056.648128] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2056.658646] wlan0: authenticated
[ 2056.661770] wlan0: associate with <MAC address removed> (try 1/3)
[ 2056.664870] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=13)
[ 2056.665524] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2056.665534] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2056.665554] wlan0: associated
[ 2064.706476] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 2064.715111] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2064.715125] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2065.648686] wlan0: authenticate with <MAC address removed>
[ 2065.650363] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2065.652085] wlan0: authenticated
[ 2065.656074] wlan0: associate with <MAC address removed> (try 1/3)
[ 2065.659248] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=13)
[ 2065.661291] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2065.661298] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2065.661310] wlan0: associated
[ 2073.683797] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 2073.701462] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2073.701482] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2074.634998] wlan0: authenticate with <MAC address removed>
[ 2074.636824] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2074.638392] wlan0: authenticated
[ 2074.642303] wlan0: associate with <MAC address removed> (try 1/3)
[ 2074.645493] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=13)
[ 2074.646726] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2074.646732] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2074.646746] wlan0: associated
[ 2082.654529] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 2082.663636] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2082.663645] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2083.597570] wlan0: authenticate with <MAC address removed>
[ 2083.599014] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2083.602171] wlan0: authenticated
[ 2083.604523] wlan0: associate with <MAC address removed> (try 1/3)
[ 2083.607733] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=13)
[ 2083.608401] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2083.608411] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2083.608434] wlan0: associated
[ 2091.645983] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 2091.661777] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2091.661785] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2092.596092] wlan0: authenticate with <MAC address removed>
[ 2092.597161] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2092.598830] wlan0: authenticated
[ 2092.602775] wlan0: associate with <MAC address removed> (try 1/3)
[ 2092.605855] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=13)
[ 2092.606548] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2092.606554] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2092.606562] wlan0: associated
[ 2100.656325] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 2100.668135] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2100.668147] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2101.602061] wlan0: authenticate with <MAC address removed>
[ 2101.603430] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2101.605113] wlan0: authenticated
[ 2101.609097] wlan0: associate with <MAC address removed> (try 1/3)
[ 2101.612308] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=13)
[ 2101.612897] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2101.612903] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2101.612919] wlan0: associated
[ 2107.344538] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2107.345616] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2107.345623] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2115.733036] wlan0: authenticate with <MAC address removed>
[ 2115.734409] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2115.736104] wlan0: authenticated
[ 2115.740061] wlan0: associate with <MAC address removed> (try 1/3)
[ 2115.743220] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=13)
[ 2115.743863] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2115.743869] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2115.743884] wlan0: associated
[ 2123.794063] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 2123.818741] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2123.818758] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2124.755685] wlan0: authenticate with <MAC address removed>
[ 2124.757214] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2124.758936] wlan0: authenticated
[ 2124.762899] wlan0: associate with <MAC address removed> (try 1/3)
[ 2124.767070] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=13)
[ 2124.767704] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2124.767710] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2124.767727] wlan0: associated
[ 2132.815013] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 2132.832248] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2132.832254] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2133.766520] wlan0: authenticate with <MAC address removed>
[ 2133.768004] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2133.769706] wlan0: authenticated
[ 2133.773646] wlan0: associate with <MAC address removed> (try 1/3)
[ 2133.777413] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=13)
[ 2133.778076] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2133.778084] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2133.778095] wlan0: associated
[ 2141.855699] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 2141.872045] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2141.872053] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2142.809483] wlan0: authenticate with <MAC address removed>
[ 2142.810836] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2142.812548] wlan0: authenticated
[ 2142.816472] wlan0: associate with <MAC address removed> (try 1/3)
[ 2142.819660] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=13)
[ 2142.820276] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2142.820282] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2142.820298] wlan0: associated
[ 2150.856491] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 2150.869948] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2150.869964] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2151.804340] wlan0: authenticate with <MAC address removed>
[ 2151.805825] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2151.807464] wlan0: authenticated
[ 2151.811252] wlan0: associate with <MAC address removed> (try 1/3)
[ 2151.814443] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=13)
[ 2151.815046] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2151.815052] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2151.815068] wlan0: associated
[ 2159.827334] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 2159.839030] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2159.839044] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2160.774694] wlan0: authenticate with <MAC address removed>
[ 2160.776345] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2160.778061] wlan0: authenticated
[ 2160.781982] wlan0: associate with <MAC address removed> (try 1/3)
[ 2160.787125] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=13)
[ 2160.787713] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2160.787720] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2160.787738] wlan0: associated
[ 2168.828153] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 2168.846886] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2168.846903] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2169.781636] wlan0: authenticate with <MAC address removed>
[ 2169.783247] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2169.784895] wlan0: authenticated
[ 2169.788717] wlan0: associate with <MAC address removed> (try 1/3)
[ 2169.791836] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=13)
[ 2169.792518] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2169.792528] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2169.792547] wlan0: associated
[ 2175.456645] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2175.457743] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2175.457749] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2193.103655] wlan0: authenticate with <MAC address removed>
[ 2193.105317] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2193.107027] wlan0: authenticated
[ 2193.111027] wlan0: associate with <MAC address removed> (try 1/3)
[ 2193.114224] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=13)
[ 2193.114830] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2193.114836] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2193.114853] wlan0: associated
[ 2201.166960] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 2201.172460] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2201.172469] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2202.106939] wlan0: authenticate with <MAC address removed>
[ 2202.108359] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2202.115291] wlan0: authenticated
[ 2202.117842] wlan0: associate with <MAC address removed> (try 1/3)
[ 2202.128447] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=13)
[ 2202.129011] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2202.129018] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2202.129035] wlan0: associated
[ 2210.219127] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 2210.227228] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2210.227243] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2211.164484] wlan0: authenticate with <MAC address removed>
[ 2211.165946] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2211.167697] wlan0: authenticated
[ 2211.171597] wlan0: associate with <MAC address removed> (try 1/3)
[ 2211.174976] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=13)
[ 2211.175596] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2211.175604] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2211.175626] wlan0: associated
[ 2219.188607] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 2219.193014] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2219.193027] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2220.126599] wlan0: authenticate with <MAC address removed>
[ 2220.128206] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2220.129928] wlan0: authenticated
[ 2220.133835] wlan0: associate with <MAC address removed> (try 1/3)
[ 2220.137047] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=13)
[ 2220.137493] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2220.137499] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2220.137516] wlan0: associated
[ 2228.149345] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 2228.163060] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2228.163077] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2229.097154] wlan0: authenticate with <MAC address removed>
[ 2229.098393] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2229.103254] wlan0: authenticated
[ 2229.104022] wlan0: associate with <MAC address removed> (try 1/3)
[ 2229.109070] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=13)
[ 2229.109743] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2229.109757] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2229.109786] wlan0: associated
[ 2237.140150] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 2237.149443] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2237.149458] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2238.084596] wlan0: authenticate with <MAC address removed>
[ 2238.085013] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2238.086628] wlan0: authenticated
[ 2238.090297] wlan0: associate with <MAC address removed> (try 1/3)
[ 2238.094763] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=13)
[ 2238.095400] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2238.095406] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2238.095419] wlan0: associated
[ 2244.011814] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2244.012813] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2244.012819] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2244.947401] wlan0: authenticate with <MAC address removed>
[ 2244.950693] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2244.954484] wlan0: authenticated
[ 2244.958150] wlan0: associate with <MAC address removed> (try 1/3)
[ 2244.966383] wlan0: RX AssocResp from <MAC address removed> (capab=0x421 status=0 aid=1)
[ 2244.966962] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2244.966969] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2244.966985] wlan0: associated
[ 2247.791479] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 2289.655116] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2289.655130] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 2289.655135] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2290.587965] wlan0: authenticate with <MAC address removed>
[ 2290.589851] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2290.613898] wlan0: send auth to <MAC address removed> (try 2/3)
[ 2290.708905] wlan0: send auth to <MAC address removed> (try 3/3)
[ 2290.781642] wlan0: authentication with <MAC address removed> timed out
[ 2295.596655] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2296.749135] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2297.965452] wlan0: authenticate with <MAC address removed>
[ 2297.968879] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2297.970475] wlan0: authenticated
[ 2297.972345] wlan0: associate with <MAC address removed> (try 1/3)
[ 2297.975696] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 2297.976330] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2297.976340] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2297.976359] wlan0: associated
[ 2297.976388] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2305.992580] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 2306.001662] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2306.001676] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2306.939047] wlan0: authenticate with <MAC address removed>
[ 2306.940470] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2306.942928] wlan0: authenticated
[ 2306.946109] wlan0: associate with <MAC address removed> (try 1/3)
[ 2306.949311] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 2306.949883] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2306.949890] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2306.949905] wlan0: associated
[ 2314.963367] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 2314.978817] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2314.978831] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2315.913034] wlan0: authenticate with <MAC address removed>
[ 2315.914491] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2315.916113] wlan0: authenticated
[ 2315.919870] wlan0: associate with <MAC address removed> (try 1/3)
[ 2315.923065] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 2315.923665] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2315.923672] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2315.923687] wlan0: associated
[ 2323.964261] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 2323.980787] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2323.980803] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2324.916698] wlan0: authenticate with <MAC address removed>
[ 2324.918375] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2324.920093] wlan0: authenticated
[ 2324.924063] wlan0: associate with <MAC address removed> (try 1/3)
[ 2324.927195] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 2324.927867] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2324.927878] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2324.927898] wlan0: associated
[ 2332.944996] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 2332.953438] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2332.953453] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2333.887017] wlan0: authenticate with <MAC address removed>
[ 2333.888633] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2333.891258] wlan0: authenticated
[ 2333.894325] wlan0: associate with <MAC address removed> (try 1/3)
[ 2333.897447] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 2333.898112] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2333.898118] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2333.898131] wlan0: associated
[ 2341.915701] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 2341.927687] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2341.927702] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2342.861296] wlan0: authenticate with <MAC address removed>
[ 2342.862886] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2342.864613] wlan0: authenticated
[ 2342.868585] wlan0: associate with <MAC address removed> (try 1/3)
[ 2342.871775] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 2342.872373] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2342.872380] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2342.872395] wlan0: associated
[ 2350.906349] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 2350.919497] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2350.919514] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2351.855798] wlan0: authenticate with <MAC address removed>
[ 2351.857153] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2351.858885] wlan0: authenticated
[ 2351.862831] wlan0: associate with <MAC address removed> (try 1/3)
[ 2351.866082] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 2351.866699] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2351.866706] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2351.866721] wlan0: associated
[ 2356.650140] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2356.651249] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2356.651264] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2368.158108] wlan0: authenticate with <MAC address removed>
[ 2368.159776] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2368.161457] wlan0: authenticated
[ 2368.165419] wlan0: associate with <MAC address removed> (try 1/3)
[ 2368.168595] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 2368.169200] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2368.169207] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2368.169223] wlan0: associated
[ 2376.216568] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 2376.226798] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2376.226814] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2377.160633] wlan0: authenticate with <MAC address removed>
[ 2377.162108] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2377.163900] wlan0: authenticated
[ 2377.167746] wlan0: associate with <MAC address removed> (try 1/3)
[ 2377.171109] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 2377.171740] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2377.171748] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2377.171764] wlan0: associated
[ 2385.217486] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 2385.237089] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2385.237112] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2386.170912] wlan0: authenticate with <MAC address removed>
[ 2386.172387] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2386.174142] wlan0: authenticated
[ 2386.177995] wlan0: associate with <MAC address removed> (try 1/3)
[ 2386.181060] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 2386.181765] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2386.181771] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2386.181783] wlan0: associated
[ 2394.198163] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 2394.207348] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2394.207363] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2395.140647] wlan0: authenticate with <MAC address removed>
[ 2395.142485] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2395.146263] wlan0: authenticated
[ 2395.148232] wlan0: associate with <MAC address removed> (try 1/3)
[ 2395.151317] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 2395.152021] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2395.152032] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2395.152051] wlan0: associated
[ 2403.188844] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 2403.201466] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2403.201475] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2404.135277] wlan0: authenticate with <MAC address removed>
[ 2404.136855] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2404.138628] wlan0: authenticated
[ 2404.142503] wlan0: associate with <MAC address removed> (try 1/3)
[ 2404.147400] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 2404.148003] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2404.148010] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2404.148025] wlan0: associated
[ 2412.159530] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 2412.169591] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2412.169607] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2413.105815] wlan0: authenticate with <MAC address removed>
[ 2413.107156] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2413.108887] wlan0: authenticated
[ 2413.112762] wlan0: associate with <MAC address removed> (try 1/3)
[ 2413.119372] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 2413.119945] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2413.119952] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2413.119967] wlan0: associated
[ 2421.130247] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 2421.146147] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2421.146180] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2422.079856] wlan0: authenticate with <MAC address removed>
[ 2422.081601] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2422.083391] wlan0: authenticated
[ 2422.087052] wlan0: associate with <MAC address removed> (try 1/3)
[ 2422.090251] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 2422.090851] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2422.090857] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2422.090873] wlan0: associated
[ 2427.733014] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2427.736921] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2427.736936] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2559.469016] wlan0: authenticate with <MAC address removed>
[ 2559.472447] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2559.480487] wlan0: authenticated
[ 2559.481269] brcmsmac bcma0:0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 2559.483861] wlan0: associate with <MAC address removed> (try 1/3)
[ 2559.587974] wlan0: associate with <MAC address removed> (try 2/3)
[ 2559.631016] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 2559.631767] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2559.631774] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2559.631790] wlan0: associated
[ 2562.227376] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 2575.939287] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 0 addresses (implement)
[ 2575.941486] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2575.941947] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2575.941960] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2576.876483] wlan0: authenticate with <MAC address removed>
[ 2576.880351] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2576.882273] wlan0: authenticated
[ 2576.883847] wlan0: associate with <MAC address removed> (try 1/3)
[ 2576.887112] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=16)
[ 2576.887762] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2576.887765] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2576.887772] wlan0: associated
[ 2584.905924] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 2584.917243] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2584.917258] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2585.851259] wlan0: authenticate with <MAC address removed>
[ 2585.853213] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2585.854884] wlan0: authenticated
[ 2585.858583] wlan0: associate with <MAC address removed> (try 1/3)
[ 2585.861698] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 2585.862389] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2585.862399] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2585.862419] wlan0: associated
[ 2595.889557] wlan0: disassociating from <MAC address removed> by local choice (reason=3)
[ 2595.890832] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2595.890846] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2595.892278] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2596.725471] wlan0: authenticate with <MAC address removed>
[ 2596.726814] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2596.728681] wlan0: authenticated
[ 2596.732414] wlan0: associate with <MAC address removed> (try 1/3)
[ 2596.735763] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 2596.736466] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2596.736476] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2596.736497] wlan0: associated
[ 2604.749698] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 2604.781808] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2604.781822] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2605.715813] wlan0: authenticate with <MAC address removed>
[ 2605.717811] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2605.719385] wlan0: authenticated
[ 2605.723148] wlan0: associate with <MAC address removed> (try 1/3)
[ 2605.726321] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 2605.726920] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2605.726927] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2605.726942] wlan0: associated
[ 2613.780430] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 2613.804563] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2613.804578] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2614.738902] wlan0: authenticate with <MAC address removed>
[ 2614.740344] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2614.742194] wlan0: authenticated
[ 2614.746018] wlan0: associate with <MAC address removed> (try 1/3)
[ 2614.749217] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 2614.749818] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2614.749824] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2614.749840] wlan0: associated
[ 2622.822215] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 2622.831457] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2622.831472] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2623.769813] wlan0: authenticate with <MAC address removed>
[ 2623.771120] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2623.772927] wlan0: authenticated
[ 2623.776797] wlan0: associate with <MAC address removed> (try 1/3)
[ 2623.779960] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 2623.780563] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2623.780569] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2623.780584] wlan0: associated
[ 2631.822032] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 2631.830162] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2631.830174] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2632.764137] wlan0: authenticate with <MAC address removed>
[ 2632.765853] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2632.770506] wlan0: authenticated
[ 2632.771588] wlan0: associate with <MAC address removed> (try 1/3)
[ 2632.774761] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 2632.776510] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2632.776518] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2632.776530] wlan0: associated
[ 2636.001434] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2636.002545] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2636.002557] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2643.345942] wlan0: authenticate with <MAC address removed>
[ 2643.347435] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2643.349133] wlan0: authenticated
[ 2643.353112] wlan0: associate with <MAC address removed> (try 1/3)
[ 2643.356469] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 2643.357197] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2643.357207] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2643.357225] wlan0: associated
[ 2653.374147] wlan0: disassociating from <MAC address removed> by local choice (reason=3)
[ 2653.376342] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2653.376356] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2653.377857] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2654.210934] wlan0: authenticate with <MAC address removed>
[ 2654.212562] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2654.214180] wlan0: authenticated
[ 2654.217887] wlan0: associate with <MAC address removed> (try 1/3)
[ 2654.221322] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 2654.221949] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2654.221955] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2654.221969] wlan0: associated
[ 2664.245723] wlan0: disassociating from <MAC address removed> by local choice (reason=3)
[ 2664.246966] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2664.246980] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2664.248234] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2665.083184] wlan0: authenticate with <MAC address removed>
[ 2665.084672] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2665.086543] wlan0: authenticated
[ 2665.090307] wlan0: associate with <MAC address removed> (try 1/3)
[ 2665.093506] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 2665.094093] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2665.094100] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2665.094115] wlan0: associated
[ 2718.300465] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2718.301656] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2718.301670] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2727.782990] wlan0: authenticate with <MAC address removed>
[ 2727.784253] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2727.786015] wlan0: authenticated
[ 2727.789898] wlan0: associate with <MAC address removed> (try 1/3)
[ 2727.793036] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 2727.793681] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2727.793688] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2727.793705] wlan0: associated
[ 2729.215845] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2729.216829] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2729.216836] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2741.834527] wlan0: authenticate with <MAC address removed>
[ 2741.836204] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2741.838064] wlan0: authenticated
[ 2741.841947] wlan0: associate with <MAC address removed> (try 1/3)
[ 2741.845150] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 2741.845732] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2741.845739] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2741.845754] wlan0: associated
[ 2749.862978] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 2749.875235] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2749.875242] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2750.809042] wlan0: authenticate with <MAC address removed>
[ 2750.810852] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2750.812464] wlan0: authenticated
[ 2750.816203] wlan0: associate with <MAC address removed> (try 1/3)
[ 2750.819619] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 2750.820261] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2750.820268] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2750.820281] wlan0: associated
[ 2804.403076] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2804.404224] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2804.404238] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2809.059490] wlan0: authenticate with <MAC address removed>
[ 2809.061402] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2809.062961] wlan0: authenticated
[ 2809.066696] wlan0: associate with <MAC address removed> (try 1/3)
[ 2809.069892] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 2809.070499] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2809.070503] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2809.070516] wlan0: associated
[ 2817.097642] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 2817.124058] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2817.124072] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2818.057968] wlan0: authenticate with <MAC address removed>
[ 2818.059353] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2818.062160] wlan0: authenticated
[ 2818.064963] wlan0: associate with <MAC address removed> (try 1/3)
[ 2818.068152] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 2818.068785] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2818.068793] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2818.068808] wlan0: associated
[ 2827.220939] wlan0: deauthenticated from <MAC address removed> (Reason: 7)
[ 2827.234073] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2827.234088] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2828.169005] wlan0: authenticate with <MAC address removed>
[ 2828.170774] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2828.174107] wlan0: authenticated
[ 2828.176496] wlan0: associate with <MAC address removed> (try 1/3)
[ 2828.179677] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 2828.180344] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2828.180353] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2828.180371] wlan0: associated
[ 2836.196285] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 2836.205888] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2836.205900] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2837.139342] wlan0: authenticate with <MAC address removed>
[ 2837.141007] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2837.142866] wlan0: authenticated
[ 2837.146759] wlan0: associate with <MAC address removed> (try 1/3)
[ 2837.149934] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 2837.150537] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2837.150543] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2837.150559] wlan0: associated
[ 2845.176997] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 2845.200145] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2845.200171] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2846.134088] wlan0: authenticate with <MAC address removed>
[ 2846.135432] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2846.137241] wlan0: authenticated
[ 2846.141003] wlan0: associate with <MAC address removed> (try 1/3)
[ 2846.147518] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 2846.148076] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2846.148082] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2846.148098] wlan0: associated
[ 2854.177809] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 2854.191063] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2854.191078] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2855.128206] wlan0: authenticate with <MAC address removed>
[ 2855.129942] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2855.134634] wlan0: authenticated
[ 2855.135265] wlan0: associate with <MAC address removed> (try 1/3)
[ 2855.142626] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 2855.144008] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2855.144014] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2855.144027] wlan0: associated
[ 2863.179004] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 2863.188666] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2863.188681] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2864.122155] wlan0: authenticate with <MAC address removed>
[ 2864.123860] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2864.125733] wlan0: authenticated
[ 2864.129529] wlan0: associate with <MAC address removed> (try 1/3)
[ 2864.132609] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 2864.133319] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2864.133329] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2864.133347] wlan0: associated
[ 2867.268354] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2867.269497] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2867.269511] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2875.379538] wlan0: authenticate with <MAC address removed>
[ 2875.380739] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2875.382586] wlan0: authenticated
[ 2875.386382] wlan0: associate with <MAC address removed> (try 1/3)
[ 2875.392628] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 2875.393248] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2875.393254] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2875.393270] wlan0: associated
[ 2883.402716] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 2883.411666] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2883.411681] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2884.345650] wlan0: authenticate with <MAC address removed>
[ 2884.346967] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2884.350667] wlan0: authenticated
[ 2884.352638] wlan0: associate with <MAC address removed> (try 1/3)
[ 2884.355835] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 2884.356422] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2884.356429] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2884.356447] wlan0: associated
[ 2892.373305] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 2892.382497] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2892.382513] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2893.319779] wlan0: authenticate with <MAC address removed>
[ 2893.321277] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2893.323185] wlan0: authenticated
[ 2893.326887] wlan0: associate with <MAC address removed> (try 1/3)
[ 2893.330055] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 2893.330661] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2893.330668] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2893.330683] wlan0: associated
[ 2901.344093] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 2901.354986] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2901.355003] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2902.290340] wlan0: authenticate with <MAC address removed>
[ 2902.292749] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2902.294759] wlan0: authenticated
[ 2902.297156] wlan0: associate with <MAC address removed> (try 1/3)
[ 2902.303829] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 2902.304376] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2902.304383] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2902.304399] wlan0: associated
[ 2910.314727] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 2910.330519] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2910.330529] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2911.264323] wlan0: authenticate with <MAC address removed>
[ 2911.265735] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2911.267596] wlan0: authenticated
[ 2911.271388] wlan0: associate with <MAC address removed> (try 1/3)
[ 2911.274563] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 2911.275149] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2911.275155] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2911.275171] wlan0: associated
[ 2919.295529] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 2919.300764] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2919.300779] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2920.234126] wlan0: authenticate with <MAC address removed>
[ 2920.235859] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2920.237763] wlan0: authenticated
[ 2920.241613] wlan0: associate with <MAC address removed> (try 1/3)
[ 2920.244750] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 2920.245402] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2920.245409] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2920.245423] wlan0: associated
[ 2928.286291] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 2928.297283] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2928.297298] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2929.232831] wlan0: authenticate with <MAC address removed>
[ 2929.234236] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2929.236138] wlan0: authenticated
[ 2929.239877] wlan0: associate with <MAC address removed> (try 1/3)
[ 2929.246335] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 2929.246965] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2929.246973] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2929.246992] wlan0: associated
[ 2976.586607] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2976.588227] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2976.588241] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2980.235482] wlan0: authenticate with <MAC address removed>
[ 2980.236902] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2980.238773] wlan0: authenticated
[ 2980.242580] wlan0: associate with <MAC address removed> (try 1/3)
[ 2980.245762] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 2980.246430] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2980.246443] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2980.246470] wlan0: associated
[ 2982.971674] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2982.972650] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2982.972655] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 3666.513756] wlan0: authenticate with <MAC address removed>
[ 3666.515172] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3666.516728] wlan0: authenticated
[ 3666.520854] wlan0: associate with <MAC address removed> (try 1/3)
[ 3666.524051] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 3666.524661] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 3666.524667] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 3666.524684] wlan0: associated
[ 3674.558245] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 3674.634272] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 3674.634288] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 3675.567829] wlan0: authenticate with <MAC address removed>
[ 3675.569497] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3675.571159] wlan0: authenticated
[ 3675.575238] wlan0: associate with <MAC address removed> (try 1/3)
[ 3675.578467] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 3675.579093] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 3675.579106] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 3675.579163] wlan0: associated
[ 3683.599025] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 3683.620593] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 3683.620618] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 3684.554319] wlan0: authenticate with <MAC address removed>
[ 3684.555785] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3684.557401] wlan0: authenticated
[ 3684.561464] wlan0: associate with <MAC address removed> (try 1/3)
[ 3684.564693] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 3684.565294] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 3684.565301] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 3684.565317] wlan0: associated
[ 3692.580575] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 3692.606796] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 3692.606810] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 3693.540603] wlan0: authenticate with <MAC address removed>
[ 3693.542056] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3693.543710] wlan0: authenticated
[ 3693.547712] wlan0: associate with <MAC address removed> (try 1/3)
[ 3693.550893] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 3693.551482] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 3693.551489] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 3693.551505] wlan0: associated
[ 3701.610632] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 3701.621028] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 3701.621041] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 3702.555094] wlan0: authenticate with <MAC address removed>
[ 3702.556365] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3702.558027] wlan0: authenticated
[ 3702.562005] wlan0: associate with <MAC address removed> (try 1/3)
[ 3702.565200] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 3702.565778] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 3702.565785] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 3702.565801] wlan0: associated
[ 3710.611353] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 3710.619531] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 3710.619556] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 3711.553184] wlan0: authenticate with <MAC address removed>
[ 3711.554614] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3711.556344] wlan0: authenticated
[ 3711.560283] wlan0: associate with <MAC address removed> (try 1/3)
[ 3711.563491] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 3711.564077] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 3711.564084] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 3711.564100] wlan0: associated
[ 3719.582126] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 3719.600885] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 3719.600901] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 3720.535523] wlan0: authenticate with <MAC address removed>
[ 3720.536847] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3720.538485] wlan0: authenticated
[ 3720.542514] wlan0: associate with <MAC address removed> (try 1/3)
[ 3720.545711] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 3720.546305] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 3720.546312] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 3720.546328] wlan0: associated
[ 3726.219677] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 3726.225198] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 3726.225213] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 3734.290797] wlan0: authenticate with <MAC address removed>
[ 3734.292554] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3734.294160] wlan0: authenticated
[ 3734.298253] wlan0: associate with <MAC address removed> (try 1/3)
[ 3734.301434] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=19)
[ 3734.302060] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 3734.302066] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 3734.302081] wlan0: associated
[ 3788.498078] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 3788.499255] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 3788.499268] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 3792.157344] wlan0: authenticate with <MAC address removed>
[ 3792.158632] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3792.160274] wlan0: authenticated
[ 3792.164278] wlan0: associate with <MAC address removed> (try 1/3)
[ 3792.167549] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 3792.168150] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 3792.168156] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 3792.168173] wlan0: associated
[ 3800.178651] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 3800.217593] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 3800.217605] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 3801.152001] wlan0: authenticate with <MAC address removed>
[ 3801.152928] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3801.154564] wlan0: authenticated
[ 3801.158571] wlan0: associate with <MAC address removed> (try 1/3)
[ 3801.161988] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 3801.162635] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 3801.162647] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 3801.162662] wlan0: associated
[ 3809.180227] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 3809.191894] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 3809.191910] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 3810.125417] wlan0: authenticate with <MAC address removed>
[ 3810.127106] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3810.130215] wlan0: authenticated
[ 3810.132785] wlan0: associate with <MAC address removed> (try 1/3)
[ 3810.135863] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[ 3810.136565] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 3810.136573] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 3810.136589] wlan0: associated


****************** done ******************



```

---

### Post by show2 on 2014-02-16
The computer connected to router successfully just right now. But I cannot open a website. And I try to connect it once again. But it fail.

---

### Post by varunendra on 2014-02-16
> **show2 said:**
> The computer connected to router successfully just right now. But I cannot open a website. And I try to connect it once again. But it fail.
The encryption type in your router is weird -
> **show2 said:**
> ```

wlan0     Scan completed :
          Cell 01 - Address: C8:3A:35:2A:AD:00
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=**43/70**  Signal level=-67 dBm  
                    ....  
                    ....
                    IE: **[COLOR="#FF0000"]WPA[/COLOR]** Version 1
                        Group Cipher : **[COLOR="#FF0000"]CCMP[/COLOR]**
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00

```
As far as I know, the WPA standard needs TKIP encryption, not CCMP (AES).

I recommend that you change the encryption type in your router to **WPA[COLOR="#0000CD"]2[/COLOR]** with AES (CCMP). Make sure not to select the WPA or WPA/WPA2 mixed mode, as that will again need TKIP which is highly discouraged.

Also, the signal quality doesn't look good. Are you too far from the router?

As for not being able to browse while apparently being connected, your DNS looks suspicious -
> **show2 said:**
> 
```

  IPv4 Settings:
    Address:         192.168.0.103
    Prefix:          24 (255.255.255.0)
   ** Gateway:         192.168.0.1**


    **DNS:             192.168.[COLOR="#FF0000"]1[/COLOR].1**

```
Like most home networks, I believe your router is performing the role of both the gateway and DNS. If so, your DNS should be same as the gateway, that is - 192.168.**[COLOR="#0000CD"]0[/COLOR]**.1 - notice the ".0", which is currently ".1".

How have you configured your DNS? Manually or is it getting that from the DHCP (router)?
If it is getting that from the router, the correction has to be made in the router, unless you are using a rather complex networking.

You can also use an external DNS, like google's 8.8.8.8, 8.8.4.4 or OpenDNS servers.

---

### Post by show2 on 2014-02-17
I don't know the password of the router(it's not my router), so I cannot change the encryption type. 
But the question is:
1. Whether I can connect to wireless is depends on fortune.(I have try to sit next to my router, but also cannot connect successfully every time. And when I use my Windows system, I can connect easily)
2.I cannot open websites most of time when the computer connected to the wireless. (there is one or two times that I open a website, but failed in a second)

You said it looks like a DNS problem, but it was same to my wired device's DNS, and it works well.
I also have changed to a Google DNS, but the problem still exisit.

---

### Post by varunendra on 2014-02-17
Since you don't have access to the admin cp of the router, there we are left with only whatever we can try with the driver, so let's try whatever options we have there.

[LIST]
[*]First, make sure IPv6 is set to "Ignore" in Network Manager. Also disable it permanently following this post : [http://ubuntuforums.org/showpost.php?p=12640479](http://ubuntuforums.org/showpost.php?p=12640479)
[*]Next, Set DNS permanently in the Network Manager to 8.8.8.8, 8.8.4.4 (you must choose "Automatic (DHCP) address only" option).
[*]Delete your current udev rules file for network devices. It contains the old entry for "wl" driver which we don't have anymore -
[/LIST]
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```
This file will be regenerated automatically when needed, with only relevant entries this time.

Reboot after having made these changes and try to connect. If still having the same way, then probably the only other things we can try is a newer or different driver. "Different" means the sta driver again, which I don't trust over the native one, so we'll keep it as our last shot.

**_ONLY if the above tweaks don't help_ :**

If the above changes don't help, ONLY THEN follow these instructions to install a newer driver -

With a working internet connection, install the basic packages required for building modules -
```
sudo apt-get install --reinstall linux-headers-generic build-essential
```

Then,

[INDENT]**1)** Download the "backports-3.12.8-1" package from here : [http://drvbp1.linux-foundation.org/~mcgrof/rel-html/backports/](http://drvbp1.linux-foundation.org/~mcgrof/rel-html/backports/)
**2)** Right-click the downloaded package > Extract here..
**3)** Open a terminal (Ctrl-Alt-T) and assuming the extracted directory is within the "Downloads" folder in your Home directory, run the following commands to compile and install the driver -
```
cd Downloads/backports-3.12.8-1
make defconfig-brcmsmac
make
sudo make install
```[/INDENT]
Watch out for errors and report back if you see any. If all went smooth, reboot the system and check the connectivity. Is it any better now?

If not, run the wireless_script again and post back its fresh report.

**PS:**
Yes the DNS can be different than the gateway, but usually it is not. Having a different DNS on the local network only means that it is not as simple as normal home networking usually is. If you can ping all of these, everything is okay on the gateway/DNS part -
```
ping -c4 192.168.1.1
ping -c4 192.168.0.1
```
If any of these fail, we have a problem, minor or major, but a problem nonetheless, and you should consult whoever is controlling the network.

---

### Post by show2 on 2014-02-17
Thank you very much! The second way repaired it!
And I have try to use the DNS automatically. And it works well too.
Thanks a lot!

---

### Post by varunendra on 2014-02-18
That's a great news ! I was loosing hope thinking maybe we can't do anything internally :D

Thanks for the feedback!

---

