---
title: "[SOLVED] Please help me set up my wireless"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by Obeide on 2008-11-03
Hello, 
I've just installed the latest version of ubuntu on my old laptop and I can't get it to see the wireless connection at home.

I'm using a Belkin wireless card using the BCM4318 chipset.  I did 'lspci' and it can see it, but it won't find my connection.

Please help me!

---

### Post by Fass on 2008-11-03
Hi!

Have you installed the firmware for the device yet? If what I just said makes no sense to you, try running the following command in a terminal (Applications -> Accessories -> Terminal):

```
sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh
```

It will ask you for the password you use to login to your user account. Enter it (it will not show up on the screen, so don't be alarmed that you can't see any asterisks) and press enter. You should see some output.

You will need a working internet connection for that, so hook up your computer to a wired connection before you run it. Once that command has run, reboot. You should now be able to see your AP/Wireless router in network manager.

---

### Post by Obeide on 2008-11-03
Thanks for your post, Fass.  I tried this by taking the network cable out of another computer and plugging it in and it didn't work.  I think I'm going to try to get this to work with a wired network first. :confused:

---

### Post by Obeide on 2008-11-03
OK, i've set up the wired network, and i'm on it now :)

I've tried what you recommended and it says command not found. It doesn't ask me for my password either.

I cut and pasted your text to make sure I got it right.

I'm a bit stumped (and it's been a long day!)

---

