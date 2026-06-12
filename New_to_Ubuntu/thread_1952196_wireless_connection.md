---
title: "wireless connection"
date: 2012-04-03
forum: New to Ubuntu
---

### Post by scoddin on 2012-04-03
just installed latest version of Ubuntu on a Dell Latitude D830 laptop.  Wireless does not work.
lshw reveals that physical id = 0.  

nm -tool says State: disconnected.
Driver: b43
State : unavailable

looked on the forum and tried "sudo ifconfig wlan0 up" but got message that there was no such file.

I am a total beginner in Linux.  How do I turn on the wireless?  Thanks

---

### Post by wildmanne39 on 2012-04-03
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

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

### Post by scoddin on 2012-04-06
I need more help than I thought.  How do you cut and paste in the terminal.  I was using xtem.  Saw in some docs that ctrl-shift-c would work.  It seems not to.  How to cut and paste?  Sorry for being so dense.

---

### Post by wildmanne39 on 2012-04-06
Hi, just hightlight the command then right click choose copy then right click in the terminal and paste.
Thanks

---

### Post by scoddin on 2012-04-07
copy from forum post in browser works.  Right click in terminal window does not seem to work at all.  I can right click and copy to LibreOffice, but not xterm.  Neither copy nor paste seems to be working in terminal window.  Is there a better terminal program to be using than "xterm"?

---

### Post by wildmanne39 on 2012-04-07
Hi, I do not know then I have never had any problem pasting to the terminal by right clicking.

It is the terminal not xterm did you open it by hitting ctrl+alt+t?
Thanks

---

### Post by scoddin on 2012-04-07
Thanks.  I was too dumb to use the right terminal.  here is the output


[steve@steve-Latitude-D830:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux steve-Latitude-D830 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux
steve@steve-Latitude-D830:~$ lspci -nnk | grep -iA2 net
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express [14e4:1673] (rev 02)
    Subsystem: Dell Device [1028:01fe]
    Kernel driver in use: tg3
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)
    Subsystem: Dell Wireless 1490 Dual Band WLAN Mini-Card [1028:0007]
    Kernel driver in use: b43-pci-bridge
steve@steve-Latitude-D830:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 007 Device 003: ID 0b97:7772 O2 Micro, Inc. OZ776 CCID Smartcard Reader
steve@steve-Latitude-D830:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
steve@steve-Latitude-D830:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
steve@steve-Latitude-D830:~$ lsmod
Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
joydev                 17393  0 
binfmt_misc            17292  1 
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
dell_laptop            13519  0 
dcdbas                 14098  1 dell_laptop
psmouse                73673  0 
serio_raw              12990  0 
arc4                   12473  2 
snd_hda_codec_idt      60049  1 
pcmcia                 39822  0 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
b43                   318816  0 
mac80211              272785  1 b43
snd_seq_midi_event     14475  1 snd_seq_midi
cfg80211              172392  2 b43,mac80211
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
nouveau               663211  3 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd                    55902  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ttm                    65224  1 nouveau
drm_kms_helper         32889  1 nouveau
drm                   192226  5 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13199  1 nouveau
mxm_wmi                12859  1 nouveau
wmi                    18744  2 dell_wmi,mxm_wmi
soundcore              12600  1 snd
video                  18908  1 nouveau
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
tg3                   132972  0 
ssb                    50682  1 b43
steve@steve-Latitude-D830:~$ 
]

---

### Post by wildmanne39 on 2012-04-07
Hi, please do:
```
sudo apt-get install --reinstall b43-fwcutter firmware-b43-installer
```

I also recommend:
```
gksudo gedit /etc/pm/power.d/wireless
```

(this will create or edit a configuration file that will override the default powermanagement behavior) and enter the following: 
```
#!/bin/sh

/sbin/iwconfig wlan0 power off
```
above exit0, then save gedit, close and reboot.
Thanks

---

### Post by scoddin on 2012-04-07
Thanks - problem (this one ) solved.  You are very patient.

---

### Post by wildmanne39 on 2012-04-07
Hi, your welcome! glad I could help would you please go to the top of the page and mark this thread solved by clicking on thread tools. 
Thank you

---

