---
title: "Can't find Dell 1390 wlan minicard after Lubuntu 13.04 install"
date: 2013-07-18
forum: New to Ubuntu
---

### Post by Show Me on 2013-07-18
After many successful installs of various versions of Ubuntu on numerous PC's (laptops and desktops) I can't seem to get the Dell 1390 wlan minicard of an Inspiron E1505 to work. I have been searching various forums for the solution, but need more help.  I may need to be walked through this as my terminal skills are at not yet well developed.

Thanks in advance for assistance.

---

### Post by Hadaka on 2013-07-18
Hi, please open a terminal ctrl/alt/t
and enter.
```
rfkill list all
lspci -nnk | grep -iA3 net
lsmod
```
post the results of each command.
thanks

---

### Post by Show Me on 2013-07-18
Here it is:

-MM061:~$ rfkill list all


-MM061:~$ lspci -nnk | grep -iA3 net
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Inspiron 6400 [1028:01af]
    Kernel driver in use: b44
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
--
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Kernel driver in use: b43-pci-bridge



-MM061:~$ lsmod
Module                  Size  Used by
bnep                   17669  2 
rfcomm                 37420  0 
bluetooth             202069  10 bnep,rfcomm
binfmt_misc            17260  1 
snd_hda_codec_idt      63896  1 
snd_hda_intel          38307  1 
snd_hda_codec         117580  2 snd_hda_codec_idt,snd_hda_intel
r592                   17707  0 
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80890  2 snd_hda_codec,snd_hda_intel
dell_wmi               12601  0 
memstick               15842  1 r592
coretemp               13131  0 
sparse_keymap          13658  1 dell_wmi
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
b43                   351961  0 
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
radeon                875070  2 
r852                   17873  0 
bcma                   39645  1 b43
joydev                 17097  0 
sm_common              16772  1 r852
gpio_ich               13236  0 
snd_rawmidi            25114  1 snd_seq_midi
ttm                    71289  1 radeon
nand                   49670  2 r852,sm_common
mac80211              526519  1 b43
nand_ecc               13105  1 nand
nand_bch               13003  1 nand
bch                    17226  1 nand_bch
nand_ids                8547  1 nand
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
drm_kms_helper         47545  1 radeon
mtd                    38922  2 nand,sm_common
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
mac_hid                13037  0 
cfg80211              436177  2 b43,mac80211
video                  18894  0 
snd_timer              24411  2 snd_pcm,snd_seq
drm                   228489  4 ttm,drm_kms_helper,radeon
wmi                    18590  1 dell_wmi
ssb_hcd                12749  0 
lpc_ich                16925  0 
dell_laptop            17161  0 
snd                    56485  11 snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
dcdbas                 14021  1 dell_laptop
psmouse                81038  0 
microcode              18286  0 
serio_raw              13031  0 
i2c_algo_bit           13197  1 radeon
soundcore              12600  1 snd
lp                     13299  0 
parport                40753  1 lp
hid_generic            12484  0 
b44                    31137  0 
firewire_ohci          35292  0 
sdhci_pci              18158  0 
firewire_core          61718  1 firewire_ohci
sdhci                  31824  1 sdhci_pci
crc_itu_t              12627  1 firewire_core
usbhid                 41805  0 
hid                    82666  2 hid_generic,usbhid
ssb                    50834  3 b43,b44,ssb_hcd
-MM061:~$

---

### Post by Hadaka on 2013-07-18
Hi,from a wired connection please do..
```
sudo apt-get install linux-headers-generic
sudo apt-get install linux-firmware-nonfree
sudo modprobe -rf b43
sudo modprobe b43
```
thanks

---

### Post by Show Me on 2013-07-19
Hadaka:  THANK YOU VERY MUCH!  Works like a charm.  I am setting this "older machine" up for a non-computer person and it will pretty much need to run on it's own.

How do you remember all of this stuff?

And how do I change the status to "Solved"?

Thanks again,

Carl

---

### Post by Hadaka on 2013-07-19
Great !!  glad that worked for you.
I dont remember..i have cheat sheets and a little first hand experience..

How to->[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
be sure to edit the FIRST post of your thread to mark solved.
thanks.

---

### Post by Elfy on 2014-07-14
@plutokrat - your post has been moved to it's own thread [http://ubuntuforums.org/showthread.php?t=2234415](http://ubuntuforums.org/showthread.php?t=2234415)

---

