---
title: "Ubuntu 12.04 won't connect to wifi"
date: 2012-08-04
forum: New to Ubuntu
---

### Post by andypanda96 on 2012-08-04
Hi, I just had my friend install Ubuntu 12.04 LTS for me. Ubuntu will not connect to my wifi network, it just says it's connecting, asks me to give the password, then repeats. My windows partition connects just fine, and Ubuntu connects fine with an ethernet cord. I'm really new to this, thanks.

---

### Post by Finnicella on 2012-08-04
Hi,
please open a terminal and post the output of these commands:
```
iwconfig
```
```
sudo rfkill list all
```
and
```
sudo lshw -C network
```
Bye

---

### Post by andypanda96 on 2012-08-04
Ok here they are

iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.


sudo rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


sudo lshw -C network
 *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 74:2f:68:db:44:b8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-27-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:ddc00000-ddc0ffff
  *-network
       description: Ethernet interface
       product: AR8151 v2.0 Gigabit Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: c0
       serial: 14:da:e9:64:6d:d4
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.0.123 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:59 memory:dc800000-dc83ffff ioport:9000(size=128)

Hope that helps.

---

### Post by Finnicella on 2012-08-04
Ok,
now post the output of these:
```
lsmod | grep ath
```
```
ls /etc/modprobe.d
```
and
```
lsmod
```
I'm not very expert, but I'll try to help you.
Sorry for my english.
Bye

---

### Post by andypanda96 on 2012-08-04
ok thanks

lsmod | grep ath

ath9k                 132390  0 
mac80211              506816  1 ath9k
ath9k_common           14053  1 ath9k
ath9k_hw              411112  2 ath9k,ath9k_common
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
cfg80211              205544  3 ath9k,mac80211,ath

ls /etc/modprobe.dalsa-base.conf              blacklist-rare-network.conf
blacklist-ath_pci.conf      blacklist-watchdog.conf
blacklist.conf              dkms.conf
blacklist-firewire.conf     nvidia-current_hybrid.conf
blacklist-framebuffer.conf  nvidia-graphics-drivers.conf
blacklist-modem.conf        oss-compat.conf
blacklist-oss.conf          vmwgfx-fbdev.conf

lsmod
Module                  Size  Used by
binfmt_misc            17540  1 
btrfs                 652957  0 
zlib_deflate           27139  1 btrfs
libcrc32c              12644  1 btrfs
ufs                    75303  0 
qnx4                   17677  0 
hfsplus                84867  0 
hfs                    54782  0 
minix                  36288  0 
ntfs                  101885  0 
vfat                   17585  0 
msdos                  17332  0 
fat                    61512  2 vfat,msdos
jfs                   186647  0 
xfs                   836544  0 
reiserfs              244805  0 
ext2                   73795  0 
hidp                   22628  1 
hid                    99559  1 hidp
rfcomm                 47604  12 
bnep                   18281  2 
parport_pc             32866  0 
ppdev                  17113  0 
snd_hda_codec_realtek   223962  1 
nvidia              12319264  0 
snd_hda_intel          33773  3 
snd_hda_codec         127706  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
arc4                   12529  2 
snd_timer              29990  2 snd_pcm,snd_seq
joydev                 17693  0 
ath9k                 132390  0 
mac80211              506816  1 ath9k
ath9k_common           14053  1 ath9k
ath9k_hw              411112  2 ath9k,ath9k_common
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
asus_nb_wmi            12710  0 
asus_wmi               24456  1 asus_nb_wmi
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
sparse_keymap          13890  1 asus_wmi
snd                    78855  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
btusb                  18288  4 
cfg80211              205544  3 ath9k,mac80211,ath
bluetooth             180104  28 hidp,rfcomm,bnep,btusb
i915                  472897  2 
drm_kms_helper         46978  1 i915
drm                   242038  3 i915,drm_kms_helper
mxm_wmi                12979  0 
wmi                    19256  2 asus_wmi,mxm_wmi
i2c_algo_bit           13423  1 i915
mei                    41616  0 
video                  19596  1 i915
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
v4l2_compat_ioctl32    17128  1 videodev
psmouse                87692  0 
mac_hid                13253  0 
serio_raw              13211  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
atl1c                  41717  0

Thanks again

---

### Post by Finnicella on 2012-08-04
Ok,
first in editing connection checks that IPv6 is set to ignore.

Edit: Please use the button code (#) for the output, thanks.

---

### Post by andypanda96 on 2012-08-04
OK that I set it to ignore, it didn't seem to do anything.

---

### Post by Finnicella on 2012-08-04
Does it work?

---

### Post by andypanda96 on 2012-08-04
No still the same thing. Says it's connecting, asks for password, i give the password, it says it's connecting, just repeats.

---

### Post by steeldriver on 2012-08-04
Try this

```
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k nohwcrypt=1
```If that works post back and we can add it to your module config file

---

### Post by Finnicella on 2012-08-04
This is a fix that sometimes works:
```
modprobe -r ath9k
```
and then:
```
modprobe ath9k
```
For me now it's time to go to bed, but let me know if it works.
See you tomorrow.
Good night.

---

### Post by andypanda96 on 2012-08-04
Niether of those solutions seemed to work.

---

### Post by Finnicella on 2012-08-05
You can try to follow this thread:
[HTML]http://ubuntuforums.org/showthread.php?t=1877120&highlight=compact+wireless[/HTML]
Bye

---

### Post by andypanda96 on 2012-08-05
Hi,
What if it is not Ubuntu but my network. The network is WPA2 encrypted, and set up using the windows 7 wifi setup wizard. Could the encryption be anything to do with it? I've been searching around and apparently there have been some problems with Ubuntu and WPA connections, but I couldn't find a solution. If anyone has one, or some troobleshooting I could try that would be great. Remember I'm really new to Linux.
Thanks

---

### Post by wildmanne39 on 2012-08-05
Hi please do:
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
if that does not get it working:

Download the zipped wireless script file then:
 Open a terminal using ctrl+alt+t then copy and paste each command online at a time.
 ```
cd ~/Downloads
 chmod +x netscript.sh
 ./netscript.sh
```
 then reply back,  and attach the netinfo.txt file.

The script removes the MAC Address, WPA and WEP key for security.
Thanks

---

