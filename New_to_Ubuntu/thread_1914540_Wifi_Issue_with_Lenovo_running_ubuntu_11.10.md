---
title: "Wifi Issue with Lenovo running ubuntu 11.10"
date: 2012-01-24
forum: New to Ubuntu
---

### Post by arorashish on 2012-01-24
Just refurbished my old laptop and installed ubuntu 11.10 the wireless doesn't run, I googled and ran certain scripts on terminal and pasting the results here, would request to help out with an step by step guide.

Thanks

Terminal Post:

lspci -nnk | grep -iA2 net
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)
	Subsystem: Broadcom Corporation Device [14e4:0466]
	Kernel modules: ssb
05:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
	Subsystem: Lenovo Device [17aa:2074]
	Kernel driver in use: 8139too
ashish@ubuntu:~$ lsmod
Module                  Size  Used by
btusb                  18160  2 
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17308  0 
fat                    55577  1 vfat
usb_storage            44173  0 
uas                    17699  0 
rfcomm                 38408  8 
bnep                   17923  2 
bluetooth             148839  23 btusb,rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
snd_hda_codec_analog    75090  1 
joydev                 17393  0 
snd_hda_intel          24262  2 
snd_hda_codec          91859  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
gspca_sn9c20x          35334  0 
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
gspca_main             27610  1 gspca_sn9c20x
wl                   2646601  0 
videodev               85626  1 gspca_main
snd_seq_midi           13132  0 
pcmcia                 39822  0 
i915                  509487  3 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
psmouse                73673  0 
serio_raw              12990  0 
snd_timer              28932  2 snd_pcm,snd_seq
r852                   17901  0 
sm_common              16737  1 r852
nand                   49706  2 r852,sm_common
nand_ids                8547  1 nand
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
nand_ecc               13070  1 nand
r592                   17808  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         32889  1 i915
drm                   192194  4 i915,drm_kms_helper
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
mtd                    35852  2 sm_common,nand
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
memstick               15857  1 r592
snd                    55902  13 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lib80211               14570  1 wl
soundcore              12600  1 snd
i2c_algo_bit           13199  1 i915
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          35854  0 
8139too                23283  0 
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
8139cp                 22636  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
ashish@ubuntu:~$

---

### Post by anewguy on 2012-01-25
Your wireless is the BCM4311.  Please click on the network manager icon - does it show any wireless networks?  Does it say anything about firmware missing?

In the mean time, hard-wire the computer in question to the router and do the following:

- open a terminal window

- type:

sudo apt-get update <press enter>

sudo apt-get upgrade <press enter>

- close out of the terminal window

- locate Additional Drivers (may say Restricted Drivers) in your menus and click on it

- let this access the net and search for a driver

- if a driver is found but not enabled, enable it

- close Additional Drivers 

- disconnect the hard-wire connection to your router

- reboot

Now check in network manager again and see if you see your networks and if you can connect.

Dave ;)

---

### Post by carl4926 on 2012-01-25
Actually, this device will work with the b43 driver
If you don't have a wired connection I can PM you the firmware to drop in place /lib/firmware/b43

---

### Post by arorashish on 2012-01-25
Brilliant it worked! thanks for the help. Cheers mate

---

