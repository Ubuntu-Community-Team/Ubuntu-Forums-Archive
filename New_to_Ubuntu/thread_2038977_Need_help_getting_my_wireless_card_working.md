---
title: "Need help getting my wireless card working"
date: 2012-08-07
forum: New to Ubuntu
---

### Post by chairsgotoschool on 2012-08-07
Hello, i need some help getting wireless internet to work, i have a dell inspiron 1525 laptop and it has a dell 1390 WLAN card in it, i tried this walkthrough [http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092) but i get stuck near the end where it says

"If that worked, then you now have Ndiswrapper installed.  Now we need to  install the drivers.  In a terminal, go to the directory where you have  the R151517.EXE file:"

i have no idea what the R151517.EXE file is, could someone please help

---

### Post by Hadaka on 2012-08-07
Hi try entering in a terminal

```
whereis R151517.EXE 
```

that should find the path to it...if you have it.
then..continue to follow that guide.
good luck

---

### Post by dcsoldschool53 on 2012-08-07
The R151517.EXE is a windows executable file. It has the driver for your wireless network. I download the file```
wget -c http://ftp.us.dell.com/network/R151517.EXE
``` The command```
unzip -a R151517.EXE
``` would not open it. So, I just right clicked on it to see if Archive manager would open it.

It did open the file and I was able to extract most of the files especially the one that you need to use. I hope this helps.

---

### Post by chairsgotoschool on 2012-08-07
thanks guys, im trying it now, i'll post back if it works

---

### Post by chairsgotoschool on 2012-08-08
ok i got it to unzip, i moved it to a folder cause it cluttered my home folder spot, im haveing another problem on the part that says this "Now **change directories to the DRIVER directory** that was just extracted." does it want me to open terminal in the driver folder that got extracted or something else, it also wants be to put this command in
cd YOUR-DRIVER-DIRECTORY sudo ndiswrapper -i bcmwl5.inf sudo ndiswrapper -l
i assume the your-driver-directory part is asking where it is? i tried putting this in place of that Desktop-UnititledFolder-DRIVER, i also tried replacing the dashed with slashes

---

### Post by dcsoldschool53 on 2012-08-08
> **chairsgotoschool said:**
> ok i got it to unzip, i moved it to a folder cause it cluttered my home folder spot, im haveing another problem on the part that says this "Now **change directories to the DRIVER directory** that was just extracted." does it want me to open terminal in the driver folder that got extracted or something else, it also wants be to put this command in
cd YOUR-DRIVER-DIRECTORY sudo ndiswrapper -i bcmwl5.inf sudo ndiswrapper -l
i assume the your-driver-directory part is asking where it is? i tried putting this in place of that Desktop-UnititledFolder-DRIVER, i also tried replacing the dashed with slashes

Yes open the terminal and cd to the folder where you put those files. Once you have cd inside of the DRIVER folder in the terminal, type in the command```
sudo ndiswrapper -i bcmwl5.inf
```

---

### Post by chairsgotoschool on 2012-08-08
> **dcsoldschool53 said:**
> Yes open the terminal and cd to the folder where you put those files. Once you have cd inside of the DRIVER folder in the terminal, type in the command```
sudo ndiswrapper -i bcmwl5.inf
```


it says command not found, i opened terminal in the DRIVER folder and the folder where all the other stuff it extracted was and it did the same thing in both

---

### Post by wildmanne39 on 2012-08-08
Hi, you do not need ndiswrapper and a windows driver the thread you looked at was from 2006.

Paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/netscript.sh && chmod +x netscript.sh && ./netscript.sh
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by chairsgotoschool on 2012-08-08
[ATTACH]222433[/ATTACH]

there's the netinfo.txt

---

### Post by wildmanne39 on 2012-08-08
Hi, please do:
```
sudo apt-get install --reinstall b43-fwcutter firmware-b43-installer
```
Reboot
Thanks

---

