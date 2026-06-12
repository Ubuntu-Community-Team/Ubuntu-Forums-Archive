---
title: "Turn on wifi"
date: 2011-09-18
forum: New to Ubuntu
---

### Post by art_monu on 2011-09-18
Hello, 
    I have Dell Inspiron 15R laptop with 2nd generation Core i5 processor. I have dual booted windows with ubuntu linux 10.10 desktop edition. I am not able to browse net in ubuntu through wifi. I cant understand whether wifi is turned on or not. I use the wifi of my hostel having cyberoam. Please tell me how to use it on ubuntu...

---

### Post by wildmanne39 on 2011-09-18
Hi, please run these commands in the terminal and post the results here:
```
cat /etc/lsb-release; uname -a
```
```
sudo lshw -C network
```
```
lspci -nn | grep -e 0280 -e 0200
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by art_monu on 2011-09-20
#(bash: cat/etc/lsb: No such file or directory
Linux ubuntu 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 x86_64 GNU/Linux)

#(Sudo lshw -c network

description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 05
       serial: 18:03:73:53:b5:89
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:47 ioport:d000(size=256) memory:f3204000-f3204fff memory:f3200000-f3203fff
  *-network UNCLAIMED
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       version: 34
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f7a00000-f7a01fff)

#(05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05) 
09:00.0 Network controller [0280]: Intel Corporation Device [8086:008a] (rev 34) 
0b:00.0 USB Controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 04) )

#(lo        no wireless extensions. 

eth0      no wireless extensions. 
)

#(0: hci0: Bluetooth 
    Soft blocked: no 
    Hard blocked: no 
1: dell-wifi: Wireless LAN 
    Soft blocked: yes 
    Hard blocked: yes 
2: dell-bluetooth: Bluetooth 
    Soft blocked: no 
    Hard blocked: yes)

#(Module                  Size  Used by 
parport_pc             30086  0 
ppdev                   6804  0 
rfcomm                 40755  4 
binfmt_misc             7984  1 
sco                     9954  2 
bnep                   11985  2 
l2cap                  42304  16 rfcomm,bnep 
snd_hda_codec_idt      64667  0 
snd_hda_intel          26019  2 
snd_hda_codec         100919  2 snd_hda_codec_idt,snd_hda_intel 
snd_hwdep               6660  1 snd_hda_codec 
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec 
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi 
i915                  330089  2 
snd_seq_midi_event      7291  1 snd_seq_midi 
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event 
snd_timer              23850  2 snd_pcm,snd_seq 
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq 
uvcvideo               62379  0 
nouveau               568848  0 
ttm                    68212  1 nouveau 
drm_kms_helper         32836  2 i915,nouveau 
videodev               49359  1 uvcvideo 
v4l1_compat            15519  2 uvcvideo,videodev 
btusb                  12929  2 
v4l2_compat_ioctl32    12646  1 videodev 
bluetooth              59213  9 rfcomm,sco,bnep,l2cap,btusb 
dell_wmi                3372  0 
snd                    64117  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
psmouse                62080  0 
serio_raw               4910  0 
dell_laptop             6722  0 
dcdbas                  6910  1 dell_laptop 
soundcore               1240  1 snd 
xhci_hcd               58578  0 
intel_agp              32080  2 i915 
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm 
video                  22176  1 i915 
drm                   206161  5 i915,nouveau,ttm,drm_kms_helper 
i2c_algo_bit            6208  2 i915,nouveau 
output                  2527  1 video 
lp                     10201  0 
parport                37032  3 parport_pc,ppdev,lp 
usb_storage            50372  0 
r8169                  42222  0 
mii                     5261  1 r8169 
ahci                   21857  0 
libahci                26167  2 ahci )


these are what appeared in response to the above given codes. please help me solve this problem.

---

### Post by wildmanne39 on 2011-09-20
Hi, please install the backport modules and then unplug your wired connection and restart your computer and see if it will connect.
```
sudo apt-get install linux-backports-modules-wireless-maverick-generic 
```
If it does not post the results of:
```
lsmod
```
again.
Thank you

---

