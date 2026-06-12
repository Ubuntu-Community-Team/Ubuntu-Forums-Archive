---
title: "Headless Jukebox on Toshiba 1735"
date: 2009-02-04
forum: Other OS Talk
---

### Post by volkswagner on 2009-02-04
Hi All,

I am seeking advice on the following hardware.

Toshiba 1735 Laptop:
Cpu 700MHz Celeron Coppermine
20Gig Hard Drive .... relatively small for family jukebox :(
RAM 64Meg Onboard + 256Meg SDRAM
Linksys wpc11 ver2 wireless PCMCIA card

The screen hinges are busted clean off the laptop (screen works).  

My plan was to install Ubuntu Server , LAMP, Jinzora output to MPD.  This would be setup in the family audio rack connected to house sound.  Currently the only user interface with the stereo system is to physically go to the rack in the pantry.

Each family member has a laptop (mac/apple). I figured Jinzora would be great since it allows sound output to server. The system would probably not be used for streaming.

The bugger is I have spent hours trying to get sound drivers working in Ubuntu Server.  The sound card (Cirrus Logic Crystal CS4281 PCI Audio (rev 01)), works out of the box with Slax5.  I did not spend anytime with the WiFi card in Slax, so I am not sure what it would take.  

Since Slax picked up the sound card, does that mean Slackware would also?  

How much learning curve would there be going from Ubuntu (my only linux experience) to Slackware?

Any other disro that would be friendly with my hardware?  The setup is for a family friend, I am hoping I can "set it and forget it".

I am open to other suggestions on implementation ie: other than Jinzora, LAMP, MPD, etc.  



```

lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:04.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
00:04.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:08.0 Multimedia audio controller: Cirrus Logic Crystal CS4281 PCI Audio (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)
02:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface

```

---

### Post by handy on 2009-02-04
You could set your Toshiba up with [*_FreeNAS_*]("http://www.freenas.org/"), which is a really small <75Mb & a very easy installation.  FreeNAS is built on FreeBSD, I have been using what was the current beta version at the time for a couple of months & it is flawless.

After it is installed, you configure it via a brilliant web browser based GUI from another machine.  You can stream video or sound over your LAN to multiple machines simultaneously.

I use mine mainly for streaming video which I access with VLC.

There is a great LiveCD called [*_GeeXboX_*]("http://www.geexbox.org/en/index.html") which apparently interfaces with FreeNAS really well also.  I don't know if it would be suitable for your needs or not.

---

### Post by volkswagner on 2009-02-05
Thanks for the reply.

After checking FreeNAS and GeexBox, I am not sure they will fit the bill.  I don't see documentation to allow FreeNas to run an instance of apache and mysql.  I do see the config is run via a web interface, I just can't confirm a fully configurable apache can run on it.

I see GeexBox now has an installer.  I just don't see how I would be able to control it remotely.  Maybe a remote desktop or something?

I may need to clarify.  I am not looking for streaming.  I want the laptop to play locally but be controlled remotely.  I figured a web interface would be the easiest and most functional for each family member is running a wireless laptop.

---

### Post by handy on 2009-02-05
> **volkswagner said:**
> 
Thanks for the reply.

After checking FreeNAS and GeexBox, I am not sure they will fit the bill.  I don't see documentation to allow FreeNas to run an instance of apache and mysql.  I do see the config is run via a web interface, I just can't confirm a fully configurable apache can run on it. 

FreeNAS is not meant to have things added to it, it has been designed to be as fast & reliable as possible, both of these can be compromised by user additions to the system.  

FreeNAS has a LOT of services provided for networking:

CIFS/SMB
FTP
SSH
NFS
AFP
RSYNCH
Unison
iSCSI Target
UPnP (this is how GeeXboX interfaces)
iTunes/DAAP
Dynamic DNS
SNMP
UNS
Webserver
Bittorrent


> **volkswagner said:**
> 
I see GeexBox now has an installer.  I just don't see how I would be able to control it remotely.  Maybe a remote desktop or something? 

I haven't used GeeXboX, but if it interfaces with FreeNAS, then under that circumstance it would be working from a client machine or machines & be used for streaming data from FreeNAS.  

> **volkswagner said:**
> 
I may need to clarify.  I am not looking for streaming.  I want the laptop to play locally but be controlled remotely. 

I'll demonstrate the way I stream videos on my home LAN below:

I have a FreeNAS box in my office, which is connected to my LAN.  I store a backup of important data & video's on the FreeNAS box which I transfer to it over the LAN.  I can easily access these files from any other machine on the LAN that has been configured to see the FreeNAS box & whichever directory(ies) it has been allowed to share.

I mostly use the FreeNAS box to stream videos across my home LAN to the desktop machine I am using to type this text, to watch video's.
  
> **volkswagner said:**
> 
I figured a web interface would be the easiest and most functional for each family member is running a wireless laptop.

If you are looking to give each family member the ability to control the jukebox remotely with their personal laptops, & the jukebox will be playing directly into your centralised household sound system, then I don't think that a FreeNAS box will be suitable, as it is a too specialised installation.

I obviously didn't fully understand your original post.  :-)

---

