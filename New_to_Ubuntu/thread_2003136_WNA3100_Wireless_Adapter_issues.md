---
title: "WNA3100 Wireless Adapter issues"
date: 2012-06-13
forum: New to Ubuntu
---

### Post by Relinies on 2012-06-13
Title is no longer relevant, if somebody could change that would be nice. 
Now trying to get the WUA-2340 D-link Wireless adapter to work with Ubuntu, if anyone can help do so please.
EDIT: I have the WUA-2340 drivers installed but it will not connect for anything. No flashing light. I know the device is detected using lsusb, but it won't work.

---

### Post by Relinies on 2012-06-13
Come on guys, I need help fast or i'm going to lose it.

---

### Post by Relinies on 2012-06-13
I have the full output of the Terminal now
```

relinies@Relinies-Ubuntu:~$ cd /home/relinies/Documents/ndis
relinies@Relinies-Ubuntu:~/Documents/ndis$ sudo make
[sudo] password for relinies: 
make -C driver
make[1]: Entering directory `/home/relinies/Documents/ndis/driver'
make -C /usr/src/linux-headers-3.2.0-23-generic M=/home/relinies/Documents/ndis/driver
make[2]: Entering directory `/usr/src/linux-headers-3.2.0-23-generic'
LD /home/relinies/Documents/ndis/driver/built-in.o
MKEXPORT /home/relinies/Documents/ndis/driver/crt_exports.h
MKEXPORT /home/relinies/Documents/ndis/driver/hal_exports.h
MKEXPORT /home/relinies/Documents/ndis/driver/ndis_exports.h
MKEXPORT /home/relinies/Documents/ndis/driver/ntoskernel_exports.h
MKEXPORT /home/relinies/Documents/ndis/driver/ntoskernel_io_exports.h
MKEXPORT /home/relinies/Documents/ndis/driver/rtl_exports.h
MKEXPORT /home/relinies/Documents/ndis/driver/usb_exports.h
MKSTUBS /home/relinies/Documents/ndis/driver/win2lin_stubs.h
CC [M] /home/relinies/Documents/ndis/driver/crt.o
CC [M] /home/relinies/Documents/ndis/driver/hal.o
CC [M] /home/relinies/Documents/ndis/driver/iw_ndis.o
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_set_essid’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:76:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_get_essid’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:110:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_set_infra_mode’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:170:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_get_infra_mode’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:198:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_get_network_type’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:241:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_get_freq’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:261:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_set_freq’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:295:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_get_tx_power’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:332:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_set_tx_power’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:351:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_get_bitrate’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:388:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_set_bitrate’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:406:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_get_rts_threshold’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:451:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_set_rts_threshold’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:469:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_get_frag_threshold’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:489:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_set_frag_threshold’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:507:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_get_ap_address’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:540:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_set_ap_address’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:554:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_get_encr’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:741:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_set_wep’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:906:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_set_nick’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:992:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_get_nick’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:1004:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_set_scan’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:1196:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_get_scan’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:1203:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_set_power_mode’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:1265:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_get_power_mode’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:1288:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_get_sensitivity’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:1320:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_set_sensitivity’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:1339:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_get_ndis_stats’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:1361:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_get_range’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:1372:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_set_mlme’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:1537:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_set_auth’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:1571:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_get_auth’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:1612:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_set_encodeext’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:1643:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_set_pmksa’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:1749:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘priv_reset’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:1828:17: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘priv_deauthenticate’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:1842:23: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘priv_power_profile’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:1850:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘priv_network_type’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:1875:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘priv_media_stream_mode’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:1907:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘priv_reload_defaults’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:1928:28: error: ‘struct net_device’ has no member named ‘priv’
make[3]: *** [/home/relinies/Documents/ndis/driver/iw_ndis.o] Error 1
make[2]: *** [_module_/home/relinies/Documents/ndis/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-3.2.0-23-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/relinies/Documents/ndis/driver'
make: *** [all] Error 2

```
Somebody tell me how I can put that in a spoiler tag or something, that would help some...

---

### Post by afixane on 2012-06-13
Hi [Relinies]("http://ubuntuforums.org/member.php?u=1673921"), there is an easy way to install proprietary driver. Just open your unity dash, and type "Additional Driver", or type "jockey-gtk" on your terminal

---

### Post by Relinies on 2012-06-13
Okay, going to try that now. I'll report the results in a moment.

