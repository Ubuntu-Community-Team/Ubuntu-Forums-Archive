---
title: "intel proset/wireless 3945ABG not working, HELP"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by shift_00 on 2008-09-14
i hate the fact that i still have to use windows to get into the internet .. i'm a noob as worst noobs can come .. so please to whoever reply my call for rescue .. assume the typical windows user, who had JUST installed ubuntu .. thanks in advance .. 

it's not working .. i'm on DELL INSPIRON 6400 .. and i have proset/wireless 3945ABG network card and has a wirless network environment, no no other way to get connected but that .. 

symptoms: 

the light isn't lit : the light of the wifi which is on the actual laptop is turned off

iwconfig returns no wireless extention 

network manager used to have a wireless network section in it, not anymore 

tried to install the ieee80211 but i keep getting this STUPID ERROR which has something to do a function first use "error: &#8216;proc_net&#8217; undeclared (first use in this function)" 

when i try to skip this and just install the ipw3945 package it and force IEEE80211_IGNORE_DUPLICATE=y or something like that .. it states that it couldn't find ieee80211

when i try: find /lib/farmeware "or something" i can notice some ipw's and ieee's but when i modprobe nothing is there and i keep getting error .. 

as of which distribution it is .. i went into the ubuntu site and downladed the latest .. hardy i guess .. 8.*.24 .. 

when i tried the windows wirless driver, the gui for ndiget or something :'( i loaded the inf file from the windows driver, and then it goes crazy, it freezez and every light there is starts flashing, the bluetooth and the wifi is lit, the capslock and the scroll lk are on and off and i have to switch it off physically .. 

i know that i'm a noob .. but i'm starting and i don't want to quite i really want to become a linux respected user .. i spent the last 6 hours just following this problem, i'm frustrated out of my mind, and i can't get to learn anything else without getting connected .. 


please do help .. PLEASE 

ps: can someone throw me some good links of where i can start my way with ubuntu .. thank you all

---

### Post by pytheas22 on 2008-09-14
Sorry that you're having so much frustration.  The iwl3945 driver is actually already installed in Ubuntu by default, however.  For some reason it must not be working for you (it does tend to be buggy).  First, make sure that you've applied all Ubuntu updates.  If after doing that and rebooting your wireless still doesn't work, please open up a terminal, run the following commands, and post their output here:
```

dmesg | grep -e iwl -e wlan -e eth1
lshw -C Network
lspci -nn
iwlist scan
```

Also, if there's a physical button on your laptop or a key combination that you have to press to enable the wireless (that is, something like [function+F2]), you tried turning that on, right?

---

### Post by shift_00 on 2008-09-15
hehe well of course sir, i know how to turn my wireless on :) 

i installed the updates available at the synaptic manager ( ?? ) and i made the ubuntu cd as a source too :s :confused:

now to what you have requested to run 

1- dmesg | grep -e iwl -e wlan -e eth1
i ran it and nothing happenned, it just gave me the $ sign again

2- lshw -C Network
```

WARNING: you should run this program as super-user.
*-network UNCLAIMED     
description: Network controller
product: PRO/Wireless 3945ABG Network Connection
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:0b:00.0
version: 02
width: 32 bits
clock: 33MHz      
capabilities: bus_master cap_list     
configuration: latency=0
*-network      
description: Ethernet interface       
product: BCM4401-B0 100Base-TX       
vendor: Broadcom Corporation       
physical id: 0      
bus info: pci@0000:03:00.0       
logical name: eth0       
version: 02      
serial: 00:15:c5:0d:91:f6       
width: 32 bits      
clock: 33MHz      
capabilities: bus_master cap_list ethernet physical       
configuration: 
broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes

```

3- lspci -nn
```

00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 
[8086:27d6] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 
[8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 
[8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 
[8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 
[8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller 
[8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e1)

00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 01)

00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller 
[8086:27c4] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller 
[8086:27da] (rev 01)
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX 
[14e4:170c] (rev 02)
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller 
[1180:0832]
03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
 [1180:0822] (rev 19)
03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller 
[1180:0843] (rev 0a)
03:01.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter 
[1180:0592] (rev 05)
03:01.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller 
[1180:0852] (rev ff)
0b:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection 
[8086:4222] (rev 02)

```

4- iwlist scan
```

lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.

```

:S now what to do sir ?

---

### Post by shift_00 on 2008-09-15
do you suggest more radical solution like downloading another ubuntu distribution and re-install the whole thing, coz I read from threads that what I downloaded is the buggiest version .. Something about it being 'generic' or something ... I'm really lost

---

### Post by Crafty Kisses on 2008-09-15
Try installing this package:
```
sudo apt-get install linux-image-2.6.17-10-generic linux-restricted-modules-2.6.17-10-generic
```

---

### Post by shift_00 on 2008-09-15
```

sudo apt-get install linux-image-2.6.17-10-generic linux-restricted-modules-2.6.17-10-generic

[sudo] password for user: 

Reading package lists... Done

Building dependency tree       

Reading state information... Done

E: Couldn't find package linux-image-2.6.17-10-generic



```

