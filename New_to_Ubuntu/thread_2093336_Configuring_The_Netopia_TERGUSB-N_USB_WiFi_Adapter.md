---
title: "Configuring The Netopia TER/GUSB-N USB WiFi Adapter"
date: 2012-12-10
forum: New to Ubuntu
---

### Post by hugoBOSS81 on 2012-12-10
Okay, so this is my NEW post in regards to this adapter since I apparently posted in an old [post]("http://ubuntuforums.org/showthread.php?p=12397578&posted=1#post12397578") and got told to make my own.

I've been having some issues with this little USB adapter recently since I installed Ubuntu 12.04 precise kernel 2.3 i believe (i got it from the official Ubuntu repo's. Well i decided to update some stuff and try to see if i'd get some better stability using the 3.4.xxx-generic kernel, and it worked to my delight. except when i had to go through the trouble of getting GPU acceleration working with built-in NVIDIA hardware (but I got it working after removing all Nouveou/NVIDIA drivers completely via purge & tty), then I rebooted, installed the proprietary Linux NVIDIA driver 304.64 from their site and bingo, issue solved. then came the WiFi adapter from Netopia...this worked fine in the clean install for 12.04 precise but apparently kernel 3.4 didn't have it included or it was broke upon the kernel upgrade or my meddling in many setup afterwards. Point is, after many forum/google searches i found this [thread]("http://http://ubuntuforums.org/showthread.php?p=12397578&posted=1#post12397578") which got my adapter working but now it won't connect even though my network has no password (i know the security issue, i don't have neighbors close enough to worry about though) and my system sees it as a hidden network now and it wont establish a connection even though it did right after i had finished the mentioned thread instructions.

So I've kept doing some troubleshooting and have reached this point:

```
lsusb
```
Bus 001 Device 002: ID 148f:9021 Ralink Technology, Corp. RT2501USB Wireless Adapter
Bus 001 Device 003: ID 05e3:0702 Genesys Logic, Inc. USB 2.0 IDE Adapter [GL811E]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:13:d3:e2:c1:81  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:5 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:47126 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47126 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2687602 (2.6 MB)  TX bytes:2687602 (2.6 MB)

wlan0     Link encap:Ethernet  HWaddr 00:d0:41:c0:b7:39  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
ifconfig wlan0 up
```

```
iwconfig
```
wlan0     IEEE 802.11g  ESSID: off/any  
          Mode:Auto  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=-121 dBm  
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.

```
ifconfig wlan0
```
wlan0     Link encap:Ethernet  HWaddr 00:d0:41:c0:b7:39  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
gedit /etc/network/interfaces
```
auto lo
iface lo inet loopback

```
modinfo rt73 | grep 9021
```
modinfo rt73 | grep rt7
ERROR: modinfo: could not find module rt73

```
modinfo
```
Usage: modinfo [-0][-F field][-k kernelversion][-b basedir]  module...
 Prints out the information about one or more module(s).
 If a fieldname is given, just print out that field (or nothing if not found).
 Otherwise, print all information out in a readable form
 If -0 is given, separate with nul, not newline.
 If -b is given, use an image of the module tree.
 
```
ls /lib/firmware |grep rt73
```
rt73.bin

```
sudo rmmod -f rt73
```

```
sudo apt-get install linux-firmware
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-firmware is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
sudo modprobe rt73
```
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
FATAL: Module rt73 not found.

```
iwconfig
```
wlan0     IEEE 802.11g  ESSID: off/any  
          Mode:Auto  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=-121 dBm  
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.

```
dmesg | grep -i rt73
```
[   18.227984] ndiswrapper: driver rt73 (Ralink,05/14/2007, 1.02.01.0000) loaded
[   18.860597] wlan0: ethernet device 00:d0:41:c0:b7:39 using NDIS driver: rt73, version: 0x0, NDIS version: 0x500, vendor: 'IEEE 802.11g Wireless Card.', 148F:9021.F.conf

