---
title: "Wireless able to connect to router, but no internet connection"
date: 2015-04-04
forum: New to Ubuntu
---

### Post by gary58 on 2015-04-04
Hey all! Sorry if this has been posted before. I'm brand new to linux (2 days new), and using Ubuntu 14.04 LTS. For the past two days, I've been browsing the forums, trying different commands when other people were helped, and even had to reinstall ubuntu 3 times (as I snarled the OS doing commands that were probably inapplicable to the situation). 

Based off of a prior forum, I figured this information may be needed. I followed the steps from this forum : [http://ubuntuforums.org/showthread.php?t=1985079](http://ubuntuforums.org/showthread.php?t=1985079)    and used the following in my terminal.

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```


This is what I got back:

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.2 LTS"
Linux garebear-Aspire-5560 3.16.0-33-generic #44~14.04.1-Ubuntu SMP Fri Mar 13 10:33:29 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

01:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:0605]
    Kernel driver in use: tg3
--
02:00.0 Network controller [0280]: Broadcom Corporation BCM43227 802.11b/g/n [14e4:4358]
    Subsystem: Foxconn International, Inc. Device [105b:e040]
    Kernel driver in use: wl


eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"NETGEAR 22"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: 8E:B8:A9:8A:D2:24   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

Module                  Size  Used by
ipt_MASQUERADE         12880  1 
xt_conntrack           12760  1 
ipt_REJECT             12541  2 
xt_tcpudp              12884  4 
iptable_filter         12810  1 
nf_nat_h323            17720  0 
nf_conntrack_h323      73895  1 nf_nat_h323
nf_nat_pptp            13115  0 
nf_nat_proto_gre       13009  1 nf_nat_pptp
nf_conntrack_pptp      19157  1 nf_nat_pptp
nf_conntrack_proto_gre    14216  1 nf_conntrack_pptp
nf_nat_tftp            12489  0 
nf_conntrack_tftp      13121  1 nf_nat_tftp
nf_nat_sip             17186  0 
nf_conntrack_sip       28460  1 nf_nat_sip
nf_nat_irc             12723  0 
nf_conntrack_irc       13518  1 nf_nat_irc
nf_nat_ftp             12770  0 
nf_conntrack_ftp       18638  1 nf_nat_ftp
iptable_nat            12970  1 
nf_conntrack_ipv4      14806  2 
nf_defrag_ipv4         12758  1 nf_conntrack_ipv4
nf_nat_ipv4            13263  1 iptable_nat
nf_nat                 22050  10 nf_nat_ftp,nf_nat_irc,nf_nat_sip,ipt_MASQUERADE,nf_nat_proto_gre,nf_nat_h323,nf_nat_ipv4,nf_nat_pptp,nf_nat_tftp,iptable_nat
nf_conntrack          105081  19 nf_nat_ftp,nf_nat_irc,nf_nat_sip,nf_conntrack_proto_gre,ipt_MASQUERADE,nf_nat,nf_nat_h323,nf_nat_ipv4,nf_nat_pptp,nf_nat_tftp,xt_conntrack,nf_conntrack_ftp,nf_conntrack_irc,nf_conntrack_sip,iptable_nat,nf_conntrack_h323,nf_conntrack_ipv4,nf_conntrack_pptp,nf_conntrack_tftp
ip_tables              27240  2 iptable_filter,iptable_nat
x_tables               34059  6 ip_tables,xt_tcpudp,ipt_MASQUERADE,xt_conntrack,iptable_filter,ipt_REJECT
wl                   6367833  0 
cfg80211              494362  1 wl
rfcomm                 69509  0 
bnep                   19624  2 
bluetooth             446409  10 bnep,rfcomm
6lowpan_iphc           18702  1 bluetooth
nls_iso8859_1          12713  1 
snd_hda_codec_hdmi     47548  1 
snd_hda_intel          30469  4 
uvcvideo               81073  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
snd_hda_controller     31056  1 snd_hda_intel
snd_hda_codec         139682  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_controller
radeon               1412941  3 
videobuf2_core         59104  1 uvcvideo
snd_hwdep              17698  1 snd_hda_codec
v4l2_common            15681  1 videobuf2_core
videodev              153793  3 uvcvideo,v4l2_common,videobuf2_core
snd_pcm               104112  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
media                  21903  2 uvcvideo,videodev
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30876  1 snd_seq_midi
snd_seq                63074  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29562  2 snd_pcm,snd_seq
ttm                    93588  1 radeon
kvm_amd                60328  0 
drm_kms_helper         61574  1 radeon
kvm                   452043  1 kvm_amd
drm                   311018  6 ttm,drm_kms_helper,radeon
snd                    79468  17 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
joydev                 17393  0 
mac_hid                13227  0 
i2c_algo_bit           13413  1 radeon
i2c_piix4              22166  0 
shpchp                 37047  0 
soundcore              15047  2 snd,snd_hda_codec
serio_raw              13483  0 
k10temp                13144  0 
parport_pc             32741  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
psmouse               106561  0 
tg3                   166618  0 
ahci                   34062  3 
libahci                32424  1 ahci
sdhci_pci              23301  0 
ptp                    19395  1 tg3
sdhci                  43685  1 sdhci_pci
pps_core               19382  1 ptp



```


Any help would be greatly appreciated! Thanks in advance!

---

### Post by stephen59 on 2015-04-04
Hi there,

lets start from the top.
Do you have an ip.
do other computers in your network have issues going out to the internet.
does your device resolve names, if not can you ping googles dns 8.8.8.8

---

### Post by Vladlenin5000 on 2015-04-04
Your wireless is```
02:00.0 Network controller [0280]: [COLOR=#008000]Broadcom[/COLOR] Corporation [COLOR=#008000]BCM43227[/COLOR] 802.11b/g/n [[COLOR=#ff0000]14e4:4358[/COLOR]]
``` in an ACER laptop and the link you followed for troubleshooting is about an Intel on a Samsung? Not the way to go...

There's a sticky in the Networking & Wireless dedicated solely to Broadcoms: [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)
Your device is listed as requiring the following drivers ```
14e4:4358                  bcmwl-kernel-source
```
Follow Dr. Chilli's instructions in the link above and you'll be fine.

---

### Post by wildmanne39 on 2015-04-05
Hi, go to the top right corner of the screen click on network manager icon then edit connections>wifi>in the drop down change ad-hoc to infrastrusture then save and close.
Then reboot computer and your wifi should connect if not click the wireless script in my signature and post the file here for us to look at.
Thanks

---

### Post by Vladlenin5000 on 2015-04-05
> **Wild Man said:**
> Hi, go to the top right corner of the screen click on network manager icon then edit connections>wifi>in the drop down change ad-hoc to infrastrusture then save and close.
Then reboot computer and your wifi should connect if not click the wireless script in my signature and post the file here for us to look at.
Thanks

Indeed. I missed that (probably because is kinda unusual...):

```
wlan0     IEEE 802.11abg  ESSID:"NETGEAR 22"  
          Mode:[COLOR=#ff0000]Ad-Hoc[/COLOR]  Frequency:2.412 GHz  Cell: 8E:B8:A9:8A:D2:24   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

---

### Post by newb85 on 2015-04-05
gary58,
FYI, if you follow Wild Man's instructions and keep communicating with him, you're in good hands.  I don't believe there's a wireless issue he can't resolve.

---

### Post by gary58 on 2015-04-05
Great! I'll give all your suggestions a go... starting with wild man's. Sorry it took so long to reply, I ended up reinstalling again thinking I may have a corrupt iso since my usb ports dont work as well and I cant even "try ubuntu" with the CD.

---

### Post by gary58 on 2015-04-05
Ok so infrastructure fails to even connect to the router.

---

### Post by gary58 on 2015-04-05
Ok so I tried Vladlenin's suggestion (using the linked guide), no avail :(. Also to cover the basics, yes my wireless card does work. I just switched from windows OS and it was working fine. I got a friend's old HDD (he was running windows 8), i erased the drive completely, switched out his with mine, and installed ubuntu onto it. Maybe my issue lies somewhere in that process? Because my usb ports don't work as well...

---

### Post by Vladlenin5000 on 2015-04-05
If yours is an ACER Aspire 5560 then you have one of this:
```
CPU AMD A series A6-3420M / 1.5 GHz
```
i.e., one (in)famous AMD APU, a very tight CPU+GPU+North&South chipsets all-in-one-(board).

With Windows 7 chances are that you don't have USB ports at all until you install the Catalyst drivers/software. Although mainly for graphics drivers the Catalyst package apparently includes also code for everything integrated in APUs. So, chances are you need the same proprietary drivers for better performance in Ubuntu, not only for graphics but also for USB and PCI (including the wireless).

Nevertheless, it's better to wait for someone more experienced with AMDs to comment. The aforementioned situation was from a recent experience with a HP 255 G3 where only Windows 8.1 and newer or Ubuntu 14.10 (or 14.04.2) and newer are recommended.

---

### Post by wildmanne39 on 2015-04-05
After you reinstalled did you do:
```
sudo apt-get install bcmwl-kernel-source
```?
or install the sta driver from additional drivers?
See when we give advice it is based on the informaton you posted but all that changed when you reinstalled so if it does not connect after you have installed the driver run the wireless script in my signature and post the file here.
Thanks

---

### Post by gary58 on 2015-04-06
Yeah, I did sudo apt-get install bcmwl-kernel-source.

Here is the txt from the wireless script:

```
########## wireless info START ##########

Report from: 06 Apr 2015 17:06 MST -0700

Booted last: 06 Apr 2015 17:01 MST -0700

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-33-generic #44~14.04.1-Ubuntu SMP Fri Mar 13 10:33:29 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:0605]
    Kernel driver in use: tg3

02:00.0 Network controller [0280]: Broadcom Corporation BCM43227 802.11b/g/n [14e4:4358]
    Subsystem: Foxconn International, Inc. Device [105b:e040]
    Kernel driver in use: wl

##### lsusb #############################

Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 064e:d20c Suyin Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

wl                   6367833  0 
cfg80211              494362  1 wl

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.23  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226a:8aff:fe67:4246/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1220 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1021 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:699927 (699.9 KB)  TX bytes:142294 (142.2 KB)
          Interrupt:11 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet6 addr: fe80::e6d5:3dff:fec5:4df2/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:17629
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:1002 (1.0 KB)
          Interrupt:11 

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"NETGEAR 22"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: <MAC 'NETGEAR 22' [AC1]>   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    NETGEAR 22:      Ad-Hoc, <MAC 'NETGEAR 22' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.23
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/NETGEAR 22 1]] (600 root)
[connection] id=NETGEAR 22 1 | type=802-11-wireless
[802-11-wireless] ssid=NETGEAR 22 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/NETGEAR 22]] (600 root)
[connection] id=NETGEAR 22 | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=NETGEAR 22 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=shared
[ipv6] method=auto

