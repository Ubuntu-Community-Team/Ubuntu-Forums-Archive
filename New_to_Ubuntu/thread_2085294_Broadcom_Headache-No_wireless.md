---
title: "Broadcom Headache-No wireless"
date: 2012-11-17
forum: New to Ubuntu
---

### Post by Sequoia Bird on 2012-11-17
I have ubuntu 12.10, and after I installed the updates about two weeks ago the wireless card stopped working. I have a Broadcom 4312 wireless card.  
```
rfkill list
```returns nothing.
Software Sources says I am using the proprietary driver.  I have fwcutter installed. 

```
lshw -C network
``` returns:
```
*-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0200000-f0203fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: b8:ac:6f:7a:6a:94
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=(tip toppity secret) latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 ioport:3000(size=256) memory:f0410000-f0410fff memory:f0400000-f040ffff memory:f0420000-f043ffff


```Thanks for any help!

---

### Post by newb85 on 2012-11-17
Which of these do you have installed?

firmware-b43-installer
firmware-b43-lpphy-installer
bcmwl-kernel-source

---

### Post by Sequoia Bird on 2012-11-17
I have firmware-b43-lpphy-installer installed

Should I change that?

Thanks

---

### Post by newb85 on 2012-11-17
No, I don't think so.

---

### Post by squakie on 2012-11-17
Try following the instructions in post #7 of this thread:

[http://ubuntuforums.org/showthread.php?t=2077104](http://ubuntuforums.org/showthread.php?t=2077104)

---

### Post by Sequoia Bird on 2012-11-17
Something changed, but it still doesn't work. Thanks for the help though...
```
rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
``````

octopus@octopus-Inspiron-1564:~$  lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f0200000-f0203fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: b8:ac:6f:7a:6a:94
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.14 latency=0 multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 ioport:3000(size=256) memory:f0410000-f0410fff memory:f0400000-f040ffff memory:f0420000-f043ffff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 78:e4:00:b3:4f:6f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.5.0-18-generic firmware=410.2160 multicast=yes wireless=IEEE 802.11bg
```EDIT: after a reboot it's back at square one, same situation as in my first post.

---

### Post by squakie on 2012-11-17
Post back the output of lsmod so we can see which modules are getting loaded at boot.

---

### Post by wildmanne39 on 2012-11-17
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by Sequoia Bird on 2012-11-18
Sorry for the delay--
```

octopus@octopus-Inspiron-1564:~$ lsmod
Module                  Size  Used by
snd_hda_codec_hdmi     32007  1 
joydev                 17457  0 
rfcomm                 46619  0 
parport_pc             32688  0 
ppdev                  17073  0 
bnep                   18140  2 
bluetooth             209199  10 rfcomm,bnep
coretemp               13400  0 
kvm_intel             132759  0 
kvm                   414070  1 kvm_intel
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
snd_hda_codec_realtek    77876  1 
dell_laptop            17369  0 
dcdbas                 14438  1 dell_laptop
snd_hda_intel          33491  5 
snd_hda_codec         134212  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                96580  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30512  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29425  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
microcode              22803  0 
uvcvideo               76749  0 
videobuf2_core         32851  1 uvcvideo
videodev              120309  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12860  1 uvcvideo
videobuf2_memops       13368  1 videobuf2_vmalloc
psmouse                95552  0 
serio_raw              13215  0 
lpc_ich                17061  0 
radeon                895653  3 
snd                    78734  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ttm                    83595  1 radeon
drm_kms_helper         46784  1 radeon
drm                   275528  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13413  1 radeon
soundcore              15047  1 snd
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
mei                    40690  0 
wmi                    19070  1 dell_wmi
video                  19335  0 
mac_hid                13205  0 
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
ums_realtek            17949  0 
usb_storage            48838  1 ums_realtek
uas                    17844  0 
r8169                  61650  0 

```

---

### Post by wildmanne39 on 2012-11-18
Hi, please do:
```
sudo apt-get install --reinstall linux-headers-$(uname -r)
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
```
Reboot
Thanks

---

### Post by Sequoia Bird on 2012-11-18
Beautiful! It works. 

Thanks for your time, Wild Man.

---

### Post by wildmanne39 on 2012-11-18
Your welcome!
Enjoy

---

