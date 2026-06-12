---
title: "Intermittent internet connection"
date: 2012-04-26
forum: New to Ubuntu
---

### Post by Zvanochek on 2012-04-26
Dear Forum

A curious problem I haven't been able to figure out the solution to, and previous threads i've read here haven't been had much joy either.

I'm running Ubuntu 11.10 and have been for a few months now. All of a sudden, my internet connection has gone intermittent. Ubuntu still says it is connected to my network, but I am unable to access the web for any great period of time (just enough to occasionally get e-mails through thunderbird).

However, both my XP dual boot and our vista laptop are having no problems.

What I suspect has happened is that we lost our connection from the ISP for a little while without our noticing, but it upset ubuntu. 

Can anyone give any idea's as to what settings might have been effected and how I go about putting them right?

---

### Post by wildmanne39 on 2012-04-26
Hi, please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Zvanochek on 2012-04-27
As requested :)

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux Study 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 17:34:21 UTC 2012 i686 athlon i386 GNU/Linux
andrew@Study:~$ lspci -nnk | grep -iA2 net
00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP67 Ethernet [10de:054c] (rev a2)
	Subsystem: ASUSTeK Computer Inc. M2N68-AM Motherbord [1043:8308]
	Kernel driver in use: forcedeth
--
01:07.0 Network controller [0280]: Ralink corp. RT2760 Wireless 802.11n 1T/2R Cardbus [1814:0701]
	Subsystem: Ralink corp. Device [1814:2760]
	Kernel driver in use: rt2800pci
andrew@Study:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 152d:2339 JMicron Technology Corp. / JMicron USA Technology Corp. 
Bus 004 Device 002: ID 04d9:1603 Holtek Semiconductor, Inc. 
Bus 007 Device 002: ID 04f3:02f4 Elan Microelectronics Corp. 2.4G Cordless Mouse
andrew@Study:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Esia"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 1C:BD:B9:2E:78:DA   
          Bit Rate=81 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:42  Invalid misc:41   Missed beacon:0

andrew@Study:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
andrew@Study:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
vesafb                 13489  1 
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
nvidia              10390874  40 
snd_hda_codec_realtek   254163  1 
usbhid                 41905  0 
binfmt_misc            17292  1 
ppdev                  12849  0 
hid                    77367  1 usbhid
arc4                   12473  2 
rt2800pci              18340  0 
rt2800lib              48909  1 rt2800pci
snd_hda_intel          24262  2 
snd_hda_codec          91859  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
crc_ccitt              12595  1 rt2800lib
rt2x00pci              14202  1 rt2800pci
rt2x00lib              48146  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              393421  3 rt2800lib,rt2x00pci,rt2x00lib
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
psmouse                73673  0 
serio_raw              12990  0 
k8temp                 12905  0 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
cfg80211              172427  2 rt2x00lib,mac80211
asus_atk0110           17742  0 
parport_pc             32114  1 
eeprom_93cx6           12653  1 rt2800pci
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
wmi                    18744  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_nforce2            12906  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usb_storage            44173  1 
uas                    17699  0 
forcedeth              58103  0 
pata_amd               13753  1 
ahci                   21634  2 
libahci                25727  1 ahci

```

---

### Post by wildmanne39 on 2012-04-27
Hi, please try this:
```
gksudo gedit /etc/modprobe.d/rt2800pci.conf
```
```
options rt2800pci nohwcrypt=1
```
Proofread carefully, save and close gedit then reboot.
Thanks

---

