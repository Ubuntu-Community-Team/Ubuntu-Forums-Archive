---
title: "No wireless or wired network connection available."
date: 2012-03-27
forum: New to Ubuntu
---

### Post by iraiderx on 2012-03-27
I am completely new to Linux and Ubuntu. I just installed Ubuntu on my HP touchsmart today. Everything was great until i saw that i had not internet connection. When i click on the internet icon "wired network" and "wireless networks" are faded. networking and Wireless are enabled but still, it doesn't even scan for routers. When i plug in the Ethernet cable it continues to scan and say it is disconnected, What should i do. please help me, i really want to use this OS.

---

### Post by CoDeHacKer on 2012-03-27
Hi, I'm completely new too.  It took me 2 days to get my wireless card working in my HP computer.  There is a nice trouble shooting guide under dash home and help, and wired/wireless network.  I guess somebody 
will need to know what kind of devices you have.  If you type in    nm-tool   it should tell you what kind 
of devices you are using, and what drivers are installed.  I guess you need to tell them what version of 
ubuntu you are using too.

---

### Post by wildmanne39 on 2012-03-27
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by bcschmerker on 2012-03-27
Hewlett-Packard® has run into quality control issues with the Touchsmart&#8482; series, in terms of Ethernet adapters; one [applicable discussion at the HP® Forum](http://h30434.www3.hp.com/t5/TouchSmart-PC/No-LAN-Ethernet-on-Touchsmart-600/td-p/337629) shows three problem reports similar to yours, involving recognition of Ethernet under Microsoft® Windows® 7.0.80xx (MultiProcessor Kernel Family 6.1.76xx).  In certain cases, replacement 'boards are needed, as it's not easy to change out an Ethernet-adapter chip on either an all-in-one or a laptop.

Should, however, USB be all systems go, a USB-to-Ethernet host adapter can be a satisfactory workaround.

---

### Post by iraiderx on 2012-03-28
Thank you all for responding. I took this long because i was in school. Also since i dont even get internet on my computer through an ethernet i had to move the commands to another computer. here they are(the commands are [COLOR=red]red[/COLOR]) btw i did a dual boot so i have both windows and ubuntu, and the internet works perfectly fine on windows, both wireless and through an ethernet.
 
 
 
