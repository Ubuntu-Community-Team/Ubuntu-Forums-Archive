---
title: "Wireless Card Problems"
date: 2013-11-23
forum: New to Ubuntu
---

### Post by vertigopher on 2013-11-23
Hi everyone,

I am attempting to set up an older computer with Lubuntu 13.10, and put in an extra wireless card I had lying around, a Rosewill RNX-G300LX, since it will be used in an area of the house where there is no hardline ethernet connection.  However, I cannot get the wireless card to work.  It does not display any available wireless networks.  I have a USB wireless stick that I use on another computer, and that works fine in it, but I can't get the PCI card to work.  

I've looked around for a while now for a solution to this problem, but haven't found anything that has worked.  Right now, I'm on a fresh install of Lubuntu (so I know I haven't messed something up in previous attempts).  From what I've seen, it appears the RT2561/RT61 is kind of a pain in the neck, but I'm hoping that someone has an idea to help me out.  I've used Ubuntu off an on for a number of years now, but am not very experienced in the technical workings of it.  Any help you might be able to provide me would be greatly appreciated!  Thanks! :)

Here are the results I'm getting from lspci and lsmod (without the USB wireless connected):

**_lspci_**
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
05:09.0 Network controller: Ralink corp. RT2561/RT61 802.11g PCI
40:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)

_**lsmod**_
Module                  Size  Used by
zram                   18070  2 
vesafb                 13500  0 
bnep                   18893  2 
rfcomm                 53664  0 
bluetooth             323534  10 bnep,rfcomm
gpio_ich               13229  0 
ppdev                  17391  0 
snd_intel8x0           33069  1 
snd_ac97_codec        105668  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                89488  2 snd_ac97_codec,snd_intel8x0
snd_page_alloc         14230  2 snd_intel8x0,snd_pcm
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25094  1 snd_seq_midi
arc4                   12536  2 
rt61pci                27249  0 
rt2x00pci              13111  1 rt61pci
rt2x00mmio             13395  1 rt61pci
rt2x00lib              48854  3 rt61pci,rt2x00pci,rt2x00mmio
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
mac80211              513247  2 rt2x00lib,rt2x00pci
microcode              18830  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24447  2 snd_pcm,snd_seq
cfg80211              401436  2 mac80211,rt2x00lib
psmouse                90642  0 
serio_raw              13189  0 
snd                    60790  10 snd_ac97_codec,snd_intel8x0,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_seq_device,snd_seq_midi
lpc_ich                16864  0 
eeprom_93cx6           13168  1 rt61pci
i915                  589697  3 
crc_itu_t              12627  1 rt61pci
soundcore              12600  1 snd
video                  18777  1 i915
drm_kms_helper         46867  1 i915
drm                   242354  4 i915,drm_kms_helper
i2c_algo_bit           13197  1 i915
wmi                    18590  0 
parport_pc             31981  1 
mac_hid                13037  0 
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
hid_generic            12492  0 
usbhid                 47361  0 
hid                    87192  2 hid_generic,usbhid
tg3                   152066  0 
ptp                    18156  1 tg3
pps_core               18546  1 ptp
floppy                 55378  0

---

### Post by dubritton on 2013-11-23
This is 'just an idea'. Have you tried looking in Settings>Software and Updates>Additional Drivers?

If that does not help, I found some older forum posts which may be of some service to you:
[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61)
[http://askubuntu.com/questions/84635/cant-enable-ralink-rt2561-rt61-wireless-card](http://askubuntu.com/questions/84635/cant-enable-ralink-rt2561-rt61-wireless-card)
[http://forum.slitaz.org/topic/wireless-ralink-rt2561-pci-not-working](http://forum.slitaz.org/topic/wireless-ralink-rt2561-pci-not-working)

---

### Post by vertigopher on 2013-11-23
> **dubritton said:**
> This is 'just an idea'. Have you tried looking in Settings>Software and Updates>Additional Drivers? 

Yes, I should have mentioned this was the first place I had checked (one of the few things I remembered how to do in Ubuntu :)).  Nothing appears here, unfortunately.

> **dubritton said:**
> 
If that does not help, I found some older forum posts which may be of some service to you:
[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61)
[http://askubuntu.com/questions/84635/cant-enable-ralink-rt2561-rt61-wireless-card](http://askubuntu.com/questions/84635/cant-enable-ralink-rt2561-rt61-wireless-card)
[http://forum.slitaz.org/topic/wireless-ralink-rt2561-pci-not-working](http://forum.slitaz.org/topic/wireless-ralink-rt2561-pci-not-working)

I had run across some of these in my search.  Blacklisting the drivers mentioned in the second link did not work for me. 

The box the wireless card had a Driver CD in it, and it has a folder labeled Linux in it with a file named Linux.tgz.  I imagine this is the driver, and normally would be of some help... but I am unfortunately clueless how to use this file.

---

### Post by dubritton on 2013-11-23
I would take a look at that first link then.

---