### Post by chairsgotoschool on 2012-08-08
> **wildmanne39 said:**
> Hi, please do:
```
sudo apt-get install --reinstall b43-fwcutter firmware-b43-installer
```
Reboot
Thanks

i rebooted and it still doesnt work

---

### Post by wildmanne39 on 2012-08-08
Hi, please post the output of:
```
ndiswrapper -l
```
if it is not installed please do not install it,
and attach the info_test file again after running:
```
./netscript.sh
```
Thanks

---

### Post by anewguy on 2012-08-08
If I might suggest, if you have done ANYTHING in regards to using ndiswrapper in the past, be sure you have removed ALL of what you did.  Otherwise you'll just be stepping all over yourself.  This includes things such as updates to the modules file (may have been an echo with | tee in it, may have been an edit, etc.).  Also, just to be safe, you should:

sudo ndiswrapper -l (lower case "L" for list)

if anything is returned you will need to remove it:

sudo ndiswrapper -e xxxxxxxx (where xxxxxxxx is what ever was returned in the list)

If needed repeat the above until nothing is returned.

Hopefully then things will be "clean" and you can re-try what wildmanne39 is helping you with - he really knows his stuff on this!

OOOPPPSSS - I see wildmanne39 posted after I started typing - sorry!

---

### Post by chairsgotoschool on 2012-08-08
for the first it says ndiswrapper is not installed

here's the file again


```
*************** info trace ****************



**** uname -a ****


Linux chairsgotoschool-Inspiron-1525 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"


**** lspci ****


09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 12)
    Subsystem: Dell Device [1028:022f]
    Kernel driver in use: sky2
--
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Kernel driver in use: b43-pci-bridge


**** lsusb ****


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 005 Device 002: ID 0461:4d63 Primax Electronics, Ltd 


**** iwconfig ****


wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


**** rfkill ****


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no


**** lsmod ****


Module                  Size  Used by
snd_hda_codec_idt      70795  1 
snd_hda_codec_hdmi     32474  1 
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
dell_laptop            18119  0 
dcdbas                 14490  1 dell_laptop
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
parport_pc             32866  0 
rfcomm                 47604  0 
ppdev                  17113  0 
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
arc4                   12529  2 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
b43                   365785  0 
mac80211              506816  1 b43
psmouse                87603  0 
r852                   18277  0 
sm_common              16865  1 r852
nand                   54955  2 r852,sm_common
nand_ids               12723  1 nand
mtd                    33087  2 sm_common,nand
nand_bch               13147  1 nand
bch                    22061  1 nand_bch
serio_raw              13211  0 
snd_seq_midi           13324  0 
nand_ecc               13230  1 nand
r592                   18144  0 
joydev                 17693  0 
memstick               16569  1 r592
snd_rawmidi            30748  1 snd_seq_midi
cfg80211              205544  2 b43,mac80211
bcma                   26696  1 b43
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
snd_seq_midi_event     14899  1 snd_seq_midi
v4l2_compat_ioctl32    17128  1 videodev
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
mac_hid                13253  0 
snd                    78855  16 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i915                  468651  3 
drm_kms_helper         46978  1 i915
drm                   242038  4 i915,drm_kms_helper
wmi                    19256  1 dell_wmi
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47199  0 
hid                    99559  1 usbhid
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
ssb                    52752  1 b43
sky2                   59043  0 


**** nm-tool ****



NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    ElFox:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 65 WEP
    NETGEAR:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 47


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.114
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             160.7.240.20
    DNS:             160.7.240.4




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

[ifupdown]
managed=false


**** interfaces ****


auto lo
iface lo inet loopback



**** iwlist ****


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption key:on
                    ESSID:"ElFox"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000044e4d291ac
                    Extra: Last beacon: 692ms ago
                    IE: Unknown: 0005456C466F78
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07000C4301000000
          Cell 02 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:off
                    ESSID:"NETGEAR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002a794c8d7d
                    Extra: Last beacon: 840ms ago
                    IE: Unknown: 00074E455447454152
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD7F0050F204104A00011010440001011041000100103B0001031047001031EC69EC35DD555114FF3B00365023F71021000D4E4554474541522C20496E632E10230009574752363134763130102400095747523631347631301042000538333235381054000800060050F204000110110009574752363134763130100800020084
                    IE: Unknown: DD090010180200F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00



**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1


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


[    1.367836] b43-pci-bridge 0000:0b:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.367854] b43-pci-bridge 0000:0b:00.0: setting latency timer to 64
[    1.384126] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243)
[    1.384140] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243)
[    1.384152] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243)
[    1.384164] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243)
[    1.448232] ssb: Sonics Silicon Backplane found on PCI device 0000:0b:00.0
[   17.425427] wmi: Mapper loaded
[   17.905890] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   18.027637] Registered led device: b43-phy0::tx
[   18.027702] Registered led device: b43-phy0::rx
[   18.027764] Registered led device: b43-phy0::radio
[   18.578045] type=1400 audit(1344461484.240:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=837 comm="apparmor_parser"
[   19.340064] b43-phy0: Loading firmware version 508.1084 (2009-01-14 01:32:01)
[   19.413950] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.415390] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   47.069960] type=1400 audit(1344461512.729:24): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=1899 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[   64.852092] b43-phy0: Radio hardware status changed to DISABLED
[   69.844081] b43-phy0: Radio hardware status changed to ENABLED
[   70.012097] b43-phy0: Loading firmware version 508.1084 (2009-01-14 01:32:01)
[   70.090244] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  266.780166] b43-pci-bridge 0000:0b:00.0: PCI INT A disabled
[  267.550991] b43-pci-bridge 0000:0b:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[  267.551024] b43-pci-bridge 0000:0b:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xfe7fc000)
[  267.551032] b43-pci-bridge 0000:0b:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[  267.551043] b43-pci-bridge 0000:0b:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100107)
[  267.597862] b43-pci-bridge 0000:0b:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  271.688078] b43-phy0: Loading firmware version 508.1084 (2009-01-14 01:32:01)
[  271.763252] ADDRCONF(NETDEV_UP): wlan0: link is not ready


**************** done ********************
```