```

[FONT=Courier New][FONT=Courier New]lazaro@ubuntu:~$ [COLOR=red]cat /etc/lsb-release; uname -a[/COLOR][/FONT]
[FONT=Courier New]DISTRIB_ID=Ubuntu[/FONT]
[FONT=Courier New]DISTRIB_RELEASE=11.10[/FONT]
[FONT=Courier New]DISTRIB_CODENAME=oneiric[/FONT]
[FONT=Courier New]DISTRIB_DESCRIPTION="Ubuntu 11.10"[/FONT]
[FONT=Courier New]Linux ubuntu 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux[/FONT]
[FONT=Courier New]lazaro@ubuntu:~$ [COLOR=red]lspci -nkk | grep -iA2 net[/COLOR][/FONT]
[FONT=Courier New]lazaro@ubuntu:~$ [COLOR=red]lsusb[/COLOR][/FONT]
[FONT=Courier New]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT]
[FONT=Courier New]Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT]
[FONT=Courier New]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]
[FONT=Courier New]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]
[FONT=Courier New]Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]
[FONT=Courier New]Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]
[FONT=Courier New]Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]
[FONT=Courier New]Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader[/FONT]
[FONT=Courier New]Bus 002 Device 002: ID 04f2:b132 Chicony Electronics Co., Ltd [/FONT]
[FONT=Courier New]Bus 003 Device 002: ID 0461:4d63 Primax Electronics, Ltd [/FONT]
[FONT=Courier New]Bus 007 Device 002: ID 08ff:1600 AuthenTec, Inc. AES1600[/FONT]
[FONT=Courier New]Bus 007 Device 003: ID 1b96:0001 N-Trig Duosense Transparent Electromagnetic Digitizer[/FONT]
[FONT=Courier New]Bus 001 Device 006: ID 0bb4:0cba High Tech Computer Corp. [/FONT]
[FONT=Courier New]lazaro@ubuntu:~$ [COLOR=red]iwconfig[/COLOR][/FONT]
[FONT=Courier New]lo        no wireless extensions.[/FONT]
 
[FONT=Courier New]eth0      no wireless extensions.[/FONT]
 
[FONT=Courier New]wlan0     IEEE 802.11bg  ESSID:off/any  [/FONT]
[FONT=Courier New]         Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   [/FONT]
[FONT=Courier New]         Retry  long limit:7   RTS thr:off   Fragment thr:off[/FONT]
[FONT=Courier New]         Power Management:on[/FONT]
 
[FONT=Courier New]lazaro@ubuntu:~$ [COLOR=red]rfkill list all[/COLOR][/FONT]
[FONT=Courier New]0: phy0: Wireless LAN[/FONT]
[FONT=Courier New]     Soft blocked: no[/FONT]
[FONT=Courier New]     Hard blocked: no[/FONT]
[FONT=Courier New]1: hp-wifi: Wireless LAN[/FONT]
[FONT=Courier New]     Soft blocked: no[/FONT]
[FONT=Courier New]     Hard blocked: no[/FONT]
[FONT=Courier New]lazaro@ubuntu:~$ lo        no wireless extensions.[/FONT]
[FONT=Courier New]lo: command not found[/FONT]
[FONT=Courier New]lazaro@ubuntu:~$ [/FONT]
[FONT=Courier New]lazaro@ubuntu:~$ eth0      no wireless extensions.[/FONT]
[FONT=Courier New]eth0: command not found[/FONT]
[FONT=Courier New]lazaro@ubuntu:~$ [/FONT]
[FONT=Courier New]lazaro@ubuntu:~$ wlan0     IEEE 802.11bg  ESSID:off/any  [/FONT]
[FONT=Courier New]wlan0: command not found[/FONT]
[FONT=Courier New]lazaro@ubuntu:~$           Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   [/FONT]
[FONT=Courier New]Mode:Managed: command not found[/FONT]
[FONT=Courier New]lazaro@ubuntu:~$           Retry  long limit:7   RTS thr:off   Fragment thr:off[/FONT]
[FONT=Courier New]Retry: command not found[/FONT]
[FONT=Courier New]lazaro@ubuntu:~$           Power Management:on[/FONT]
[FONT=Courier New]Power: command not found[/FONT]
[FONT=Courier New]lazaro@ubuntu:~$ [COLOR=red]lsmod[/COLOR][/FONT]
[FONT=Courier New]Module                  Size  Used by[/FONT]
[FONT=Courier New]cdc_ether              13536  0 [/FONT]
[FONT=Courier New]usbnet                 26212  1 cdc_ether[/FONT]
[FONT=Courier New]parport_pc             36962  0 [/FONT]
[FONT=Courier New]ppdev                  17113  0 [/FONT]
[FONT=Courier New]rfcomm                 47946  0 [/FONT]
[FONT=Courier New]bnep                   18436  2 [/FONT]
[FONT=Courier New]bluetooth             166112  10 rfcomm,bnep[/FONT]
[FONT=Courier New]binfmt_misc            17540  1 [/FONT]
[FONT=Courier New]snd_hda_codec_si3054    13008  1 [/FONT]
[FONT=Courier New]snd_hda_codec_realtek   330769  1 [/FONT]
[FONT=Courier New]hp_wmi                 18092  0 [/FONT]
[FONT=Courier New]sparse_keymap          13890  1 hp_wmi[/FONT]
[FONT=Courier New]snd_hda_intel          33390  2 [/FONT]
[FONT=Courier New]snd_hda_codec         104802  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel[/FONT]
[FONT=Courier New]snd_hwdep              13668  1 snd_hda_codec[/FONT]
[FONT=Courier New]snd_pcm                96755  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec[/FONT]
[FONT=Courier New]snd_seq_midi           13324  0 [/FONT]
[FONT=Courier New]snd_rawmidi            30547  1 snd_seq_midi[/FONT]
[FONT=Courier New]joydev                 17693  0 [/FONT]
[FONT=Courier New]snd_seq_midi_event     14899  1 snd_seq_midi[/FONT]
[FONT=Courier New]uvcvideo               72711  0 [/FONT]
[FONT=Courier New]videodev               93004  1 uvcvideo[/FONT]
[FONT=Courier New]v4l2_compat_ioctl32    17083  1 videodev[/FONT]
[FONT=Courier New]snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event[/FONT]
[FONT=Courier New]hid_ntrig              13034  0 [/FONT]
[FONT=Courier New]snd_timer              29991  2 snd_pcm,snd_seq[/FONT]
[FONT=Courier New]snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq[/FONT]
[FONT=Courier New]arc4                   12529  2 [/FONT]
[FONT=Courier New]snd                    68266  14 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device[/FONT]
[FONT=Courier New]radeon               1015995  3 [/FONT]
[FONT=Courier New]psmouse                73882  0 [/FONT]
[FONT=Courier New]soundcore              12680  1 snd[/FONT]
[FONT=Courier New]serio_raw              13166  0 [/FONT]
[FONT=Courier New]k10temp                13166  0 [/FONT]
[FONT=Courier New]sp5100_tco             13791  0 [/FONT]
[FONT=Courier New]i2c_piix4              13301  0 [/FONT]
[FONT=Courier New]snd_page_alloc         18529  2 snd_hda_intel,snd_pcm[/FONT]
[FONT=Courier New]ir_lirc_codec          12898  0 [/FONT]
[FONT=Courier New]b43                   341198  0 [/FONT]
[FONT=Courier New]lirc_dev               19204  1 ir_lirc_codec[/FONT]
[FONT=Courier New]ttm                    76805  1 radeon[/FONT]
[FONT=Courier New]drm_kms_helper         42558  1 radeon[/FONT]
[FONT=Courier New]ir_sony_decoder        12549  0 [/FONT]
[FONT=Courier New]drm                   236330  5 radeon,ttm,drm_kms_helper[/FONT]
[FONT=Courier New]ir_jvc_decoder         12546  0 [/FONT]
[FONT=Courier New]mac80211              310872  1 b43[/FONT]
[FONT=Courier New]ir_rc6_decoder         12546  0 [/FONT]
[FONT=Courier New]ir_rc5_decoder         12546  0 [/FONT]
[FONT=Courier New]rc_rc6_mce             12502  0 [/FONT]
[FONT=Courier New]ir_nec_decoder         12546  0 [/FONT]
[FONT=Courier New]cfg80211              199587  2 b43,mac80211[/FONT]
[FONT=Courier New]ene_ir                 22796  0 [/FONT]
[FONT=Courier New]rc_core                26963  9 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,rc_rc6_mce,ir_nec_decoder,ene_ir[/FONT]
[FONT=Courier New]i2c_algo_bit           13423  1 radeon[/FONT]
[FONT=Courier New]video                  19412  0 [/FONT]
[FONT=Courier New]wmi                    19256  1 hp_wmi[/FONT]
[FONT=Courier New]shpchp                 37345  0 [/FONT]
[FONT=Courier New]lp                     17799  0 [/FONT]
[FONT=Courier New]parport                46562  3 parport_pc,ppdev,lp[/FONT]
[FONT=Courier New]usbhid                 47198  1 hid_ntrig[/FONT]
[FONT=Courier New]ums_realtek            13272  0 [/FONT]
[FONT=Courier New]usb_storage            57901  1 ums_realtek[/FONT]
[FONT=Courier New]hid                    95463  2 hid_ntrig,usbhid[/FONT]
[FONT=Courier New]uas                    18027  0 [/FONT]
[FONT=Courier New]pata_atiixp            13164  0 [/FONT]
[FONT=Courier New]r8169                  52788  0 [/FONT]
[FONT=Courier New]ssb                    52752  1 b43[/FONT]
[FONT=Courier New]ahci                   26002  1 [/FONT]
[FONT=Courier New]libahci                26861  1 ahci[/FONT]
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
[/FONT]
```

