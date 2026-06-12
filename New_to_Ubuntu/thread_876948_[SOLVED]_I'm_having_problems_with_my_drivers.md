---
title: "[SOLVED] I'm having problems with my drivers"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by circus_animals on 2008-08-01
I tried to do a dual boot (XP and Ubuntu) and it didn't work out, so now I'm having to get to grips with Ubuntu without the familiarity of XP.
What I'd like to know is how can I view my system information , I need to update drivers to be able to use the visual effects. 
I've  tried " sudo apt-get install hardinfo " what do I do now?

---

### Post by northern lights on 2008-08-01
Run ```
sudo lshw
``` to get detailed info on your hardware. If you want it in a permanent file, run ```
sudo lshw -html > HardwareInfo.html
```

If you only want a certain part, run ```
sudo lshw -C CLASS
```where CLASS needs to be replaced by an actual class.

As for the drivers, check whether you're offered one in "System > Administration > Hardware Drivers". If not, post the output of ```
sudo lshw -C display
```to figure out what drivers you need.

---

### Post by tuxxy on 2008-08-01
Install drivers here 

System > Administration > Hardware Drivers

If no luck try install them using envy, also for system information just go to application > system > sysinfo

---

### Post by circus_animals on 2008-08-01
Thankf for your help  northern lights. 
I put // sudo lshw -C display

and this appeared , what should I do now?
 *-display UNCLAIMED     
       description: VGA compatible controller
       product: UniChrome Pro IGP
       vendor: VIA Technologies, Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller bus_master cap_list
       configuration: latency=32 mingnt=2

---

### Post by circus_animals on 2008-08-01
> **tuxxy said:**
> Install drivers here 

System > Administration > Hardware Drivers

If no luck try install them using envy, also for system information just go to application > system > sysinfo

I had a look in the Hardware Drivers and there were no drivers there , just the message "No     proprietary drivers are in use on this system"

Thanks for your help

---

### Post by northern lights on 2008-08-01
The driver you need is 'openchrome'.

Run ```
sudo apt-get install xserver-xorg-video-openchrome
```

Then, reconfigure X. First, exit the desktop environment (jot down the next few lines first)

```
sudo /etc/init.d/gdm stop
```

reconfigure X```
sudo dpkg-reconfigure -phigh xserver-xorg
```

restart desktop environment```
sudo /etc/init.d/gdm start
```

Sorted?

---

### Post by circus_animals on 2008-08-01
Thanks for geting back to me. I really am a novice and new to all of this what does "reconfigure X " mean and how do I do it.
Sorry to be so slow .

---

### Post by northern lights on 2008-08-02
> **circus_animals said:**
> Thanks for geting back to me. I really am a novice and new to all of this what does "reconfigure X " mean and how do I do it.
Sorry to be so slow .
No need to be sorry at all.

The lines between the commands you're supposed to run are simply meant to tell you what the next command will do. 'sudo dpkg-reconfigure -phigh xserver-xorg' reconfigures X...

---

### Post by chuckyp on 2008-08-02
Do you possibly have onboard video; as well as, an add in card?  Or is that the only response for video from the lshw command?

---

### Post by circus_animals on 2008-08-02
> **northern lights said:**
> No need to be sorry at all.

The lines between the commands you're supposed to run are simply meant to tell you what the next command will do. 'sudo dpkg-reconfigure -phigh xserver-xorg' reconfigures X...

I attempted to follow your instructions yesterday and the screen just became lined and illegible.

  Today , after pasting in the first line of code (  second attempt today)   this was the result :

 "howhow@howhow-desktop:~$ sudo apt-get install xserver-xorg-video-openchrome
[sudo] password for howhow: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-openchrome is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
howhow@howhow-desktop:~$ "

What should I do now .
Maybe I have installed them and just not configured them, if that's possible?
My pc is only a couple of years old 

Thanks.

---

### Post by circus_animals on 2008-08-02
> **chuckyp said:**
> Do you possibly have onboard video; as well as, an add in card?  Or is that the only response for video from the lshw command?

Thanks for taking the time to answer my question.
I really haven't got a clue  what's in my pc or how to find out.I was using XP and now I'm all at sea .Having said that it's a fairly friendly sea.

---

### Post by sdowney717 on 2008-08-02
post what says

lspci

---

### Post by circus_animals on 2008-08-02
> **sdowney717 said:**
> post what says

lspci

Thanks, that's definitely one to remember.

---

### Post by sdowney717 on 2008-08-02
open a terminal and type it in, you will get an output like this
in my case it shows the video as
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
```