---

### Post by Relinies on 2012-06-13
> **afixane said:**
> Hi [Relinies]("http://ubuntuforums.org/member.php?u=1673921"), there is an easy way to install proprietary driver. Just open your unity dash, and type "Additional Driver", or type "jockey-gtk" on your terminal


relinies@Relinies-Ubuntu:~$ jockey-gtk

(jockey-gtk:2027): Gtk-CRITICAL **: gtk_icon_set_render_icon_pixbuf: assertion `icon_set != NULL' failed

(jockey-gtk:2027): Gtk-CRITICAL **: gtk_icon_set_render_icon_pixbuf: assertion `icon_set != NULL' failed

I need an internet connection for that. GUESS WHAT I'M TRYING TO GET? ANY IDEA?

---

### Post by Relinies on 2012-06-13
My first time running Ubuntu is gonna be the last I suppose.

---

### Post by wildmanne39 on 2012-06-13
Hi, I am sorry that you are having issues but we are all volunteers here and when someone comes online that knows how to help you they will answer you.

It is rude to post more then once in a twenty four hour period to bump your thread.

I work with wireless but not ndiswrapper.

---

### Post by Relinies on 2012-06-13
Terribly sorry, but I never took the time to read the rules. I'll see to that now.

If you work with wireless, maybe you can help anyway, with finding some alternative route to getting internet access?

---

### Post by wildmanne39 on 2012-06-13
Hi, it is okay, I will try to help you with this tomorrow it is getting late here and I have been out of town for almost a week so I am exhausted tonight.

If you will please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

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

### Post by anewguy on 2012-06-14
Also, note that one never really has a need to compile ndiswrapper - I'm not sure why the post you pointed to is saying so, unless it was pulled from an old post.

A couple of things to keep in mind:

- ndiswrapper only works with Windows XP drivers (unless something has changed)

- the architecture of the driver MUST match the architecture of your Ubuntu installation - if you installed 64-bit ubuntu, the driver must be 64-bit, if you installed 32-bit ubuntu the driver must be 32-bit.

Do try to do the things Wildmanne39 is asking - he is an expert!

In the meantime, I'll look and see if I can find more info on getting this working for you.

wildmanne39:  great to see you back!  Rest up my friend!

Dave ;)

---

### Post by anewguy on 2012-06-14
Please see [this]("http://ubuntuforums.org/showthread.php?t=1965989&page=5") thread for how to get this working.  You'll need to undo everything you've done so far first so you are starting at a clean slate.

The biggest things I noticed in the thread:

- no compilation of a driver or ndiswrapper

- the router must be changed to only b/g modes, no n.  This seems to be a common theme on other posts as well.

See:  google search:

ubuntu 12.04 wna3100




Dave ;)

---

### Post by Relinies on 2012-06-14
When I save the output of those commands into a text file, it spreads it out across 4 lines when I open the file up back in Windows. I can still post what it gave, but it's up to you to tell what's what. I have no idea.
```
relinies@Relinies-Ubuntu:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux Relinies-Ubuntu 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

relinies@Relinies-Ubuntu:~$ lspci -nnk | grep -iA2 net
00:0a.0 Ethernet controller [0200]: NVIDIA Corporation MCP77 Ethernet [10de:0760] (rev a2)
	Subsystem: Hewlett-Packard Company Device [103c:2a9e]
	Kernel driver in use: forcedeth

relinies@Relinies-Ubuntu:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04f2:0841 Chicony Electronics Co., Ltd 
Bus 003 Device 003: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 002 Device 002: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 002 Device 003: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer

relinies@Relinies-Ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

relinies@Relinies-Ubuntu:~$ rfkill list all
relinies@Relinies-Ubuntu:~$ 

relinies@Relinies-Ubuntu:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61512  1 vfat
snd_hda_codec_realtek   223867  1 
parport_pc             32866  0 
ppdev                  17113  0 
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
joydev                 17693  0 
snd_hda_intel          33773  3 
snd_hda_codec         127706  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
usbhid                 47199  0 
psmouse                87603  0 
serio_raw              13211  0 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
hid                    99559  1 usbhid
k10temp                13166  0 
nouveau               774571  3 
ttm                    76949  1 nouveau
drm_kms_helper         46978  1 nouveau
edac_core              53746  0 
edac_mce_amd           23709  0 
drm                   242038  5 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13423  1 nouveau
mxm_wmi                12979  1 nouveau
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
video                  19596  1 nouveau
wmi                    19256  1 mxm_wmi
mac_hid                13253  0 
i2c_nforce2            13058  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usb_storage            49198  1 
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
forcedeth              63460  0

```
Okay, apparently it fixes itself when pasted into something else. I suppose .txt files don't like the Return key.

