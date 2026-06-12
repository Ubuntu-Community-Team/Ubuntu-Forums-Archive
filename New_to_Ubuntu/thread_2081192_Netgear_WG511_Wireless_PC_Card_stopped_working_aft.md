---
title: "Netgear WG511 Wireless PC Card stopped working after upgrade  to Ubuntu 12.04 Precise"
date: 2012-11-06
forum: New to Ubuntu
---

### Post by mg2011 on 2012-11-06
Last year I decided to try Linux and installed Ubuntu 11.04 Natty Narwhal onto a Dell Latitude C600 notebook (Pentium III, 512MB system memory). I was able to get the Netgear WG511 Wireless PC Card (PCMCIA) to work (ndiswrapper process) by reading postings in this forum (thanks!). I was able to get regular software updates through this PCMCIA card throughout the year until last Saturday when I was informed no more would be available for Natty Narwhal -- but an upgrade was available. I took the upgrade. After several hours and a reboot I was in Ubuntu 11.10 with the (new to me) Unity graphical desktop. I again checked for software updates and saw that the 12.04LTS Precise Pangolin was available. I learned that LTS was short for Long Term Support (I thought this might give me a stable environment upon which to continue learning Linux). So again I took the upgrade. The 12.04LTS upgrade was downloaded using the Wireless Netgear WG511 PCMCIA card. The only difficulty encountered occurred several hours into and toward the end of the download process. But a review of this forum's postings suggested I change the "Download from: Server for United States" to "Download from: Main Server" on the "Ubuntu Software" tab on the "Software Sources". The upgrade download was started again and it picked up where it left off. Once the download finished Ubuntu 12.04LTS completed installation a couple of hours later. Although two times toward the end of the installation process a popup window asked me to make a decision about some sort of file conflict. Both times I chose to go with the new 12.04LTS file over the existing file (possible mistake?). And after the reboot I was in Ubuntu 12.04LTS but my Netgear Wireless PC Card no longer worked and no wireless options appeared under the wireless configuration icon in the top right corner of the desktop. I was able to ping another computer on a wired Ethernet LAN as a test of network connectivity. And a review of this forum's postings suggested I download the "linux-firmware_nonfree-1.11.all.deb" package and install it from a terminal session using the command "sudo dpkg -i". I did this and as a result a bunch of files were installed into the /int/firmware directory. But the PCMCIA card still does not work. I wanted to confirm that I still had the windows driver in the ndiswrapper for the PCMCIA card, but I do not know how to do this. I ran the application "Additional Drivers" that produced a window with the statement "No proprietary drivers are in use on this system."

Please advise how I can get this PCMCIA card to work with Ubuntu 12.04LTS (but please remember I am still quite new to all of this). Other similar posts to this forum were requested to provide additional information. And the commands and the results of the those commands follow:

cat /etc/lsb-release; uname -a

DISTRIB_ID=Ubuntu DISTRIB_RELEASE=12.04 DISTRIB_CODENAME=precise DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS" Linux mg10-Latitude-C600 3.2.0-32-generic #51-Ubuntu SMP Wed Sep 26 21:32:50 UTC 2012 i686 i686 i386 GNU/Linux

lspci -nnk |grep -iA2 net

00:10.0 Ethernet controller [0200]: 3Com Corporation 3c556 Hurricane CardBus [Cyclone] [10b7:6055] (rev 10) Subsystem: 3Com Corporation Device [10b7:6456] Kernel driver in use: 3c59x

-- 06:00.0 Network controller [0280]: Intersil Corporation ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] [1260:3890] (rev 01) Subsystem: Netgear WG511 v2/v3 54 Mbps Wireless PC Card [1385:4800] Kernel modules: p54pci, prism54

lsusb

Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 001 Device 002: ID 062a:0000 Creative Labs Optical mouse

iwconfig

lo no wireless extensions.

vboxnet0 no wireless extensions.

eth0 no wireless extensions.

rfkill list all

(nothing was returned from this command)

lsmod

Module Size Used by

atmel_cs 12735 0

atmel 40492 1 atmel_cs

vboxnetadp 13328 0

vboxnetflt 27840 0

vboxdrv 230140 2 vboxnetadp,vboxnetflt

vesafb 13516 1

joydev 17393 0

snd_maestro3 23064 2

snd_ac97_codec 106082 1 snd_maestro3

ac97_bus 12642 1 snd_ac97_codec

snd_pcm 80845 2 snd_maestro3,snd_ac97_codec

snd_page_alloc 14115 1 snd_pcm

dcdbas 14098 0

snd_seq_midi 13132 0

snd_rawmidi 25424 1 snd_seq_midi

snd_seq_midi_event 14475 1 snd_seq_midi

snd_seq 51567 2 snd_seq_midi,snd_seq_midi_event

snd_timer 28931 2 snd_pcm,snd_seq

snd_seq_device 14172 3 snd_seq_midi,snd_rawmidi,snd_seq

psmouse 96684 0

snd 62064 11 strong textsnd_maestro3,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device serio_raw 13027 0

soundcore 14635 1 snd

i2c_piix4 13093 0

video 19068 0

mac_hid 13077 0

rfcomm 38139 0

bnep 17830 2

bluetooth 158438 10 rfcomm,bnep

parport_pc 32114 1

ppdev 12849 0

pcmcia 39791 1 atmel_cs

binfmt_misc 17292 1

yenta_socket 27428 0

pcmcia_rsrc 18367 1 yenta_socket

pcmcia_core 21511 3 pcmcia,yenta_socket,pcmcia_rsrc

shpchp 32325 0

lp 17455 0

parport 40930 3 parport_pc,ppdev,lp

usbhid 41906 0

3c59x 37445 0

hid 77367 1 usbhid

floppy 60310 0

---

### Post by ajgreeny on 2012-11-06
Unfortunately there is a bug in ndiswrapper in 12.04 which stops the driver installing.  I had the same problem in Lubuntu 12.04 with the same netgear card and solved it by using what is, I think, the only way to get it working, ie compiling ndiswrapper following the info at:-

[http://ubuntuforums.org/showthread.php?p=11970543](http://ubuntuforums.org/showthread.php?p=11970543)
[http://ubuntuforums.org/showthread.php?t=1967383](http://ubuntuforums.org/showthread.php?t=1967383)
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) *- (section 4)*

It is not as difficult as it may seem, but takes a while to compile and go through compared with a normal installation.  Just make sure you follow all the instructions fully, and I think that first link is easiest to follow.

Good Luck!

---

### Post by mg2011 on 2012-11-07
Thanks ajgreeny for pointing me in the right direction!  I recompiled the 1.57 version of ndiswrapper and got the Netgear PCMCIA PC Card working again.  Cheers!

---

### Post by ajgreeny on 2012-11-07
Great!

This is very annoying and I'm surprised that there is no other quicker and easier way to get round the problem.

If there is, I didn't find it, and I suppose that apart from the time taken to compile the package, it is not difficult, but it's the first time I've had a problem with this pcmcia card, which seems to work very well.

In previous Ubuntu versions up to around 9.04, I think, it did not work with any encryption on the wireless connection, then WEP was added and now full WPA2 works fine.

I have no idea about the 12.10 situation with ndiswrapper, so be prepared to do the same compiling job if you choose to upgrade, as it may still be as problem for all I know.

---