scott@scott-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
05:04.0 Communication controller: Agere Systems 56k WinModem (rev 01)
05:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VM (LOM) Ethernet Controller (rev 81)
scott@scott-desktop:~$ 


```

---

### Post by circus_animals on 2008-08-02
> **sdowney717 said:**
> open a terminal and type it in, you will get an output like this
in my case it shows the video as
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
```

scott@scott-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
05:04.0 Communication controller: Agere Systems 56k WinModem (rev 01)
05:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VM (LOM) Ethernet Controller (rev 81)
scott@scott-desktop:~$ 


```

Thanks, I did that it read:

<code>
howhow@howhow-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01)
<code>

Am I right in thinking that my video is:
01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01)

What should I do now to update my drivers ?

---

### Post by sdowney717 on 2008-08-02
[http://unichrome.sourceforge.net/](http://unichrome.sourceforge.net/)

I wonder if that video card will ever have 3d acceleration in linux


[http://ubuntuforums.org/archive/index.php/t-467178.html](http://ubuntuforums.org/archive/index.php/t-467178.html)

---

### Post by northern lights on 2008-08-02
Easiest solution probably indeed would be to log onto eBay and grab some 3 to 5 year old GeForce. Something along the lines of a 4 series with 128 megs of RAM will do the job to perfection. Twenty bucks ought to cut it.

---

### Post by circus_animals on 2008-08-02
It looks like  I should upgrade. Thanks for the links and the help.

---

### Post by circus_animals on 2008-08-02
> **northern lights said:**
> Easiest solution probably indeed would be to log onto eBay and grab some 3 to 5 year old GeForce. Something along the lines of a 4 series with 128 megs of RAM will do the job to perfection. Twenty bucks ought to cut it.

Yep, I'll have to do that by the looks of thing. Even after only a couple of days I'm beginning to like the look and feel of this OS. I'll have to read up about this terminal thingy .
Thank you for the help and your patience.
*****

---

### Post by circus_animals on 2008-08-02
> **northern lights said:**
> Easiest solution probably indeed would be to log onto eBay and grab some 3 to 5 year old GeForce. Something along the lines of a 4 series with 128 megs of RAM will do the job to perfection. Twenty bucks ought to cut it.

Would something like this do the trick ?
[http://cgi.ebay.co.uk/512MB-nVidia-GeForce-7200GS-PCI-Express-Graphics-Card_W0QQitemZ370071336996QQcmdZViewItem?hash=item370071336996&_trkparms=72%3A12|39%3A1|66%3A2|65%3A12&_trksid=p3286.c0.m14.l1308](http://cgi.ebay.co.uk/512MB-nVidia-GeForce-7200GS-PCI-Express-Graphics-Card_W0QQitemZ370071336996QQcmdZViewItem?hash=item370071336996&_trkparms=72%3A12|39%3A1|66%3A2|65%3A12&_trksid=p3286.c0.m14.l1308)

---

### Post by OldTimeTech on 2008-08-02
More like what is on the top of this page is what  Northern Lights is talking about....the one you had was much newer and more than likely wouldn't of worked in your machine.

[http://search.ebay.com/Nvidia-Geforce-4-128mb_W0QQcatrefZC3QQdfspZ32QQfromZR2QQssPageNameZRC0021QQ_trksidZp1638Q2em120](http://search.ebay.com/Nvidia-Geforce-4-128mb_W0QQcatrefZC3QQdfspZ32QQfromZR2QQssPageNameZRC0021QQ_trksidZp1638Q2em120)

---

### Post by circus_animals on 2008-08-02
> **OldTimeTech said:**
> More like what is on the top of this page is what  Northern Lights is talking about....the one you had was much newer and more than likely wouldn't of worked in your machine.

[http://search.ebay.com/Nvidia-Geforce-4-128mb_W0QQcatrefZC3QQdfspZ32QQfromZR2QQssPageNameZRC0021QQ_trksidZp1638Q2em120](http://search.ebay.com/Nvidia-Geforce-4-128mb_W0QQcatrefZC3QQdfspZ32QQfromZR2QQssPageNameZRC0021QQ_trksidZp1638Q2em120)

OK, I'll have to have a nosey about and try read up about it.
Thanks for the reply.

---

### Post by northern lights on 2008-08-02
> **circus_animals said:**
> Would something like this do the trick ?
[http://cgi.ebay.co.uk/512MB-nVidia-GeForce-7200GS-PCI-Express-Graphics-Card_W0QQitemZ370071336996QQcmdZViewItem?hash=item370071336996&_trkparms=72%3A12|39%3A1|66%3A2|65%3A12&_trksid=p3286.c0.m14.l1308](http://cgi.ebay.co.uk/512MB-nVidia-GeForce-7200GS-PCI-Express-Graphics-Card_W0QQitemZ370071336996QQcmdZViewItem?hash=item370071336996&_trkparms=72%3A12|39%3A1|66%3A2|65%3A12&_trksid=p3286.c0.m14.l1308)
Well, not quite indeed. The price is okay, but you seem not to have a board with PCI Express. Make sure it's an AGP card. I like the fact that it's passively cooled though. Energy efficient and quiet.

> **OldTimeTech said:**
> More like what is on the top of this page is what  Northern Lights is talking about....the one you had was much newer and more than likely wouldn't of worked in your machine.

[http://search.ebay.com/Nvidia-Geforce-4-128mb_W0QQcatrefZC3QQdfspZ32QQfromZR2QQssPageNameZRC0021QQ_trksidZp1638Q2em120](http://search.ebay.com/Nvidia-Geforce-4-128mb_W0QQcatrefZC3QQdfspZ32QQfromZR2QQssPageNameZRC0021QQ_trksidZp1638Q2em120)
Pretty much and then also not at all.
You have missed that that's for a Mac/Apple. I might not have noticed either, if it wasn't for the price - 90 USD is way too much.

I found a [Geforce 7600GS]("http://cgi.ebay.co.uk/ASUS-N7600GS-HTD-256M-GeForce-7600GS-256-MB-AGP-V_W0QQitemZ300246019175QQcmdZViewItem?hash=item300246019175&_trkparms=39%3A1|66%3A2|65%3A1&_trksid=p3286.c0.m14.l1318") and an [FX5200]("FX5200"). Both with 256 megs of RAM. Most 4 series come with 64MB apparently. And these cards are priced so low, that you can indeed step it up a bit. I was just giving an approximate area. Of the two, The first would be my preference. Good chip, decent manufacturer.

[List of cards supported by the current nvidia driver for i386 Linux]("http://us.download.nvidia.com/XFree86/Linux-x86/173.14.12/README/appendix-a.html")

---

### Post by circus_animals on 2008-08-03
northern lights posted
[I found a [Geforce 7600GS]("http://cgi.ebay.co.uk/ASUS-N7600GS-HTD-256M-GeForce-7600GS-256-MB-AGP-V_W0QQitemZ300246019175QQcmdZViewItem?hash=item300246019175&_trkparms=39%3A1|66%3A2|65%3A1&_trksid=p3286.c0.m14.l1318") and an [FX5200]("FX5200"). Both with 256 megs of RAM. Most 4 series come with 64MB apparently. And these cards are priced so low, that you can indeed step it up a bit. I was just giving an approximate area. Of the two, The first would be my preference. Good chip, decent manufacturer.]

I had a look at your first choice and it states :
"System Requirements
Operating System:	Microsoft Windows 2000, Microsoft Windows Vista, Microsoft Windows XP "
I only have Ubuntu Linux on my PC now, would this product ( or one like it) still be compatible?

---

### Post by northern lights on 2008-08-03
> **circus_animals said:**
> I had a look at your first choice and it states :
"System Requirements
Operating System:	Microsoft Windows 2000, Microsoft Windows Vista, Microsoft Windows XP "
I only have Ubuntu Linux on my PC now, would this product ( or one like it) still be compatible?
Where did it state that? On the vendor's box? In the year it was first sold - fair enough there weren't any linux drivers.
Today I would for once not post an incompatible product and also, if you looked at the [compatible cards]("http://us.download.nvidia.com/XFree86/Linux-x86/173.14.12/README/appendix-a.html") link I gave you below the two ebay items, you'd see that there's a driver (if you don't want to read the whole hing, hit "Ctrl+F" and search for "7600 GS").

---

### Post by circus_animals on 2008-08-03
[QUOTE=northern lights;5514241]Where did it state that? On the vendor's box? In the year it was first sold - fair enough there weren't any linux drivers.


In the last page of this item the seller appears to be stating that this card is not suitable for my PC. I know that I haven't really given you much info about the type of PC  that I'm using, or what is inside.


"	
Additional Information about ASUS N7600GS/HTD/256M GeForce 7600GS, (256 MB) AGP Video Card

Product MPN
MPN:	N7600GS/HTD/256

Processor
Graphic Processor:	NVIDIA GeForce 7600 GS
GPU Clock Speed:	400 MHz
RAMDAC Speed:	400 MHz

Key Features
Card Interface:	AGP 8x
Compatibility:	PC

Memory
Installed Memory:	256 MB
Memory Tech:	DDR SDRAM
Memory Data Width:	128-bit
Installed Memory / Technology:	256 MB (DDR SDRAM)

Technical Features
Form Factor:	Plug-in card
Video Compression Standards:	MPEG-4
Max. Screen Resolution:	2048 x 1536
Pipeline Engines:	12 Pipeline Engines
Special Features:	HDTV TV-out Support

Input / Output
Display Interface:	DVI x 1, VGA - 15 pin D-Sub x 2
Output Interface:	HDTV Out

[COLOR="Red"]System Requirements
Operating System:	Microsoft Windows 2000, Microsoft Windows Vista, Microsoft Windows XP[/COLOR]

Miscellaneous
Included Accessories:	DVI to VGA Adapter x 2, HDTV out adapter
Package Type:	Retail
UPC:	610839024230 "

Thanks for the links and your help.

---

### Post by northern lights on 2008-08-03
> **circus_animals said:**
> [COLOR="Red"]System Requirements
Operating System:	Microsoft Windows 2000, Microsoft Windows Vista, Microsoft Windows XP[/COLOR]
eBay vendor's bogus.

---

### Post by circus_animals on 2008-08-03
> **northern lights said:**
> Where did it state that? On the vendor's box? In the year it was first sold - fair enough there weren't any linux drivers.
Today I would for once not post an incompatible product and also, if you looked at the [compatible cards]("http://us.download.nvidia.com/XFree86/Linux-x86/173.14.12/README/appendix-a.html") link I gave you below the two ebay items, you'd see that there's a driver (if you don't want to read the whole hing, hit "Ctrl+F" and search for "7600 GS").

> **northern lights said:**
> eBay vendor's bogus.

You may have just saved me 25 quid!
I have never bought anything from ebay before .
Thanks again .

---

### Post by X4320 on 2008-11-14
> **northern lights said:**
> The driver you need is 'openchrome'.

Run ```
sudo apt-get install xserver-xorg-video-openchrome
```

Then, reconfigure X. First, exit the desktop environment (jot down the next few lines first)

```
sudo /etc/init.d/gdm stop
```

reconfigure X```
sudo dpkg-reconfigure -phigh xserver-xorg
```

restart desktop environment```
sudo /etc/init.d/gdm start
```

Sorted?


thanks a ton and more....
worked perfectly !!

---

