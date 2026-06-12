---
title: "Wieless conexton problem compaq presario v5000"
date: 2012-09-17
forum: New to Ubuntu
---

### Post by roster on 2012-09-17
I cant find the option  to conect using wireless.
I dont know if on or off the wireless card

---

### Post by NikTh on 2012-09-17
Hi , 
this command will show you if wireless is ON or OFF . 

```
rfkill list all
``` 

But if you have a problem with wireless , then you must follow a procedure to provide full info. 
Is a script you must download and execute.
**You must have an active Internet Connection to execute the commands.**
The procedure described in this post => [http://ubuntuforums.org/showpost.php?p=12242857&postcount=5](http://ubuntuforums.org/showpost.php?p=12242857&postcount=5)

Thanks

---

### Post by lkraemer on 2012-09-18
roster,
1. How do I know if I have Broadcom Hardware?

Open a Terminal Window and use these commands to get more information
on your hardware, wireless, Windows loaded drivers, and Linux drivers
that are currently blacklisted. Copy & Paste to prevent errors!
```

lspci
lsusb
lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist.conf
iwconfig

```
iwconfig will show what the wireless is detected as......wlan0, ath0, etc.

Post the output of the commands so we also know what is detected.

#2 Use DEFAULT Broadcom Driver
The Firmware may be missing, and you just need to have an Ethernet Connection to download the Firmware, or if you don't have an Ethernet Connection, you can just copy the Firmware to the proper folders.

Download the Firmware files located at:
[http://www.omattos.com/node/6](http://www.omattos.com/node/6)
to a USB Flash Drive and copy them to your Desktop, and Extract.
You should have two folders b43 & b43legacy. You will be copying
these folders to /lib/firmware/b43 and /lib/firmware/b43legacy

Here are the commands I used on my old Compaq V5201US, running the
10.04 LiveCD to get it working: (Open a Terminal Window)
```

cd /
cd /lib
cd firmware
pwd
ls
sudo cp -r /home/loginname/Desktop/b43* .
cd b43
ls
cd ..
cd b43legacy
ls
exit

```
Now you just have to Enable the default Driver:
SYSTEM -> ADMINISTRATION ->HARDWARE DRIVERS
should have a default Driver listed a driver listed for your wireless,
if so enable it. (If by chance you have already ENABLED it, go ahead
and let it try to uninstall, then install it again by clicking again.
It should find the drivers and load them, because the Firmware is where
it needs to be.

Check Network Manager (right click on the icon) to be sure the "Enable Wireless" box is checked (It should be ENABLED already by default.)

Check to see if you have wireless now. If not, you might need to
check the Loaded Modules, making sure there are no conflicts with other
Wifi drivers that might have been loaded, or others that cause conflicts.
```

lsmod

```
Post the output of lsmod.

You can check for errors with:
```

dmesg | tail

```
You may have to remove other modules depending on what lsmod shows:.... ..
What you will REMOVE depends on what you post as output from your commands.

If lsmod shows module bcm43xx and other conflicts installed you will
need to blacklist them, since you are going to be using the system default driver.
You may have to remove the following depending on what lsmod
shows:
```

modprobe -r b44

```

You can use sudo nano /etc/modprobe.d/blacklist.conf
and add the necessary modules to blacklist.

Once this is all straightened up..........
I'd reboot or try:
```

sudo /etc/init.d/networking restart

```

FINISH:
Click on the Wifi Icon in the top right toolbar and select the Network.

Manual Choice:
If you know the routers essid and the correct <interface>,
shown by using iwconfig ie wlan0, ath0, etc.... replace that
as the <interface> below:
```

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo iwconfig <interface> essid "youressidofrouter"
sudo iwconfig <interface> mode Managed
sudo ifconfig <interface> up
sudo dhclient <interface>
iwconfig

```
example......for Airlink and Wlan0
sudo iwconfig Wlan0 essid "Airlink"

It shouldn't take more than about 15 minutes......

LK

---

### Post by roster on 2012-09-26
*************** info trace ****************



**** uname -a ****


Linux roster-Presario-V5000-EZ427UA-ABA 3.2.0-30-generic-pae #48-Ubuntu SMP Fri Aug 24 17:14:09 UTC 2012 i686 i686 i386 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"


**** lspci ****


06:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Hewlett-Packard Company BCM4311 802.11b/g Wireless LAN Controller [103c:1363]
    Kernel modules: wl, ssb
08:08.0 Ethernet controller [0200]: Intel Corporation PRO/100 VE Network Connection [8086:1092] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:30a5]
    Kernel driver in use: e100


**** lsusb ****


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler / Genius NetScroll 120


**** iwconfig ****




**** rfkill ****


0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no


**** lsmod ****


Module                  Size  Used by
nls_utf8               12493  1 
udf                    84466  1 
crc_itu_t              12627  1 udf
bnep                   17830  2 
bluetooth             158438  7 bnep
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
snd_hda_codec_conexant    52554  1 
snd_hda_intel          32765  2 
snd_hda_codec         109562  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
joydev                 17393  0 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
wl                   2646601  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
psmouse                72919  0 
snd                    62064  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  414817  3 
drm_kms_helper         45466  1 i915
lib80211               14040  1 wl
mac_hid                13077  0 
wmi                    18744  1 hp_wmi
serio_raw              13027  0 
soundcore              14635  1 snd
drm                   197692  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41906  0 
hid                    77367  1 usbhid
e100                   36289  0 


**** nm-tool ****



NetworkManager Tool

State: connected (global)

- Device: eth0  [Conexión cableada 1] -----------------------------------------
  Type:              Wired
  Driver:            e100
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.129
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254




**** NetworkManager.state ****



[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


**** NetworkManager.conf ****



[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=<MAC address removed>,

[ifupdown]
managed=false


**** NetworkManager.conf-10.04 ****




**** interfaces ****


auto lo
iface lo inet loopback



**** iwlist ****




**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
search gateway.2wire.net


**** blacklist.conf ****


# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac


**** dmesg ****


[    0.000000] DMI: Hewlett-Packard Presario V5000 (EZ427UA#ABA)      /30A8, BIOS F.13 05/10/2006
[   19.394143] wmi: Mapper loaded
[   20.667096] wl: module license 'MIXED/Proprietary' taints kernel.
[   20.696576] wl 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   20.696589] wl 0000:06:00.0: setting latency timer to 64


**************** done ********************

---

### Post by lkraemer on 2012-09-26
roster,
I grabbed a DVD-RW and burned Ubuntu (32 Bit) 12.04.1 ISO to the DVD.
I booted the DVD and ran it in Live Mode (versus Install).

When it was finished booting, I saw on the Wifi Icon Displayed in the Top Right
Panel that the Wifi wasn't Enabled because of missing Firmware.  That firmware is
located at the above site.  I also had it on my ubuntu 8.04 LTS
Hard Drive on my Compaq V5201US.  I just copied it to the 12.04.1 running
system (RAM) and the wifi was enabled when the copy was completed.

I used this command, but yours will be somewhat different.
```

cd ~
cd /lib/firmware
sudo cp -r /media/26b1c6d7-36da-41c3-a16d-b21c0df8fe4b/lib/firmware/b43* .

```
Your copy will be (copy & paste to prevent errors):
```

cd /
cd /lib/firmware
sudo cp -r /path/to/downloaded/firmware/on/desktop/b43* .

```

As a matter of fact I'm posting this from my V5201US using my Wifi connection.

So, it shouldn't take more than 15 minutes to get it working.

```

lsmod

```
Displays:
> 
ubuntu@ubuntu:/lib/firmware$ lsmod
Module                  Size  Used by
dm_crypt               22528  0 
arc4                   12473  2 
b43                   342643  0 
mac80211              436455  1 b43
snd_atiixp_modem       18604  0 
snd_atiixp             19337  2 
snd_ac97_codec        106082  2 snd_atiixp_modem,snd_atiixp
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80845  3 snd_atiixp_modem,snd_atiixp,snd_ac97_codec
snd_seq_midi           13132  0 
cfg80211              178679  2 b43,mac80211
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  12 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
joydev                 17393  0 
k8temp                 12905  0 
i2c_piix4              13093  0 
shpchp                 32325  0 
bcma                   25651  1 b43
hp_wmi                 13652  0 
soundcore              14635  1 snd
dm_multipath           22710  0 
mac_hid                13077  0 
snd_page_alloc         14108  3 snd_atiixp_modem,snd_atiixp,snd_pcm
psmouse                72919  0 
parport_pc             32114  0 
serio_raw              13027  0 
ppdev                  12849  0 
bnep                   17830  2 
rfcomm                 38139  0 
sparse_keymap          13658  1 hp_wmi
bluetooth             158438  8 bnep,rfcomm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
squashfs               36095  1 
overlayfs              27511  1 
nls_utf8               12493  1 
isofs                  39553  1 
dm_raid45              76451  0 
xor                    25987  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 638208  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
usbhid                 41906  0 
hid                    77367  1 usbhid
radeon                737789  3 
8139too                23283  0 
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
drm                   197692  5 radeon,ttm,drm_kms_helper
8139cp                 26759  0 
ssb                    50691  1 b43
pata_atiixp            12999  3 
ati_agp                13242  0 
i2c_algo_bit           13199  1 radeon
wmi                    18744  1 hp_wmi
video                  19068  0 
ubuntu@ubuntu:/lib/firmware$


LK

---

### Post by Hadaka on 2012-09-26
Hi, Broadcom 4311 wireless requires the STA driver.

```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
 
```

this should work for you.

---

### Post by lkraemer on 2012-09-27
roster,
What does this command display?
```

lspci -vnn | grep 14e4

```

REF:
[https://wiki.archlinux.org/index.php/Broadcom_wireless#Determine_which_driver_you_need.2Fcan_use](https://wiki.archlinux.org/index.php/Broadcom_wireless#Determine_which_driver_you_need.2Fcan_use)
[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

LK

---

### Post by roster on 2012-09-30
This is shown

lspci -vnn | grep 14e4

---

### Post by bkratz on 2012-09-30
> **roster said:**
> This is shown

lspci -vnn | grep 14e4



Although the description is not quite accurate, the two commands in post #6 are the correct steps to get the BCM4311 working on 12.04.  Of course you will need a wired connection to get the files.

---

### Post by roster on 2012-09-30
Sorry correction: 

06:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

---

### Post by roster on 2012-10-01
Thanks a lot

---

### Post by gobuzz on 2012-10-08
Thank you all very much.  I had tried a bunch of stuff (and al also real new to Ubuntu) and this:

Download the Firmware files located at:
[http://www.omattos.com/node/6](http://www.omattos.com/node/6)
to a USB Flash Drive and copy them to your Desktop, and Extract.
You should have two folders b43 & b43legacy. You will be copying
these folders to /lib/firmware/b43 and /lib/firmware/b43legacy

solved my issue!

Thanks!!

---