##### iw reg get ########################

Region: America/Phoenix (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Channel 32 : 5.16 GHz
          Channel 34 : 5.17 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 50 : 5.25 GHz
          Channel 52 : 5.26 GHz
          Channel 54 : 5.27 GHz
          Channel 56 : 5.28 GHz
          Channel 58 : 5.29 GHz
          Channel 60 : 5.3 GHz
          Channel 62 : 5.31 GHz
          Channel 64 : 5.32 GHz
          Channel 66 : 5.33 GHz
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'NETGEAR 22' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=0 dBm  
                    Encryption key:off
                    ESSID:"NETGEAR 22"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 68340ms ago

##### module infos ######################

[wl]
filename:       /lib/modules/3.16.0-33-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     9A49255BA90267D99664757
depends:        cfg80211
vermagic:       3.16.0-33-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/3.16.0-33-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     4A525D9D32B0C6D120CA547
depends:        
intree:         Y
vermagic:       3.16.0-33-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        25:26:EE:FE:32:C9:58:B4:CD:85:CA:5F:BF:EB:ED:A1:75:D1:B2:18
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

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

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x14e4:0x16b5 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4358 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[  290.726038] ERROR @wl_dev_intvar_get : error (-1)

########## wireless info END ############

```

---

### Post by wildmanne39 on 2015-04-06
Hi, it is still set to ```
 Mode:Ad-Hoc
```it must be set to infratructure to connect to the internet.

---

### Post by gary58 on 2015-04-06
Aye, sorry I originally made that change. Had to reformat and start again. Forgot to change that setting before running the script. Just made that change and no avail, it won't connect to my router.

---

### Post by wildmanne39 on 2015-04-06
Run the wireless script and post the new file created, please use code tags.

---

### Post by gary58 on 2015-04-06
```

########## wireless info START ##########

Report from: 06 Apr 2015 20:27 MST -0700

Booted last: 06 Apr 2015 20:16 MST -0700

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-33-generic #44~14.04.1-Ubuntu SMP Fri Mar 13 10:33:29 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:0605]
    Kernel driver in use: tg3

02:00.0 Network controller [0280]: Broadcom Corporation BCM43227 802.11b/g/n [14e4:4358]
    Subsystem: Foxconn International, Inc. Device [105b:e040]
    Kernel driver in use: wl

##### lsusb #############################

Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 064e:d20c Suyin Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

wl                   6367833  0 
cfg80211              494362  1 wl

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.23  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226a:8aff:fe67:4246/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2507 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2039 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:987575 (987.5 KB)  TX bytes:277463 (277.4 KB)
          Interrupt:11 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet6 addr: fe80::e6d5:3dff:fec5:4df2/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.23
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/NETGEAR 22]] (600 root)
[connection] id=NETGEAR 22 | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=NETGEAR 22 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=shared
[ipv6] method=auto