```
lsmod | grep rt
```
gameport               15055  2 snd_cs46xx
parport_pc             32006  1 
parport                36664  3 ppdev,parport_pc,lp

```
nm-tool
```
NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             unavailable
  Default:           no
  HW Address:        00:13:d3:E2:C1:81

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ndiswrapper
  State:             disconnected
  Default:           no
  HW Address:        00:d0:41:c0:b7:39

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points

```
sudo iwlist wlan0 scan
```
wlan0 No scan results

```
lsmod
```
Module                  Size  Used by
pci_stub               12550  1 
vboxpci                22881  0 [permanent]
vboxnetadp             13328  0 [permanent]
vboxnetflt             27211  0 [permanent]
vboxdrv               252210  3 vboxpci,vboxnetadp,vboxnetflt,[permanent]
dm_crypt               22384  0 
nvidia              10258144  40 [permanent]
rfcomm                 37611  0 
bnep                   17749  2 
snd_cs46xx             83403  2 
bluetooth             180442  10 rfcomm,bnep
gameport               15055  2 snd_cs46xx
snd_intel8x0           33330  2 
snd_ac97_codec        105573  2 snd_cs46xx,snd_intel8x0
ac97_bus               12670  1 snd_ac97_codec
snd_pcm                80683  3 snd_cs46xx,snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
ndiswrapper           192644  0 [permanent]
snd_rawmidi            25371  2 snd_cs46xx,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51256  2 snd_seq_midi,snd_seq_midi_event
snd_timer              24609  2 snd_pcm,snd_seq
snd_seq_device         14130  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62211  16 snd_cs46xx,snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14556  1 snd
snd_page_alloc         14108  3 snd_cs46xx,snd_intel8x0,snd_pcm
ppdev                  12900  0 
psmouse                86987  0 
serio_raw              13027  0 
nv_tco                 13364  0 
i2c_nforce2            12906  0 
k8temp                 12872  0 
dm_multipath           22637  0 
parport_pc             32006  1 
mac_hid                13037  0 
binfmt_misc            17258  1 
lp                     13349  0 
parport                36664  3 ppdev,parport_pc,lp
dm_mirror              21694  0 
dm_region_hash         15976  1 dm_mirror
dm_log                 18126  2 dm_mirror,dm_region_hash
btrfs                 735563  0 
zlib_deflate           26506  1 btrfs
libcrc32c              12543  1 btrfs
usb_storage            39358  1 
uas                    17683  0 
forcedeth              57767  0 
pata_amd               13743  3 
sata_nv                23129  0 
floppy                 59798  0

```
cat /etc/resolf.conf
```
cat: /etc/resolf.conf: No such file or directory

Not sure if I messed up somewhere in all that code cuz I've been doin this for several hours already today and my eyes are strained. I'm thinking i botched it up somewhere along the way.

Odd thing is, it worked fine at first when i had the clean install of 12.04 precise. I didn't know upgrading the kernel would affect the WiFi drivers from what I've read online. I'm almost to the point of taking on the task of recompiling the kernel to include the drivers from either the original 12.04 or the ones off the install CD from the USB adapter even though they are windows drivers. I used the "windows wireless drivers" tool app if that helps any.

Any help/solutions/advise is welcome even if it's scratch it all and start from zero, just need to know what to uninstall/delete to try again from scratch...short of OS re-installation because it took me long enough just to get the video issue working properly.

---

### Post by chili555 on 2012-12-10
Please let us see:```
modinfo rt73[COLOR="Red"]usb[/COLOR] | grep 9021
```Since the link you used involved using the native built-in driver rt73usb, why did you install ndiswrapper? What does this tell us?```
ndiswrapper -l
```> cat: /etc/resolf.conf: No such file or directoryThe name of the file is /etc/resol[COLOR="Red"]v[/COLOR].conf.

---