### Post by Obeide on 2008-11-03
I don't know if any of this info will help:
**lspci**
> 00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: S3 Inc. SuperSavage IX/C SDR (rev 05)
02:00.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:00.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:02.0 Communication controller: Agere Systems WinModem 56k (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
03:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

iwconfig
> lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

lspci -v
> 03:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
	Subsystem: Belkin Device 7011
	Flags: bus master, fast devsel, latency 64, IRQ 11
	Memory at c4000000 (32-bit, non-prefetchable) [size=8K]
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb

Any/all help gratefully received

---

### Post by igknighted on 2008-11-03
Latest = 8.10?

If so, go to system->administration->hardware drivers and mark it to enable the broadcom STA driver (you will need to be online)

If you are on 8.04.1 then you will need to install all available updates before this driver is available.

---

### Post by Obeide on 2008-11-03
thank you so much for your post.  Yes I'm using 8.10, downloaded yesterday and freshly installed on my mum's old thinkpad. 

I went to system - administration - hardware drivers and it said 'no proprietary drivers are in use on this system'

not sure where to go from here.

---

### Post by Fass on 2008-11-03
> **Obeide said:**
> I've tried what you recommended and it says command not found. It doesn't ask me for my password either

Run "sudo aptitude install b43-fwcutter". Then run the command I gave you again.

Also, please post the output of "lsmod".

---

### Post by Obeide on 2008-11-03
Hello lovely Fass, thank you for posting again.  I did as you suggested and ran sudo aptitude, it unpacked something (it went so fast and i know so little I couldn't tell you what), and I tried the install firmware again with the same result as last time.

here is lsmod
> 
Module                  Size  Used by
ipv6                  263972  8 
savage                 39424  2 
drm                    86056  3 savage
af_packet              25728  4 
binfmt_misc            16904  1 
rfkill_input           12672  0 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
rfcomm                 44432  0 
sco                    18308  2 
l2cap                  30464  6 bnep,rfcomm
bluetooth              61924  6 bnep,rfcomm,sco,l2cap
thinkpad_acpi          66176  0 
nvram                  16524  1 thinkpad_acpi
ppdev                  15620  0 
speedstep_ich          11920  0 
speedstep_lib          12676  1 speedstep_ich
cpufreq_stats          13188  0 
cpufreq_userspace      11396  0 
cpufreq_conservative    14600  0 
cpufreq_ondemand       14988  1 
freq_table             12672  3 speedstep_ich,cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       9856  0 
container              11520  0 
pci_slot               12552  0 
wmi                    14504  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
lp                     17156  0 
arc4                    9984  2 
ecb                    10880  2 
crypto_blkcipher       25476  1 ecb
b43                   131356  0 
rfkill                 17176  3 rfkill_input,thinkpad_acpi,b43
mac80211              216820  1 b43
cfg80211               32392  1 mac80211
led_class              12164  2 thinkpad_acpi,b43
input_polldev          11912  1 b43
ssb                    40580  1 b43
pcmcia                 43052  0 
usbhid                 35840  0 
hid                    50560  1 usbhid
battery                18436  0 
ac                     12292  0 
evdev                  17696  11 
snd_intel8x0           37532  3 
snd_ac97_codec        111652  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
psmouse                45200  0 
serio_raw              13444  0 
yenta_socket           31756  3 
rsrc_nonstatic         19072  1 yenta_socket
pcmcia_core            43412  3 pcmcia,yenta_socket,rsrc_nonstatic
video                  25104  0 
output                 11008  1 video
snd_seq_dummy          10884  0 
nsc_ircc               28816  0 
parport_pc             39204  1 
parport                42604  3 ppdev,lp,parport_pc
irda                  199612  1 nsc_ircc
crc_ccitt              10112  1 irda
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
button                 14224  0 
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcspkr                 10624  0 
snd                    63268  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              33724  1 
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_intel8x0,snd_pcm
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
agpgart                42184  2 drm,intel_agp
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
ext3                  133256  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42264  3 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
ata_piix               24580  2 
ata_generic            12932  0 
pata_acpi              12160  0 
libata                177312  3 ata_piix,ata_generic,pata_acpi
e100                   41356  0 
mii                    13440  1 e100
scsi_mod              155212  4 sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
uhci_hcd               30736  0 
usbcore               148848  3 usbhid,uhci_hcd
thermal                23708  0 
processor              42156  2 thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3


---

### Post by Fass on 2008-11-03
Well, now at least you have b43-cutter. We'll just have to install the firmware manually. Do the following in a terminal (keep the same terminal window open).

```
wget http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2
```

This will download the firmware.

```
tar xjf broadcom-wl-4.150.10.5.tar.bz2
```

This will unpack it.

```
cd broadcom-wl-4.150.10.5/driver
```

This will put us in driver directory.

```
sudo b43-fwcutter -w /lib/firmware wl_apsta_mimo.o
```

This will cut and install the firmware. Check that you have a directory called "b43" in your /lib/firmware - if everything went correctly, it should be there and contain a bunch of files.

Next run:

```
sudo rmmod b43 [press enter]
sudo modprobe b43
```

Check network manager. You should now be able to pick up APs/Wireless routers. If not reboot. Then you should be able to pick up APs/Wireless routers. If not... then come back here and we'll try to troubleshoot.

---

### Post by Obeide on 2008-11-03
Um, i'm not sure it unpacked.
Here's what happened:
> rosi@rosi-laptop:~$ wget [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)
--2008-11-03 20:30:30--  [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)
Resolving mirror2.openwrt.org... 88.198.39.176
Connecting to mirror2.openwrt.org|88.198.39.176|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3888794 (3.7M) [application/x-tar]
Saving to: `broadcom-wl-4.150.10.5.tar.bz2'

100%[======================================>] 3,888,794    226K/s   in 18s     

2008-11-03 20:30:59 (205 KB/s) - `broadcom-wl-4.150.10.5.tar.bz2' saved [3888794/3888794]

rosi@rosi-laptop:~$ tar xjf broadcom-wl-4.150.10.5.tar.bz2
rosi@rosi-laptop:~$ tar xjf broadcom-wl-4.150.10.5.tar.bz2
rosi@rosi-laptop:~$ cd broadcom-wl-4.150.10.5/driver
rosi@rosi-laptop:~/broadcom-wl-4.150.10.5/driver$ 
rosi@rosi-laptop:~/broadcom-wl-4.150.10.5/driver$ sudo b43-fwcutter -w /lib/firmware wl_apsta_mimo.o
[sudo] password for rosi: 
sudo: b43-fwcutter: command not found
rosi@rosi-laptop:~/broadcom-wl-4.150.10.5/driver$ 


---

### Post by Fass on 2008-11-03
It seems b43-fwcutter wasn't installed. Tell you what, go to Applications -> System -> Administration -> Synaptic.

There make sure that in "Settings - Repositories" you have ticked all tickable boxes in the "Ubuntu software" section, i.e. you should have ticked all the boxes next to "main, universe, restricted, multiverse". Deselect the CD-rom. 

Then, in Synaptic click on the button that says: "Reload". After that, use synaptics search function (not "quick search", but the proper search) and look for "b43-fwcutter". It'll take a moment. Once it's found, right click the package and choose "Mark for installation" and then click the "Apply" button in the upper left hand corner in the Synaptics window. Once b43-fwcutter is installed, continue on from "sudo b43-fwcutter -w /lib/firmware wl_apsta_mimo.o" (make sure to be in the "/broadcom-wl-4.150.10.5/driver" directory).

---

### Post by Obeide on 2008-11-03
> **Fass said:**
> 

There make sure that in "Settings - Repositories" you have ticked all tickable boxes in the "Ubuntu software" section, i.e. you should have ticked all the boxes next to "main, universe, restricted, multiverse". Deselect the CD-rom. 



ok, it is ticked against everything except source code,  there is a dash in this box, it can be either empty or a dash.

---

### Post by Fass on 2008-11-03
Let it be dashed. Now, kindly follow the rest of the instructions (from clicking "Reload" and onward.)

---

### Post by johnehowe on 2008-11-03
These steps worked great for me. However, I am getting a higher latency time that expected. If I ping another device on the same subnet I get an average of about 3ms. If I place a NetGear wg511 card in the PCMCIA slot and use it instead I get less than 1ms average. I know that is not huge but can have an effect on the overall network speed. What are you seeing?

---

### Post by Obeide on 2008-11-03
Fass you are a magnificent being! I am now typing this over my new wireless connection! WooHoo :)

---

### Post by Fass on 2008-11-03
> **Obeide said:**
> Fass you are a magnificent being! I am now typing this over my new wireless connection! WooHoo :)

