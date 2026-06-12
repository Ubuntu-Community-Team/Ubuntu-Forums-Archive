---
title: "Wifi hardware switch key combination moved"
date: 2014-04-05
forum: New to Ubuntu
---

### Post by knulp2 on 2014-04-05
Hello,
I'm new to linux, and recently switched to lubuntu 13.10 as a windows XP refugee. I have everything working quite well and am very pleased with the performance boost, but have a slight issue with the key combination (Fn+F1) to switch my wifi on and off. At first I couldn't get it to work, but after some forum searching and trial and error I found out that the key combination to switch the wifi on and off on my laptop (a BenQ joybook A33E with Ralink2500 wireless chip) changed from the normal Fn+F1 to Fn+F12. After I turn my wifi on with Fn+F12 it works perfectly and I can also switch it on and off with the usual combination of Fn+F1. Every time I reboot I have to use Fn+F12 again. It's not a big issue, it's just a bit annoying because Fn+F12 also puts the laptop in sleep mode. Is there any way to fix this?
Thank you in advance!

---

### Post by varunendra on 2014-04-05
Welcome to the forums knulp2!

> **knulp2 said:**
> ....because Fn+F12 also puts the laptop in sleep mode..
This sounds familiar. It seems your wifi works only after a suspend-resume cycle, doesn't matter you do it via Fn+F12 or any other way.

Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates. Run the script before doing the suspend (preferably after a fresh reboot).

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by knulp2 on 2014-04-05
Thank you for the welcome and the very beginner friendly help.
You're right, I tried entering sleep mode by closing the lid and that fixed the wifi aswell. Here is the outcome of the script after rebooting, when the wifi was not working.
```

########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy

##### kernel #####

Linux benq-Joybook-A33 3.11.0-19-generic #33-Ubuntu SMP Tue Mar 11 18:48:32 UTC 2014 i686 i686 i686 GNU/Linux

##### lspci #####

01:04.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Subsystem: Mitac Device [1071:8048]
    Kernel driver in use: 8139too
01:05.0 Network controller [0280]: Ralink corp. RT2500 Wireless 802.11bg [1814:0201] (rev 01)
    Subsystem: Ralink corp. RT2500 Wireless 802.11bg [1814:2560]
    Kernel driver in use: rt2500pci

##### lsusb #####

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA Card Info #####

##### rfkill #####

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

##### iw reg get #####

##### interfaces #####

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

##### iwconfig #####

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #####

##### nm-tool #####

NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2500pci
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### iwlist #####

##### iwlist channel #####

wlan0     14 channels in total; available frequencies :
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

##### lsmod #####

rt2500pci              22682  0 
rt2x00pci              13111  1 rt2500pci
rt2x00mmio             13395  1 rt2500pci
rt2x00lib              48933  3 rt2x00pci,rt2500pci,rt2x00mmio
mac80211              517444  2 rt2x00lib,rt2x00pci
cfg80211              401762  2 mac80211,rt2x00lib
eeprom_93cx6           13168  1 rt2500pci

##### modinfo #####

filename:       /lib/modules/3.11.0-19-generic/kernel/drivers/net/wireless/rt2x00/rt2500pci.ko
license:        GPL
description:    Ralink RT2500 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     19216BE5041DE34C99CD219
alias:          pci:v00001814d00000201sv*sd*bc*sc*i*
depends:        rt2x00lib,rt2x00mmio,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       3.11.0-19-generic SMP mod_unload modversions 686 

filename:       /lib/modules/3.11.0-19-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     8422005AAAD8B7D2F811DC4
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.11.0-19-generic SMP mod_unload modversions 686 

filename:       /lib/modules/3.11.0-19-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     2C5ADAF564EF1DAD569D9C3
depends:        rt2x00lib
intree:         Y
vermagic:       3.11.0-19-generic SMP mod_unload modversions 686 

filename:       /lib/modules/3.11.0-19-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     EB7C454417ADECB5D8A7F2A
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.11.0-19-generic SMP mod_unload modversions 686 

##### modules #####

lp

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

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

##### udev rules #####

# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x1814:0x0201 (rt2500pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[   18.267979] intel_rng: don't want to disable this in firmware setup, and if
[   19.133403] ieee80211 phy0: rt2x00_set_chip: Info - Chipset detected - rt: 2560, rf: 0003, rev: 0004
[   23.772901] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

########## wireless info END ############


```

---

### Post by varunendra on 2014-04-05
Not many clues in the above output, so all I can suggest as of now is to try this -
```
sudo iwconfig wlan0 power off
```
If it returns any errors, please post them back here. If not, try -
```
sudo rfkill unblock all
```
Does the wifi turn on after this? If not, please post the outputs of -
```
iwconfig
lsmod
egrep -i 'phy|rt25|switch|firmware|error' /var/log/syslog | tail -40
```

---

