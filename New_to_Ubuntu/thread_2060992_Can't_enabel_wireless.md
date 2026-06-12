---
title: "Can't enabel wireless"
date: 2012-09-21
forum: New to Ubuntu
---

### Post by delipekan on 2012-09-21
Hi,

I've installed ubuntu 12.04 on my Dell vostro 1520.
I think that I've already installed the driver. I did:
```
sudo apt-get install firmware-b43-lpphy-installer
```

After rebooting, I still could not enable the wireless.
What should I do next??

Thanks in advance!

```
>>sudo lshw -class network
 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 03
       serial: 00:24:e8:b0:cc:8a
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-1.fw ip=192.168.0.58 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:47 ioport:3000(size=256) memory:f6004000-f6004fff memory:f6000000-f6003fff memory:f6020000-f603ffff
  *-network
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0e:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:fa000000-fa003fff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:22:5f:b0:97:91
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.2.0-30-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg

```

---

### Post by Finnicella on 2012-09-21
I know that this is the right command:
```
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
```
Did you unistall first broadcom STA?
If you didn 't give this command first:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Bye :D

---

### Post by Sagimore on 2012-09-21
I had same issue last night, but I actually had to use the hotkey on the keyboard to turn wireless back on. just a thought.

---

### Post by daslinkard on 2012-09-21
The hotkey should work especially after it has been downloaded.  How is it that you are trying to enable your wireless?

---

### Post by delipekan on 2012-09-22
I tried the hotkey (Fn + F2) and nothing. Maybe it's important to mention that the wireless LED is off (it's on when I restart to WINDOWS).

I also did as Finnicella suggest + reboot. This is the output:
```
>> sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package broadcom-sta-common is not installed, so not removed
Package broadcom-sta-source is not installed, so not removed
Package bcmwl-kernel-source is not installed, so not removed
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-29 linux-headers-3.2.0-29-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

>> sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
b43-fwcutter set to manually installed.
firmware-b43-lpphy-installer is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-29 linux-headers-3.2.0-29-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by Finnicella on 2012-09-22
Hi, if it didn't work yet, enable additional drivers in "System setting" and then type these commands in the terminal:
```
sudo modprobe -r b43 ssb
```
```
sudo modprobe b43
```
I hope this works.
Bye

---

### Post by delipekan on 2012-09-22
> **Finnicella said:**
> Hi, if it didn't work yet, enable additional drivers in "System setting" and then type these commands in the terminal:
```
sudo modprobe -r b43 ssb
``````
sudo modprobe b43
```I hope this works.
Bye

The only "additional driver" that I can enable is the Broadcom STA driver. Still try it?

---

### Post by Finnicella on 2012-09-22
Yes, try it.
:D

---

### Post by delipekan on 2012-09-22
Now the wireless LED is on, but I still can't enable it (and I've try the hotkey).

---

### Post by StinkySQL on 2012-09-22
That is what worked for me to get mine up and running. You're going to want to force it enabled on reboots also. Got this from Chili555,

sudo su 
echo b43 >> /etc/modules 
exit

---

### Post by Finnicella on 2012-09-22
Try with:
```
sudo rfkill unblock all
```
and tell me if it works.
Bye

---

### Post by delipekan on 2012-09-22
> **Finnicella said:**
> Try with:
```
sudo rfkill unblock all
```and tell me if it works.
Bye

No... and I also try echo b43 >> /etc/modules
:(

---

### Post by Finnicella on 2012-09-22
Sorry, but now I must go.
Please, show the output of these commands:
```
lspci -k
```
```
sudo lshw -C network
```
```
iwconfig
```
```
sudo rfkill list all
```
See you tomorrow.
Bye

---

### Post by delipekan on 2012-09-22
Thanks Finnicella!

lspci -k:
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
    Subsystem: Dell Device 02bc
    Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
    Subsystem: Dell Device 02bc
    Kernel driver in use: i915
    Kernel modules: i915
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
    Subsystem: Dell Device 02bc
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
    Subsystem: Dell Device 02bc
    Kernel driver in use: uhci_hcd
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
    Subsystem: Dell Device 02bc
    Kernel driver in use: uhci_hcd
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
    Subsystem: Dell Device 02bc
    Kernel driver in use: uhci_hcd
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
    Subsystem: Dell Device 02bc
    Kernel driver in use: ehci_hcd
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: Dell Device 02bc
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
    Subsystem: Dell Device 02bc
    Kernel driver in use: uhci_hcd
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
    Subsystem: Dell Device 02bc
    Kernel driver in use: uhci_hcd
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
    Subsystem: Dell Device 02bc
    Kernel driver in use: uhci_hcd
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
    Subsystem: Dell Device 02bc
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
    Subsystem: Dell Device 02bc
    Kernel modules: iTCO_wdt
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
    Subsystem: Dell Device 02bc
    Kernel driver in use: ahci
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
    Subsystem: Dell Device 02bc
    Kernel modules: i2c-i801
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
    Subsystem: Dell Device 02bc
    Kernel driver in use: r8169
    Kernel modules: r8169
0e:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
    Subsystem: Dell Wireless 1397 WLAN Mini-Card
    Kernel driver in use: wl
    Kernel modules: wl, ssb
1a:00.0 FireWire (IEEE 1394): O2 Micro, Inc. Device 10f7 (rev 01)
    Subsystem: Dell Device 02bc
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci
1a:00.1 SD Host controller: O2 Micro, Inc. Device 8120 (rev 01)
    Subsystem: Dell Device 02bc
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci
1a:00.2 Mass storage controller: O2 Micro, Inc. Device 8130 (rev 01)
    Subsystem: Dell Device 02bc

```sudo lshw -C network:
```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 03
       serial: 00:24:e8:b0:cc:8a
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-1.fw ip=192.168.0.122 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:47 ioport:3000(size=256) memory:f6004000-f6004fff memory:f6000000-f6003fff memory:f6020000-f603ffff
  *-network DISABLED
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth1
       version: 01
       serial: 00:22:5f:b0:97:91
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:fa000000-fa003fff

```iwconfig:
```
lo        no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

eth0      no wireless extensions.

```sudo rfkill list all:
```
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
2: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

---

### Post by Finnicella on 2012-09-23
Hi,
give this command and see if wifi works:
```
sudo rfkill unblock 1
```
or
```
sudo rfkill unblock wifi
```
and show the output of these commands:
```
lspci -nn | grep -i net
```
```
lsmod | grep -e wl -e b43
```
Bye
Finny

---

### Post by delipekan on 2012-09-23
Both of the command didn't change the state.

lspci -nn |grep -i net:
```
08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
0e:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

