---
title: "How to get Wireless working..."
date: 2012-02-25
forum: New to Ubuntu
---

### Post by paulskycaptain on 2012-02-25
Hello.

I just installed Ubuntu on my Dell Inspiron 6400, replacing Windows Vista.
Everything's looking nice so far, however I am at a loss as to how I can get my wireless connection working.
In Additional Drivers it says the Broadcom STA wireless driver is activated and currently in use, however I cannot figure out how to actually hook up to the wireless network.
This seems like a simple issue, but I can't figure it out for whatever reason.
Right now I'm chalking it up to my unfamiliarity of Ubuntu :P
any help is greatly appreciated!
thanks

paul

---

### Post by enjoijesus94 on 2012-02-25
> **paulskycaptain said:**
> Hello.

I just installed Ubuntu on my Dell Inspiron 6400, replacing Windows Vista.
Everything's looking nice so far, however I am at a loss as to how I can get my wireless connection working.
In Additional Drivers it says the Broadcom STA wireless driver is activated and currently in use, however I cannot figure out how to actually hook up to the wireless network.
This seems like a simple issue, but I can't figure it out for whatever reason.
Right now I'm chalking it up to my unfamiliarity of Ubuntu :P
any help is greatly appreciated!
thanks

paul
Hello welcome to ubuntu linux 

can you give the output in terminal

go to
Applications > accessories > terminal
and paste this inside it and press enter
> lspci

---

### Post by fcomstoc on 2012-02-25
if you click on the network icon in the top taskbar it should list the available networks if your wireless card is on and working. You can then select one and enter the password.

---

### Post by enjoijesus94 on 2012-02-25
> **fcomstoc said:**
> if you click on the network icon in the top taskbar it should list the available networks if your wireless card is on and working. You can then select one and enter the password.

i think hes having problems installing it 
maybe to do something with the wireless card itself.

---

### Post by UltimateCat on 2012-02-25
Once you know which NIC Network Interface Card you have you'll know what you are dealing with.

Almost all of the Realtek RTL's need drivers....at least mine did and until I installed the driver I could not get my wireless connection to work in Ubuntu 10.04

[http://www.official-drivers.com](http://www.official-drivers.com)

If your card isn't a Realtek try Googling what your " lspci" result gives you

Best regards

---

### Post by westie457 on 2012-02-25
Hi, welcome to UF.

As it has already been suggested that you open a terminal and run a command, just going to ask that you change the command to ```
cat /etc/lsb-release; uname -a

lspci -nnk | grep -iA2 net

iwconfig

lshw -C network

lsmod

rfkill list all
```

Highlight all of the output and in a new reply paste between [ code] [/code] brackets by clicking on the # at the top of the message pane.

Thank you.

---

### Post by paulskycaptain on 2012-02-25
Thanks for the help everyone;
here's the output:

```
paul@skycaptain:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux skycaptain 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:50:54 UTC 2012 i686 i686 i386 GNU/Linux
paul@skycaptain:~$ 
paul@skycaptain:~$ lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Inspiron 6400 [1028:01af]
    Kernel driver in use: b44
--
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Kernel driver in use: b43-pci-bridge
paul@skycaptain:~$ 
paul@skycaptain:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

paul@skycaptain:~$ 
paul@skycaptain:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:efcfc000-efcfffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:74:a3:10
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.101 latency=64 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:17 memory:ef9fe000-ef9fffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
paul@skycaptain:~$ 
paul@skycaptain:~$ lsmod
Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
joydev                 17393  0 
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
snd_hda_codec_idt      60049  1 
snd_hda_intel          24262  2 
snd_hda_codec          91859  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
dell_laptop            13519  0 
dcdbas                 14098  1 dell_laptop
b44                    31443  0 
binfmt_misc            17292  1 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
ssb                    50682  1 b44
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73673  0 
serio_raw              12990  0 
r592                   17808  0 
wl                   2646601  0 
r852                   17901  0 
sm_common              16737  1 r852
nand                   49706  2 r852,sm_common
nand_ids                8547  1 nand
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
nand_ecc               13070  1 nand
mtd                    35852  2 sm_common,nand
memstick               15857  1 r592
radeon                929507  3 
snd                    55902  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lib80211               14570  1 wl
soundcore              12600  1 snd
wmi                    18744  1 dell_wmi
video                  18908  0 
ttm                    65224  1 radeon
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
drm_kms_helper         32889  1 radeon
drm                   192194  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13199  1 radeon
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          35854  0 
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
paul@skycaptain:~$ 
paul@skycaptain:~$ rfkill list all
```

---

### Post by paulskycaptain on 2012-02-25
Found a fix!!
works like a dream:

 $ sudo apt-get update

then:

$ sudo apt-get install firmware-b43-installer

then:

$ sudo apt-get remove bcmwl-kernel-source

then:

$ sudo reboot


found here: [http://nfolamp.wordpress.com/2011/10/15/ubuntu-11-10-getting-wireless-bcm4311-working/](http://nfolamp.wordpress.com/2011/10/15/ubuntu-11-10-getting-wireless-bcm4311-working/)

---

### Post by westie457 on 2012-02-26
Glad you got it working. Enjoy your Ubuntu experirnce. Could you mark this as solved please using 'Thread Tools' at the top of the page.

---