:( 

and please do not assume that i know how to install updates, re-compile headers or drivers or install subsystems on the fly for that matter, i want to get there, at the moment i don't know how .. and no matter how i try my case is always different than those solved threads, i will be bothering you with something basic like this, but please do help :)

btw the OS version is : Ubuntu 8.04.1, Kernel 2.6.24-19-generic

---

### Post by manadi on 2008-09-15
Can you post the o/p of lsmod here....

---

### Post by pytheas22 on 2008-09-15
> 1- dmesg | grep -e iwl -e wlan -e eth1
i ran it and nothing happenned, it just gave me the $ sign again

It looks like the driver for your card is not loaded for some reason...it should be automatically loaded if you're using Hardy, unless you deleted it at some point.  If you type:
```

sudo modprobe iwl3945
```

it would load the driver, or give you an error message about why it can't load the driver.  What does it say?
> 
do you suggest more radical solution like downloading another ubuntu distribution and re-install

If the 'modprobe' command above fails, you may want to reinstall Hardy, because I'm not sure what's going on...probably in your previous attempts to get the card working, you accidentally removed something very important.

You could also try installing Ubuntu 7.10 (Gutsy).  It uses an older driver for your card that tends to work more reliably than the one in Hardy.

---

### Post by shift_00 on 2008-09-15
i'm sorry for the late reply i was at work :) 

as for the lsmod 
```
lsmod
Module                  Size  Used by
ipv6                  267780  10 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
nbd                    24864  0 
ppdev                  10372  0 
capifs                  6920  1 
snd_atiixp_modem       17544  0 
snd_via82xx_modem      16264  0 
snd_intel8x0m          18956  0 
snd_ac97_codec        101028  3 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m
ac97_bus                3072  1 snd_ac97_codec
acpi_cpufreq           10796  1 
cpufreq_userspace       5284  0 
cpufreq_conservative     8712  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7104  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
sbs                    15112  0 
container               5632  0 
dock                   11280  0 
sbshc                   7680  1 sbs
af_packet              23812  0 
prism2_usb             75908  0 
p80211                 33160  1 prism2_usb
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
nls_iso8859_1           4992  1 
nls_cp437               6656  1 
vfat                   14464  1 
fat                    54556  1 vfat
aes_i586               33536  0 
dm_crypt               15364  0 
dm_mod                 62660  1 dm_crypt
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
loop                   18948  0 
joydev                 13120  0 
snd_hda_intel         344728  3 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
hci_usb                16540  2 
snd_pcm                78596  6 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ac97_codec,snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  5 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
bluetooth              61156  7 rfcomm,l2cap,hci_usb
snd_seq_dummy           4868  0 
usbhid                 31872  0 
hid                    38784  1 usbhid
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ndiswrapper           192920  0 
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
sdhci                  19076  0 
ricoh_mmc               4352  0 
video                  19856  0 
output                  4736  1 video
serio_raw               7940  0 
mmc_core               51460  1 sdhci
snd                    56996  21 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ac97_codec,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi_acer                9644  0 
ac                      6916  0 
battery                14212  0 
button                  9232  0 
iTCO_wdt               13092  0 
intel_agp              25492  1 
dcdbas                  9504  0 
soundcore               8800  1 snd
iTCO_vendor_support     4868  1 iTCO_wdt
agpgart                34760  2 intel_agp
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
evdev                  13056  8 
psmouse                40336  0 
pcspkr                  4224  0 
usb_storage            73664  4 
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
libusual               19108  1 usb_storage
sg                     36880  0 
sd_mod                 30720  10 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
ata_generic             8324  0 
b44                    28432  0 
ata_piix               19588  4 
ohci1394               33584  0 
pata_acpi               8320  0 
ssb                    34308  1 b44
mii                     6400  1 b44
ieee1394               93752  2 sbp2,ohci1394
libata                159344  3 ata_generic,ata_piix,pata_acpi
scsi_mod              151436  6 sbp2,usb_storage,sg,sd_mod,sr_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  9 prism2_usb,hci_usb,usbhid,ndiswrapper,usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  4 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  13 

```

and as for the modprobe it just flashed the $ sign again ... i pressed enter and nothing happenned .. 

shall i reinstall ? is it hopeless ? or if the gutsy older distribution is more reliable and will save me this frustration please send me a download link .. i don't want to do anything on my own .. i always get the wrong things ..

---

### Post by odin1965 on 2008-09-15
Does your wireless work if you boot with the live CD?

---

### Post by shift_00 on 2008-09-15
nope .. just a slower version of the same frustration .. :s

---

### Post by odin1965 on 2008-09-15
You mentioned that there used to be a "wireless section" in network manager. Is it still there when you use the live CD? If so what does it say? Is it detecting any networks and maybe just not connecting? What does "iwlist scan" return when using the live CD?

---

### Post by shift_00 on 2008-09-15
if the ultimate question is "is the wireless works at the first place, as in hardware stuff" .. well here it is i'm using it right now .. and if i did something accidently wrong .. well it should be reversable .. right ? i mean that's the whole point of having an open source operating system ..

---

### Post by odin1965 on 2008-09-15
Yes, that is the question, but we would like to compare an original setup with what you have now to determine what is different. That way we can see if it might have worked in the first place with a little tweaking and now has a different problem, or if it's still just the same problem you had originally. The fact that wireless WAS listed in NM would seem to indicate that the iwl3945 driver WAS working at some point.
 I see from a previous post that you have the NDISwrapper module still loaded. That shouldn't be needed with the 3945 card.

---

### Post by shift_00 on 2008-09-15
well the thing is the network manager had these three categories "wireless, point to point, and the wired connection i think" now i tried to set up the wireless, though the card wasn't working from the first boot, now the network manager has only two, the wireless is out .. the wrapper i got it to try the inf file of the driver that windows has .. and it got stuck when i used it anyways ...

---

### Post by shift_00 on 2008-09-15
i tried to reinstall a fresh version, and i noticed that the installer failed to configure DHCP ... i quit the installation .. is that the problem ??

---

### Post by shift_00 on 2008-09-15
i call upon the respected members of this forum to help me .. please

---

### Post by panhandle on 2008-09-15
Since I haven't seen it elsewhere in this thread, let's just be certain:

Does your machine have a wifi card kill switch? If so, are you *positive* the card is enabled?

Often, the LED light associated with this switch does not work, so do not use that as an indicator.

---

### Post by shift_00 on 2008-09-15
well i understand your point, but when i boot the xp .. the light is lit the card is functioning fine .. and it does come to life "the light that is" when it gets a freez

---

### Post by panhandle on 2008-09-15
Does that mean you are positive the switch is in the "on" position?

---

### Post by shift_00 on 2008-09-15
yes, because the switch turns both wifi and bluetooth on together, and when ubuntu is on and i turn it on the bluetooth fires and is recognized, i wish i can say the same for my wifi ... 

can anyone give me a link to download a clean stable reliable ubuntu distribution for my machine? 

dell inspiron 6400
1.83 centrino duo
1 g ram 
:S

---

### Post by panhandle on 2008-09-15
Here...the official Ubuntu website. 

[http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)

Choose the nearest mirror and download.

---

### Post by shift_00 on 2008-09-15
well what do i download dapper, gutsy, edgy, feisty, or hardy, kubuntu or edubuntu  ???? what's the difference ? i downloaded hardy and look where i am ..  it's getting too overwhelming

---

### Post by shift_00 on 2008-09-15
and does this "failed to configure DHCP" message i got while installing has anything to do with anything ? coz i want to re-install a fresh copy if that will solve anything .. coz i checked the md5sum and the version i downloaded is good, and checked the cd for defects, nothing is wrong, and it's not the hardware .. so if it is not the software, it should be me .. so if i reinstalled and from the top it didn't recognize my wifi card, like it did,  what should i do ?

---

### Post by pytheas22 on 2008-09-15
There's some strange stuff going on.  You say that you were able to insert the iwl3945 module without an error, yet 'lsmod' does not list iwl3945 as present.  On top of that, you should not need to insert iwl3945 manually at all--it should be auto-inserted.

Perhaps something strange happened to the wireless stack earlier when you were trying to sort this out that's causing iwl3945 not to work.  You can install the latest stable version of iwl3945 by running the following commands (provided you're plugged in via ethernet first):