---

### Post by Relinies on 2012-06-14
> **anewguy said:**
> You'll need to undo everything you've done so far first so you are starting at a clean slate.
Will simply deleting the files work, or is there some command(s) I have to use to undo what's been done so far?

> **anewguy said:**
> Please see [this]("http://ubuntuforums.org/showthread.php?t=1965989&page=5") thread for how to get this working.  
Read through that thread's first 3 pages, barely understand it. I have no skill with Ubuntu whatsoever, sorry if that wasn't clear!
My install is the 64 bit 12.04, so atleast the thread is relevant.

This guy in this thread - [http://ubuntuforums.org/showthread.php?p=11803770#post11803770](http://ubuntuforums.org/showthread.php?p=11803770#post11803770)
> **cybpabeofm said:**
> this is a working guide anyone looking for a comprenhensive way to install the driver for a Netgear N300 WNA3100 USB wifi adapter can follow these steps.
Install NDISWRAPPER
Download the latest NDISWRAPPER source code
browse to it in terminal: cd /path/to/source/code
Once your in the directory: 
make uninstall
make
sudo make install
Installing the driver:
The wna3100 driver can be found on page 1
Browse to the directory with the wna3100 driver: cd /path/to/driver
sudo ndiswrapper -i bcmwlhigh5.inf
sudo modprobe ndiswrapper
iwconfig
If iwconfig shows that the USB device is scanning then you have installed the driver correctly and will have wireless capabilities with a minute, if not you either dont have the correct driver or its not installed correctly.
This guide wouldnt be possible without the help of chili555
He says to install NDISwrapper, but if i'm not mistaken, that is my problem. I'm a clever guy, and i'm sure I could find out what I need to do if I could do so.

Just went through the instructions I quoted earlier, it worked well up until sudo ndiswrapper -i bcmwlhigh5.inf. I don't remember the exact wording, and didn't think to copy it down, but it said something along the lines of, no such _____ as "."
And then it said installation may be incomplete. When I ran the next command, sudo modprobe ndiswrapper, it broke the terminal. The directory that would normally be listed when a command completed was gone, and nothing replaced it. Whenever I pressed a key, such as an arrow key, it came up with something like ]>. Note, this was after about 5 minutes of waiting, nothing happening all that time.

Unrelated question: Would I be right in assuming that sudo is the general command for installations?

---

