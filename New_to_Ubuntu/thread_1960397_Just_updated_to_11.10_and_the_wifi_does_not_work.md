---
title: "Just updated to 11.10 and the wifi does not work"
date: 2012-04-17
forum: New to Ubuntu
---

### Post by blake7 on 2012-04-17
I have a an acer revo and it simple has no wifi


Help

---

### Post by raja.genupula on 2012-04-17
is it recognizing it ? hardware drivers are installed ?

EDIT : you can get more help from this 
[https://help.ubuntu.com/community/CategoryWireless](https://help.ubuntu.com/community/CategoryWireless)

---

### Post by blake7 on 2012-04-17
is it recognizing it ? hardware drivers are installed ?

The wifi simple has no life. As if it's turned off and what  do u mean hardware drivers installed. Should that not happen automatically 

Cheers

---

### Post by daslinkard on 2012-04-17
I found this [site]("http://azuliadesigns.com/installing-ubuntu-acer-revo/") talking about the Revo & having to update the drivers.  It seems the wireless configuration is in a file located in  /etc/network/interfaces. This needs to be edited to add adaptor  information for the wireless lan.

---

### Post by blake7 on 2012-04-17
auto wlan0
iface wlan0 inet dhcp
wireless-essid   WIRELESS_SSID
wireless-key     s:WIRELESS_KEY
wireless-channel 11
wireless-mode    managed


How do I exit out of this mode or save it

Thank u

---

### Post by blake7 on 2012-04-17
There is a symbol followed by x for exit but I don't know what the symbol means

---

### Post by blake7 on 2012-04-17
etc/network/interfaces but I am trying to change and save this file

---

### Post by daslinkard on 2012-04-17
I am assuming you are talking about "^"...in that case you will use CTRL plus whatever letter you need to fulfill saving, to quit, etc.

---

### Post by daslinkard on 2012-04-17
What are your options given for making changes?

---

### Post by blake7 on 2012-04-17
I found this site talking about the Revo & having to update the drivers. It seems the wireless configuration is in a file located in /etc/network/interfaces. This needs to be edited to add adaptor information for the wireless lan.

Just followed the above

It failed

Ifdown failed to open statefile /var/run/network/ifstate. Permission denied
Ifup failed to open statefile /var/run/network/ifstate. Permission denied


Thank you

---

### Post by wildmanne39 on 2012-04-17
Hi, that file should not need to be edited using newer versions of ubuntu.

Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by blake7 on 2012-04-27
How can I copy and passt when Internet does not work?

---

### Post by blake7 on 2012-04-27
> **blake7 said:**
> auto wlan0
iface wlan0 inet dhcp
wireless-essid   WIRELESS_SSID
wireless-key     s:WIRELESS_KEY
wireless-channel 11
wireless-mode    managed


How do I exit out of this mode or save it

Thank u

I did the above and I now my computer can see and connect to my wi if.   But there is no speeded is its slower then 56k in the old days. Much slower can any one help that you very much

---

### Post by wildmanne39 on 2012-04-27
Hi, you can copy and paste the information using an flash drive.

As for as how do you get out of that mode what is it in the terminal nano, gedit? how did you get in that mode as you call it?
Thanks

---

### Post by blake7 on 2012-05-02
ok great found aWAy to copy and past thank you
i have updated my sysytem to 10.04 in the hope it would sovel the praoblem it has not 
so i have done what you asked and the results are as follows i hope that you can find what the problem is and find a solution 

thanks again

pea@pea:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux pea 3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:52 UTC 2012 i686 i686 i386 GNU/Linux
pea@pea:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]
	Subsystem: Lite-On Communications Inc Device [11ad:6622]
	Kernel driver in use: rt2800pci
--
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Subsystem: Acer Incorporated [ALI] Device [1025:8000]
	Kernel driver in use: r8169
pea@pea:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
pea@pea:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

pea@pea:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
pea@pea:~$ lsmod
Module                  Size  Used by
dm_crypt               22528  0 
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
nvidia              10958194  30 
snd_hda_codec_hdmi     31775  4 
joydev                 17393  0 
psmouse                87213  0 
snd_hda_codec_realtek   174055  1 
serio_raw              13027  0 
arc4                   12473  2 
rt2800pci              18340  0 
rt2800lib              53264  1 rt2800pci
crc_ccitt              12595  1 rt2800lib
rt2x00pci              14202  1 rt2800pci
rt2x00lib              48858  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              436455  3 rt2800lib,rt2x00pci,rt2x00lib
snd_hda_intel          32765  5 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
cfg80211              178679  2 rt2x00lib,mac80211
eeprom_93cx6           12653  1 rt2800pci
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
wmi                    18744  0 
snd                    62064  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
vesafb                 13516  1 
hid_logitech           22024  0 
ff_memless             12945  1 hid_logitech
usbhid                 41906  1 hid_logitech
hid                    77367  2 hid_logitech,usbhid
r8169                  56321  0 
pea@pea:~$

---

### Post by blake7 on 2012-05-03
can any one help

---

### Post by wildmanne39 on 2012-05-03
Hi, the easiest thing would be to upgrade to 12.04 the driver comes with 12.04 and not in 10.04.
Thanks

---

