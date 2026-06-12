---
title: "Setup MA111 USB Wireless adapter in Fiesty"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by dlstrife on 2008-07-05
I'm running Xubuntu 7.04. I've got the onboard LAN working but I'd like to get my Netgear MA111 USB wireless adapter working as well. I can't get the system to recognize it though. I have installed linux-wlan-ng and network-manager packages through Synaptics but can't tell if they're being used. The system is seeing the adapter as a USB device. Running lsusb recognizes the adapter:
"Bus 002 Device 002: ID 0846:4230 NetGear, Inc. MA111 WiFi"
But ifconfig only sees my onboard LAN (eth1) and the loopback (lo). The is no wireless connection listed in System->Network either. I've tried upgrading to 7.10 Gutsyy because the above listed packages are automatically installed in that distro I believe, but for some reason I get an "Authentication Failed" message after the files are downloaded. My system does not have an optical drive so I can't upgrade through the CD image either.
Any help resolving this through any method would be appreciated.

---

### Post by ryanhaigh on 2008-07-06
[This is]("https://help.ubuntu.com/community/WifiDocs/Device/NetgearMA111") what I used to get my MA111 working with Gutsy, can't guarantee it will work with fiesty but worth a shot.

Also just a note, are you using ```
ifconfig -a
``` by default ifconfig only shows active interfaces so if your wireless hasn't been ifupd then it won't be shown.

