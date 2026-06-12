---
title: "can't get my wireless to work =\"
date: 2012-11-22
forum: New to Ubuntu
---

### Post by CristianXfree on 2012-11-22
I completely suck at ubuntu 12.04 so far, but its really cool. I downloaded it a days ago off of a different computer to install on my new hard drive when it came in. well it came in and the install went fine and fast. I can't get my wireless to work it says networks disable.  i have checked all over the internet looking for a solution. I hope to fix it soon any help is greatly appreciated.

---

### Post by wildmanne39 on 2012-11-22
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by CristianXfree on 2012-11-22
sorry it took so long I fell asleep but here is what i got:

*************** info trace ****************



**** uname -a ****


Linux cristiancook-Vostro-1520 3.2.0-33-generic-pae #52-Ubuntu SMP Thu Oct 18 16:39:21 UTC 2012 i686 i686 i386 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"


**** lspci ****


08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
    Subsystem: Dell Device [1028:02bc]
    Kernel driver in use: r8169
--
0e:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
    Kernel driver in use: wl


**** lsusb ****


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0c45:63e0 Microdia Sonix Integrated Webcam


**** iwconfig ****


eth2      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0



**** rfkill ****


0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
3: brcmwl-2: Wireless LAN
    Soft blocked: no
    Hard blocked: no


**** lsmod ****


Module                  Size  Used by
xt_limit               12541  8 
xt_tcpudp              12531  7 
ipt_LOG                12783  8 
ipt_MASQUERADE         12663  0 
xt_DSCP                12549  0 
ipt_REJECT             12512  1 
nf_conntrack_irc       13138  0 
nf_conntrack_ftp       13183  0 
xt_state               12514  6 
joydev                 17393  0 
snd_hda_codec_idt      60251  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
iptable_nat            13016  0 
nf_nat                 24959  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19084  9 iptable_nat,nf_nat
nf_conntrack           73847  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
iptable_mangle         12646  0 
iptable_filter         12706  1 
ip_tables              18106  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               21974  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
lib80211_crypt_tkip    17275  0 
snd_timer              28931  2 snd_pcm,snd_seq
dell_laptop            17767  0 
wl                   2646601  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
dcdbas                 14098  1 dell_laptop
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
psmouse                86486  0 
serio_raw              13027  0 
snd                    62064  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  419110  3 
lib80211               14040  2 lib80211_crypt_tkip,wl
drm_kms_helper         45466  1 i915
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
drm                   197599  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
rfcomm                 38139  0 
bnep                   17830  2 
parport_pc             32114  0 
bluetooth             158438  10 rfcomm,bnep
ppdev                  12849  0 
mac_hid                13077  0 
video                  19068  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          40172  0 
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
r8169                  56321  0 


**** nm-tool ****



NetworkManager Tool

State: connected (global)

- Device: eth2 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


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
    Address:         192.168.0.109
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1




**** NetworkManager.state ****



[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


**** NetworkManager.conf ****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false


**** NetworkManager.conf-10.04 ****




**** interfaces ****


auto lo
iface lo inet loopback



**** iwlist ****


eth2      Scan completed :
          Cell 01 - Address: <MAC address removed>
                    ESSID:"buchholznet"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:5/5  Signal level:-42 dBm  Noise level:-92 dBm
                    IE: Unknown: DD930050F204104A0001101044000102103B000103104700106304125310192006122800E04C8196351021001B5265616C74656B2053656D69636F6E647563746F7220436F72702E1023000752544C387878781024000D45562D323030362D30372D32371042000F3132333435363738393031323334371054000800060050F20400011011000852544C3831393662100800020086
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 02 - Address: <MAC address removed>
                    ESSID:"NETGEAR"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/5  Signal level:-92 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s



**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1


**** blacklist.conf ****


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


**** dmesg ****


[    6.877625] wl: module license 'MIXED/Proprietary' taints kernel.
[    7.101774] wl 0000:0e:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    7.101789] wl 0000:0e:00.0: setting latency timer to 64
[    7.576479] eth1: Broadcom BCM4315 802.11 Hybrid Wireless Controller 5.100.82.38
[    7.612899] udevd[334]: renamed network interface eth1 to eth2
[    7.683646] type=1400 audit(1353602267.891:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=869 comm="apparmor_parser"
[  434.172575] wl 0000:0e:00.0: PCI INT A disabled
[  434.172931] wl 0000:0e:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[  434.172950] wl 0000:0e:00.0: setting latency timer to 64
[  434.548793] udevd[626]: renamed network interface eth1 to eth2
[  491.828548] wl 0000:0e:00.0: PCI INT A disabled
[  491.828897] wl 0000:0e:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[  491.828916] wl 0000:0e:00.0: setting latency timer to 64
[  491.905302] udevd[14606]: renamed network interface eth1 to eth2
[ 3097.855902] wl 0000:0e:00.0: PCI INT A disabled
[ 3099.040790] wl 0000:0e:00.0: restoring config space at offset 0xf (was 0x100, writing 0x105)
[ 3099.040850] wl 0000:0e:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xfa000004)
[ 3099.040862] wl 0000:0e:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 3099.040879] wl 0000:0e:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100006)
[ 3099.098590] wl 0000:0e:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 3099.098602] wl 0000:0e:00.0: setting latency timer to 64


**************** done ********************

---

### Post by wildmanne39 on 2012-11-22
Hi, please do:
```
echo "blacklist dell_laptop" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Then:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Then:
```
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
```
Watch for errors.
Reboot

---

### Post by CristianXfree on 2012-11-22
thank you so much that worked!!!!

---

### Post by wildmanne39 on 2012-11-22
Your welcome!
Enjoy

---

