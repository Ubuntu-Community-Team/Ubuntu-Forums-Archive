---
title: "How to make wireless card work?"
date: 2012-11-27
forum: New to Ubuntu
---

### Post by littlewenwen on 2012-11-27
Hi,

I just installed Ubintu 12.10 on my Dell 6400 laptop; however, I couldn't make the wireless card work. Can anyone help me?

(I am learning Linux now; and I prefer to use command line to solve the above problem).

---

### Post by BertN45 on 2012-11-27
If you copy and paste the output of the next commands we could see what wifi controller your PC has and which driver has been loaded or not.
lspci
lsmod

---

### Post by littlewenwen on 2012-11-28
I am terribly sorry for the late response (I had to go to a meeting yesterday and cannot reply your message).

I have run lspci; however, how can I copy the output?

---

### Post by audiomick on 2012-11-28
> **littlewenwen said:**
> however, how can I copy the output?

In the terminal you can
highlight the text by dragging the mouse (click and hold) across it
and then

choose "copy" out of the "edit" menu

or
right click on the highlighted text and choose "copy" out of the context menu

or
do ctrl+shift+c

When you paste that here, use the # button at the top of the post window to put code tags around it. That puts it in a nice box with a scroll bar if it is a lot of text, and makes sure that it is presented as pure text without interpreting any character combinations as smileys or what have you.

---

### Post by littlewenwen on 2012-11-28
Thank you; here is output of lspci

> 00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 4 (rev 01)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 01)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

---

### Post by haqking on 2012-11-28
You have a Broadcom 4311 see this thread for getting it to work in Ubuntu 12.10
[http://ubuntuforums.org/showthread.php?t=2072887](http://ubuntuforums.org/showthread.php?t=2072887)

Hope this helps 

Peace

---

### Post by littlewenwen on 2012-11-28
And here is output of lsmod

```
Module                  Size  Used by
parport_pc             31968  0 
rfcomm                 37276  0 
ppdev                  12817  0 
bnep                   17707  2 
bluetooth             183228  10 rfcomm,bnep
joydev                 17161  0 
snd_hda_codec_idt      59761  1 
gpio_ich               13159  0 
coretemp               13168  0 
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
dell_laptop            17161  0 
dcdbas                 14054  1 dell_laptop
microcode              18209  0 
snd_hda_intel          32515  3 
b43                   347284  0 
snd_hda_codec         111547  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80163  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25382  1 snd_seq_midi
r852                   17905  0 
sm_common              16737  1 r852
nand                   49496  2 r852,sm_common
nand_ids                8547  1 nand
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
mac_hid                13037  0 
psmouse                84843  0 
serio_raw              13031  0 
snd_timer              24411  2 snd_pcm,snd_seq
r592                   17707  0 
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              461161  1 b43
mtd                    38602  2 sm_common,nand
nand_bch               13003  1 nand
bch                    17199  1 nand_bch
nand_ecc               13070  1 nand
memstick               15842  1 r592
snd                    61991  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    18590  1 dell_wmi
lpc_ich                16925  0 
ssb_hcd                12749  0 
soundcore              14599  1 snd
cfg80211              175375  2 b43,mac80211
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
i915                  457161  3 
bcma                   34483  1 b43
drm_kms_helper         45271  1 i915
drm                   230463  4 i915,drm_kms_helper
i2c_algo_bit           13197  1 i915
video                  18847  1 i915
lp                     13299  0 
parport                40753  3 parport_pc,ppdev,lp
b44                    31326  0 
firewire_ohci          35521  0 
firewire_core          57492  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci_pci              18155  0 
sdhci                  27830  1 sdhci_pci
ssb                    50087  3 b43,ssb_hcd,b44
```

---

### Post by audiomick on 2012-11-28
The last entry is your wireless card
> Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01) 

do the lsmod and put the output of that up too, so that people can see it. I don't know what you are looking for there, though. I just looked at mine, and didn't understand much of it. ;)

Edit: never mind. Beaten to it again...

---

### Post by littlewenwen on 2012-11-28
Thank you all very much.

I followed Haqking's suggestion and ran the following codes:

```
sudo apt-get remove bcmwl-kernel-source
sudo apt-get install firmware-b43-installer b43-fwcutter 			 		
```

After that, I rebooted the computer, and WOW! The wireless is working!

Again, thank you  all very much for helping me!

---

### Post by haqking on 2012-11-28
> **littlewenwen said:**
> Thank you all very much.

I followed Haqking's suggestion and ran the following codes:

```
sudo apt-get remove bcmwl-kernel-source
sudo apt-get install firmware-b43-installer b43-fwcutter                      
```After that, I rebooted the computer, and WOW! The wireless is working!

Again, thank you  all very much for helping me!

You are welcome.

Remember to mark thread as solved using thread tools.

Peace

---

### Post by littlewenwen on 2012-11-28
Thank you, haqking; I have marked the thread as solved.

---