---

### Post by wildmanne39 on 2012-08-08
Hi, it is trying to connect now, what network do you want to connect too?

Go to the top right corner of the screen and click on the internet icon and make sure enabled wireless is checked.

Did you try to set up your connection manually if so remove the networks from network manager and reboot letting network manager find your network.
Thanks

---

### Post by chairsgotoschool on 2012-08-08
> **wildmanne39 said:**
> Hi, it is trying to connect now, what network do you want to connect too?

Go to the top right corner of the screen and click on the internet icon and make sure enabled wireless is checked.

Did you try to set up your connection manually if so remove the networks from network manager and reboot letting network manager find your network.
Thanks

what the... thats weird, it still wouldnt connect but i jsut logged on and BOOM its working haha. thanks a lot, i just got ubuntu on a dual boot yesturday, im trying it cause i heard games run better on it and my laptop kinda sucks. thanks again

---

### Post by wildmanne39 on 2012-08-08
Hi, from what I seen your signal strength is weak, that is one of the reasons I wanted to know what network your were trying to connect too, also one of the networks listed does not have encryption turned on and the other one is using wep which is very weak and should be set to wpa2 only if possible.

Please use thread tools at the top of the page to mark the thread solved.
Thanks

---

### Post by chairsgotoschool on 2012-08-08
> **wildmanne39 said:**
> Hi, from what I seen your signal strength is weak, that is one of the reasons I wanted to know what network your were trying to connect too, also one of the networks listed does not have encryption turned on and the other one is using wep which is very weak and should be set to wpa2 only if possible.

Please use thread tools at the top of the page to mark the thread solved.
Thanks

thanks for your help, i marked it as solved and my internet seems to be working fine, im on my home network and things are downloading at the normal rate. thanks :)

---