### Post by wildmanne39 on 2012-06-14
Hi, in the link in your post chili555 a good friend of mine and the expert says that your device will only work with the 32 bit version of ubuntu, please see post 14.
[http://ubuntuforums.org/showthread.php?t=1965989&highlight=bcmwlhigh5&page=2](http://ubuntuforums.org/showthread.php?t=1965989&highlight=bcmwlhigh5&page=2)
Thanks

---

### Post by Relinies on 2012-06-14
> **wildmanne39 said:**
> Hi, in the link in your post chili555 a good friend of mine and the expert says that your device will only work with the 32 bit version of ubuntu, please see post 14.
[http://ubuntuforums.org/showthread.php?t=1965989&highlight=bcmwlhigh5&page=2](http://ubuntuforums.org/showthread.php?t=1965989&highlight=bcmwlhigh5&page=2)
Thanks

Well then. I have another adapter however, perhaps it will work. I'd much prefer not to resort to a 32 bit installation.
Give me about 10 minutes so I can go get it and the model #
Boom: [http://www.dlink.com/products/?pid=473](http://www.dlink.com/products/?pid=473)
D-Link wua-2340 wireless adapter

---

### Post by wildmanne39 on 2012-06-14
Hi, you will need to post all the output from the commands again for this new device.
Thanks

---

### Post by Relinies on 2012-06-14
> **wildmanne39 said:**
> Hi, you will need to post all the output from the commands again for this new device.
Thanks

Okay, give me about 15 minutes. It's annoying to keep switching operating systems -_-

Got it, much faster than I expected

```
relinies@Relinies-Ubuntu:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux Relinies-Ubuntu 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

relinies@Relinies-Ubuntu:~$ lspci -nnk | grep -iA2 net
00:0a.0 Ethernet controller [0200]: NVIDIA Corporation MCP77 Ethernet [10de:0760] (rev a2)
	Subsystem: Hewlett-Packard Company Device [103c:2a9e]
	Kernel driver in use: forcedeth

relinies@Relinies-Ubuntu:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04f2:0841 Chicony Electronics Co., Ltd 
Bus 003 Device 003: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 002 Device 002: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 002 Device 003: ID 07d1:3a08 D-Link System WUA-2340 RangeBooster G Adapter(rev.A) (no firmware) [Atheros AR5523]

relinies@Relinies-Ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

rfkill list all did nothing

relinies@Relinies-Ubuntu:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61512  1 vfat
parport_pc             32866  0 
ppdev                  17113  0 
snd_hda_codec_realtek   223867  1 
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
joydev                 17693  0 
usbhid                 47199  0 
hid                    99559  1 usbhid
nouveau               774571  3 
snd_hda_intel          33773  3 
snd_hda_codec         127706  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
ttm                    76949  1 nouveau
psmouse                87603  0 
k10temp                13166  0 
drm_kms_helper         46978  1 nouveau
drm                   242038  5 nouveau,ttm,drm_kms_helper
serio_raw              13211  0 
edac_core              53746  0 
edac_mce_amd           23709  0 
i2c_algo_bit           13423  1 nouveau
mxm_wmi                12979  1 nouveau
snd_pcm                97188  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    19256  1 mxm_wmi
video                  19596  1 nouveau
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mac_hid                13253  0 
i2c_nforce2            13058  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usb_storage            49198  1 
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
forcedeth              63460  0 


```

---

### Post by Relinies on 2012-06-14
Come on guys. I posted the info you needed. Anything?

---

### Post by Relinies on 2012-06-14
Entire thread is useless now, I'm just gonna go out and buy a compatible adapter today or tomorrow. WNDA3100, it's not only compatible but Plug n Play.

---

### Post by anewguy on 2012-06-14
You posted 3 hours ago and you wanted an instant reply?  Sorry, but this forum is all volunteer.  We do have other things going on in our lives as well.  You are not supposed to bump a thread before 24 hours since your last post unless you are adding useful information to what has already been posted.  We understand your frustration, but you need to be patient.  As for your WND3100 being compatible - obviously not.  Plug and play - that's a Windows term.

I wouldn't just rush out and get another adapter!  You need to read the list of adapters that are known to work with Ubuntu first, and you need to know the chipset, not just make and model as sometimes the chipset changes.

As for the adapter you are trying now, the d-link, notice that it says the chipset is Atheros AR5523.  

Bus 002 Device 003: ID 07d1:3a08 D-Link System WUA-2340 RangeBooster G Adapter(rev.A) (no firmware) [Atheros AR5523]

Unless someone is using that adapter and posts how they got it working, what we have to do to answer your thread - and what you should be trying - is another search of the forum using:

12.04 d-linkWUA-2340 AR5523

and see what turns up.  Then do a net search with the same search string.  These steps are what we do to try to help you.  Notice the link that wildmanne39 pointed you to posted by chili555?  He didn't know that off the top of his head (well, wildmanne39 might have - he is an expert in this area ;) ).  We read all of those things to try to help you.

In addition, no matter what the thread you quoted said, you DON'T need to compile ndiswrapper.  Notice the driver inf file they are using - 

bcmwlhigh5.inf (as wildmanne39 said in the thread from chili555, this MUST be the 32-bit version.  In scanning the thread I pointed you to, it appears no one has gotten the 64-bit version working.).  In addition you need the actuall .sys file that is the driver as well.

I hope you read this:

Old March 25th, 2012 	  #2
chili555
Ubuntu addict and loving it
 
chili555's Avatar
 
Join Date: Aug 2005
Location: South Carolina, USA
Beans: 13,690
Ubuntu 12.04 Precise Pangolin
Send a message via AIM to chili555 Send a message via Yahoo to chili555
	
Re: WNA3100 Support
Quote:
Then I followed the guide up until ndiswrapper -l. I typed this in and it only showed the driver, not any hardware
That suggests the .inf is incorrect for your device. Here is a better package that might work better.

I'd remove the current .inf:
Code:

sudo ndiswrapper -e bcmwlhigh5

Wipe out all the vestiges of the old incorrect .inf:
Code:

sudo rm -rf /etc/ndiswrapper/*

Download this file to your desktop and then right-click it and select Extract Here. Now do:
Code:

sudo ndiswrapper -i Desktop/wna3100-drivers/bcmwlhigh5.inf
ndiswrapper -l
iwconfig

Any improvement?
Attached Files
File Type: zip 	wna3100-drivers.zip (448.2 KB, 73 views)
__________________
Registered Linux User #374501
"Oh, Ubuntu, you are my favorite Linux-based operating system." --Dr. Sheldon Cooper
chili555 is online now Report Post   	Reply With Quote

It's pretty self explanatory.  Use 32-bit Ubuntu (the 64-bit version really doesn't gain you much in Linux - it's not Windows in that regard) as recommended.  Follow the above steps if it works we have to do some other changes to make it "stick" between boots.

Again, there is NO NEED to compile ndiswrapper.  What is in the 12.04 repositories is already 1.57-1.  In addition, instead of using the command line for ndiswrapper, where one little misstep can lead to some work, install ndisgtk from the repositories as well:

- put the installation CD in the drive AFTER you are already running - we don't want to boot from it

- using "places", or the file/folder browser if you are using the default Unity desktop, navigate the CD to the /pool/main/n folder

- within that folder you will see 2 folders:  ndisgtk and ndiswrapper - you need to install ndiswrapper fist:

navigate to the ndiswrapper folder
double click on the ndiswrapper common file to begin it's installation and wait for it to finish
double click on the ndiswrapper utils file to begin it's installation and wait for it to finish

- next, install ndisgtk:

navigate back 1 folder so you are again at the /pool/main/n folder
go to the ndisgtk folder
double click on the ndisgtk file to begin it's installation and wait for it to finish

- now you can use ndisgtk - a GUI front-end to ndiswrapper - just do the search in the Unity dash and run it

- point it to the driver files

- click the install/yes/ok whatever it is button

- this will install your driver.  If updates are needed to the blacklist or to the "load these extra modules when you start" file /etc/modules so it will run when you reboot also, ndisgtk tries to take care of those as well.

---

### Post by Relinies on 2012-06-14
When I got Ubuntu, the main page said there were 20 million people who had downloaded the OS. Considering the fact that 1. Many of these are probably repeat downloads, and 2. Another lot may have given up on Linux altogether, even a hundredth of the original number would still make for a thriving community. And considering the advanced nature of the OS, atleast 1/5 of those people would know what they're doing, as i'm sure you do. And 20,000 people is a lot, even if at any given moment about 3/5ths of that number, or so, are offline. But so far my thread has gotten the attention of three others, and only one of them stuck around.

But enough of the rant. 
Check this link, 2nd from bottom. [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear#USB) Here's your chipset too: Atheros AR9001U-2NX

EDIT: Also I did get ndiswrapper installed using another thread's instructions. So we have that.
EDITEDIT: Also, yes, I did read that. But I gave up on the adapter because I don't want to use 32 bit Ubuntu in the first place. Mostly because 1. 64 bit is going to run faster, however slightly, for my computer and 2. Minecraft will crash much more often in 32 bit. I don't know why, but I don't really have the time or patience to test it further, but it always did so on 32 bit windows, and on a 64 bit system with 32 bit java installed, etc.

---

### Post by anewguy on 2012-06-14
Wireless N, and did you notice it doesn't say 64-bit?  You really aren't going to notice that much of a difference with Linux.  Don't take things like performance and ratings for another OS and dump them into Linux - it's a different animal.

Also, I'm afraid I have to tell you that your posts are getting rather rude and arguementative.  Have you TRIED any of the suggestions?

At this point, with the attitude you have presented, nobody will go out of their way to help you.

Good luck.

---

### Post by Relinies on 2012-06-14
> **anewguy said:**
> Wireless N, and did you notice it doesn't say 64-bit?  You really aren't going to notice that much of a difference with Linux.  Don't take things like performance and ratings for another OS and dump them into Linux - it's a different animal.

Also, I'm afraid I have to tell you that your posts are getting rather rude and arguementative.  Have you TRIED any of the suggestions?

At this point, with the attitude you have presented, nobody will go out of their way to help you.

Good luck.
I have tried MOST the suggestions, but you know, none of them have worked. 
As for my posts leaning toward rude/argumentative, that happens a lot to me. Particularly when **** doesn't work right. I would really like to try Ubuntu, but it's pretty useless to me without an internet connection.

---

### Post by sffvba[e0rt on 2012-06-14
*Thread **closed **for staff review.*


404

---

### Post by sffvba[e0rt on 2012-06-14
It can be frustrating when things don't work. It is however counter productive when these frustrations lead us down a path where we are not communicating efficiently.

@OP - As has been pointed out to you, the forum's are used by people who volunteer there time and effort.  If they don't know the answer to your problem, or don't want to help then they won't.

Patience is key.  For more direct interaction you can try IRC ([http://www.ubuntu.com/support/community/chat](http://www.ubuntu.com/support/community/chat)) ([https://help.ubuntu.com/community/InternetRelayChat](https://help.ubuntu.com/community/InternetRelayChat)) or you could always pay for support - ([http://www.ubuntu.com/business/services/overview](http://www.ubuntu.com/business/services/overview))

I am re-opening the thread for now and ask you all to review the [CoC]("http://ubuntuforums.org/index.php?page=policy") and to strive together to find the solution to the problem.


404

---

### Post by Relinies on 2012-06-14
I understand. Thank you.

Now following the given instructions on this thread to get my WUA-2340 working: [http://ubuntuforums.org/showthread.php?t=861855&highlight=WUA-2340+wireless+adapter&page=3](http://ubuntuforums.org/showthread.php?t=861855&highlight=WUA-2340+wireless+adapter&page=3)
Started off at step 11, and the driver IS installed now, but I have an issue with step three. What exactly is a deb, and where can I get the one(s) I need? Whatever it is, it might be the reason for my current issue, being, it just won't work. Drivers installed, light won't start flashing (the "working" indicator). Since I'm just a newbie, I don't really know any other ways of detecting the device, but the other thing I did was check up on the icon in the upper right. No change.
EDIT: Herpderpderp. They're installer files for Linux. 
Should've reread the thread sooner. So the debs are installers for ndiswrapper.



Okay, driver installed and now I have a new issue. The thing just won't work. No flashing light, no connections listed. I know the device is detected thanks to lsusb, but I don't have any idea how to make it detect connections. It's as though it isn't connected.

Finished reading the thread now, as it turns out they had the same problem I have now. And that was a thread started in 2008, with replies up to Jan 2011. It was never solved.

---

### Post by wildmanne39 on 2012-06-15
Hi, we are going to try to get the second device to work, sorry that I was not on much yesterday I attended an online class for two hours about wireless drivers so I can better help people on the forum then I had to go to the Doctor.

I friend of mine the wireless expert has offered to help today so hopefully we can get this going.

Please give us a link to were you got the wireless drivers and post the output of:
```
lsmod
sudo lshw
ndiswrapper -l
```
please tell us where you installed ndiswrapper from.

The one you need is in the repositories and can be installed with synaptic or software center.
Thanks

---

### Post by Zill on 2012-06-15
> **Relinies said:**
> ...What exactly is a deb, and where can I get the one(s) I need?...
If you do some background reading it will help you considerably with your new system.  Firstly, you should know that [Linux is not Windows]("http://linux.oneandoneis2.org/LNW.htm") and things are done differently here. ;-)

Secondly, by reading the Ubuntu documentation on [InstallingSoftware]("https://help.ubuntu.com/community/InstallingSoftware"), you will find that a "deb" is software (i.e. a program and its dependencies) packaged in the Debian format used by Ubuntu.  These packages are held in "repositories" which are specifically for your version of Ubuntu.  They can easily be installed, either from a GUI such as the Ubuntu Software Centre, the Synaptic Package Manager or a CLI command using the Terminal:
```
sudo apt-get install xxxx
```

It may not have been mentioned yet but it is far easier to install and configure a Linux system with an Ethernet cable connected to your router.  This connection should "just work" straight out of the box, connecting you to the internet, without any configuration needed.  Once the system is installed and connected to the internet via a Ethernet cable, it is then far simpler to install wifi as any necessary drivers can often be installed automatically via the Hardware Drivers menu option.  Even without the automatic driver install, the Ethernet cable allows the download of any packages required.

So, I suggest you plug a cable in and see if your system advises anything about hardware drivers.

---

### Post by Elfy on 2012-06-16
Thread closed. Please do not post duplicates, it dilutes community effort.

---