##### iw reg get ########################

Region: America/Phoenix (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Channel 32 : 5.16 GHz
          Channel 34 : 5.17 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 50 : 5.25 GHz
          Channel 52 : 5.26 GHz
          Channel 54 : 5.27 GHz
          Channel 56 : 5.28 GHz
          Channel 58 : 5.29 GHz
          Channel 60 : 5.3 GHz
          Channel 62 : 5.31 GHz
          Channel 64 : 5.32 GHz
          Channel 66 : 5.33 GHz

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     No scan results

##### module infos ######################

[wl]
filename:       /lib/modules/3.16.0-33-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     9A49255BA90267D99664757
depends:        cfg80211
vermagic:       3.16.0-33-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/3.16.0-33-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     4A525D9D32B0C6D120CA547
depends:        
intree:         Y
vermagic:       3.16.0-33-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        25:26:EE:FE:32:C9:58:B4:CD:85:CA:5F:BF:EB:ED:A1:75:D1:B2:18
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

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

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x14e4:0x16b5 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4358 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[    8.428770] wl: module license 'MIXED/Proprietary' taints kernel.
[    8.433777] wl: module verification failed: signature and/or  required key missing - tainting kernel
[    8.436449] wl 0000:02:00.0: can't find IRQ for PCI INT A; probably buggy MP table
[    8.498670] wlan0: Broadcom BCM4358 802.11 Hybrid Wireless Controller 6.30.223.248 (r487574)
[  647.093539] ERROR @wl_dev_intvar_get : error (-1)

########## wireless info END ############

```

---

### Post by gary58 on 2015-04-07
I noticed on the report that it showed no wireless access ports. I tried running it again while my wifi was trying to connect, but then it keeps telling me that it is ad-hoc. I then go to settings and it shows that it is infrastructure... I'm so confused with this...

---

### Post by mytien on 2015-04-09
Me too! Wireless able to connect to router, but no internet connection :(

---

### Post by GrouchyGaijin on 2015-04-10
I could be totally off base, but I had a somewhat similar problem.  In my case I could connect to the router, but not to the internet.  When I ran the script in the Wireless fourm I noticed that what was happening was that the wireless card was in an almost constant state of connecting/dropping/reconnecting although this didn't show up just looking at the network icon in the panel (or whatever that place next to the clock is called in Ubuntu). Changing the bandwidth on the router from 20/40 MHz (Auto) to 20 MHz solved my problem.

---