```lsmod | grep -e wl -e b43:
```
wl                   2568210  0 
lib80211               14381  2 lib80211_crypt_tkip,wl

```

---

### Post by MARP1961 on 2012-09-23
STA and B43 drivers seem to conflict. The B43 driver should work fine but if you have installed STA then B43 will be blacklisted.  

I've found one way round the problem is to do a fresh install of Ubuntu with an ethernet connection. Do not install STA driver as Additional Drivers urges you to do. Instead install Synaptic Package Manager (always useful) and search for and install **B43-firmware-installer**. It will also install **fw-cutter** at the same time. Reboot the computer with ethernet disconnected and it should detect your wireless. Click on icon to connect.

---

### Post by delipekan on 2012-09-23
> **MARP1961 said:**
> STA and B43 drivers seem to conflict. The B43 driver should work fine but if you have installed STA then B43 will be blacklisted.  

I've found one way round the problem is to do a fresh install of Ubuntu with an ethernet connection. Do not install STA driver as Additional Drivers urges you to do. Instead install Synaptic Package Manager (always useful) and search for and install **B43-firmware-installer**. It will also install **fw-cutter** at the same time. Reboot the computer with ethernet disconnected and it should detect your wireless. Click on icon to connect.

Is there any way to accomplish the same aim without a new installation? :(

---

### Post by Finnicella on 2012-09-24
You can unistall STA with:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
and then try:
```
sudo modprobe -r b43 ssb wl
```
and
```
sudo modprobe b43
```
If this don't work we must see the blacklist with:
```
cat /etc/modprobe.d/blacklist.conf
```
Bye

---

### Post by delipekan on 2012-09-25
I'm stuck. :(

I did a new installation and followed MARP1961's advice but I still can't enable the wireless.

Because I have a BCM4321 LP-PHY card model 4315, I need the STA driver.
Reference:
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)
[https://wiki.archlinux.org/index.php/Broadcom_wireless](https://wiki.archlinux.org/index.php/Broadcom_wireless)

According to the first link, I removed everything that was installed, reboot, install broadcom-sta-source + broadcom-sta-common + firmware-b43-lpphy-installer + bcmwl-kerrnel-source, reboot and you know...

As you can see, the wi-fi is blocked:
```
>> rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
2: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

How can I unblock it?? I'v try:
```
rfkill unblock all
rfkill unblock wifi
rfkill unblock wlan
```
But nothing!!!

Btw, why the bluetooth & wireless appear twice?

---

