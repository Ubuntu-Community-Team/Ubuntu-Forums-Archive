---
title: "Internet Connection Problem"
date: 2012-02-19
forum: New to Ubuntu
---

### Post by emreergecen on 2012-02-19
I am using ubuntu alongside windows 7. After accidentally disabling the dhcp server mode on my modem, ubuntu could not connect to my modem wirelessly, despite seeing the wireless network. On ubuntu, I could not log into modem's interface. Then, I started windows and successfully logged into the interface of modem and turned on the dhcp server mode on. On windows, everything went fine. I have internet connection on windows. But when I log into ubuntu, although I connect to the wireless network and my computer obtains an IP, I cannot connect to internet. What could be the reason??

---

### Post by wildmanne39 on 2012-02-19
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by emreergecen on 2012-02-19
#[DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux HomeServer 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:44:39 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller [11ab:4362] (rev 20)
    Subsystem: ASUSTeK Computer Inc. Marvell 88E8053 Gigabit Ethernet controller PCIe (Asus) [1043:8142]
    Kernel driver in use: sky2
    Kernel modules: sky2
03:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller [11ab:4362] (rev 20)
    Subsystem: ASUSTeK Computer Inc. Marvell 88E8053 Gigabit Ethernet controller PCIe (Asus) [1043:8142]
    Kernel driver in use: sky2
    Kernel modules: sky2


lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"EER"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 50:67:F0:85:22:34   
          Bit Rate=24 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=63/70  Signal level=-47 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:46   Missed beacon:0

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
dm_crypt               23199  0 
binfmt_misc            17540  1 
arc4                   12529  2 
gspca_m5602            57141  0 
gspca_main             28314  1 gspca_m5602
videodev               92992  1 gspca_main
v4l2_compat_ioctl32    17083  1 videodev
rtl8187                57035  0 
mac80211              462046  1 rtl8187
cfg80211              199630  2 rtl8187,mac80211
eeprom_93cx6           12725  1 rtl8187
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  2 
snd_hda_codec         104931  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
asus_atk0110           18078  0 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
lm63                   14398  0 
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i82975x_edac           13055  0 
edac_core              53746  1 i82975x_edac
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
radeon               1016475  3 
crc_itu_t              12707  1 firewire_core
sky2                   58674  0 
ttm                    76805  1 radeon
floppy                 70365  0 
drm_kms_helper         42558  1 radeon
drm                   236290  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13423  1 radeon
]

thanks

---

### Post by wildmanne39 on 2012-02-19
Hi, is this an usb adapter? if so please post:
```
lsusb
```
Thanks

---

### Post by emreergecen on 2012-02-19
Yes, I think so. Because it says:

Bus 001 Device 006: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter

I wonder if this problem can be caused by a DNS problem. Because when I ping an address by using its name, it does not work. But when I do it with its IP address, it does ping. F. ex. I use [www.facebook.com](www.facebook.com) for pinging, it does not work. But when I use 66.220.158.53 (I got this IP from windows), it does ping. Can it be the problem?

---

### Post by wildmanne39 on 2012-02-19
Hi, I am not sure, but a few weeks ago there were a lot of people having trouble with these devices, it started out of nowhere.

Please post the output of:
```
nm-tool
sudo iwlist scan
iwlist chan
cat /var/lib/NetworkManager/NetworkManager.state

```
```
sudo cat /var/log/syslog | grep -e rtl -e firmware -e wlan -e wpa -e etork | tail -n75
```
Thanks

---

### Post by emreergecen on 2012-02-19
Thanks for your interest wildmanne39.

I solved the problem. The problem was due to DNS configuration of modem. After reconfiguring modem's DNS settings, the problem got solved.

Thanks a lot :)

---

### Post by wildmanne39 on 2012-02-19
Hi, thats great please use the thread tools to mark thread solved.
Thanks

---

