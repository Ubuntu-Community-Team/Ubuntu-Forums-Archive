---
title: "ubuntu 12.04 inbuilt web cam not working"
date: 2015-02-21
forum: New to Ubuntu
---

### Post by santosh7 on 2015-02-21
I bought new dell i15 3542 ubuntu 64 bit laptop. webcam or skype is not working


The output of lsusb is :

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 248a:8564  
Bus 001 Device 008: ID 0cf3:0036 Atheros Communications, Inc. 
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. 



The output of lspci is :
00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 0b)
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
00:03.0 Audio device: Intel Corporation Device 0a0c (rev 0b)
00:16.0 Communication controller: Intel Corporation Lynx Point-LP HECI #0 (rev 04)
00:1b.0 Audio device: Intel Corporation Lynx Point-LP HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 1 (rev e4)
00:1c.2 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 3 (rev e4)
00:1c.3 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 4 (rev e4)
00:1d.0 USB controller: Intel Corporation Lynx Point-LP USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Lynx Point-LP LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Lynx Point-LP SMBus Controller (rev 04)
06:00.0 Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 07)



The output of gstreamer-properties is:

[IMG]http://i57.tinypic.com/dh4l5z.png[/IMG]


please suggest me steps to find out solutions.

Thanks

---

### Post by sandyd on 2015-02-22
> **santosh7 said:**
> I bought new dell i15 3542 ubuntu 64 bit laptop. webcam or skype is not working


The output of lsusb is :

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 248a:8564  
Bus 001 Device 008: ID 0cf3:0036 Atheros Communications, Inc. 
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. 



The output of lspci is :
00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 0b)
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
00:03.0 Audio device: Intel Corporation Device 0a0c (rev 0b)
00:16.0 Communication controller: Intel Corporation Lynx Point-LP HECI #0 (rev 04)
00:1b.0 Audio device: Intel Corporation Lynx Point-LP HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 1 (rev e4)
00:1c.2 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 3 (rev e4)
00:1c.3 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 4 (rev e4)
00:1d.0 USB controller: Intel Corporation Lynx Point-LP USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Lynx Point-LP LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Lynx Point-LP SMBus Controller (rev 04)
06:00.0 Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 07)



The output of gstreamer-properties is:

[IMG]http://i57.tinypic.com/dh4l5z.png[/IMG]


please suggest me steps to find out solutions.

Thanks
Can you post the output of
```

xinput list
```

Thanks!

---

### Post by santosh7 on 2015-02-22
Hi
Thanks for your kind suppport.Below is output of xinput list

santosh@santosh-Inspiron-3542:~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Telink Wireless Receiver                    id=10    [slave  pointer  (2)]
&#9116;   &#8627; DLL0651:00 06CB:2985                        id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=13    [slave  keyboard (3)]


Please suggest me next step.

---

### Post by sandyd on 2015-02-22
> **santosh7 said:**
> Hi
Thanks for your kind suppport.Below is output of xinput list

santosh@santosh-Inspiron-3542:~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Telink Wireless Receiver                    id=10    [slave  pointer  (2)]
&#9116;   &#8627; DLL0651:00 06CB:2985                        id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=13    [slave  keyboard (3)]


Please suggest me next step.

That.. is an issue.

The webcam does not show up in xinput.

Does ```
dmesg |grep video
``` give any output?

---

### Post by jacobpratt909 on 2015-02-22
Maybe it doesn't have drivers...?

-Wyz

---

### Post by santosh7 on 2015-02-22
Yes, command"dmesg |grep video" shows output as below


santosh@santosh-Inspiron-3542:~$ dmesg |grep video
[   10.245203] Modules linked in: aesni_intel i915(+) ath9k_hw rts5139(C) snd_seq ablk_helper cryptd ath3k(+) lrw hid_rmi btusb ath gf128mul joydev i2c_hid snd_timer snd_seq_device glue_helper aes_x86_64 drm_kms_helper drm cfg80211 bluetooth snd dell_laptop i2c_designware_platform dcdbas dw_dmac mac_hid dell_wmi shpchp mei_me serio_raw sparse_keymap dw_dmac_core mei soundcore i2c_algo_bit i2c_designware_core snd_page_alloc lpc_ich wmi video lp parport hid_generic usbhid hid r8169 ahci libahci mii
[ 1971.094509] video LNXVIDEO:00: Restoring backlight state


