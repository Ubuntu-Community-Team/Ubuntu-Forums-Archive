---
title: "Wireless?"
date: 2012-01-14
forum: New to Ubuntu
---

### Post by matt0218 on 2012-01-14
So I just installed Linux on my laptop and I it says the firmware for my wireless is missing. I already tried the additional drivers thing and I keep getting this error that says "SystemError: installArchives() failed". I don't really know what to do because I am a complete noob. What can I do? I really would like to surf without the cord.

---

### Post by wildmanne39 on 2012-01-14
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

### Post by matt0218 on 2012-01-14
```
user@user:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
Linux user 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686 i686 i386 GNU/Linux
user@user:~$ lspci -nnk | grep -iA2 net
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 12)
    Subsystem: Dell Device [1028:022f]
    Kernel driver in use: sky2
--
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Dell Wireless 1395 WLAN Mini-Card [1028:000b]
    Kernel modules: ssb
user@user:~$ iwconfig
lo        no wireless extensions.

eth3      no wireless extensions.

user@user:~$ rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
user@user:~$ lsmod
Module                  Size  Used by
usbhid                 36882  0 
hid                    67742  1 usbhid
btrfs                 489451  0 
zlib_deflate           19266  1 btrfs
crc32c                  2531  1 
libcrc32c                887  1 btrfs
ufs                    73069  0 
qnx4                    6877  0 
hfsplus                71344  0 
hfs                    41250  0 
minix                  25303  0 
ntfs                   95015  0 
msdos                   6436  0 
jfs                   171034  0 
xfs                   693150  0 
exportfs                3449  1 xfs
reiserfs              225942  0 
nls_iso8859_1           3261  0 
nls_cp437               4931  0 
vfat                    9201  0 
fat                    48240  2 msdos,vfat
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
snd_hda_codec_idt      54887  1 
snd_hda_codec_intelhdmi     9812  1 
snd_hda_intel          22107  2 
snd_hda_codec          87552  3 snd_hda_codec_idt,snd_hda_codec_intelhdmi,snd_hda_intel
i915                  290938  4 
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
arc4                    1165  0 
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
drm_kms_helper         30200  1 i915
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
joydev                  8735  0 
drm                   168054  5 i915,drm_kms_helper
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
dell_laptop             5730  0 
mac80211              231541  0 
cfg80211              144470  1 mac80211
snd                    49006  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
r852                    9536  0 
sm_common               3285  1 r852
nand                   34905  2 r852,sm_common
nand_ids                2903  1 nand
uvcvideo               55847  0 
videodev               43098  1 uvcvideo
intel_agp              26360  2 i915
i2c_algo_bit            5168  1 i915
lp                      7342  0 
nand_ecc                3938  1 nand
dcdbas                  5402  1 dell_laptop
soundcore                880  1 snd
v4l1_compat            13359  2 uvcvideo,videodev
psmouse                59033  0 
video                  18712  1 i915
mtd                    18877  2 sm_common,nand
agpgart                32011  2 drm,intel_agp
output                  1883  1 video
dell_wmi                2852  0 
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
serio_raw               4022  0 
parport                31492  3 parport_pc,ppdev,lp
usb_storage            40172  0 
firewire_ohci          21106  0 
sdhci_pci               6339  0 
firewire_core          46643  1 firewire_ohci
sdhci                  15890  1 sdhci_pci
led_class               2633  1 sdhci
ahci                   19013  0 
crc_itu_t               1383  1 firewire_core
libahci                21667  3 ahci
sky2                   45127  0 
```

---

### Post by matt0218 on 2012-01-14
Hey, it turns out I needed to restart my computer to finish installing some updates. My wireless now works. Thanks for the help though. :D




lol i really am a n00b

---

### Post by wildmanne39 on 2012-01-15
Hi your welcome! I am glad it is working.

---