---

### Post by Gleichsnerd on 2012-03-28
Can you quickly plug

```
lshw -C network
```

into the terminal? It should reveal the manufacturer of your ethernet and wireless chips, which can help point us in the right direction, whether you need third party drivers or whatnot.

---

### Post by iraiderx on 2012-03-28
> **Gleichsnerd said:**
> Can you quickly plug
 
```
lshw -C network
```
 
into the terminal? It should reveal the manufacturer of your ethernet and wireless chips, which can help point us in the right direction, whether you need third party drivers or whatnot.
 
 
```

[FONT=Courier New][SIZE=3]lazaro@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:d1100000-d1103fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:23:8b:b5:0d:d4
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:d1010000-d1010fff memory:d1000000-d100ffff memory:d1020000-d102ffff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:21:00:e5:2c:af
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.0.0-12-generic firmware=N/A multicast=yes wireless=IEEE 802.11bg
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

 [/SIZE][/FONT]

```

---

### Post by Gleichsnerd on 2012-03-28
> **iraiderx said:**
> ```

[FONT=Courier New][SIZE=3]
  *-network               
       description: Network controller
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:d1100000-d1103fff
  [/SIZE][/FONT]

```

Oh Lord... Broadcom...

This sucker is a bit notorious for pulled hair and headaches, mine included.