i am completely unable to understand above lines. please help.

---

### Post by santosh7 on 2015-02-22
> **jacobpratt909 said:**
> Maybe it doesn't have drivers...?

-Wyz

How can i check if driver installed or working ?

---

### Post by sandyd on 2015-02-23
> **santosh7 said:**
> Yes, command"dmesg |grep video" shows output as below


santosh@santosh-Inspiron-3542:~$ dmesg |grep video
[   10.245203] Modules linked in: aesni_intel i915(+) ath9k_hw rts5139(C) snd_seq ablk_helper cryptd ath3k(+) lrw hid_rmi btusb ath gf128mul joydev i2c_hid snd_timer snd_seq_device glue_helper aes_x86_64 drm_kms_helper drm cfg80211 bluetooth snd dell_laptop i2c_designware_platform dcdbas dw_dmac mac_hid dell_wmi shpchp mei_me serio_raw sparse_keymap dw_dmac_core mei soundcore i2c_algo_bit i2c_designware_core snd_page_alloc lpc_ich wmi video lp parport hid_generic usbhid hid r8169 ahci libahci mii
[ 1971.094509] video LNXVIDEO:00: Restoring backlight state


i am completely unable to understand above lines. please help.
Seems to be a driver issue, Ubuntu does not detect the device at all.

I just noticed that you are using 12.04 LTS. Can you boot up using a Ubuntu 14.04 LTS livecd and see if it works? Your hardware is newer and Ubuntu 12.04 may not have support for your webcam.

