---
title: "wireless help"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by madfirefighter on 2008-08-04
Having trouble with connecting to network. I can see them but am unable to connect. I am on a toughbook cf-50. Any help!!

 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:80:45:29:ab:77  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::280:45ff:fe29:ab77/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:54417 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30009 errors:0 dropped:0 overruns:1 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:80012908 (76.3 MB)  TX bytes:2470451 (2.3 MB)
          Interrupt:9 Base address:0x5000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2008 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2008 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100400 (98.0 KB)  TX bytes:100400 (98.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:02:78:e7:20:4f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1826 (1.7 KB)  TX bytes:398 (398.0 B)
          Interrupt:9 Base address:0x4800 

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b+  ESSID:""  Nickname:"acx v0.3.36"
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:22 Mb/s   Tx-Power=18 dBm   Sensitivity=176/255  
          Retry min limit:7   RTS thr:off   
          Power Management:off
          Link Quality=57/100  Signal level=41/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:6  Invalid misc:0   Missed beacon:0
```

 lsmod
Module                  Size  Used by
acx                    98692  0 
ipv6                  267780  8 
af_packet              23812  2 
radeon                124192  2 
drm                    82452  3 radeon
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
speedstep_ich           6288  0 
speedstep_lib           6532  1 speedstep_ich
cpufreq_ondemand        9740  1 
cpufreq_powersave       2688  0 
cpufreq_conservative     8712  0 
cpufreq_stats           7104  0 
freq_table              5536  3 speedstep_ich,cpufreq_ondemand,cpufreq_stats
cpufreq_userspace       5284  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
sbp2                   24072  0 
lp                     12324  0 
joydev                 13120  0 
pcmcia                 40876  0 
container               5632  0 
video                  19856  0 
output                  4736  1 video
snd_intel8x0           35356  2 
snd_ac97_codec        101028  1 snd_intel8x0
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
evdev                  13056  1 
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
snd_seq_dummy           4868  0 
yenta_socket           27276  3 
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
psmouse                40336  0 
snd_seq_oss            35584  0 
serio_raw               7940  0 
battery                14212  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
ac                      6916  0 
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
button                  9232  0 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
shpchp                 34452  0 
intel_agp              25492  1 
snd                    56996  15 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pci_hotplug            30880  1 shpchp
agpgart                34760  2 drm,intel_agp
soundcore               8800  1 snd
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
pcspkr                  4224  0 
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
pata_acpi               8320  0 
ata_generic             8324  0 
floppy                 59588  0 
ata_piix               19588  2 
ohci1394               33584  0 
8139cp                 24704  0 
libata                159344  3 pata_acpi,ata_generic,ata_piix
8139too                27520  0 
mii                     6400  2 8139cp,8139too
ieee1394               93752  2 sbp2,ohci1394
uhci_hcd               27024  0 
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
usbcore               146028  3 acx,uhci_hcd
thermal                16796  0 
processor              36872  2 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3
```

---