Here's a link to Ubuntu's fix for the whole shabang:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers")

If your ethernet is faulty still, you'll need the STA without internet instructions.

Before you get too carried away, though, try booting with the LiveCD and seeing if you can connect to the internet that way.

---

### Post by iraiderx on 2012-03-28
> **Gleichsnerd said:**
> Oh Lord... Broadcom...
 
This sucker is a bit notorious for pulled hair and headaches, mine included.
 
Here's a link to Ubuntu's fix for the whole shabang:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers)
 
If your ethernet is faulty still, you'll need the STA without internet instructions.
 
Before you get too carried away, though, try booting with the LiveCD and seeing if you can connect to the internet that way.
 
i had found that same website yesterday but is really complicated to follow those steps. they say if i have no internet access to go to the restricted folder under .../pool/restricted/b/bcwml in order to install that kernel but i have no idea where that restricted folder is found. please help me and thanks in advance and for replying to my posts.

---

### Post by iraiderx on 2012-03-28
_**i just got internet connection. I connected my phone through usb tethering and finally have internet. Now im enableing the drivers. Hopefully i get wireless internet**_. ;d
 
 
 
edit: the drivers were successful and i finally have wireless internet. thank you all for your help.

---

### Post by wildmanne39 on 2012-03-28
Hi, glad you got it working.

---

### Post by Rickx84 on 2012-03-29
Hello Ubuntu community ):P.

I'm relatively new to Ubuntu and have just got a problem that I can't solve myself. I think my biggest problem is I am not fluent in gobbledegook :lolflag:.

I recently bought a wireless PCI adapter (Tenda W322P V2.0) that I can't get to work. I think all the information anyone needs to be able to help me is below:

