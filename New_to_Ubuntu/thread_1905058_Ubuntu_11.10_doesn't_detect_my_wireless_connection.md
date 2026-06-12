---
title: "Ubuntu 11.10 doesn't detect my wireless connection"
date: 2012-01-05
forum: New to Ubuntu
---

### Post by leunamiam on 2012-01-05
I recently installed ubuntu 11.10 on my dell inspiron 1520 laptop and i doesnt want to connect to my wireless network which worked before my transition over to ubuntu. Any help? please. I've seen others with this problem but i assume this differs from machine to machine.

---

### Post by wildmanne39 on 2012-01-05
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
Thanks

---

### Post by leunamiam on 2012-01-05
woah, quick response! here are the results:
1. david@david-Inspiron-1520:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux david-Inspiron-1520 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 i686 i386 GNU/Linux

2. david@david-Inspiron-1520:~$ lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Device [1028:01f1]
    Kernel driver in use: b44
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Kernel driver in use: b43-pci-bridge

3. david@david-Inspiron-1520:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

4. david@david-Inspiron-1520:~$ rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes

5. david@david-Inspiron-1520:~$ lsmod
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_idt      60049  1 
binfmt_misc            17292  1 
joydev                 17393  0 
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
dell_laptop            13519  0 
dcdbas                 14098  1 dell_laptop
b44                    31443  0 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
ssb                    50682  1 b44
wl                   2646601  0 
snd_seq_midi_event     14475  1 snd_seq_midi
r852                   17901  0 
sm_common              16737  1 r852
nand                   49706  2 r852,sm_common
r592                   17808  0 
nand_ids                8547  1 nand
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
nand_ecc               13070  1 nand
mtd                    35852  2 sm_common,nand
memstick               15857  1 r592
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73673  0 
serio_raw              12990  0 
snd                    55902  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lib80211               14570  1 wl
i915                  505159  3 
wmi                    18744  1 dell_wmi
drm_kms_helper         32889  1 i915
drm                   192194  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
crc_itu_t              12627  1 firewire_core
ahci                   21634  2 
libahci                25727  1 ahci

---

### Post by wildmanne39 on 2012-01-05
Hi, please do this:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
```
echo "blacklist dell-laptop" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

Make sure your wireless switch on the laptop is on.
then reboot.
Thanks

---

### Post by drpjkurian on 2012-01-05
Implement this thread [http://ubuntuforums.org/showthread.php?t=1901157](http://ubuntuforums.org/showthread.php?t=1901157)

---

### Post by BertN45 on 2012-01-05
I have the 1521 laptop and had the same problem. You have the infamous Broadcom wifi. See [http://ubuntuforums.org/showthread.php?p=10802562#post10802562](http://ubuntuforums.org/showthread.php?p=10802562#post10802562) 

In short:

- de-activate the (recommended) Broadcom STA driver using "Additional Drivers"
- Go to the synaptic package manager and type bcm and unstall everything related to the wifi drivers (just to be sure).
- type b43 and install the firmware-b43-installer and b43-fwcutter. (also possible from the software center)

That was enough to get my BCM4311 working.

If you do not have a wired internet connection, take the CD you used for installation and look in the following folder:
/pool/restricted/b/bcmwl/

Do not forget to tick the box of that cd in the software sources, in system settings.

---

### Post by leunamiam on 2012-01-05
Magic! works great now! thank you soo much.

> **wildmanne39 said:**
> Hi, please do this:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
``````
sudo apt-get install b43-fwcutter firmware-b43-installer
``````
echo "blacklist dell-laptop" | sudo tee -a /etc/modprobe.d/blacklist.conf
```Make sure your wireless switch on the laptop is on.
then reboot.
Thanks

---

### Post by wildmanne39 on 2012-01-05
Hi, your welcome! would you please go to the top of the page and mark this thread solved by clicking on thread tools. 
Thank you

---

### Post by alionilla on 2012-01-08
Worked for me and my inspiron 1520 too!! Thank you very much!! :D

---

### Post by wildmanne39 on 2012-01-08
Hi, your welcome!

---

### Post by MARP1961 on 2012-01-09
Does anyone know the story with the STA driver? This Broadcom card is supposed to work with it but it would appear that only the B43 (not listed in Additional Drivers) is working for users.

When I tried out Fedora 15 last year, my Dell's  Broadcom 4311 worked directly from install. How do Fedora manage this? 

These wireless cards are common in Dell and Acer laptops.

---

### Post by TBABill on 2012-01-09
I don't think it's the driver itself, but I could be wrong. I can't verify because I have a BCM4312, not a 4311, but I'd be interested to know if anyone with a bcm4311 installed the wl driver, then went and blacklisted other active modules that may be conflicting (think it's bcma and brcm80211 that are also activated in the install routine with the bcm4311 on 11.10 but cannot recall for certain). It's possible that the module installs properly and all that needs to be done is a blacklisting of other modules that conflict, much like the Ralink problem with the RT2860 and others.

---

### Post by wayneh901 on 2012-01-09
I had the same issue - finally found a solution posted
1) go to Ubuntu Software 
2) Locate firmware-b43
3) install firmware-b43

---

### Post by wayneh901 on 2012-01-09
x

---

### Post by wildmanne39 on 2012-01-09
Hi, we can make it work here is a link to the directions, it is not hard but the b43 usually works better and is updated more often so in networking we use it instead.
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
> In Ubuntu 11.04, if the driver fails to load, you may need to reinstall the bcmwl-kernel-source package.

This an issue with 11.04 and 11.10.
I hope this helps.
Thanks

---

### Post by 2muchcoffeeman on 2012-01-26
Just chiming in quickly to vouch for the method prescribed by wildmanne39. I was having the same problem with my Broadcomm wireless driver: Ubuntu was not detecting my local wifi network, or any of the other wireless signals that wash over the neighborhood.

After opening a terminal window and executing the three lines of code as instructed by wildmanne39, and then rebooting, the network indicator in the upper-right portion of the screen listed not only my own wifi network but also all others in range -- very familiar to Windows users who rely upon the "find wireless networks in range" utility that continually hums in the lower-right portion of the screen.

Now I am free of the cable. Thank you, wildmanne39.

---

### Post by wildmanne39 on 2012-02-03
Hi 2muchcoffeeman, your welcome!

---