### Post by hugoBOSS81 on 2012-12-10
ok im trying it out right now :) yet i have a hunch that's (rt73[COLOR=red]usb[/COLOR]) also going to come up a problem thanks to some of my previous troubleshooting efforts before I got here lol. at one point i recall having blacklisted the driver and also uninstalling it later and trying to put it back in but never verified it actually installed and unblacklisted.
 
Funny you caught the type-o on the conf file, it completely went unnoticed by me, i must of read that info over 20 times along with all the reboots and blackscreen's i had at one point (tty screen) i also now get the boot screen where u see the ubuntu logo as its booting and a bunch of ndiswrapper info starts scrolling up the screen till it gets to the log in screen (i know that has to do with the vesa drivers and the grub being in "text" mode or something, it was the result of fixing the tty screen a-la another forum search/fix. but i wont get ahead of myself on that plus that doesn't bother me really. lol.

I did notice it seems strange in some of the output regarding the driver rt73 driver and ndiswrapper. i just wasn't sure if that was correct or not as this is my 1st go at using ubuntu plus i took it upon myself to do many advanced things that most probably wouldn't have done. hence the reason i spent so many days/hours consistently searching for answers as i botched up 3 previous installs on the same machine plus having to take notes for commands as there isn't any documentation just showing a general hoarding of commands available to you upon install or that are included with each piece of software you add as you go unless you read the entire docs, think a-la "commands for dummies list" lol. i've had to type up my own doc's saving all the commands i've gathered from all the posts i've read thus far. with short explanations as to what they do and how to revert the process in case of a mess up.

Update:
```
modinfo rt73[COLOR="Red"]usb[/COLOR] | grep 9021
```
alias:   [COLOR="red"]usb[/COLOR]:v0EB0p[COLOR="Red"]9021[/COLOR]d*dc*dsc*dp*ic*isc*ip*
alias:   [COLOR="red"]usb[/COLOR]:v148Fp[COLOR="red"]9021[/COLOR]d*dc*dsc*dp*ic*isc*ip*

```
ndiswrapper -l
```
[COLOR="red"]Warning[/COLOR]: all config files need .conf: /etc/modprobe.d/blacklist. It will be ignored in a future release.
nvstor32: driver installed
[COLOR="red"]Warning[/COLOR]: all config files need .conf: /etc/modprobe.d/blacklist. It will be ignored in a future release.
rt73: driver installed
      device (148F:9021) present (alternate driver rt73usb)

(this doesn't require the colon symbol or i get an error msg)```
cat /etc/resolv.conf
```
#Dynamic resolv.conf(5) file for glibc resolv(3) generated by resolvconf(8)
#DO NOT EDIT FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN

so i still cant connect to the usb wifi, yet i know it has to do with ndiswrapper acting as the driver for the device according to this:
```
nm-tool
```
Network Manager Tool

State: disconnected
-Device: eth0------------------------
 Type: Wired
 Driver: forcedeth
 State: unavailable
 Default: No
 HW Address: MAC
   Capabilities:
    Carrier: yes
 Wired Properties:
   Carrier: off

-Device: wlan0
 Type: 802.11 wifi
 Driver: ndiswrapper
 State: Disconnected
 Default: No
 HW Address: MAC

```
dmesg | grep -l rt7
```
[  16.646855] ndiswrapper: driver rt73 (Ralink,05/14/2007, 1.02.01.0000) loaded
[  17.264481] wlan0: ethernet device 00:41:c0:b7:39 using ndis driver: rt73, version 0x0, NDIS version: 0x500, verndor: IEEE 802.11g Wireless Card, 148F:9021.F.conf

The big stomper for me is that I don't exactly get how  the device is associating the ndiswrapper driver to wlan0 because I can't recall any point at which i would have made that connection in a terminal command since i was following text instructions that if not done exact i'd get errors or blank screens needing reboot or just no internet connection. but I'm sure I'll be shocked by my overlook soon lol.

---