### Post by Finnicella on 2012-09-25
We must see your modules at this time:
```
lspci -k
```
```
lsmod
```
I think there is a conflict between the driver.
Bye

---

### Post by delipekan on 2012-09-25
lspci -k:
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
    Subsystem: Dell Device 02bc
    Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
    Subsystem: Dell Device 02bc
    Kernel driver in use: i915
    Kernel modules: i915
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
    Subsystem: Dell Device 02bc
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
    Subsystem: Dell Device 02bc
    Kernel driver in use: uhci_hcd
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
    Subsystem: Dell Device 02bc
    Kernel driver in use: uhci_hcd
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
    Subsystem: Dell Device 02bc
    Kernel driver in use: uhci_hcd
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
    Subsystem: Dell Device 02bc
    Kernel driver in use: ehci_hcd
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: Dell Device 02bc
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
    Subsystem: Dell Device 02bc
    Kernel driver in use: uhci_hcd
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
    Subsystem: Dell Device 02bc
    Kernel driver in use: uhci_hcd
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
    Subsystem: Dell Device 02bc
    Kernel driver in use: uhci_hcd
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
    Subsystem: Dell Device 02bc
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
    Subsystem: Dell Device 02bc
    Kernel modules: iTCO_wdt
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
    Subsystem: Dell Device 02bc
    Kernel driver in use: ahci
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
    Subsystem: Dell Device 02bc
    Kernel modules: i2c-i801
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
    Subsystem: Dell Device 02bc
    Kernel driver in use: r8169
    Kernel modules: r8169
0e:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
    Subsystem: Dell Wireless 1397 WLAN Mini-Card
    Kernel driver in use: wl
    Kernel modules: wl, ssb
1a:00.0 FireWire (IEEE 1394): O2 Micro, Inc. Device 10f7 (rev 01)
    Subsystem: Dell Device 02bc
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci
1a:00.1 SD Host controller: O2 Micro, Inc. Device 8120 (rev 01)
    Subsystem: Dell Device 02bc
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci
1a:00.2 Mass storage controller: O2 Micro, Inc. Device 8130 (rev 01)
    Subsystem: Dell Device 02bc

```

lsmod:
```
Module                  Size  Used by
arc4                   12529  0 
rt73usb                31735  0 
rt2x00usb              20762  1 rt73usb
rt2x00lib              51144  2 rt73usb,rt2x00usb
mac80211              506816  2 rt2x00usb,rt2x00lib
cfg80211              205544  2 rt2x00lib,mac80211
hidp                   22628  1 
joydev                 17693  0 
parport_pc             32866  0 
ppdev                  17113  0 
rfcomm                 47604  12 
bnep                   18281  2 
snd_hda_codec_idt      70795  1 
uvcvideo               72627  0 
lib80211_crypt_tkip    17390  0 
usbhid                 47199  0 
dell_laptop            18119  0 
videodev               98259  1 uvcvideo
btusb                  18288  4 
hid                    99559  2 hidp,usbhid
v4l2_compat_ioctl32    17128  1 videodev
dcdbas                 14490  1 dell_laptop
bluetooth             180104  28 hidp,rfcomm,bnep,btusb
wl                   2568210  0 
psmouse                87692  0 
serio_raw              13211  0 
snd_hda_intel          33773  3 
snd_hda_codec         127706  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
lib80211               14381  2 lib80211_crypt_tkip,wl
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
i915                  472941  3 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13253  0 
drm_kms_helper         46978  1 i915
drm                   242038  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  2 rt73usb,firewire_core
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
r8169                  62099  0 

```

Thanks for the quick response. I know nothing on drivers... :(

---

### Post by Finnicella on 2012-09-25
We must see if there is ssb with
```
sudo modprobe -l | grep ssb
```

---

### Post by delipekan on 2012-09-25
sudo modprobe -l | grep ssb:
```
kernel/drivers/ssb/ssb.ko
```

---

### Post by Finnicella on 2012-09-25
I don't know if it work but try:
```
sudo modprobe -r wl
```
```
sudo modprobe ssb
```
and try if it work.
Bye

---

### Post by delipekan on 2012-09-25
wi-fi still blocked

---

### Post by Finnicella on 2012-09-25
After that I don't  know what to do:
```
sudo modprobe -r b43 ssb wl
```
```
sudo modprobe b43
```
And tell me.
Give this command too:
```
sudo rfkill list all
```
Check the blacklist with:
```
cat /etc/modprobe.d/blacklist.conf
```
Bye

---

### Post by delipekan on 2012-09-25
Still blocked.

cat /etc/modprobe.d/blacklist.conf:
```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

