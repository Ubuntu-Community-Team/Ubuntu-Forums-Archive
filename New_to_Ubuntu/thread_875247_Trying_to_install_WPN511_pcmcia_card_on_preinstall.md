---
title: "Trying to install WPN511 pcmcia card on preinstalled 8.04 for x86"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by surnj1 on 2008-07-30
Hi,

I am trying to add a wireless adapter (Netgear WPN511 PCMCIA with Atheros chipset) to an already installed Ubuntu 8.04 OS on a Dell inspiron 2650.

I installed a madwifi driver from following url before inserting the card:

[http://packages.ubuntu.com/hardy/i386/madwifi-tools/download](http://packages.ubuntu.com/hardy/i386/madwifi-tools/download)

But there is no sign that Ubuntu has detected the card, I restarted the system without any success. 

Please guide me,, what should I do next?

Thx,

---

### Post by caljohnsmith on 2008-07-30
Probably a good place to start would be to make sure Ubuntu sees your new wireless card OK, and also to see what other modules are currently loaded (sometimes there can be interfering modules). Please post the output of:
```
sudo lshw -C network
lsmod
```

---

### Post by surnj1 on 2008-09-01
bharat@bharat-laptop:/$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 78
       serial: 00:08:74:e6:5a:e7
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=192.168.2.110 latency=80 link=yes maxlatency=10 mingnt=10 module=3c59x multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0 maxlatency=28 mingnt=10
bharat@bharat-laptop:/$ 
bharat@bharat-laptop:/$ lsmod
Module                  Size  Used by
af_packet              23812  2 
ipv6                  267780  8 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
speedstep_ich           6288  0 
speedstep_lib           6532  1 speedstep_ich
cpufreq_ondemand        9740  1 
cpufreq_userspace       5284  0 
cpufreq_conservative     8712  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7104  0 
freq_table              5536  3 speedstep_ich,cpufreq_ondemand,cpufreq_stats
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
lp                     12324  0 
joydev                 13120  0 
pcmcia                 40876  0 
snd_intel8x0           35356  3 
snd_ac97_codec        101028  1 snd_intel8x0
evdev                  13056  7 
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
serio_raw               7940  0 
snd_seq_dummy           4868  0 
battery                14212  0 
container               5632  0 
video                  19856  0 
output                  4736  1 video
ac                      6916  0 
dcdbas                  9504  0 
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
snd_seq_oss            35584  0 
yenta_socket           27276  2 
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
psmouse                40336  0 
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcspkr                  4224  0 
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
button                  9232  0 
snd                    56996  17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
intel_agp              25492  1 
agpgart                34760  1 intel_agp
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  2 
pata_acpi               8320  0 
ata_generic             8324  0 
floppy                 59588  0 
ata_piix               19588  1 
libata                159344  3 pata_acpi,ata_generic,ata_piix
uhci_hcd               27024  0 
scsi_mod              151436  4 sg,sr_mod,sd_mod,libata
3c59x                  46376  0 
mii                     6400  1 3c59x
usbcore               146028  2 uhci_hcd
thermal                16796  0 
processor              36872  2 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  1 
bharat@bharat-laptop:/$

---