```
rick@rick-N61PB-M2S:~$ 
rick@rick-N61PB-M2S:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"
Linux rick-N61PB-M2S 2.6.35-32-generic #67-Ubuntu SMP Mon Mar 5 19:35:26 UTC 2012 i686 GNU/Linux
rick@rick-N61PB-M2S:~$ lspci -nnk | grep -iA2 net
00:07.0 Bridge [0680]: nVidia Corporation MCP61 Ethernet [10de:03ef] (rev a2)
	Subsystem: Biostar Microtech Int'l Corp Device [1565:2505]
	Kernel driver in use: forcedeth
--
01:06.0 Network controller [0280]: RaLink Device [1814:3062]
	Subsystem: RaLink Device [1814:3062]
	Kernel driver in use: rt2800pci
rick@rick-N61PB-M2S:~$ lsusb
Bus 002 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
rick@rick-N61PB-M2S:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
rick@rick-N61PB-M2S:~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
rick@rick-N61PB-M2S:~$ lsmod
Module                  Size  Used by
rfcomm                 33843  4 
binfmt_misc             6599  1 
sco                     7998  2 
bnep                    9542  2 
l2cap                  37040  16 rfcomm,bnep
snd_hda_codec_realtek   218460  1 
nvidia               9329739  38 
snd_hda_intel          22235  2 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
arc4                    1165  2 
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
rt2800pci               8852  0 
rt2800lib              28961  1 rt2800pci
rt2x00usb               9779  1 rt2800lib
rt2x00pci               6029  1 rt2800pci
crc_ccitt               1351  1 rt2800pci
rt2x00lib              27307  4 rt2800pci,rt2800lib,rt2x00usb,rt2x00pci
led_class               2633  1 rt2x00lib
mac80211              231959  3 rt2x00usb,rt2x00pci,rt2x00lib
btusb                  11065  2 
ppdev                   5556  0 
snd                    49102  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             26058  1 
bluetooth              50500  9 rfcomm,sco,bnep,l2cap,btusb
agpgart                32011  1 nvidia
cfg80211              144758  2 rt2x00lib,mac80211
psmouse                59027  0 
soundcore                880  1 snd
eeprom_93cx6            1345  1 rt2800pci
k10temp                 2607  0 
serio_raw               4022  0 
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
lp                      7342  0 
i2c_nforce2             5179  0 
parport                31492  3 ppdev,parport_pc,lp
floppy                 54311  0 
forcedeth              49433  0 
pata_amd                8746  2 
sata_nv                19420  0 
rick@rick-N61PB-M2S:~$ 

```

I don't know if I'm just being thick, but any attempts I have had to get it working tell me that Autorun cannot be found.

Any help will be greatly appreciated.

Thanks.

Rick

---