Great! Now, you just have to mark this thread as "solved" - not just by writing "[SOLVED]" in the subject line as that won't be seen by others. Instead, choose "thread tools" and there choose to "mark this thread as solved".

---

### Post by Fass on 2008-11-03
> **johnehowe said:**
> These steps worked great for me. However, I am getting a higher latency time that expected. If I ping another device on the same subnet I get an average of about 3ms. If I place a NetGear wg511 card in the PCMCIA slot and use it instead I get less than 1ms average. I know that is not huge but can have an effect on the overall network speed. What are you seeing?

I average "time=0.944 ms", and I have a BCM4306 card running this same firmware.

---

### Post by johnehowe on 2008-11-03
Any ideas why I may be seeing a higher latency time than with the other card? Obviously, something is not completely right with the driver or firmware. Don't get me wrong, it is awesome that it is working and the fact I no longer need a PCMCIA card sticking out of the side of my laptop but I would like it to be faster.

---

### Post by johnehowe on 2008-11-03
I am getting some latency times as high as 20ms.


64 bytes from 192.169.0.3: icmp_seq=355 ttl=128 time=9.30 ms
64 bytes from 192.169.0.3: icmp_seq=356 ttl=128 time=26.5 ms
64 bytes from 192.169.0.3: icmp_seq=361 ttl=128 time=82.5 ms
64 bytes from 192.169.0.3: icmp_seq=362 ttl=128 time=1.09 ms
64 bytes from 192.169.0.3: icmp_seq=363 ttl=128 time=0.879 ms
64 bytes from 192.169.0.3: icmp_seq=364 ttl=128 time=0.333 ms
64 bytes from 192.169.0.3: icmp_seq=365 ttl=128 time=0.642 ms
64 bytes from 192.169.0.3: icmp_seq=366 ttl=128 time=0.817 ms
64 bytes from 192.169.0.3: icmp_seq=367 ttl=128 time=6.43 ms
64 bytes from 192.169.0.3: icmp_seq=368 ttl=128 time=8.93 ms
64 bytes from 192.169.0.3: icmp_seq=369 ttl=128 time=8.06 ms
64 bytes from 192.169.0.3: icmp_seq=370 ttl=128 time=2.91 ms
64 bytes from 192.169.0.3: icmp_seq=371 ttl=128 time=4.64 ms
64 bytes from 192.169.0.3: icmp_seq=372 ttl=128 time=15.2 ms
64 bytes from 192.169.0.3: icmp_seq=373 ttl=128 time=1.21 ms
64 bytes from 192.169.0.3: icmp_seq=374 ttl=128 time=0.312 ms

---

### Post by Fass on 2008-11-03
> **johnehowe said:**
> I am getting some latency times as high as 20ms.

It depends on the load yours and the other machine is under. For instance, I get higher latencies if I ping my router while it's doing something else than just responding to my ping. You should try to see if the latencies are different with other machines, if they're different when they are idle and not, and also of course check with machines not on your own network to see if the latencies are relevantly different for regular use at all.

---

### Post by johnehowe on 2008-11-03
I had already narrowed it down to the Broadcom 4311 card. Using the NetGear card in the same machine, pinging with other machines on the same network, and pinging the same node (Server). All instances produced less than 1ms average with mostly 0% packet loss. The Broadcom produces close to 15ms latency.

37 packets transmitted, 36 received, 2% packet loss, time 177735ms
rtt min/avg/max/mdev = 0.301/**14.898**/332.244/54.898 ms

---