[https://help.ubuntu.com/community/WifiDocs/Device/NetgearMA111](https://help.ubuntu.com/community/WifiDocs/Device/NetgearMA111)

---

### Post by dlstrife on 2008-07-07
Thanks for the reply, but what did you use to get it working in Gutsy? Maybe I'm blind but I think you forgot to include that information... heh.

---

### Post by ryanhaigh on 2008-07-07
[https://help.ubuntu.com/community/WifiDocs/Device/NetgearMA111](https://help.ubuntu.com/community/WifiDocs/Device/NetgearMA111)

---

### Post by ryanhaigh on 2008-07-09
I found this in my google notebook, I don't know if it differs from what is provided on that page but thought it might be usefule

> MA111 Install

```
sudo apt-get install linux-wlan-ng
sudo nano /etc/network/interfaces
```
[QUOTE]    
iface wlan0 inet dhcp
    wireless_mode managed
    wireless_essid ESSID
   
    auto wlan0
```

sudo ifup wlan0 #to test
```[/QUOTE]

---

### Post by dlstrife on 2008-07-10
first, thanks for the help.
so i followed that, and i'm definitely using the v1 card, so it should be the prism chipset, but it's not picking it up. i had to manually load the drivers, and tried putting the alias call in the modprobe.d/wlan file, but it didn't work. when i run > sudo ifup wlan0 it fails saying > wlanctl-ng: No such device
Failed to enable the device, exitcode= 1 .
run-parts: /etc/network/if-pre-up.d/linux-wlan-ng-pre-up exited with return code 1
wlan0: ERROR while getting interface flags: No such device
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; No such device.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/wlanctl-ng:](http://www.isc.org/sw/dhcp/wlanctl-ng:) No such device
Failed to enable the device, exitcode= 1 .
run-parts: /etc/network/if-pre-up.d/linux-wlan-ng-pre-up exited with return code 1
wlan0: ERROR while getting interface flags: No such device
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; No such device.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.


SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.


suggestions?

---

### Post by ryanhaigh on 2008-07-11
Post the output of dmesg for the time when you plug in your device. Possibly also lsmod and ifconfig -a

---

### Post by dlstrife on 2008-07-11
dmesg output:
```
[11396.124000] usb 3-1: new full speed USB device using uhci_hcd and address 3
[11396.272000] usb 3-1: configuration #1 chosen from 1 choice
```
lsmod:
```
Module                  Size  Used by
nfsd                  218992  13 
exportfs                6912  1 nfsd
nfs                   241004  0 
lockd                  64904  3 nfsd,nfs
sunrpc                161340  10 nfsd,nfs,lockd
ipv6                  269088  14 
ppdev                  10116  0 
via                    44160  2 
drm                    81044  3 via
cpufreq_powersave       2688  0 
cpufreq_stats           7360  0 
cpufreq_userspace       5408  0 
cpufreq_ondemand        9228  0 
cpufreq_conservative     8200  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
tc1100_wmi              8068  0 
pcc_acpi               13184  0 
sony_acpi               6284  0 
dev_acpi               12292  0 
video                  16388  0 
battery                10756  0 
container               5248  0 
sbs                    15652  0 
button                  8720  0 
i2c_ec                  6016  1 sbs
dock                   10268  0 
ac                      6020  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
ipt_REJECT              5632  6 
xt_tcpudp               4224  6 
iptable_filter          3968  1 
ip_tables              13796  1 iptable_filter
x_tables               16388  3 ipt_REJECT,xt_tcpudp,ip_tables
af_packet              23816  2 
ieee80211              34760  0 
ieee80211_crypt         7040  1 ieee80211
sbp2                   23812  0 
lp                     12452  0 
snd_via82xx            29208  2 
gameport               16520  1 snd_via82xx
snd_ac97_codec         98464  1 snd_via82xx
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11272  2 snd_via82xx,snd_pcm
snd_mpu401_uart         9472  1 snd_via82xx
snd_seq_dummy           4740  0 
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
psmouse                38920  0 
serio_raw               7940  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
pcspkr                  4224  0 
i2c_viapro             10132  0 
i2c_core               22656  2 i2c_ec,i2c_viapro
via_ircc               27540  0 
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
irda                  201276  1 via_ircc
crc_ccitt               3072  1 irda
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  15 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
via_agp                11264  1 
soundcore               8672  1 snd
agpgart                35400  2 drm,via_agp
tsdev                   8768  0 
evdev                  11008  3 
reiserfs              247680  1 
ide_disk               17024  2 
generic                 5124  0 [permanent]
floppy                 59524  0 
via82cxxx              10372  0 [permanent]
via_rhine              25608  0 
mii                     6528  1 via_rhine
ata_generic             9092  0 
libata                125720  1 ata_generic
scsi_mod              142348  2 sbp2,libata
ehci_hcd               34188  0 
uhci_hcd               25360  0 
usbcore               134280  3 ehci_hcd,uhci_hcd
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

```
if i run this after running sudo modprobe prism2_usb the following entries are new
```

strife@wallpanel:~$ lsmod | grep prism
prism2_usb             74628  0 
p80211                 31884  1 prism2_usb
usbcore               134280  4 prism2_usb,ehci_hcd,uhci_hcd

```
ifconfig:
```
eth1      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: XXXX::XXX:XXXX:XXXX:XXXX/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19846 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16040 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21943155 (20.9 MiB)  TX bytes:2598008 (2.4 MiB)
          Interrupt:11 Base address:0xec00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:170 errors:0 dropped:0 overruns:0 frame:0
          TX packets:170 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10448 (10.2 KiB)  TX bytes:10448 (10.2 KiB)

```
(addresses X'd by me. they show up correctly)

---

### Post by dlstrife on 2008-07-11
ok, still not working, but i upgraded the system to 7.10 since most of the resources i've come across claim this is easier in gutsy. i don't know why it let me now and not before when i was getting "authentication failed", but its up now. here's a new posting of those calls:

dmesg:
```
[ 4774.940000] usb 2-1: new full speed USB device using uhci_hcd and address 3
[ 4775.088000] usb 2-1: configuration #1 chosen from 1 choice

```
lsmod:
```

Module                  Size  Used by
ipv6                  273892  14 
nfsd                  221040  13 
exportfs                7040  1 nfsd
lockd                  67592  2 nfsd
sunrpc                172412  8 nfsd,lockd
ppdev                  10244  0 
via                    43904  2 
drm                    83348  3 via
cpufreq_powersave       2688  0 
cpufreq_stats           7232  0 
cpufreq_userspace       5280  0 
cpufreq_ondemand        9612  0 
cpufreq_conservative     8072  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
video                  18060  0 
container               5504  0 
sbs                    19592  0 
button                  8976  0 
dock                   10656  0 
ac                      6148  0 
battery                11012  0 
ipt_REJECT              5760  6 
xt_tcpudp               4224  6 
iptable_filter          3968  1 
ip_tables              13924  1 iptable_filter
x_tables               16260  3 ipt_REJECT,xt_tcpudp,ip_tables
af_packet              24840  2 
prism2_usb             74756  0 
p80211                 33036  1 prism2_usb
sbp2                   24072  0 
lp                     12580  0 
snd_via82xx            29336  2 
gameport               16776  1 snd_via82xx
snd_ac97_codec        100644  1 snd_via82xx
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11400  2 snd_via82xx,snd_pcm
snd_mpu401_uart         9600  1 snd_via82xx
parport_pc             37412  1 
snd_seq_dummy           4740  0 
parport                37448  3 ppdev,lp,parport_pc
psmouse                39952  0 
serio_raw               8068  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
pcspkr                  4224  0 
snd_rawmidi            25728  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
vt8623fb               18560  0 
svgalib                10624  1 vt8623fb
vgastate               11008  1 vt8623fb
snd                    54660  15 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_viapro             10004  0 
i2c_core               26112  1 i2c_viapro
via_ircc               27668  0 
soundcore               8800  1 snd
irda                  202300  1 via_ircc
crc_ccitt               3072  1 irda
via_agp                11264  1 
agpgart                35016  2 drm,via_agp
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
evdev                  11136  3 
reiserfs              248704  1 
ide_disk               18560  2 
floppy                 60004  0 
via82cxxx              10372  0 [permanent]
ide_core              116804  2 ide_disk,via82cxxx
via_rhine              25992  0 
mii                     6528  1 via_rhine
ata_generic             8452  0 
libata                125168  1 ata_generic
scsi_mod              147084  2 sbp2,libata
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  4 prism2_usb,ehci_hcd,uhci_hcd
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor

```
lsmod after "sudo modprobe prism2_usb":
```

Module                  Size  Used by
ipv6                  273892  14 
nfsd                  221040  13 
exportfs                7040  1 nfsd
lockd                  67592  2 nfsd
sunrpc                172412  8 nfsd,lockd
ppdev                  10244  0 
via                    43904  2 
drm                    83348  3 via
cpufreq_powersave       2688  0 
cpufreq_stats           7232  0 
cpufreq_userspace       5280  0 
cpufreq_ondemand        9612  0 
cpufreq_conservative     8072  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
video                  18060  0 
container               5504  0 
sbs                    19592  0 
button                  8976  0 
dock                   10656  0 
ac                      6148  0 
battery                11012  0 
ipt_REJECT              5760  6 
xt_tcpudp               4224  6 
iptable_filter          3968  1 
ip_tables              13924  1 iptable_filter
x_tables               16260  3 ipt_REJECT,xt_tcpudp,ip_tables
af_packet              24840  2 
prism2_usb             74756  0 
p80211                 33036  1 prism2_usb
sbp2                   24072  0 
lp                     12580  0 
snd_via82xx            29336  2 
gameport               16776  1 snd_via82xx
snd_ac97_codec        100644  1 snd_via82xx
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11400  2 snd_via82xx,snd_pcm
snd_mpu401_uart         9600  1 snd_via82xx
parport_pc             37412  1 
snd_seq_dummy           4740  0 
parport                37448  3 ppdev,lp,parport_pc
psmouse                39952  0 
serio_raw               8068  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
pcspkr                  4224  0 
snd_rawmidi            25728  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
vt8623fb               18560  0 
svgalib                10624  1 vt8623fb
vgastate               11008  1 vt8623fb
snd                    54660  15 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_viapro             10004  0 
i2c_core               26112  1 i2c_viapro
via_ircc               27668  0 
soundcore               8800  1 snd
irda                  202300  1 via_ircc
crc_ccitt               3072  1 irda
via_agp                11264  1 
agpgart                35016  2 drm,via_agp
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
evdev                  11136  3 
reiserfs              248704  1 
ide_disk               18560  2 
floppy                 60004  0 
via82cxxx              10372  0 [permanent]
ide_core              116804  2 ide_disk,via82cxxx
via_rhine              25992  0 
mii                     6528  1 via_rhine
ata_generic             8452  0 
libata                125168  1 ata_generic
scsi_mod              147084  2 sbp2,libata
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  4 prism2_usb,ehci_hcd,uhci_hcd
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor

```
ifconfig:
```

eth1      Link encap:Ethernet  HWaddr 00:40:63:D4:AE:DD  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:63ff:fed4:aedd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8891 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4876 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12112952 (11.5 MB)  TX bytes:476971 (465.7 KB)
          Interrupt:11 Base address:0xec00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5176 (5.0 KB)  TX bytes:5176 (5.0 KB)

```

---

### Post by ryanhaigh on 2008-07-16
unfortunately I don't know how much more help I can be, I had my adaptor working on my gutsy install with the instructions I posted previously. The only thing I can think of is that I did a fresh install rather than upgrade.

---

### Post by dlstrife on 2008-07-20
well, thanks for all the help. anyone else out there got a suggestion?

---

