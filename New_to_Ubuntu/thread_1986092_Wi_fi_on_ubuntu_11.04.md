---
title: "Wi fi on ubuntu 11.04"
date: 2012-05-24
forum: New to Ubuntu
---

### Post by bogdanonyshenko on 2012-05-24
Hello all!
Here is a problem. I installed ubuntu 12.04 on Acer extenza 4620z. Everythink went ok, but I can't  connect to wi fi. Network manager showes "Wireless device not ready missing firmware" what can I do?

---

### Post by chamber on 2012-05-24
Post the output of 

```
lspci
dmesg | tail -n 20
lsmod | sort
```

In seperate code tags.

---

### Post by bogdanonyshenko on 2012-05-24
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 03)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
04:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
0f:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0f:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0f:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0f:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
bogdan@bogdan-Extensa-4620:~$ BCBBBBBBBBBBBBBBBBBBBBB
```

```
bogdan@bogdan-Extensa-4620:~$ dmesg | tail -n 20
[ 4106.514320] sd 8:0:0:0: [sdb] Device not ready
[ 4106.514323] sd 8:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4106.514328] sd 8:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 4106.514335] sd 8:0:0:0: [sdb]  Add. Sense: Medium not present
[ 4106.514341] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 10 3f 00 00 01 00
[ 4106.514356] end_request: I/O error, dev sdb, sector 4159
[ 4106.515194] sd 8:0:0:0: [sdb] Device not ready
[ 4106.515198] sd 8:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4106.515203] sd 8:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 4106.515209] sd 8:0:0:0: [sdb]  Add. Sense: Medium not present
[ 4106.515215] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 10 40 00 00 01 00
[ 4106.515230] end_request: I/O error, dev sdb, sector 4160
[ 4106.516073] sd 8:0:0:0: [sdb] Device not ready
[ 4106.516079] sd 8:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4106.516087] sd 8:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 4106.516097] sd 8:0:0:0: [sdb]  Add. Sense: Medium not present
[ 4106.516107] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 10 41 00 00 06 00
[ 4106.516132] end_request: I/O error, dev sdb, sector 4161
[ 4106.522984] sdb: detected capacity change from 15938355200 to 0
[ 4108.932039] usb 2-4: USB disconnect, device number 5
bogdan@bogdan-Extensa-4620:~$ 
```


```
acer_wmi               23612  0 
arc4                   12473  2 
b43                   342643  0 
bcma                   25651  1 b43
bluetooth             158438  10 bnep,rfcomm
bnep                   17830  2 
cfg80211              178679  2 b43,mac80211
crc_ccitt              12595  1 irda
crc_itu_t              12627  1 firewire_core
drm                   197692  4 i915,drm_kms_helper
drm_kms_helper         45466  1 i915
firewire_core          56906  1 firewire_ohci
firewire_ohci          40172  0 
i2c_algo_bit           13199  1 i915
i915                  414603  3 
irda                  185517  1 nsc_ircc
joydev                 17393  0 
lp                     17455  0 
mac80211              436455  1 b43
mac_hid                13077  0 
Module                  Size  Used by
nsc_ircc               23240  0 
parport                40930  3 parport_pc,ppdev,lp
parport_pc             32114  0 
pcmcia                 39791  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
pcmcia_rsrc            18367  1 yenta_socket
ppdev                  12849  0 
psmouse                72846  0 
rfcomm                 38139  0 
sdhci                  28241  1 sdhci_pci
sdhci_pci              18324  0 
serio_raw              13027  0 
snd                    62064  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hda_codec_realtek   174055  1 
snd_hda_intel          32765  3 
snd_hwdep              13276  1 snd_hda_codec
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_rawmidi            25424  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_timer              28931  2 snd_pcm,snd_seq
soundcore              14635  1 snd
sparse_keymap          13658  1 acer_wmi
ssb                    50691  1 b43
tg3                   141369  0 
tifm_7xx1              12937  0 
tifm_core              15040  1 tifm_7xx1
uas                    17699  0 
usb_storage            39646  0 
uvcvideo               67203  0 
video                  19068  1 i915
videodev               86588  1 uvcvideo
wmi                    18744  1 acer_wmi
yenta_socket           27465  0 



```

---

### Post by ikt on 2012-05-24
Try Wi-Fi in Ubuntu 12.04 live cd, it's been a year since 11.04, a lot has changed. :)

---

### Post by bogdanonyshenko on 2012-05-24
Yes. But I am using 12.04. And having this issue

---

### Post by chamber on 2012-05-24
Get a wired connection for now and check in the additional drivers section.  If nothing is there open a terminal and run

```
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe -r b43
sudo modprobe b43
```

---

### Post by bogdanonyshenko on 2012-05-24
Thank you! The code helped!

---

### Post by chamber on 2012-05-24
Mark your thread as solved please using the Thread Tools.

---

