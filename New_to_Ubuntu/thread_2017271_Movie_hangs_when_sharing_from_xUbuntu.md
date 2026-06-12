---
title: "Movie hangs when sharing from xUbuntu"
date: 2012-07-05
forum: New to Ubuntu
---

### Post by cr1st1 on 2012-07-05
Hello,[B]

i have:[/B]
- WD Live - firmware: 1.05.04_V-WDLXTV-Live-0.5.1.1 [flash]
- a computer with 2 operating systems : windows xp and xUbuntu 12.4

**connections:**
- WD Live is connected via cable to the wireless router
- the computer is connected to the router via this wireless dongle : [http://www.amazon.com/D-Link-DWA-140-RANGEBOSTER-USB-ADAPTER/dp/B000PE8ONG](http://www.amazon.com/D-Link-DWA-140-RANGEBOSTER-USB-ADAPTER/dp/B000PE8ONG)

[COLOR=#BF0000]**the problem:**[/COLOR]
when i share the folder from windows XP everything works well
[COLOR=#BF0000][B]but when i share THE SAME folder with the same movie from xUbuntu - i can see the share on WD Live - i can play the movie _BUT after 30 seconds the movie hangs _
The xUbuntu share is NFS[/B][/COLOR]

/etc/exports has:
/home/x/Documents 192.168.1.3(ro,no_subtree_check) 
(192.168.1.3 is the IP of WD LIve)

on WD Live - File Sharing: Network Mounts - i have :
xmount 192.168.1.2:/home/x/Documents share nfs

[COLOR=SeaGreen]**Note: if i connect my computer to the router with a cable everything works very well.  So it seems that the problem is related to the wireless dongle ...**[/COLOR]

[B][COLOR=Blue]Does anybody have an idea how to solve this problem ?[/COLOR]

[/B]the output of media info :
```

$ mediainfo ~/Documents/test.mkv
General
Unique ID                                : 11096087495274303023292389139878184408 (0x859075A03D2FD11A2F1FDDCD5FB05D8)
Complete name                            : /home/x/Documents/test.mkv
Format                                   : Matroska
Format version                           : Version 2
File size                                : 4.35 GiB
Duration                                 : 1h 44mn
Overall bit rate                         : 5 963 Kbps
Encoded date                             : UTC 2012-06-28 17:32:25
Writing application                      : mkvmerge v5.1.0 ('And so it goes') built on Feb  1 2012 11:31:23
Writing library                          : libebml v1.2.2 + libmatroska v1.3.0

Video
ID                                       : 1
Format                                   : AVC
Format/Info                              : Advanced Video Codec
Format profile                           : High@L4.1
Format settings, CABAC                   : Yes
Format settings, ReFrames                : 5 frames
Muxing mode                              : Header stripping
Codec ID                                 : V_MPEG4/ISO/AVC
Duration                                 : 1h 44mn
Bit rate                                 : 4 485 Kbps
Width                                    : 1 280 pixels
Height                                   : 544 pixels
Display aspect ratio                     : 2.35:1
Frame rate                               : 23.976 fps
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Progressive
Bits/(Pixel*Frame)                       : 0.269
Stream size                              : 3.16 GiB (73%)
Writing library                          : x264 core 125 r2200 999b753
Encoding  settings                        : cabac=1 / ref=5 / deblock=1:0:0 /  analyse=0x3:0x113 / me=umh / subme=7 / psy=1 / psy_rd=1.00:0.00 /  mixed_ref=1 / me_range=16 / chroma_me=1 / trellis=1 / 8x8dct=1 / cqm=0 /  deadzone=21,11 / fast_pskip=0 / chroma_qp_offset=-2 / threads=18 /  lookahead_threads=3 / sliced_threads=0 / nr=0 / decimate=1 /  interlaced=0 / bluray_compat=0 / constrained_intra=0 / bframes=3 /  b_pyramid=2 / b_adapt=1 / b_bias=0 / direct=1 / weightb=1 / open_gop=0 /  weightp=2 / keyint=250 / keyint_min=23 / scenecut=40 / intra_refresh=0 /  rc_lookahead=40 / rc=2pass / mbtree=1 / bitrate=4485 / ratetol=1.0 /  qcomp=0.60 / qpmin=0 / qpmax=69 / qpstep=4 / cplxblur=20.0 / qblur=0.5 /  ip_ratio=1.40 / aq=1:1.00
Language                                 : English
Default                                  : Yes
Forced                                   : No

Audio
ID                                       : 2
Format                                   : DTS
Format/Info                              : Digital Theater Systems
Muxing mode                              : Header stripping
Codec ID                                 : A_DTS
Duration                                 : 1h 44mn
Bit rate mode                            : Constant
Bit rate                                 : 1 510 Kbps
Channel(s)                               : 6 channels
Channel positions                        : Front: L C R, Side: L R, LFE
Sampling rate                            : 48.0 KHz
Bit depth                                : 24 bits
Compression mode                         : Lossy
Stream size                              : 1.10 GiB (25%)
Language                                 : English
Default                                  : Yes
Forced                                   : No

Text
ID                                       : 3
Format                                   : UTF-8
Codec ID                                 : S_TEXT/UTF8
Codec ID/Info                            : UTF-8 Plain Text
Language                                 : English
Default                                  : No
Forced                                   : No
```

---

### Post by Merrattic on 2012-07-05
Need some cli output on the wireless dongle and driver? Did you have to install a driver or was it automagically in the kernel? What happens if you try to watch a movie from another PC (not through the WD Live)? Also it may be nfs causing the problem so why not try a samba server on the PC and see if that works OK seeing as it works OK from XP?

---

### Post by afixane on 2012-07-05
Try to play it with VLC. I'm not very know about this subject, but usually VLC can Play anything, even broken video. Please be aware that VLC is not very lightweight.

---

### Post by cr1st1 on 2012-07-05
> Did you have to  install a driver or was it automagically in the kernel? i haven't installed any driver - so i use the default driver

> What happens if  you try to watch a movie from another PC (not through the WD Live)? 
I do not need another PC- the movie plays very well with "Parole" player

> Also  it may be nfs causing the problem so why not try a samba server on the  PC and see if that works OK seeing as it works OK from XP?Samba share works even worse

> Try to play it with VLC. I'm not very know about this subject, but  usually VLC can Play anything, even broken video. Please be aware that  VLC is not very lightweight.I want to use my media player and watch the movie on TV
[B]

[COLOR=Blue]I think the problem is related to the parameters of the wireless dongle... but i do not know how to see them or change them.

The movie hangs after 22 seconds.[/COLOR][/B]

---

### Post by Merrattic on 2012-07-05
Please provide output of:
```
ifconfig -a
```
```
iwconfig
```
```
sudo lshw -c network
```
```
lsmod
```

---

### Post by cr1st1 on 2012-07-05
```
$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:855 errors:0 dropped:0 overruns:0 frame:0
          TX packets:855 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100497 (100.4 KB)  TX bytes:100497 (100.4 KB)

wlan0     Link encap:Ethernet  HWaddr  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: /64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5750 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4634 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5825280 (5.8 MB)  TX bytes:1009715 (1.0 MB)
``````
$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"NET1"  
          Mode:Managed  Frequency:2.437 GHz  Access Point:    
          Bit Rate=135 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=47/70  Signal level=-63 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:153  Invalid misc:141   Missed beacon:0

eth0      no wireless extensions.
``````
$ sudo lshw -c network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:e800(size=256) memory:f8fff000-f8ffffff memory:f8fe0000-f8feffff memory:febf0000-febfffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:5
       logical name: wlan0
       serial:
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=3.2.0-26-generic firmware=0.29 ip=192.168.1.2 link=yes multicast=yes wireless=IEEE 802.11bgn
``````
lsmod
Module                  Size  Used by
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             13328  0 
vboxnetflt             27211  0 
vboxdrv               252189  3 vboxpci,vboxnetadp,vboxnetflt
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
nfsd                  229850  13 
binfmt_misc            17292  1 
nfs                   307297  0 
lockd                  78804  2 nfsd,nfs
fscache                50642  1 nfs
auth_rpcgss            39597  2 nfsd,nfs
nfs_acl                12771  2 nfsd,nfs
sunrpc                205647  19 nfsd,nfs,lockd,auth_rpcgss,nfs_acl
vesafb                 13516  1 
arc4                   12473  2 
usbhid                 41906  0 
hid                    77367  1 usbhid
snd_hda_codec_realtek   174055  1 
rt2800usb              22300  0 
rt2800lib              53264  1 rt2800usb
crc_ccitt              12595  1 rt2800lib
rt2x00usb              20061  1 rt2800usb
rt2x00lib              48858  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              436455  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              178679  2 rt2x00lib,mac80211
nvidia              10958194  30 
snd_hda_intel          32765  4 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
ppdev                  12849  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             32114  1 
asus_atk0110           17742  0 
snd                    62064  17 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13077  0 
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
uas                    17828  0 
usb_storage            39646  1 
r8169                  56321  0
```

---

### Post by SeijiSensei on 2012-07-05
See if you can expand the NFS read buffer size on the WDLive box to something like 32768.  I'd also add "async" to the option list in /etc/exports.

Just to make sure, the Matroska file isn't using "ordered chapters" is it?

---

### Post by cr1st1 on 2012-07-06
From Windows XP the movie plays well with the same WDLive and the same movie. 
I expect xUbuntu to work too so_ i will not try _to modify the movie or WDLive settings.

I have tried "async" in  /etc/exports but i get the same result - the movie stops playing after 22 seconds.

---

### Post by Merrattic on 2012-07-06
Just to confirm, check device is supported by the driver:
```
lsusb
``` then look at: [http://wiki.debian.org/rt2800usb](http://wiki.debian.org/rt2800usb)

I had allsorts of trouble with my r8169 built in wireless, and gave up in the end and plugged in an ethernet cable. (Then wired the house! - but you may not want to do this ;))

Unless things have changed I remember nfs being very flaky over wireless, for a variety of reasons, may be worth trying samba/cifs again if you don't want to fiddle with the WD Live settings on nfs.([http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534))

And,.....um, is it just one movie you are having trouble with, or all movies, and all containers (avi/mpg/mkv/mp4 etc) ?

Also useful link? [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch29_:_Remote_Disk_Access_with_NFS#Troubleshooting_NFS](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch29_:_Remote_Disk_Access_with_NFS#Troubleshooting_NFS)

---

### Post by cr1st1 on 2012-07-16
First of all thank you all for you help

[COLOR=Green]**I have solved my problem and this is how i did it :**[/COLOR]

I have downloaded the driver from this site : [http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501)

and then ....

```
$ sudo modprobe -r rt2800usb
$ sudo leafpad /etc/modprobe.d/blacklist.conf
```and added these lines at the end of the file:
blacklist rt2800usb
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib

```
$ cd ~/Download/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux/
$ leafpad config.mk
```and changed these lines from n to y

HAS_WPA_SUPPLICANT=y
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

```
$ cd ~/Download/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/
$ sudo make && sudo make install
```After i have made these changes -> Reboot

[FONT=Arial Black][B][COLOR=DarkOrange][FONT=Verdana][COLOR=Green]Now it works VERY WELL even with Samba share.
[/COLOR][/FONT][/COLOR][/B][/FONT]

---

### Post by Merrattic on 2012-07-16
Great ! :D

---