### Post by knulp2 on 2014-04-06
I already tried those first two commands earlier, without effect. I just tried again after rebooting and nothing changes, it still says "wifi disabled by hardware switch", while the LED on my laptop indicates it is turned on. Here is the total output from the terminal for those commands you asked. I don't want to take up too much of your time for a problem that is as easily fixed as closing and opening my laptop though, so I understand if you use your time to help other people.

```
benq@benq-Joybook-A33:~$ sudo iwconfig wlan0 power off
[sudo] password for benq: 
benq@benq-Joybook-A33:~$ sudo rfkill unblock all
benq@benq-Joybook-A33:~$ iwconfig
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

eth0      no wireless extensions.

benq@benq-Joybook-A33:~$ lsmod
Module                  Size  Used by
zram                   18070  1 
joydev                 17097  0 
snd_hda_codec_realtek    50315  1 
parport_pc             31981  0 
ppdev                  17391  0 
bnep                   18959  2 
rfcomm                 53664  0 
bluetooth             323656  10 bnep,rfcomm
snd_hda_intel          42658  1 
snd_hda_codec         164003  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                89488  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
arc4                   12536  2 
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
rt2500pci              22682  0 
snd_rawmidi            25094  1 snd_seq_midi
pcmcia                 51368  0 
rt2x00pci              13111  1 rt2500pci
rt2x00mmio             13395  1 rt2500pci
microcode              18894  0 
binfmt_misc            13140  1 
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
rt2x00lib              48933  3 rt2x00pci,rt2500pci,rt2x00mmio
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
i915                  594442  2 
mac80211              517444  2 rt2x00lib,rt2x00pci
snd_timer              24447  2 snd_pcm,snd_seq
psmouse                90642  0 
ext2                   67224  1 
yenta_socket           40193  0 
cfg80211              401762  2 mac80211,rt2x00lib
serio_raw              13189  0 
snd                    60790  12 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
drm_kms_helper         46867  1 i915
pcmcia_rsrc            18319  1 yenta_socket
lpc_ich                16864  0 
eeprom_93cx6           13168  1 rt2500pci
pcmcia_core            22328  3 pcmcia,pcmcia_rsrc,yenta_socket
drm                   242400  3 i915,drm_kms_helper
soundcore              12600  1 snd
video                  18777  1 i915
i2c_algo_bit           13197  1 i915
mac_hid                13037  0 
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
firewire_ohci          35463  0 
firewire_core          57656  1 firewire_ohci
8139too                32530  0 
8139cp                 27130  0 
crc_itu_t              12627  1 firewire_core
mii                    13654  2 8139cp,8139too
benq@benq-Joybook-A33:~$ egrep -i 'phy|rt25|switch|firmware|error' /var/log/syslog | tail -40
Apr  5 23:39:00 benq-Joybook-A33 kernel: [  979.540043] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Apr  5 23:39:00 benq-Joybook-A33 kernel: [  979.972043] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Apr  5 23:39:00 benq-Joybook-A33 kernel: [  980.132043] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Apr  5 23:39:01 benq-Joybook-A33 kernel: [  980.964096] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Apr  5 23:39:01 benq-Joybook-A33 kernel: [  981.125842] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Apr  5 23:39:02 benq-Joybook-A33 kernel: [  981.556071] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Apr  5 23:39:02 benq-Joybook-A33 kernel: [  981.716083] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Apr  5 23:39:02 benq-Joybook-A33 kernel: [  982.148059] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Apr  5 23:39:02 benq-Joybook-A33 kernel: [  982.308049] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Apr  5 23:39:03 benq-Joybook-A33 kernel: [  982.793448] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Apr  5 23:39:03 benq-Joybook-A33 kernel: [  982.952082] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Apr  5 23:39:03 benq-Joybook-A33 kernel: [  983.436067] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Apr  5 23:39:04 benq-Joybook-A33 kernel: [  983.596054] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Apr  5 23:50:56 benq-Joybook-A33 kernel: [ 1696.164040] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Apr  5 23:50:56 benq-Joybook-A33 kernel: [ 1696.324049] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Apr  5 23:50:57 benq-Joybook-A33 kernel: [ 1696.692058] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Apr  5 23:50:57 benq-Joybook-A33 kernel: [ 1696.852051] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Apr  5 23:54:56 benq-Joybook-A33 kernel: [ 1936.160053] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Apr  5 23:54:57 benq-Joybook-A33 kernel: [ 1936.608034] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Apr  5 23:56:56 benq-Joybook-A33 kernel: [ 2056.180046] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Apr  6 12:26:33 benq-Joybook-A33 kernel: [ 3647.591531] rt2500pci 0000:01:05.0 wlan0: disabling HT/VHT due to WEP/TKIP use
Apr  6 12:26:33 benq-Joybook-A33 kernel: [ 3647.591536] rt2500pci 0000:01:05.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
Apr  6 12:26:33 benq-Joybook-A33 kernel: [ 3647.591540] rt2500pci 0000:01:05.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
Apr  6 12:33:21 benq-Joybook-A33 kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Apr  6 12:33:21 benq-Joybook-A33 kernel: [    0.124074] Switched to clocksource hpet
Apr  6 12:33:21 benq-Joybook-A33 kernel: [    0.796616] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
Apr  6 12:33:21 benq-Joybook-A33 kernel: [    0.797942] ACPI: Lid Switch [LID]
Apr  6 12:33:21 benq-Joybook-A33 kernel: [    1.081233] libphy: Fixed MDIO Bus: probed
Apr  6 12:33:21 benq-Joybook-A33 kernel: [   18.447048] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
Apr  6 12:33:21 benq-Joybook-A33 kernel: [   18.548437] intel_rng: Firmware space is locked read-only. If you can't or
Apr  6 12:33:21 benq-Joybook-A33 kernel: [   18.548437] intel_rng: don't want to disable this in firmware setup, and if
Apr  6 12:33:21 benq-Joybook-A33 kernel: [   19.401624] ieee80211 phy0: rt2x00_set_chip: Info - Chipset detected - rt: 2560, rf: 0003, rev: 0004
Apr  6 12:33:21 benq-Joybook-A33 kernel: [   19.466796] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
Apr  6 12:33:21 benq-Joybook-A33 kernel: [   20.235009] Console: switching to colour frame buffer device 160x50
Apr  6 12:33:25 benq-Joybook-A33 NetworkManager[721]: <info> monitoring kernel firmware directory '/lib/firmware'.
Apr  6 12:33:25 benq-Joybook-A33 NetworkManager[721]: <info> rfkill0: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:1e.0/0000:01:05.0/ieee80211/phy0/rfkill0) (driver rt2500pci)
Apr  6 12:33:25 benq-Joybook-A33 NetworkManager[721]: <info> WiFi disabled by radio killswitch; enabled by state file
Apr  6 12:33:25 benq-Joybook-A33 NetworkManager[721]: <info> WWAN enabled by radio killswitch; enabled by state file
Apr  6 12:33:25 benq-Joybook-A33 NetworkManager[721]: <info> WiMAX enabled by radio killswitch; enabled by state file
Apr  6 12:33:25 benq-Joybook-A33 NetworkManager[721]: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2500pci' ifindex: 3)
benq@benq-Joybook-A33:~$ 

```

