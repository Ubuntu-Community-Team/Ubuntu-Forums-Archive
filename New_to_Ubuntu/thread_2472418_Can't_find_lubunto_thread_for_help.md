---
title: "Can't find lubunto thread for help"
date: 2022-02-26
forum: New to Ubuntu
---

### Post by jvee2 on 2022-02-26
I am trying to unstall lubuntu latest download on my new Google Chromebook without success. I can download to download file and have found how to make external drive .iso correctly (I think).  Cannot successfully install from that tho.

---

### Post by guiverc on 2022-02-26
Some specifics may help.

What Lubuntu are you trying to use?  You mention the *latest*, but not if you downloaded the 

 *- latest* respin of the Lubuntu 20.04.4 LTS (ie. the 2020-April release), or
- Lubuntu 21.10 (the 2021-October release), ie. *latest* release

as both are offered at Lubuntu's website (*each being the latest in different regards*).

Lubuntu only offer *amd64* ISOs for download, but Chromebooks come in a number of architectures as I understand it; is yours a *amd64* that matches Lubuntu ?, or *arm64* ? which won't be able to boot Lubuntu due to incompatible architecture.

I'd likely test your ISO write to media using a standard PC; watch the boot to ensure the media check messages report a valid write (ie. *no errors*).

---

### Post by jvee2 on 2022-02-26
My post was "last gasp" afterthought of +8 hours trying.  Deleted everything except what is on my external flash drive.  However, can't find original site but pretty sure it was 20.04.4.  Ready and for sure willing to start over if help available (grateful too).

---

### Post by jvee2 on 2022-02-26
Please note:  Google Pixel book I have is i7 Intel with SSD 500 gig.

---