```

---

### Post by Finnicella on 2012-09-25
With:
```
sudo gedit /etc/modprobe.d/blacklist.conf
```
change this part from this:
```
# replaced by b43 and ssb.
blacklist bcm43xx
```
to this by adding #:
```
# replaced by b43 and ssb.
# blacklist bcm43xx
```
and save.
Restart and see if it works.
If it doesn't work delete the # and brings everything to how it was before.
Bye

---

### Post by delipekan on 2012-09-25
Didn't change (after reboot of course).
I removed the comment.

---

### Post by Finnicella on 2012-09-25
We can try to remove broadcom and reinstall b43 lpphy.
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
```
sudo apt-get install --reinstall b43-fwcutter firmware-b43-lpphy-installer
```
then
```
sudo modprobe -r b43 ssb
```
and
```
sudo modprobe b43
```
Sorry, but this is my last try, then I'll ask for help a more experienced person than me.
Bye 
Finny

---

### Post by delipekan on 2012-09-25
Same state...

Many thanks Finny. I'm very appreciate it!

---

### Post by chili555 on 2012-09-25
I believe the correct driver *IS* the STA driver, so I'd reinstall it and amend /etc/modules to not load b43.```
sudo apt-get install bcmwl-kernel-source
sudo gedit /etc/modules
```If b43 is in there, remove it, proofread, save and close gedit.

Now the *REAL* problem is here:> 0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: [COLOR="Red"]dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes[/COLOR]
2: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: noAs a temporary step, please do:```
sudo modprobe -r dell-laptop
sudo rfkill unblock all
```Any improvements?

Also, why are these wireless modules loaded? Do you have a second wireless device?> [COLOR="Red"]rt73usb[/COLOR]                31735  0 
rt2x00usb              20762  1 rt73usb
rt2x00lib              51144  2 rt73usb,rt2x00usb
mac80211              506816  2 rt2x00usb,rt2x00lib
cfg80211              205544  2 rt2x00lib,mac80211Thanks.

---

### Post by daslinkard on 2012-09-25
Any luck with Chili's suggestion?

---

### Post by delipekan on 2012-09-26
YES!!! I'm writing this message without a wired connection. :)

chili555, why did you wrote that this is only a temporary step?
The other modules belong to a USB wireless card that I thought to use it instead of the laptop's card.

---

### Post by chili555 on 2012-09-26
It is a temporary step because the module *dell-laptop* will reload and hard block your wireless again unless we blacklist it:```
sudo su
echo "blacklist dell-laptop" >> /etc/modprobe.d/blacklist.conf
exit
```If everything works well, we needn't get too excited about rt73usb.

---

### Post by delipekan on 2012-09-26
You right. The wireless became disable after a restart.

1. Why the "dell-laptop" blocking the wireless?
2. What are the implications of entering "dell-laptop" to the black list?

---

### Post by chili555 on 2012-09-27
> **delipekan said:**
> You right. The wireless became disable after a restart.

1. Why the "dell-laptop" blocking the wireless?
2. What are the implications of entering "dell-laptop" to the black list?The module *dell-laptop* is supposed to recognize and act upon key presses specific to Dell laptops, especially wireless. Due to a bug, it doesn't. We have learned, by trial and error, that simply removing the module will actually enable the wireless! Blacklisting keeps it out of the way permanently, or until you remove it from the blacklist.

In newer Ubuntu versions, this is fixed.

---

### Post by yinkoo on 2012-09-27
i had the same issue (wireless firmware missing).  i tried several offline solutions (firmware installation and such) but nothing works and got me like hours solving. 
the last sol, i simply plugin ethernet cable and tried system> additional drivers, n activate my broadcom STA. it works. :p

---

### Post by delipekan on 2012-09-27
O.K.

I want to thank you **all**! I could never do it without you!!
This thread can tag as SOLVED. :)

---

### Post by Timoteo32 on 2012-09-28
I'm having a similar problem as posted above but when I tried Chill's suggestion my modules folder was completely empty. Maybe I skipped some of the intermediate steps that I should have done? I didn't try them because they didn't work but I can.  This is all a little over my head.

Details:
It's also a Dell laptop and it was also fine before installing 12.04.

I can see the driver I need under "Additional Drivers" but when I try and Activate I get the message:
> Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log

But I have no clue where that is or exactly what details I'd be looking for there.

---

### Post by Timoteo32 on 2012-09-28
Anyone? I was trying to be a good forum member by using an existing thread but it seems like people don't want to respond if there's more than a page of posts already :/

---