If we can get it working in 14.04 LTS, but you want to stay at 12.04, we can simply use [LTSEnablementStack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack") to get things working in 12.04.

---

### Post by santosh7 on 2015-02-24
> **sandyd said:**
> Seems to be a driver issue, Ubuntu does not detect the device at all.

I just noticed that you are using 12.04 LTS. Can you boot up using a Ubuntu 14.04 LTS livecd and see if it works? Your hardware is newer and Ubuntu 12.04 may not have support for your webcam.

If we can get it working in 14.04 LTS, but you want to stay at 12.04, we can simply use [LTSEnablementStack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack") to get things working in 12.04.

Hello,

I try using ubuntu 14.04 live cd . i used empathy to check video call . it seems that video camera was not working.



Followed link of LTSEnablementStack. this is giving the output -

sudo apt-get install --install-recommends linux-generic-lts-trusty xserver-xorg-lts-trusty libgl1-mesa-glx-lts-trusty
[sudo] password for santosh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgl1-mesa-glx-lts-trusty is already the newest version.
xserver-xorg-lts-trusty is already the newest version.
linux-generic-lts-trusty is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.


The output of lsmod is as below : 

Module                  Size  Used by
nls_iso8859_1          12713  2 
nls_utf8               12557  1 
isofs                  40287  1 
usb_storage            66714  3 
ctr                    13193  2 
ccm                    17856  2 
rfcomm                 74748  12 
bnep                   19884  2 
parport_pc             32866  0 
ppdev                  17711  0 
intel_rapl             19228  0 
snd_hda_codec_realtek    66377  1 
snd_hda_codec_hdmi     47006  1 
x86_pkg_temp_thermal    14312  0 
arc4                   12573  2 
snd_hda_intel          57302  5 
snd_hda_codec         199156  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
ath9k                 166619  0 
intel_powerclamp       19031  0 
snd_hwdep              13613  1 snd_hda_codec
mac80211              658141  1 ath9k
snd_pcm               107140  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
coretemp               17728  0 
snd_rawmidi            30465  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
ath9k_common           13551  1 ath9k
rts5139               318332  0 
kvm_intel             144664  0 
kvm                   472641  1 kvm_intel
ath9k_hw              462940  2 ath9k,ath9k_common
snd_seq                66061  2 snd_seq_midi,snd_seq_midi_event
crct10dif_pclmul       14250  0 
crc32_pclmul           13160  0 
ath3k                  13368  0 
btusb                  32519  0 
ghash_clmulni_intel    13216  0 
snd_timer              30038  2 snd_pcm,snd_seq
ath                    29145  3 ath9k,ath9k_common,ath9k_hw
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  821766  5 
joydev                 17575  0 
mei_me                 18674  0 
cfg80211              502970  3 ath9k,mac80211,ath
drm_kms_helper         59668  1 i915
mei                    87127  1 mei_me
drm                   308868  4 i915,drm_kms_helper
bluetooth             411194  25 rfcomm,bnep,ath3k,btusb
aesni_intel            55720  4 
snd                    73890  21 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
hid_rmi                17732  0 
i2c_hid                19186  0 
i2c_designware_platform    13006  0 
dell_laptop            18315  0 
dell_wmi               12761  0 
ablk_helper            13597  1 aesni_intel
cryptd                 20530  3 ghash_clmulni_intel,aesni_intel,ablk_helper
sparse_keymap          13890  1 dell_wmi
lrw                    13323  1 aesni_intel
i2c_designware_core    14990  1 i2c_designware_platform
gf128mul               14951  1 lrw
shpchp                 37201  0 
serio_raw              13462  0 
lpc_ich                21163  0 
i2c_algo_bit           13564  1 i915
wmi                    19363  1 dell_wmi
soundcore              12680  1 snd
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
dcdbas                 15017  1 dell_laptop
video                  19914  1 i915
mac_hid                13253  0 
glue_helper            14095  1 aesni_intel
aes_x86_64             17131  1 aesni_intel
dw_dmac                12814  0 
dw_dmac_core           28517  1 dw_dmac
lp                     17799  0 
parport                42481  3 parport_pc,ppdev,lp
hid_generic            12548  0 
usbhid                 53111  0 
hid                   106605  4 hid_rmi,i2c_hid,hid_generic,usbhid
ahci                   34159  3 
libahci                32825  1 ahci
r8169                  73299  0 
mii                    13981  1 r8169



Does the driver/module for webcam is installed or not ? how should i go with installing required driver/modules for my webcam ?

---

### Post by santosh7 on 2015-02-24
Hello Everyone ,
Please suggest me solution of my webcam.

Here is one more output i am publishing for your reference.



 cat /proc/modules 
nls_iso8859_1 12713 0 - Live 0x0000000000000000
nls_utf8 12557 0 - Live 0x0000000000000000
isofs 40287 0 - Live 0x0000000000000000
usb_storage 66714 0 - Live 0x0000000000000000
ctr 13193 2 - Live 0x0000000000000000
ccm 17856 2 - Live 0x0000000000000000
rfcomm 74748 12 - Live 0x0000000000000000
bnep 19884 2 - Live 0x0000000000000000
parport_pc 32866 0 - Live 0x0000000000000000
ppdev 17711 0 - Live 0x0000000000000000
intel_rapl 19228 0 - Live 0x0000000000000000
snd_hda_codec_realtek 66377 1 - Live 0x0000000000000000
snd_hda_codec_hdmi 47006 1 - Live 0x0000000000000000
x86_pkg_temp_thermal 14312 0 - Live 0x0000000000000000
arc4 12573 2 - Live 0x0000000000000000
snd_hda_intel 57302 5 - Live 0x0000000000000000
snd_hda_codec 199156 3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel, Live 0x0000000000000000
ath9k 166619 0 - Live 0x0000000000000000
intel_powerclamp 19031 0 - Live 0x0000000000000000
snd_hwdep 13613 1 snd_hda_codec, Live 0x0000000000000000
mac80211 658141 1 ath9k, Live 0x0000000000000000
snd_pcm 107140 3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec, Live 0x0000000000000000
snd_seq_midi 13324 0 - Live 0x0000000000000000
coretemp 17728 0 - Live 0x0000000000000000
snd_rawmidi 30465 1 snd_seq_midi, Live 0x0000000000000000
snd_seq_midi_event 14899 1 snd_seq_midi, Live 0x0000000000000000
ath9k_common 13551 1 ath9k, Live 0x0000000000000000
rts5139 318332 0 - Live 0x0000000000000000 (C)
kvm_intel 144664 0 - Live 0x0000000000000000
kvm 472641 1 kvm_intel, Live 0x0000000000000000
ath9k_hw 462940 2 ath9k,ath9k_common, Live 0x0000000000000000
snd_seq 66061 2 snd_seq_midi,snd_seq_midi_event, Live 0x0000000000000000
crct10dif_pclmul 14250 0 - Live 0x0000000000000000
crc32_pclmul 13160 0 - Live 0x0000000000000000
ath3k 13368 0 - Live 0x0000000000000000
btusb 32519 0 - Live 0x0000000000000000
ghash_clmulni_intel 13216 0 - Live 0x0000000000000000
snd_timer 30038 2 snd_pcm,snd_seq, Live 0x0000000000000000
ath 29145 3 ath9k,ath9k_common,ath9k_hw, Live 0x0000000000000000
snd_seq_device 14497 3 snd_seq_midi,snd_rawmidi,snd_seq, Live 0x0000000000000000
i915 821766 5 - Live 0x0000000000000000
joydev 17575 0 - Live 0x0000000000000000
mei_me 18674 0 - Live 0x0000000000000000
cfg80211 502970 3 ath9k,mac80211,ath, Live 0x0000000000000000
drm_kms_helper 59668 1 i915, Live 0x0000000000000000
mei 87127 1 mei_me, Live 0x0000000000000000
drm 308868 4 i915,drm_kms_helper, Live 0x0000000000000000
bluetooth 411194 25 rfcomm,bnep,ath3k,btusb, Live 0x0000000000000000
aesni_intel 55720 4 - Live 0x0000000000000000
snd 73890 21 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device, Live 0x0000000000000000
hid_rmi 17732 0 - Live 0x0000000000000000
i2c_hid 19186 0 - Live 0x0000000000000000
i2c_designware_platform 13006 0 - Live 0x0000000000000000
dell_laptop 18315 0 - Live 0x0000000000000000
dell_wmi 12761 0 - Live 0x0000000000000000
ablk_helper 13597 1 aesni_intel, Live 0x0000000000000000
cryptd 20530 3 ghash_clmulni_intel,aesni_intel,ablk_helper, Live 0x0000000000000000
sparse_keymap 13890 1 dell_wmi, Live 0x0000000000000000
lrw 13323 1 aesni_intel, Live 0x0000000000000000
i2c_designware_core 14990 1 i2c_designware_platform, Live 0x0000000000000000
gf128mul 14951 1 lrw, Live 0x0000000000000000
shpchp 37201 0 - Live 0x0000000000000000
serio_raw 13462 0 - Live 0x0000000000000000
lpc_ich 21163 0 - Live 0x0000000000000000
i2c_algo_bit 13564 1 i915, Live 0x0000000000000000
wmi 19363 1 dell_wmi, Live 0x0000000000000000
soundcore 12680 1 snd, Live 0x0000000000000000
snd_page_alloc 18798 2 snd_hda_intel,snd_pcm, Live 0x0000000000000000
dcdbas 15017 1 dell_laptop, Live 0x0000000000000000
video 19914 1 i915, Live 0x0000000000000000
mac_hid 13253 0 - Live 0x0000000000000000
glue_helper 14095 1 aesni_intel, Live 0x0000000000000000
aes_x86_64 17131 1 aesni_intel, Live 0x0000000000000000
dw_dmac 12814 0 - Live 0x0000000000000000
dw_dmac_core 28517 1 dw_dmac, Live 0x0000000000000000
lp 17799 0 - Live 0x0000000000000000
parport 42481 3 parport_pc,ppdev,lp, Live 0x0000000000000000
hid_generic 12548 0 - Live 0x0000000000000000
usbhid 53111 0 - Live 0x0000000000000000
hid 106605 4 hid_rmi,i2c_hid,hid_generic,usbhid, Live 0x0000000000000000
ahci 34159 3 - Live 0x0000000000000000
libahci 32825 1 ahci, Live 0x0000000000000000
r8169 73299 0 - Live 0x0000000000000000
mii 13981 1 r8169, Live 0x0000000000000000

---

