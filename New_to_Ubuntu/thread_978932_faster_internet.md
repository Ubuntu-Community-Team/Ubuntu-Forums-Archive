---
title: "faster internet?"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by phantomjoker on 2008-11-11
I just moved house, and used to have wired internet - now have wireless. My wireless card is working fine and i have a connection - it's just unbelievably slow... we should be getting a 8mb download speed, but i dont get more than 25kb/s

any ideas?

---

### Post by CLomax on 2008-11-11
Are you with Pipex by any chance?

---

### Post by gletob on 2008-11-11
Are wired computers running at a higher speed?

---

### Post by phantomjoker on 2008-11-11
pipex? no - if that's an isp - mine is sky, if not then please explain.

---

### Post by phantomjoker on 2008-11-11
the wired system was working at 16mb/s, my new connection is ment to be 8mb/s - but im not getting that - in fact if i click connection information it says 1mb

---

### Post by gletob on 2008-11-11
Ok thats your problem your modems getting 8 Mbps but your wireless connection rate is only 1 Mbps.  The connection rate in network manager is the rate at which data is tranfered from your router to your PC could you please post the output of the commands
```
lspci
```
```
lsusb
```

---

### Post by phantomjoker on 2008-11-11
```
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 12)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 12)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 12)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 12)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]
02:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:0a.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
02:0a.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
02:0a.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63)
02:0b.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)

```

```
Bus 005 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 005 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 090c:1000 Feiya Technology Corp. Memory Bar
Bus 002 Device 002: ID 8086:1120 Intel Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

---

### Post by gletob on 2008-11-11
Did your wifi card "work" right after you installed ubuntu or did you use NDISWRAPPER?

---

### Post by phantomjoker on 2008-11-11
im prety sure i used ndiswrapper.... i installed the card about 6 months ago so not sure.

---

### Post by handydan918 on 2008-11-11
> **phantomjoker said:**
> im prety sure i used ndiswrapper.... i installed the card about 6 months ago so not sure.

Well, let's find out .
Output of ```
lsmod
```if you please.

---

### Post by phantomjoker on 2008-11-11
```
mckenzie@ubuntu:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           4992  1 
nls_cp437               6656  1 
vfat                   14464  1 
fat                    54556  1 vfat
af_packet              23812  4 
binfmt_misc            12808  1 
radeon                124192  2 
drm                    82452  3 radeon
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
rfkill_input            5760  0 
ipv6                  267780  12 
ppdev                  10372  0 
speedstep_lib           6532  0 
cpufreq_conservative     8712  0 
cpufreq_stats           7104  0 
cpufreq_userspace       5284  0 
cpufreq_ondemand        9740  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       2688  0 
video                  19856  0 
output                  4736  1 video
dock                   11280  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
container               5632  0 
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0 
ndiswrapper           192920  0 
lp                     12324  0 
loop                   18948  0 
snd_cmipci             38528  5 
gameport               16008  1 snd_cmipci
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_cmipci,snd_pcm_oss
snd_page_alloc         11400  1 snd_pcm
snd_opl3_lib           12928  1 snd_cmipci
snd_hwdep              10500  1 snd_opl3_lib
snd_mpu401_uart         9728  1 snd_cmipci
arc4                    2944  2 
ecb                     4480  2 
evdev                  13056  4 
blkcipher               8324  1 ecb
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
snd_seq_dummy           4868  0 
serio_raw               7940  0 
psmouse                40336  0 
b43                   144548  0 
rfkill                  8596  3 rfkill_input,b43
mac80211              165652  1 b43
cfg80211               15112  1 mac80211
led_class               6020  1 b43
input_polldev           5896  1 b43
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  4 snd_pcm,snd_opl3_lib,snd_seq
snd_seq_device          9612  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  21 snd_cmipci,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcspkr                  4224  0 
soundcore               8800  1 snd
button                  9232  0 
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
intel_agp              25492  1 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
agpgart                34760  2 drm,intel_agp
ext3                  136840  3 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
usb_storage            73664  1 
libusual               19108  1 usb_storage
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  7 
ata_piix               19588  4 
ata_generic             8324  0 
floppy                 59588  0 
pata_acpi               8320  0 
ehci_hcd               37900  0 
uhci_hcd               27024  0 
libata                159344  3 ata_piix,ata_generic,pata_acpi
ssb                    34308  1 b43
usbcore               146412  6 ndiswrapper,usb_storage,libusual,ehci_hcd,uhci_hcd
scsi_mod              151436  5 usb_storage,sg,sr_mod,sd_mod,libata
thermal                16796  0 
processor              37384  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 

```

---

### Post by phantomjoker on 2008-11-11
```
mckenzie@ubuntu:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           4992  1 
nls_cp437               6656  1 
vfat                   14464  1 
fat                    54556  1 vfat
af_packet              23812  4 
binfmt_misc            12808  1 
radeon                124192  2 
drm                    82452  3 radeon
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
rfkill_input            5760  0 
ipv6                  267780  12 
ppdev                  10372  0 
speedstep_lib           6532  0 
cpufreq_conservative     8712  0 
cpufreq_stats           7104  0 
cpufreq_userspace       5284  0 
cpufreq_ondemand        9740  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       2688  0 
video                  19856  0 
output                  4736  1 video
dock                   11280  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
container               5632  0 
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0 
ndiswrapper           192920  0 
lp                     12324  0 
loop                   18948  0 
snd_cmipci             38528  5 
gameport               16008  1 snd_cmipci
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_cmipci,snd_pcm_oss
snd_page_alloc         11400  1 snd_pcm
snd_opl3_lib           12928  1 snd_cmipci
snd_hwdep              10500  1 snd_opl3_lib
snd_mpu401_uart         9728  1 snd_cmipci
arc4                    2944  2 
ecb                     4480  2 
evdev                  13056  4 
blkcipher               8324  1 ecb
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
snd_seq_dummy           4868  0 
serio_raw               7940  0 
psmouse                40336  0 
b43                   144548  0 
rfkill                  8596  3 rfkill_input,b43
mac80211              165652  1 b43
cfg80211               15112  1 mac80211
led_class               6020  1 b43
input_polldev           5896  1 b43
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  4 snd_pcm,snd_opl3_lib,snd_seq
snd_seq_device          9612  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  21 snd_cmipci,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcspkr                  4224  0 
soundcore               8800  1 snd
button                  9232  0 
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
intel_agp              25492  1 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
agpgart                34760  2 drm,intel_agp
ext3                  136840  3 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
usb_storage            73664  1 
libusual               19108  1 usb_storage
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  7 
ata_piix               19588  4 
ata_generic             8324  0 
floppy                 59588  0 
pata_acpi               8320  0 
ehci_hcd               37900  0 
uhci_hcd               27024  0 
libata                159344  3 ata_piix,ata_generic,pata_acpi
ssb                    34308  1 b43
usbcore               146412  6 ndiswrapper,usb_storage,libusual,ehci_hcd,uhci_hcd
scsi_mod              151436  5 usb_storage,sg,sr_mod,sd_mod,libata
thermal                16796  0 
processor              37384  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 

```

---

### Post by phantomjoker on 2008-11-12
so is there anything i can do?

---

### Post by tuxulin on 2008-11-12
what you could do is talk to sky...
a few of my friends moaned about connection speed
that it is slow. maybe its teething problems with 
new connections (accounts).

when i switched to another cable company the same thing happened
to me, first couple of weeks the speed was fluctuating then
it settle down.

dont ask me why but these things can happen 

Good luck
Tux

---