### Post by wildmanne39 on 2012-03-29
Hi, please do:
```
echo "blacklist rt2800usb" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Then unplug your wired connection and reboot does it work?
Thanks

---

### Post by simoncfc on 2012-03-29
i have the same issue but with the wifi only, i have followed the commands requested above and this is my results red fr the commands and orange for discrepancies i found

root@simon:/home/simon#[COLOR=Red] cat /etc/lsb-release; uname -a[/COLOR]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux simon 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 17:34:21 UTC 2012 i686 i686 i386 GNU/Linux
root@simon:/home/simon# [COLOR=Red]lspci -nkk | grep -ia2 net[/COLOR]
root@simon:/home/simon# [COLOR=Red]lsusb[/COLOR]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 003: ID 04f2:b091 Chicony Electronics Co., Ltd Webcam
Bus 006 Device 002: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
root@simon:/home/simon#[COLOR=Red] iwconfig[/COLOR]
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
        [COLOR=DarkOrange]  Power Management:off[/COLOR]
          
root@simon:/home/simon# rfkill list all
0: hp-wifi: Wireless LAN
   [COLOR=DarkOrange] Soft blocked: yes
    Hard blocked: yes[/COLOR]
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
root@simon:/home/simon#[COLOR=Red] lsmod[/COLOR]
Module                  Size  Used by
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
joydev                 17393  0 
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
binfmt_misc            17292  1 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_conexant    52460  1 
arc4                   12473  2 
snd_hda_intel          24262  2 
snd_hda_codec          91859  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73673  0 
nvidia               7098131  37 
serio_raw              12990  0 
ath5k                 145100  0 
ath                    19387  1 ath5k
mac80211              393421  1 ath5k
snd                    55902  14 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    18744  1 hp_wmi
video                  18908  0 
cfg80211              172427  3 ath5k,ath,mac80211
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
ums_realtek            13096  0 
usb_storage            44173  1 ums_realtek
hid                    77367  1 usbhid
uas                    17699  0 
ahci                   21634  2 
libahci                25727  1 ahci
r8169                  43104  0 
root@simon:/home/simon#[COLOR=Red] lshw -c network[/COLOR]
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:16:42:18:7c
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.0.6 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:3000(size=256) memory:d3010000-d3010fff memory:d3000000-d300ffff memory:d3020000-d303ffff
  *-network
       description: Wireless interface
       product: AR242x / AR542x Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:23:4e:41:86:ba
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=3.0.0-17-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:d5100000-d510ffff
root@simon:/home/simon# [COLOR=Red]rfkill unblock al[/COLOR]l
root@simon:/home/simon#[COLOR=Yellow] rfkill list all[/COLOR]
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by Gleichsnerd on 2012-03-29
Simon,

Have you tried looking for additional drivers while connected to the internet through a wired connection?

To do so, just click the System Settings icon on the unity dash and select "Additional Drivers;" there should hopefully be a driver for your wireless card that can fix your issues.

---

### Post by simoncfc on 2012-03-29
**Re: No wireless or wired network connection available.**
 		Gleichsnerd

 thank you for replying so quickly, i did as suggested but the only additional driver i was presented with was a graphics driver and nothing to do with the wireless, i have checked on another thread and a suggestion was to place a blank file in the /etc/pm/power.d directory called wireless and i did but still nothing when using the /sbin/iwconfig wlan0 power on command i get the reply 

Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.

any thoughts? the wireless worked fine until i tried to use aircrack-ng to locate the password on an old wireless router i am trying to set up its a never ending circle

---

### Post by Gleichsnerd on 2012-03-29
Simon,

No problem! My fingers are crossed that aircrack didn't do anything to alter your wireless driver. According to your output above, the driver that is installed for your card is locked and loaded (as seen in lsmod).

To be honest, my experience with wireless dissection and troubleshooting lies mostly within broadcom cards. I strongly suggest you follow the Wireless Network Troubleshooter, found in the Ubuntu help guide (just type in "Help" into the unity dash). I'll take a deeper look into the matter in the meantime.

---

### Post by wildmanne39 on 2012-03-29
Hi, the power management off is not a problem it is better that way in a lot of cases for laptops.

The problem is you have a soft and a hard block, and I have helped 2 other people with this same card with this same issue and it is very hard to solve apparently this is a problem with ubuntu 11.10 if you ever turned the wireless off with the physical switch.

Please try this: just copy and paste the commands for accuracy:
```
echo "blacklist hp-wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Then
```
gksudo gedit /etc/rc.local
```
Add your three lines above exit 0:
```
rmmod -r ath5k
rfkill unblock all
modprobe ath5k
```
Proofread carefully, save and close gedit. Reboot and tell us if it's working as expected.

This topic aircrack-ng  is not supported in the forum so we can not discuss it.
Thank you

---

### Post by simoncfc on 2012-04-01
[wildmanne39]("http://ubuntuforums.org/member.php?u=508533") many many thanks for the code and the direction it proved excellent advice and i now have my wifi up and running. i must add that the blacklist.conf line did not work as i received a permission denied so i navigated to the file and ran the gedit code once i inserted the 3 lines as directed on save i had a failure but i checked and the save held.

finally the reference to my mentioning aircrack-ng i actually realise that this program has a taboo attached to it as some lets say less than honest people would use this for bad but as i explained i was in fact trying to use this to solve an issue i have with my own private wifi hubs i was trying to convert to open source if you have any suggestions on how i not only discover my forgotten password and settings but enable me to unlock a homehub and use it with my current isp then i welcome them.

again many thanks for the sound advice - porblem solved

---