---

### Post by varunendra on 2014-04-08
In fact I am not able to help 'Anybody' these days. My posting frequency has come down from 20-40 posts a day to 7-8 posts a week.

I couldn't notice any obvious culprit in the above outputs (there is a clear message that the wifi is disabled by hardware switch, but no clues on why). So now, I would suggest to upload your full 'syslog' and 'pm-suspend.log' files at [http://pastebin.ubuntu.com/](http://pastebin.ubuntu.com/) and post their links here or wherever you are currently seeking help. Both these files are located in '**/var/log**' directory.

Hopefully these may give some significant clue. If not, it would be all 'shots in the dark', whatever else we try.

---

### Post by knulp2 on 2014-04-08
Well you're helping me, so that's at least somebody. And I have plenty of time, so no rush.

Here are the log files. I rebooted and suspended-resumed for you one more time, I thought it might save you some reading if you only have to look at the end. Wifi was not working after reboot, and was fixed again after the last suspend cycle timestamped Tue Apr 8 19:30. I hope that helps you.

syslog: [http://pastebin.ubuntu.com/7222619/](http://pastebin.ubuntu.com/7222619/)
pm-suspend.log: [http://pastebin.ubuntu.com/7222626/](http://pastebin.ubuntu.com/7222626/)

---

### Post by varunendra on 2014-04-10
Sorry, with severe cough & cold on top of my hectic schedule these days, I am unable to concentrate. Even if there are hints in the logs, I couldn't notice any.

I have no further suggestions other than filing a bug report at launchpad, and wait for a fix.

Or, contact (PM) one of these gentlemen for help - chili555, Wild Man, praseodym, Hadaka, and see if they have any more ideas for you.

**PS:**
You may try installing a newer driver for the card and hope for a miracle. Although I don't think it may help in a 'hard-block' issue like you are having, but it shouldn't hurt anything either. If you wish to try that, please follow the instructions in this post (the last line in the post about "nohwcrypt" parameter is not applicable to you, just ignore it) : [http://ubuntuforums.org/showthread.php?t=2204912&p=12927696#post12927696](http://ubuntuforums.org/showthread.php?t=2204912&p=12927696#post12927696)

---

### Post by knulp2 on 2014-04-10
Ok, I think I'll file a bug report. I tried the update, that indeed didn't seem to do anything.

Thank you very much for all your help Varunendra, and I hope you get better soon.

---

