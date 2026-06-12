---
title: "Slow wireless internet"
date: 2012-08-14
forum: New to Ubuntu
---

### Post by Prioryjk on 2012-08-14
Ubuntu seems to have a slower Internet speed then Windows on a dual boot I was wondering if there was anything I could do to fix it? 

> DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"
Linux ampersand 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:03:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
> 02:00.0 Ethernet controller [0200]: Realtek Semiconductor  Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller  [10ec:8168] (rev 03)
    Subsystem: ASUSTeK Computer Inc. M4A785TD Motherboard [1043:83a3]
    Kernel driver in use: r8169
> Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 1737:0078 Linksys WUSB100 v2 RangePlus Wireless Network Adapter [Ralink RT3070]
Bus 002 Device 003: ID 03f0:a007 Hewlett-Packard 
Bus 002 Device 004: ID 413c:2005 Dell Computer Corp. RT7D50 Keyboard
Bus 002 Device 005: ID 04d9:0420 Holtek Semiconductor, Inc. 
> lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"TNCAPB38EF1"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 08:76:FF:B3:8E:F1   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:eek:ff   Fragment thr:eek:ff
          Power Management:eek:n
          Link Quality=47/70  Signal level=-63 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:5413  Invalid misc:3326   Missed beacon:0

eth0      no wireless extensions.
> 0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
> Module                  Size  Used by
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17113  0 
dm_crypt               23125  1 
arc4                   12529  2 
rt2800usb              22684  0 
rt2800lib              58925  1 rt2800usb
crc_ccitt              12667  1 rt2800lib
rt2x00usb              20762  1 rt2800usb
rt2x00lib              51144  3 rt2800usb,rt2800lib,rt2x00usb
snd_usb_audio         122982  2 
mac80211              506816  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              205544  2 rt2x00lib,mac80211
snd_usbmidi_lib        25395  1 snd_usb_audio
snd_hda_codec_via      51398  1 
snd_hda_intel          33773  3 
snd_hda_codec         127706  2 snd_hda_codec_via,snd_hda_intel
nvidia              12319264  40 
snd_hwdep              13668  2 snd_usb_audio,snd_hda_codec
snd_pcm                97188  3 snd_usb_audio,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
i7core_edac            28102  0 
snd_rawmidi            30748  2 snd_usbmidi_lib,snd_seq_midi
asus_atk0110           18078  0 
mac_hid                13253  0 
snd_seq_midi_event     14899  1 snd_seq_midi
edac_core              53746  3 i7core_edac
psmouse                87692  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
serio_raw              13211  0 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  21  snd_usb_audio,snd_usbmidi_lib,snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
vesafb                 13844  1 
firewire_ohci          41000  0 
usbhid                 47199  0 
hid                    99559  1 usbhid
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
pata_jmicron           12747  0 
r8169                  62099  0 
> NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        90:E6:BA:10:7A:2B

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [TNCAPB38EF1] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800usb
  State:             connected
  Default:           yes
  HW Address:        00:25:9C:BA:31:59

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *TNCAPB38EF1:    Infra, 08:76:FF:B3:8E:F1, Freq 2412 MHz, Rate 54 Mb/s, Strength 59 WPA WPA2
    TALKTALK-762752: Infra, 84:C9:B2:76:27:52, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.64
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254



---

### Post by Kalanac on 2012-08-14
I know it sounds like a terrible cliché, but have you tried turning the router off for a couple of minutes then back on?  It's amazing how often that clears up slow down problems.

---

### Post by Prioryjk on 2012-08-14
I'll give it a try but I have windows 7 on my pc as well and its downloads are much faster, im going from about 30kbs on ubuntu upto at least 400kbs on win7.

---

### Post by wildmanne39 on 2012-08-14
Hi, please do:
```
gksudo gedit /etc/pm/power.d/wireless
```

(this will create or edit a configuration file that will override the default powermanagement behavior) and enter the following: 
#!/bin/sh

```
/sbin/iwconfig wlan0 power off
```

above exit0, then save gedit, close and reboot.

Then:
```
echo "options rt2800usb nohwcrypt=1" | sudo tee /etc/modprobe.d/rt2800usb.conf
sudo modprobe -rfv rt2800usb
sudo modprobe -v rt2800usb 
```
Thanks

---

### Post by Prioryjk on 2012-08-14
Hi, it created a new file with no info in and i entered 

#!/bin/sh
/sbin/iwconfig wlan0 power off
exit0

I entered the commands and got this 

rich@ampersand:~$ echo "options rt2800usb nohwcrypt=1" | sudo tee /etc/modprobe.d/rt2800usb.conf
[sudo] password for rich: 
options rt2800usb nohwcrypt=1
rich@ampersand:~$ sudo modprobe -rfv rt2800usb
rmmod /lib/modules/3.2.0-29-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
rmmod /lib/modules/3.2.0-29-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
rmmod /lib/modules/3.2.0-29-generic/kernel/lib/crc-ccitt.ko
rmmod /lib/modules/3.2.0-29-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
rmmod /lib/modules/3.2.0-29-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
rmmod /lib/modules/3.2.0-29-generic/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.2.0-29-generic/kernel/net/wireless/cfg80211.ko
rich@ampersand:~$ sudo modprobe -v rt2800usb
insmod /lib/modules/3.2.0-29-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.2.0-29-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.2.0-29-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko 
insmod /lib/modules/3.2.0-29-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko 
insmod /lib/modules/3.2.0-29-generic/kernel/lib/crc-ccitt.ko 
insmod /lib/modules/3.2.0-29-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko 
insmod /lib/modules/3.2.0-29-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko nohwcrypt=1


Thanks in advance.

---

### Post by wildmanne39 on 2012-08-14
Hi exit 0 should already be in the file but if not then you need to add it to the very bottom, if any doubts please post the contents of the file.
Thanks

---

### Post by Prioryjk on 2012-08-14
redid it im going to compare a certain download and see the result doesn't seem any faster however.

---

### Post by wildmanne39 on 2012-08-14
Hi, also setting your network settings to match the screenshots usually speeds up internet a lot.

---

### Post by Prioryjk on 2012-08-14
Thanks comparing them now they are compatible the speed seems to boost at the start and then drop off but i think thats not Ubuntu specific, thanks for your help!

---

### Post by wildmanne39 on 2012-08-14
Hi, glad to hear if you issue is resolved please use thread tools at the top of the page to mark the thread solved.
Thanks

---

