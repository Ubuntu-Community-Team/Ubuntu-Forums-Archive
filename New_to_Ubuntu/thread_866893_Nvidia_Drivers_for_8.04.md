---
title: "Nvidia Drivers for 8.04"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by poscomp on 2008-07-22
I finally loaded 8.04 on a desktop computer. Everything seems ok but the Nvidia drivers don't work. How can I fix this problem?

---

### Post by drs305 on 2008-07-22
You can try EnvyNG to install the correct nvidia (or ATI) driver. I've had good success with it.

To install:
```
sudo aptitude install envyng-gtk
```

To run:
System Tools, EnvyNG. Select Nvidia and auto-install.

---

### Post by coffeephen on 2008-07-22
Hello :)

I really hope this is the right place for my question. I have been looking for related topics or instructions but I fear I might not be familiar enough with things yet to understand whether the stuff I found actually has something to do with my problem.

I came across this thread and since I have some trouble installing Nvidia drivers, too, I thought I might add it here. 

I installed Ubuntu 8.04 this morning. Everything so far is great. The installation was easy and fast and an hour later I was already browsing the internet (and this is from a person who doesn't even know what exactly a motherboard is!)

I installed it on my laptop, a Sony VAIO VGN-FS115M.
Most people add a whole bunch of important system information...but my knowledge is so very basic that I wouldn't even know what is relevant here. 

Now to my only problem so far, which is, that I didn't manage to install the Nvidia accelerated graphic driver. When I try to enable it via System>>Administration>>Hardware Drivers>>Enable it attempts to download for a second and then I get this error message:
[I][COLOR="DarkRed"]
W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.13-18.41_i386.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.13-18.41_i386.deb)
  404 Not Found[/COLOR][/I]

I then tried what drs305 suggested.

But after entering sudo aptitude install envyng-gtk (and after that my password) I get this message:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
Writing extended state information... Done
Building tag database... Done             
Couldn't find any package whose name or description matched "envyng-gtk"
Couldn't find any package whose name or description matched "envyng-gtk"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done 

...

So, I'm a bit lost. 
It might be a really simple matter but as I said (several times actually I think) I'm not really that much into computers (understatement ;) ) and having kicked off Windows all on my own is already a big achievement for me :mrgreen:

I'd be more than grateful if anyone could enlighten me :)

Thanks in advance!

---

### Post by philinux on 2008-07-22
post the output of

[FONT="Palatino Linotype"]lspci[/FONT]

---

### Post by coffeephen on 2008-07-22
This ?

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce Go 6200/6400] (rev a1)
06:03.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
06:03.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
06:03.3 Mass storage controller: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller
06:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
06:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 04)

---

### Post by philinux on 2008-07-22
Ok so you've got a

01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce Go 6200/6400] (rev a1)

Graphics card. Now we need to look in synaptic under nvidia to se which driver to use.

what's displayed under 
System>Admin Hardware Drivers

---

### Post by coffeephen on 2008-07-22
Oi, you're amazingly fast :)

Do I find this on the Nvidia website?

_________________________

Err...memo to myself:read first, reply thereafter.

Is synaptic another code or ...?

---

### Post by philinux on 2008-07-22
See previous post. did the system not offer to install the driver for you?

---

### Post by coffeephen on 2008-07-22
System>>Administration>>Hardware Drivers does bring up the option to download "NVIDIA accelerated graphics driver (latest cards)", but as I explained in my first post the download always fails. 

"W: Failed to fetch [http://security.ubuntu.com/ubuntu/po...18.41_i386.deb](http://security.ubuntu.com/ubuntu/po...18.41_i386.deb)
404 Not Found"

---

### Post by philinux on 2008-07-22
ah missed that.

post this

cat /etc/apt/sources.list

when you post it highlight the text and click the # symbol. This will wrap the text in code marks making it easier to read. Thats not the keyboard hash key.

---

### Post by coffeephen on 2008-07-22
Uh...that's a big lot of letters :confused: hehehe 

```
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy universe
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
```

---

### Post by philinux on 2008-07-22
Ok we need to edit that file.

gksudo gedit /etc/apt/source.list

See these last lines.
deb [http://**security](http://**security)**.ubuntu.com/ubuntu hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

They need changing to look like this
deb [http://**archive](http://**archive)**.ubuntu.com/ubuntu hardy-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-security multiverse

Once you've made the changes click the save button

Then in a terminal

sudo apt-get update && sudo apt-get upgrade

Then try the hardware drivers again.

---

### Post by coffeephen on 2008-07-22
I'm really impressed :)

Now, where do I edit this? Do I enter gksudo gedit /etc/apt/source.list in terminal also?

---

### Post by philinux on 2008-07-22
> **coffeephen said:**
> I'm really impressed :)

Now, where do I edit this? Do I enter gksudo gedit /etc/apt/source.list in terminal also?

Yes.

---

### Post by coffeephen on 2008-07-22
I entered it there and now I got an empty window to type something in. 

Do I need to open the part that needs editing from somewhere, copy it in there and then save it somewhere particular or something else?

---

### Post by philinux on 2008-07-22
If you make a mistake typing the file name, gedit, the text editor will create an empty file. Or in my case missing the s out of sources.

copy and paste is the best way, normally. i think I need a beer.

gksudo gedit /etc/apt/sources.list

---

### Post by philinux on 2008-07-22
In fact thats where I'm off to. The pub.

Hope it works. It should be fine.

---

### Post by Sbarton on 2008-07-22
> **philinux said:**
> In fact thats where I'm off to. The pub.

Hope it works. It should be fine.


Have one for me while your there :)
regards

---

### Post by coffeephen on 2008-07-22
awwwww...you so deserve your beer =D>

I edited it and tried the hardware driver thing again, which now says:

Device driver

  nvidia_new                      enabled 

:)

Does that mean it's installed?

---

### Post by philinux on 2008-07-22
Should be ok

---

### Post by coffeephen on 2008-07-22
Yup, seems to be :)

Thank you sooo much, that was awesome =D>

---

### Post by philinux on 2008-07-22
Ok thats a good result.

How did your sources.list get mangled.

You can thank anybody who helps by clicking the medal icon.

Don't forget it's best to start your own thread.

---

### Post by coffeephen on 2008-07-22
Ok, will do next time (it's often so discouraged in other forums that I didn't think about it being more practical on here ;) )

---

### Post by philinux on 2008-07-22
> **coffeephen said:**
> Ok, will do next time (it's often so discouraged in other forums that I didn't think about it being more practical on here ;) )

The guy who started the thread has no posted back. Very odd.

This forum is THE best.

Welcome to Ubuntu.

---

