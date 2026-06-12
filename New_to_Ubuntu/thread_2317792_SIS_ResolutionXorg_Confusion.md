---
title: "SIS Resolution/Xorg Confusion"
date: 2016-03-19
forum: New to Ubuntu
---

### Post by abnormalsheep on 2016-03-19
Hey,

I know this bug/issue crops up a lot with the weird resolution but each post I've read is so slightly different that I end up a bit lost, so I thought I'd try posting a fresh thread. Funnily enough my resolution right now is how it should be. Only thing is, I don't know how I did it. It happened about an hour ago too, but after I restarted it was back to the 800x600 size. 

I tried some xrandr commands to add resolution modes, but got the gamma error and nothing happened so I assumed it didn't work. I did also try --gamma 0:0:0 or something. Other than that I've been trying to figure out the xorg.conf thing in root shell. Every time I enter X -configure the output concludes in an error so I assumed that didn't work either. I have Ubuntu 14.04 LTS, so there is no xorg.conf, though I did find **"usr/share/X11/xorg.conf.d" **..but I was trying to create one in **"etc/X11/xorg.conf"** (as most posts and articles recommend, and there is an X11 folder in there, just no xorg.conf file..?!) ..which didn't seem to be happening in root shell. When I tried the cd or cp commands to move/backup, I would receive error that it could not be created or the directory didn't exist. Yet, twice now when I've accessed Ubuntu from the recovery menu (where you select "Advanced options") it's booted in 1024x768... !? I did try rebooting the first time it happened and it came back with 800x600. Then I loaded root shell again and tried to configure xorg again (errors), rebooted from the same menu, and here I am with the 1024x768 again. 

These are the two pages that have explained most simply so far:
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)
[https://help.ubuntu.com/community/BinaryDriverHowto/Sis](https://help.ubuntu.com/community/BinaryDriverHowto/Sis)

I haven't looked for the driver yet because I'm trying to sort out this xorg.conf thing.
It's been quite a long evening, and I've got lost amongst the posts I could reference reading. 
The Ubuntu articles above make it sound incredibly straightforward, but creating the xorg.conf has been a muddle.

The thing that boggles me most is how the resolution changed, when all the outputs concluded in error... When I reboot it will likely revert, though to see it in 1024 has given me fresh hope :KS ...I just don't know how it happened!

Any advice or explanation would be greatly appreciated,
Much gratitude 

#-o

---

### Post by sandyd on 2016-03-19
Hi, can you post the output of the following:

Xorg Logs
```

cat /var/log/Xorg.0.log
```

Hardware Check
```

lspci
```

Modules Loaded
```

lsmod
```

Contents of xorg.conf if existing and check for additional configuration files
```

cat /etc/X11/xorg.conf
ls -l /etc/X11/xorg.conf.d
```

Check for sis drivers
```

dpkg -l | grep "xserver-xorg-video-sis"
```

---

### Post by abnormalsheep on 2016-03-19
Thank you :)


Xorg logs: no such directory

Hardware:
```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 IDE Controller (rev 01)
00:03.0 USB controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
00:1f.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)
02:00.0 Network controller: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 01)


```

Modules Loaded:
```
Module                  Size  Used by
ctr                    16384  1 
ccm                    20480  1 
snd_hda_codec_realtek    86016  1 
snd_hda_codec_generic    69632  1 snd_hda_codec_realtek
snd_hda_intel          36864  5 
snd_hda_controller     32768  1 snd_hda_intel
snd_hda_codec         143360  4 snd_hda_codec_realtek,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              20480  1 snd_hda_codec
rfcomm                 69632  0 
snd_pcm               106496  4 snd_hda_codec,snd_hda_intel,snd_hda_controller
bnep                   20480  2 
bluetooth             491520  10 bnep,rfcomm
arc4                   16384  2 
snd_seq_midi           16384  0 
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
ath9k                 147456  0 
uvcvideo               90112  0 
ath9k_common           32768  1 ath9k
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
ath9k_hw              458752  2 ath9k_common,ath9k
videobuf2_core         53248  1 uvcvideo
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
v4l2_common            16384  1 videobuf2_core
coretemp               16384  0 
videodev              159744  3 uvcvideo,v4l2_common,videobuf2_core
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
mac80211              712704  1 ath9k
snd_timer              32768  2 snd_pcm,snd_seq
media                  24576  2 uvcvideo,videodev
snd                    86016  19 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
joydev                 20480  0 
serio_raw              16384  0 
cfg80211              524288  4 ath,ath9k_common,ath9k,mac80211
soundcore              16384  2 snd,snd_hda_codec
shpchp                 40960  0 
asus_laptop            32768  0 
sparse_keymap          16384  1 asus_laptop
input_polldev          16384  1 asus_laptop
parport_pc             32768  0 
ppdev                  20480  0 
mac_hid                16384  0 
lp                     20480  0 
parport                45056  3 lp,ppdev,parport_pc
xts                    16384  1 
gf128mul               16384  1 xts
dm_crypt               24576  1 
psmouse               118784  0 
r8169                  81920  0 
mii                    16384  1 r8169
sata_sis               16384  3 
pata_acpi              16384  0 
sis_agp                16384  1 
video                  20480  0 

```

Contents of xorg.conf if existing and check for additional configuration files: None
(There is a conf.d file in /usr/share though)

SIS Drivers:
```
dpkg: error: unknown option -1

Type dpkg --help for help about installing and uninstalling packages 
[*];
Use 'apt' or 'aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked 
[*] produce a lot of output - pipe it through 'less' or 'more' !
```
I haven't looked for drivers yet, but there aren't any in "Additional Drivers"

---

### Post by cariboo on 2016-03-19
Unfortunately, there has never been a viable solution for SIS graphics in Ubuntu, or any other distributiuon. Every once in a while someone pops up saying they will create a driver for that brand, but they seem to disappear, never to be heard from again.

---

### Post by abnormalsheep on 2016-03-19
But how is my screen at 1074x768...now? It probably will be back to 800x600 tomorrow..

---

### Post by abnormalsheep on 2016-03-19
Drivers?

[http://manpages.ubuntu.com/manpages/lucid/man4/sis.4.html](http://manpages.ubuntu.com/manpages/lucid/man4/sis.4.html)

---

### Post by mörgæs on 2016-03-20
I have tried to gather some SIS advice in the thread here: 
[http://ubuntuforums.org/showthread.php?t=2215422](http://ubuntuforums.org/showthread.php?t=2215422)

For the 771/671 series cards you need some modifications to get a decent resolution.

---