### Post by mIk3_08 on 2022-02-26
> **jvee2 said:**
> My post was "last gasp" afterthought of +8 hours trying.  Deleted everything except what is on my external flash drive.  However, can't find original site but pretty sure it was 20.04.4.  Ready and for sure willing to start over if help available (grateful too).
Hi there. Here are some of the quick link that might help you in your installation of Linux L[COLOR=#000000]ubuntu[/COLOR] Operating System.Please [Click Here]("https://help.ubuntu.com/community/Installation/FromUSBStickQuick") for a Quick Install from USB. This is a quick guide to installing from a USB memory stick.
And Please [Click Here]("https://help.ubuntu.com/community/Installation/FromUSBStick") for Installation from USB - Installing from a USB memory stick (full version).
USB stick + grub - Similar to above but using grub. [Click Here]("https://help.ubuntu.com/community/Installation/FromCForUSBStick")
Installation/iso2usb - Overview: cloning and extraction, tools and a simple 'Do it yourself' extracting method. [Click Here]("https://help.ubuntu.com/community/Installation/iso2usb")
Smart Boot Manager - Installing from a PC which will not boot from a CD. [Click Here]("https://help.ubuntu.com/community/SmartBootManager")
Just follow some installation instructions for more best and accurate results. And Here some detailed instructions links from Installation/UEFI-and-BIOS configuration. [Click Here]("https://help.ubuntu.com/community/Installation/UEFI-and-BIOS")
Good Luck and Cheers.

---

### Post by Impavidus on 2022-02-26
You wrote you can't successfully install Lubuntu, but you didn't write how far you got. So you created a live disk.
- Can you tell your Chromebook to boot from the live disk?
- Does the live disk start booting?
- Do you get to the desktop in a live session?
- Can you see the hard drive in the live session?
- Can you partition the hard drive for Lubuntu?
- Can you install the Lubuntu files?
- Can you install the bootloader?
We know you can't boot the installed system, but where do you get stuck? Note that Chromebooks are a bit special. It's the price we pay for a cheap system with long battery life.

---

### Post by MAFoElffen on 2022-02-26
> **guiverc said:**
> Some specifics may help...

<EDITED>
Lubuntu only offer *amd64* ISOs for download, but Chromebooks come in a number of architectures as I understand it; is yours a *amd64* that matches Lubuntu ?, or *arm64* ? which won't be able to boot Lubuntu due to incompatible architecture.

Not to muddy the waters... "quiverc" is who I feel is a Lubuntu Guru.

@guiverc --
If arch arm64... It is possible through a different route... But just not from a Lubuntu ISO... All the arm64 packages for Lubuntu are in the Repo's. I've done it and have arch arm64 Lubuntu machines in my test section. If interested, I'll tell you how in PM.

---

### Post by guiverc on 2022-02-26
> **MAFoElffen said:**
> 
@guiverc --
If arch arm64... It is possible through a different route... But just not from a Lubuntu ISO... 

I realize that; some ARM installation media was created & tested out by [Rudra]("https://launchpad.net/~rs2009") if I remember correctly; but it's unofficial. [Dan ]("https://launchpad.net/~kc2bez")also tested out (*likely others too*) on some Pis awhile ago (*I meant to buy a SD card to I could test on my pi; yet never remembered*) particularly with Wimpys [*desktopify*]("https://github.com/wimpysworld/desktopify") which had issues with `sddm` (used by us & Kubuntu) but workarounds existed for that issue (*if the issue still exists*).

Our [web site]("https://lubuntu.me/downloads/") contains none of that though with official ISOs only (*loads of it will be on our discourse but not in single easy-to-read threads I bet*).  My wording probably wasn't ideal, but thank you.

---

### Post by uninvolved on 2022-02-26
They mention an i7 and, to the best of my recollection, none of those were ARM-based.

---

### Post by ActionParsnip on 2022-02-26
Could install the Ubuntu server version then run
```

sudo apt install lxde

```
Then reboot.

---

### Post by uninvolved on 2022-02-26
Lubuntu uses LXQt, not LXDE. The change was made after 18.04. I believe the package now would be "lubuntu-desktop" but I've yet to actually try that. It can also be done with tasksel from the server build, I'm pretty sure.

I think I'll spin up a VM and see how well it works.

---

### Post by uninvolved on 2022-02-26
FWIW and just to confirm... Using 21.10 Ubuntu, I installed Lubuntu with:

```
sudo apt install lubuntu-desktop
```

I did choose to use SDDM as the display manager. Ubuntu still works, but says I can't lock the screen without Gnome Display Manager. So, it mostly works still - from brief testing.

---

### Post by jvee2 on 2022-03-01
I do have a separate volume with 16.04 Ubuntu via Crouton on this Google Pixelbook i7, 16gb, 512gb. Seems to work OK except for USB C can't connect drive.  Used code suggested by Uninvolved above to try to install lubuntu-desktop instead.  All seemed to download and install smoothly.  However, when complete, I could not access setup for new files.  I could not even reboot from the install terminal (xenial).  Get whole series of errors: Failed to set wall message, failed to call ScheduleShutdown in logind ++, failed to run telinit 6--- ,  Need to be root  + more.

---

### Post by jvee2 on 2022-03-01
Maybe no advantage to me for lubuntu as this version of Ubuntu seems to run very well but with major problem only being no connect to USB C.  Maybe somehow need ugrade to newer version instead?

---

### Post by Quarkrad on 2022-03-05
Ubuntu 16.04 is not supported any more - I suggest you move to ubuntu 20.04.  I would boot to live session, delete your 16.04 volume and install 20.04.  With updated s/w and kernel you may find it solves your usb c issue.

---

### Post by guiverc on 2022-03-05
Ubuntu 16.04 LTS was the 2016-April release of Ubuntu (a *year.month* format exists so it's easy to know when a version was released; and when it reaches/reached EOL), and came with 5 years of *standard or public support*, ie. reached end of standard support in 2021-April.

- [https://fridge.ubuntu.com/2021/03/13/extended-security-maintenance-for-ubuntu-16-04-xenial-xerus-begins-april-30-2021/](https://fridge.ubuntu.com/2021/03/13/extended-security-maintenance-for-ubuntu-16-04-xenial-xerus-begins-april-30-2021/)

If your device is off-line, then 16.04 is fine; but it should be avoided if you're online to protect both yourself & those around you (*or sharing networks with you*). ESM or *Extended Security Maintenance is available, but its specific packages only, and does** not*** *include Lubuntu as its support ended in 2019-April for 16.04 as it was a flavor (flavors have shorter lives than main Ubuntu Desktop, Ubuntu Server**).*

You can verify your support status using the command

```
ubuntu-support-status
```

---

