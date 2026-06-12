---
title: "[SOLVED] USB Webcam worked  hardy, does not work under Intrepid"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by eatingganesh on 2008-11-01
My previously fine webcam no longer works since I upgraded. It worked under Hardy just fine and did so automatically. I had fiddled to death trying to get it to work under Intrepid.

When I run lsusb I get:

> Bus 003 Device 002: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 WebCam


But under Camorama I get: > could not connect to video device (/dev/video0

Under Cheese I get: > no camera found and alot of bars and fuzz.

No propietary drivers are installed. And they weren't needed under Hardy.

I am totally stumped. Ideas?

---

### Post by eatingganesh on 2008-11-01
a little more info from lsmod | grep video:

> video                  25104  0 
output                 11008  1 video
videodev               41344  1 zc0301
v4l1_compat            22404  1 videodev


---

### Post by Dropbear on 2008-11-01
Try this

Plug your camera in then open a terminal and run

```
sudo chmod a+rw /dev/video0
```

---

### Post by eatingganesh on 2008-11-01
Thanks for the reply bear... love the koala!

Ran command as suggested and got :
> sudo chmod a+rw /dev/video0

---

### Post by phoenix_abhi on 2008-12-12
> **Dropbear said:**
> Try this

Plug your camera in then open a terminal and run

```
sudo chmod a+rw /dev/video0
```

Not worked for me :confused:

> abhi@phoenixabhi:~$ sudo chmod a+rw /dev/video0
[sudo] password for abhi: 
chmod: cannot access `/dev/video0': No such file or directory
abhi@phoenixabhi:~$ lsmod | grep video
video                  28948  0 
output                 11776  1 video


> abhi@phoenixabhi:~$ lsusb
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 WebCam
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0a5c:2035 Broadcom Corp. BCM2035 Bluetooth
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


> abhi@phoenixabhi:~$ lsmod
Module                  Size  Used by
ipv6                  314312  10 
af_packet              29568  2 
binfmt_misc            18700  1 
i915                   44544  2 
drm                   110304  3 i915
rfcomm                 51104  2 
bridge                 64544  0 
stp                    11268  1 bridge
bnep                   23168  2 
sco                    20612  2 
l2cap                  33280  16 rfcomm,bnep
ppdev                  16904  0 
acpi_cpufreq           16400  0 
cpufreq_userspace      12420  0 
cpufreq_stats          14468  0 
cpufreq_powersave      10368  0 
cpufreq_ondemand       16400  2 
freq_table             13568  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative    16392  0 
wmi                    15808  0 
video                  28948  0 
output                 11776  1 video
sbs                    22288  0 
sbshc                  14592  1 sbs
pci_slot               13704  0 
container              12288  0 
battery                21128  0 
iptable_filter         11520  0 
ip_tables              28176  1 iptable_filter
x_tables               31752  1 ip_tables
ac                     13448  0 
lp                     19588  0 
snd_hda_intel         489264  2 
snd_pcm_oss            52608  0 
snd_mixer_oss          25088  1 snd_pcm_oss
evdev                  20512  6 
psmouse                51612  0 
snd_pcm                99208  2 snd_hda_intel,snd_pcm_oss
serio_raw              14596  0 
snd_seq_dummy          11524  0 
snd_seq_oss            42368  0 
btusb                  21912  3 
pcspkr                 11136  0 
snd_seq_midi           15872  0 
bluetooth              70820  11 rfcomm,bnep,sco,l2cap,btusb
snd_rawmidi            34176  1 snd_seq_midi
snd_seq_midi_event     16768  2 snd_seq_oss,snd_seq_midi
snd_seq                67168  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34320  2 snd_pcm,snd_seq
snd_seq_device         16404  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             44200  1 
parport                50096  3 ppdev,lp,parport_pc
zc0301                 60804  0 
compat_ioctl32         18176  1 zc0301
videodev               46720  2 zc0301,compat_ioctl32
snd                    79432  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
v4l1_compat            24580  1 videodev
soundcore              16800  1 snd
snd_page_alloc         17680  2 snd_hda_intel,snd_pcm
button                 15904  0 
intel_agp              39280  1 
shpchp                 42140  0 
pci_hotplug            39472  1 shpchp
iTCO_wdt               21072  0 
iTCO_vendor_support    12420  1 iTCO_wdt
jfs                   199248  2 
sr_mod                 24644  0 
cdrom                  47784  1 sr_mod
sd_mod                 45864  5 
crc_t10dif             10240  1 sd_mod
sg                     45408  0 
pata_acpi              13568  0 
ata_piix               29444  4 
ata_generic            14212  0 
libata                200160  3 pata_acpi,ata_piix,ata_generic
scsi_mod              183160  4 sr_mod,sd_mod,sg,libata
dock                   18464  1 libata
r8169                  40196  0 
ehci_hcd               48908  0 
uhci_hcd               34336  0 
usbcore               175376  5 btusb,zc0301,ehci_hcd,uhci_hcd
thermal                27424  0 
processor              47800  2 acpi_cpufreq,thermal
fan                    13576  0 
fbcon                  51200  0 
tileblit               11264  1 fbcon
font                   17152  1 fbcon
bitblit                14592  1 fbcon
softcursor             10496  1 bitblit
fuse                   68288  5 


This webcam working under Vista. Please someone help. I have Intrepid x64

---

### Post by phoenix_abhi on 2008-12-12
No reply ????????

---