```
sudo apt-get install build-essential
wget http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-3945-ucode-15.28.1.6.tgz
tar -xzvf iwlwifi*
cp iwlwifi-3945-ucode-15.28.1.6/iwlwifi-3945-1.ucode /lib/firmware
wget http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-old.tar.bz2
bunzip2 compat-wireless*
tar xf compat-wireless*
cd compat-wireless-2.6-old/
make ###it will take a few minutes here to compile
sudo make install
sudo make unload
sudo make load
```

Then reboot.  If things still don't work after rebooting, please post:
```

lsmod | grep iwl
lshw -C Network
dmesg | grep -e iwl -e wlan
lspci -nn
iwconfig
```

If you want to try using Gutsy instead, you can download the ISO from [here]("http://releases.ubuntu.com/7.10/") (specific links are at the bottom of the page, depending on which version of Gutsy you need).  But I'd give the commands above a try first, as they might solve the problem.

---

### Post by shift_00 on 2008-09-15
can there be an alternate code ? coz i don't have any other way of connecting to the internet .. :S .. might i manually download the packages, tar xzvf "or something", then cd, then make ?

---

### Post by shift_00 on 2008-09-15
coz that's what i've been doing so far, get a solution wherever a wget is found i download them from xp put them on a usb device then manually use them there .. have one pc, one internet connecting method "wifi" .. so if that's wrong, i've messed up, and what is the right way of doing it otherwise ?

