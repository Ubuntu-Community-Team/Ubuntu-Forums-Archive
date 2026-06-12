---
title: "Wireless Firmware missing?"
date: 2012-09-21
forum: New to Ubuntu
---

### Post by romeoette on 2012-09-21
I have a Latitude D610 computer. I just downloaded Ubuntu a few days ago, and it works great except for the fact that I can't connect to wireless. Anyone help????
It keeps telling me "firmware missing."

---

### Post by NikTh on 2012-09-22
Hi , 
please open a terminal (ctrl+alt+t combo keys) and copy-paste from here bellow commands , one at time. Press Enter after each command . One line = One command 
```
cat /etc/lsb-release 
uname -a 
dmesg | grep -ie firm 
lspci -nnk | grep -iA2 net 
lsusb 
lsmod
``` 
Above commands are only informational . 
Post the results of each command back here and put the results between the brackets **[noparse]```
Here
```[/noparse]** 

Thanks

---

### Post by romeoette on 2012-09-22
> **NikTh said:**
> Hi , 
please open a terminal (ctrl+alt+t combo keys) and copy-paste from here bellow commands , one at time. Press Enter after each command . One line = One command 
```
cat /etc/lsb-release 
uname -a 
dmesg | grep -ie firm 
lspci -nnk | grep -iA2 net 
lsusb 
lsmod
``` 
Above commands are only informational . 
Post the results of each command back here and put the results between the brackets **[noparse]```
Here
```[/noparse]** 

Thanks

cat /etc/lsb-release
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"
```

uname -a 
```
Linux JulietsCrappyLaptop 3.2.0-30-generic-pae #48-Ubuntu SMP Fri Aug 24 17:14:09 UTC 2012 i686 i686 i386 GNU/Linux

```

dmesg | grep -ie firm 
```
[   20.673361] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[   23.422270] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   23.422277] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   23.422281] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.

```

lspci -nnk | grep -iA2 net
```
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] (rev 01)
	Subsystem: Dell Latitude D610 [1028:0182]
	Kernel driver in use: tg3
--
03:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
	Subsystem: Dell Wireless 1370 WLAN Mini 
```

lsusb 
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c05a Logitech, Inc. Optical Mouse M90

```

lsmod
```
Module                  Size  Used by
snd_intel8x0           33455  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
joydev                 17393  0 
snd_pcm                80845  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
radeon                737820  3 
snd_seq_midi_event     14475  1 snd_seq_midi
arc4                   12473  2 
pcmcia                 39791  0 
b43                   342643  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
dell_laptop            17767  0 
dcdbas                 14098  1 dell_laptop
mac80211              436455  1 b43
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                72919  0 
cfg80211              178679  2 b43,mac80211
yenta_socket           27465  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
bcma                   25651  1 b43
serio_raw              13027  0 
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
soundcore              14635  1 snd
drm                   197692  5 radeon,ttm,drm_kms_helper
snd_page_alloc         14108  2 snd_intel8x0,snd_pcm
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
ppdev                  12849  0 
i2c_algo_bit           13199  1 radeon
parport_pc             32114  1 
mac_hid                13077  0 
video                  19068  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41906  0 
hid                    77367  1 usbhid
ssb                    50691  1 b43
tg3                   141369  0 

```

Here you go and thanks. :)

---

### Post by carl4926 on 2012-09-22
If you have a wired connection do this

```
sudo apt-get install firmware-b43-installer
```

---

### Post by NikTh on 2012-09-22
**@carl4926** beat me to it.  :)

Follow his advice and reboot your PC. 

Thanks

---

### Post by romeoette on 2012-09-22
It worked! Thank you both. :)

---

### Post by carl4926 on 2012-09-22
> **romeoette said:**
> It worked! Thank you both. :)

enjoy    :D

---