---

### Post by shift_00 on 2008-09-15
anyone? so i can get to work ??

---

### Post by pytheas22 on 2008-09-15
You can install the new driver offline, with a little more work.

First, put your Ubuntu live CD in your drive.  Then go to System>Administration>Software Sources.  Under the "Ubuntu Software" tab, you should see a box that you can check to enable the use of your CD as a repository.  Make sure this box is checked.  Then close the window (if you're asked about reloading the sources list, say yes).  Then run:
```

sudo apt-get update
sudo apt-get install build-essential
```

When that's finished, go to a computer that has Internet and download [this file]("http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-3945-ucode-15.28.1.6.tgz") and [this file]("http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-old.tar.bz2").  Save them onto a USB drive or something, and then transfer both files to your desktop on Ubuntu.  After you've saved them to your desktop, run these commands on Ubuntu:
```

cd ~/Desktop
tar -xzvf iwlwifi*
sudo cp iwlwifi-3945-ucode-15.28.1.6/iwlwifi-3945-1.ucode /lib/firmware
bunzip2 compat-wireless*
tar xf compat-wireless*
cd compat-wireless-2.6-old/
make ###it will take a few minutes here to compile
sudo make install
sudo make unload
sudo make load
```

EDIT: sorry, I screwed a few instructions up (forgot that you needed to download two files, not one), but I fixed them now.  If you tried this once and it failed, try it again now please using the corrected instructions above.

---

### Post by master5o1 on 2008-09-15
> **shift_00 said:**
> and as for the modprobe it just flashed the $ sign again ... i pressed enter and nothing happenned .. 

modprobe doesn't give any `success` notification -- only error warnings. like "WARNING: blahblah.ko not found" or something.

---

### Post by shift_00 on 2008-09-15
the results are back .. i think we are close .. please bare with me people .. 


```
lsmod | grep iwl
iwl3945                93304  0 
led_class               6020  2 ath5k,iwl3945
mac80211              222324  13 ath5k,at76_usb,rt2x00usb,rt2x00pci,rt2x00lib,iwl3945,rtl8187,rtl8180,zd1211rw,adm8211,p54usb,p54pci,p54common
cfg80211               36192  8 ath5k,rt2x00lib,iwl3945,rtl8187,rtl8180,adm8211,mac80211,ipw2100
```

```

lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 02
       serial: 00:13:02:34:12:44
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:0d:91:f6
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes

```

```

dmesg | grep -e iwl -e wlan
[  192.138179] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[  192.138186] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[  192.138793] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[  192.200215] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
[  192.201020] phy0: Selected rate control algorithm 'iwl-3945-rs'
[  192.408328] iwlwifi_mac80211: disagrees about version of symbol wiphy_register
[  192.408337] iwlwifi_mac80211: Unknown symbol wiphy_register
[  192.408373] iwlwifi_mac80211: disagrees about version of symbol wiphy_new
[  192.408377] iwlwifi_mac80211: Unknown symbol wiphy_new
[  192.408927] iwlwifi_mac80211: disagrees about version of symbol wiphy_unregister
[  192.408930] iwlwifi_mac80211: Unknown symbol wiphy_unregister
[  192.409680] iwlwifi_mac80211: disagrees about version of symbol wiphy_free
[  192.409701] iwlwifi_mac80211: Unknown symbol wiphy_free
[  192.413274] iwl4965: Unknown symbol iwlwifi_ieee80211_rx_irqsafe
[  192.413355] iwl4965: Unknown symbol iwlwifi_ieee80211_get_hdrlen
[  192.413502] iwl4965: Unknown symbol iwlwifi_iwlwifi_ieee80211_tx_status_irqsafe
[  192.413602] iwl4965: Unknown symbol iwlwifi_iwlwifi_ieee80211_stop_queues
[  192.413744] iwl4965: Unknown symbol iwlwifi_ieee80211_tx_status
[  192.413801] iwl4965: Unknown symbol iwlwifi_ieee80211_rate_control_unregister
[  192.413912] iwl4965: Unknown symbol iwlwifi_ieee80211_stop_queue
[  192.413968] iwl4965: Unknown symbol iwlwifi_sta_info_put
[  192.414080] iwl4965: Unknown symbol iwlwifi_ieee80211_free_hw
[  192.414136] iwl4965: Unknown symbol iwlwifi_ieee80211_beacon_get
[  192.414198] iwl4965: Unknown symbol iwlwifi_sta_info_get
[  192.414327] iwl4965: Unknown symbol iwlwifi_ieee80211_alloc_hw
[  192.414405] iwl4965: Unknown symbol iwlwifi_ieee80211_scan_completed
[  192.414554] iwl4965: Unknown symbol iwlwifi_ieee80211_register_hw
[  192.414751] iwl4965: Unknown symbol iwlwifi_ieee80211_wake_queue
[  192.414808] iwl4965: Unknown symbol iwlwifi_ieee80211_rate_control_register
[  192.414906] iwl4965: Unknown symbol iwlwifi_iwlwifi_ieee80211_register_hwmode
[  192.415148] iwl4965: Unknown symbol iwlwifi_ieee80211_unregister_hw
[  192.415255] iwl4965: Unknown symbol iwlwifi_ieee80211_start_queues
[  192.445888] Registered led device: iwl-phy0:radio
[  192.445910] Registered led device: iwl-phy0:assoc
[  192.445965] Registered led device: iwl-phy0:RX
[  192.445982] Registered led device: iwl-phy0:TX
[  192.467179] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  192.888302] usbcore: registered new interface driver rndis_wlan
[  193.212577] wlan0: authenticate with AP 00:1d:7e:b4:7d:70
[  193.215251] wlan0: authenticated
[  193.215256] wlan0: associate with AP 00:1d:7e:b4:7d:70
[  195.122012] wlan0: RX AssocResp from 00:1d:7e:b4:7d:70 (capab=0x431 status=0 aid=1)
[  195.122017] wlan0: associated
[  195.122062] wlan0 (WE) : Wireless Event too big (314)
[  195.125562] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  205.110942] wlan0: disassociating by local choice (reason=3)
[  205.522178] wlan0: no IPv6 routers present
[  204.546419] wlan0: deauthenticated
[  206.450914] wlan0: authenticate with AP 00:1d:7e:b4:7d:70
[  204.549976] wlan0: authenticate with AP 00:1d:7e:b4:7d:70
[  204.556376] wlan0: authenticated
[  204.556382] wlan0: associate with AP 00:1d:7e:b4:7d:70
[  204.565210] wlan0: RX ReassocResp from 00:1d:7e:b4:7d:70 (capab=0x431 status=0 aid=1)
[  204.565217] wlan0: associated
[  204.565288] wlan0 (WE) : Wireless Event too big (314)
[  207.562206] wlan0: deauthenticated
[  208.559053] wlan0: authenticate with AP 00:1d:7e:b4:7d:70
[  208.561693] wlan0: authenticated
[  208.561700] wlan0: associate with AP 00:1d:7e:b4:7d:70
[  208.565899] wlan0: RX ReassocResp from 00:1d:7e:b4:7d:70 (capab=0x431 status=0 aid=1)
[  208.565906] wlan0: associated
[  208.565978] wlan0 (WE) : Wireless Event too big (314)
[  211.560329] wlan0: deauthenticated
[  212.556054] wlan0: authenticate with AP 00:1d:7e:b4:7d:70
[  212.558700] wlan0: authenticated
[  212.558707] wlan0: associate with AP 00:1d:7e:b4:7d:70
[  212.562887] wlan0: RX ReassocResp from 00:1d:7e:b4:7d:70 (capab=0x431 status=0 aid=1)
[  212.562894] wlan0: associated
[  212.562966] wlan0 (WE) : Wireless Event too big (314)
[  215.558609] wlan0: deauthenticated
[  216.557073] wlan0: authenticate with AP 00:1d:7e:b4:7d:70
[  216.559723] wlan0: authenticated
[  216.559730] wlan0: associate with AP 00:1d:7e:b4:7d:70
[  216.563960] wlan0: RX ReassocResp from 00:1d:7e:b4:7d:70 (capab=0x431 status=0 aid=1)
[  216.563967] wlan0: associated
[  216.564040] wlan0 (WE) : Wireless Event too big (314)
[  219.557023] wlan0: deauthenticated
[  220.554082] wlan0: authenticate with AP 00:1d:7e:b4:7d:70
[  220.556731] wlan0: authenticated
[  220.556738] wlan0: associate with AP 00:1d:7e:b4:7d:70
[  220.560838] wlan0: RX ReassocResp from 00:1d:7e:b4:7d:70 (capab=0x431 status=0 aid=1)
[  220.560845] wlan0: associated
[  220.560917] wlan0 (WE) : Wireless Event too big (314)
[  223.555135] wlan0: deauthenticated
[  224.551096] wlan0: authenticate with AP 00:1d:7e:b4:7d:70
[  224.553763] wlan0: authenticated
[  224.553771] wlan0: associate with AP 00:1d:7e:b4:7d:70
[  224.557815] wlan0: RX ReassocResp from 00:1d:7e:b4:7d:70 (capab=0x431 status=0 aid=1)
[  224.557822] wlan0: associated
[  224.557895] wlan0 (WE) : Wireless Event too big (314)
[  227.553381] wlan0: deauthenticated
[  228.552100] wlan0: authenticate with AP 00:1d:7e:b4:7d:70
[  228.554738] wlan0: authenticated
[  228.554744] wlan0: associate with AP 00:1d:7e:b4:7d:70
[  228.558984] wlan0: RX ReassocResp from 00:1d:7e:b4:7d:70 (capab=0x431 status=0 aid=1)
[  228.558991] wlan0: associated
[  228.559063] wlan0 (WE) : Wireless Event too big (314)
[  231.551701] wlan0: deauthenticated
[  232.549105] wlan0: authenticate with AP 00:1d:7e:b4:7d:70
[  232.551751] wlan0: authenticated
[  232.551758] wlan0: associate with AP 00:1d:7e:b4:7d:70
[  232.555855] wlan0: RX ReassocResp from 00:1d:7e:b4:7d:70 (capab=0x431 status=0 aid=1)
[  232.555862] wlan0: associated
[  232.555935] wlan0 (WE) : Wireless Event too big (314)
[  235.551826] wlan0: deauthenticated
[  236.550114] wlan0: authenticate with AP 00:1d:7e:b4:7d:70
[  236.554448] wlan0: authenticated
[  236.554455] wlan0: associate with AP 00:1d:7e:b4:7d:70
[  236.558572] wlan0: RX ReassocResp from 00:1d:7e:b4:7d:70 (capab=0x431 status=0 aid=1)
[  236.558578] wlan0: associated
[  236.558651] wlan0 (WE) : Wireless Event too big (314)
[  246.548659] wlan0: disassociating by local choice (reason=3)
[  250.610896] wlan0: deauthenticated
[  250.612625] wlan0: authenticate with AP 00:1d:7e:b4:7d:70
[  248.712733] wlan0: authenticate with AP 00:1d:7e:b4:7d:70
[  248.712751] wlan0: authenticated
[  248.712756] wlan0: associate with AP 00:1d:7e:b4:7d:70
[  248.721286] wlan0: RX ReassocResp from 00:1d:7e:b4:7d:70 (capab=0x431 status=0 aid=1)
[  248.721293] wlan0: associated
[  248.721364] wlan0 (WE) : Wireless Event too big (314)
[  251.712850] wlan0: deauthenticated
[  252.709868] wlan0: authenticate with AP 00:1d:7e:b4:7d:70
[  252.712587] wlan0: authenticated
[  252.712594] wlan0: associate with AP 00:1d:7e:b4:7d:70
[  252.716805] wlan0: RX ReassocResp from 00:1d:7e:b4:7d:70 (capab=0x431 status=0 aid=2)
[  252.716812] wlan0: associated
[  252.716884] wlan0 (WE) : Wireless Event too big (314)
[  257.613527] wlan0: deauthenticated
[  258.609379] wlan0: authenticate with AP 00:1d:7e:b4:7d:70
[  256.710282] wlan0: authenticated
[  256.710290] wlan0: associate with AP 00:1d:7e:b4:7d:70
[  256.714660] wlan0: RX ReassocResp from 00:1d:7e:b4:7d:70 (capab=0x431 status=0 aid=2)
[  256.714667] wlan0: associated
[  256.714739] wlan0 (WE) : Wireless Event too big (314)
[  261.611774] wlan0: deauthenticated
[  262.611371] wlan0: authenticate with AP 00:1d:7e:b4:7d:70
[  262.614020] wlan0: authenticated
[  262.614025] wlan0: associate with AP 00:1d:7e:b4:7d:70
[  262.618776] wlan0: RX ReassocResp from 00:1d:7e:b4:7d:70 (capab=0x431 status=0 aid=2)
[  262.618781] wlan0: associated
[  262.618822] wlan0 (WE) : Wireless Event too big (314)
[  263.712566] wlan0: deauthenticated
[  266.611390] wlan0: authenticate with AP 00:1d:7e:b4:7d:70
[  264.719496] wlan0: authenticated
[  264.719504] wlan0: associate with AP 00:1d:7e:b4:7d:70
[  264.722980] wlan0: RX ReassocResp from 00:1d:7e:b4:7d:70 (capab=0x431 status=0 aid=2)
[  264.722987] wlan0: associated
[  264.723059] wlan0 (WE) : Wireless Event too big (314)
[  267.725862] wlan0: deauthenticated
[  268.721863] wlan0: authenticate with AP 00:1d:7e:b4:7d:70
[  268.724502] wlan0: authenticated
[  268.724510] wlan0: associate with AP 00:1d:7e:b4:7d:70
[  268.728122] wlan0: RX ReassocResp from 00:1d:7e:b4:7d:70 (capab=0x431 status=0 aid=2)
[  268.728129] wlan0: associated
[  268.728201] wlan0 (WE) : Wireless Event too big (314)
[  271.724082] wlan0: deauthenticated
[  272.722872] wlan0: authenticate with AP 00:1d:7e:b4:7d:70
[  272.725516] wlan0: authenticated
[  272.725523] wlan0: associate with AP 00:1d:7e:b4:7d:70
[  272.728989] wlan0: RX ReassocResp from 00:1d:7e:b4:7d:70 (capab=0x431 status=0 aid=2)
[  272.728996] wlan0: associated
[  272.729069] wlan0 (WE) : Wireless Event too big (314)
[  275.722323] wlan0: deauthenticated
[  276.719884] wlan0: authenticate with AP 00:1d:7e:b4:7d:70
[  276.722528] wlan0: authenticated
[  276.722535] wlan0: associate with AP 00:1d:7e:b4:7d:70
[  276.726153] wlan0: RX ReassocResp from 00:1d:7e:b4:7d:70 (capab=0x431 status=0 aid=2)
[  276.726159] wlan0: associated
[  276.726232] wlan0 (WE) : Wireless Event too big (314)
[  279.720603] wlan0: deauthenticated
[  280.716896] wlan0: authenticate with AP 00:1d:7e:b4:7d:70
[  280.719542] wlan0: authenticated
[  280.719549] wlan0: associate with AP 00:1d:7e:b4:7d:70
[  280.723124] wlan0: RX ReassocResp from 00:1d:7e:b4:7d:70 (capab=0x431 status=0 aid=2)
[  280.723130] wlan0: associated
[  280.723203] wlan0 (WE) : Wireless Event too big (314)
[  292.613960] wlan0: disassociating by local choice (reason=3)
[  292.666200] wlan0: deauthenticated
[  292.669224] wlan0: authenticate with AP 00:1d:7e:b4:7d:70
[  292.671617] wlan0: authenticate with AP 00:1d:7e:b4:7d:70
[  292.675956] wlan0: authenticated
[  292.675962] wlan0: associate with AP 00:1d:7e:b4:7d:70
[  292.679447] wlan0: RX ReassocResp from 00:1d:7e:b4:7d:70 (capab=0x431 status=0 aid=2)
[  292.679454] wlan0: associated
[  292.679525] wlan0 (WE) : Wireless Event too big (314)
[  295.673911] wlan0: deauthenticated
[  296.673000] wlan0: authenticate with AP 00:1d:7e:b4:7d:70
[  296.675664] wlan0: authenticated
[  296.675671] wlan0: associate with AP 00:1d:7e:b4:7d:70
[  296.679323] wlan0: RX ReassocResp from 00:1d:7e:b4:7d:70 (capab=0x431 status=0 aid=2)
[  296.679330] wlan0: associated
[  296.679401] wlan0 (WE) : Wireless Event too big (314)
[  299.677019] wlan0: deauthenticated

```

```

lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 [8086:27d6] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 01)
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 0a)
03:01.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 05)
03:01.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)
0b:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] (rev 02)

```

```


iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"2Octopos"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1D:7E:B4:7D:70   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=94/100  Signal level:-35 dBm  Noise level=-127 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



```

---

### Post by shift_00 on 2008-09-15
symptoms:

the light of the wifi got flashing and all the system just overall slowed very much, the network manager won't open and "manage wireless connections" won't open quickly, but when it does no networks detected .. so i thought i would reboot, and when i did, everything was gone, i had to go through the whole process again to get the flashy wifi .. when i turned off the system got back on track .. in terms of speed that is .. 

we are close aren't we ???

---

### Post by shift_00 on 2008-09-15
i think i should mention this, while building, a repetitive "clock skew detected, build might be incomplete" message kept coming out .. and building essentials i got it from synaptic rather than apt-get .. thanks

---

### Post by pytheas22 on 2008-09-15
Yes, you're a lot closer now--you have a wireless interface recognized, are able to see networks and apparently associate.  This is much better than before.  Unfortunately, however, there are still some errors mentioned by dmesg and I'm not sure what they mean, e.g.:
```

05.110942] wlan0: disassociating by local choice (reason=3)
[  205.522178] wlan0: no IPv6 routers present
[  204.546419] wlan0: deauthenticated
[  206.450914] wlan0: authenticate with AP 00:1d:7e:b4:7d:70
[  204.549976] wlan0: authenticate with AP 00:1d:7e:b4:7d:70
[  204.556376] wlan0: authenticated
[  204.556382] wlan0: associate with AP 00:1d:7e:b4:7d:70
[  204.565210] wlan0: RX ReassocResp from 00:1d:7e:b4:7d:70 (capab=0x431 status=0 aid=1)
[  204.565217] wlan0: associated
[  204.565288] wlan0 (WE) : Wireless Event too big (314)
[  207.562206] wlan0: deauthenticated
```

It sounds maybe like the router is rejecting you for some reason after you get associated.  I'll google some of this stuff and see what comes up.  In the meantime, please try turning off all encryption on your router, then run these commands:
```

sudo kill -9 $(ps -e | grep NetworkManager)
sudo iwconfig wlan0 mode managed essid "2Octopos"
sudo dhclient wlan0
```

If that works, you will get an IP address.  Do you?

EDIT: this [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/176602") looks relevant.  Was your network encrypted when you tried to connect?  They seem to think that the problem is related to WEP and/or WPA (but not WPA2).  There is a solution in that thread, but it involves installing Ubuntu updates, which you obviously can't do without any connection.  Please run the commands above to see if it gets you online with the router unsecured, then you can try downloading the patches and see if they solve the problem for good.

Also, I don't know if it's feasible, but if there's another wireless network somewhere that you could try connecting to, it would be good to know if that works, because it appears that the errors you're getting may be caused only by certain routers.

---

### Post by shift_00 on 2008-09-16
reporting from inside the dear ubuntu :) :guitar:

what happenned is that i got overwhelmed with everything that was so new to me, so i decided to go radical, reinstall, if not, download a gutsy, if not, cry by the wall .. 

i reinstalled, and it is working, the light is off though, but it is working, i couldn't care less about that stupid light, i'm online, and i am ready to begin my journey to one day become a linux expert like you guys, perhaps even one of the good guys "hackers" :P .. not crackers, i read the how-to :D 

thanks to everyone who helped .. thank you all .. :KS

---

### Post by pytheas22 on 2008-09-16
I'm glad it finally worked and that you can now spend some time enjoying Linux instead of fighting with it :)

Just for the benefit of anyone else who stumbles on this thread, though, how exactly did you solve the problem?  Did you reinstall Ubuntu Hardy 8.04 and everything worked, or was it installing Gutsy 7.10 that solved the problem?

---

### Post by shift_00 on 2008-09-16
nope just the same old hardy edition .. and you are true on the money sir, i am enjoying my experience ... :D thanks alot m8

---

### Post by adept_king on 2008-10-23
same exact problem here. 

the methods described above helped (i think) but i got more of the kind of results i was looking for from these two commands:

sudo dhclient wlan0

sudo iwlist scanning

i am trying to connect to a connection that brings you to a login page... by command line.  if only i knew how to see html on command line.

---

### Post by pytheas22 on 2008-10-23
> same exact problem here.

the methods described above helped (i think) but i got more of the kind of results i was looking for from these two commands:

sudo dhclient wlan0

sudo iwlist scanning

i am trying to connect to a connection that brings you to a login page... by command line. if only i knew how to see html on command line.

How far exactly have you gotten?  Have you gotten to the point where it says you're connected?  Having to log in via a web page shouldn't be a problem; in most cases you would just connect first as normal, then be redirected in your web browser to log in after the connection has been established.

---

### Post by adept_king on 2008-10-23
thanks very much for your reply by the way!

--

heres the elusive formula:

i first re-installed the 3945 driver.
then found a file called compatable old drivers or something.

then iwconfig shows lo, eth0, wmaster0 and wlan0

wlan0 is the one i wanted, it had info next to it.  the others do not, so ignoring them was my biggest lesson of the day.

next:

sudo dhclient wlan0   #(this command was AWESOME & my new obsession)

sudo iwlist scanning   #(to find what connection you want, take note of the name and the many coloned number.  very very useful.)

sudo iwconfig wlan0 essid "netwhatever"   #use to fix the name of the network if its wrong by some chance

sudo iwconfig wlan0 ap xxxxxx #replace the x's with the many coloned alphanumeric string found in iwlist scanning.

and if need be do this again:

sudo dhclient wlan0    #(you might have to replace wlan0 with your own special funny little word)

go ahead and ping google.com, hitting ctrl+c when you're tired of watching the results.

and better use 'sudo apt-get update' like crazy!

i came up for air and sudo apt-get install xmonad
...a little easier than one big scary bash window?

---

### Post by pytheas22 on 2008-10-23
Alright, so you're all set then?  The problem is solved?

Also, if you want to know how to make it connect automatically, take a look at [this post]("http://ubuntuforums.org/showpost.php?p=6022384&postcount=12") which I typed out for someone else a few minutes ago and see if you can figure out what to do...the process should basically be the same for you.  If you can't figure it out let me know.

---

### Post by jrecortel on 2008-10-23
[http://ubuntuforums.org/showthread.php?t=808516](http://ubuntuforums.org/showthread.php?t=808516)

---

### Post by steve789 on 2008-10-24
nope it didnt work on my inspiron 1525

---

### Post by Pagh on 2008-10-24
Have you just tried to install the driver from Intels home page - there is a linux version as well (thats the good thing about intel PRO wifi) here is a link for the official driver: [http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&Inst=Yes&ProductID=2259&DwnldID=10315&strOSs=39&OSFullname=Linux*&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&Inst=Yes&ProductID=2259&DwnldID=10315&strOSs=39&OSFullname=Linux*&lang=eng)

---

### Post by pytheas22 on 2008-10-24
> nope it didnt work on my inspiron 1525

What is the output of:
```

lspci -nn
lshw -C Network
sudo iwlist scan
modinfo iwl3945
dmesg | grep -e wlan -e iwl
```

---

### Post by caglar.dursun on 2008-11-11
I have the same problem on Asus F3S laptop.I did everything written on this page, but still not scanning networks

---

### Post by pytheas22 on 2008-11-11
> I have the same problem on Asus F3S laptop.I did everything written on this page, but still not scanning networks

Please post the output of:
```

lspci -nn
lshw -C Network
sudo iwlist scan
modinfo iwl3945
dmesg | grep -e wlan -e iwl
```

Also, which version of Ubuntu are you using (8.04, 8.10...)?

---

