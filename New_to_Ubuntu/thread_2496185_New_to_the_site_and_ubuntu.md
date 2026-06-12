---
title: "New to the site and ubuntu"
date: 2024-03-17
forum: New to Ubuntu
---

### Post by tonyr55 on 2024-03-17
Hello everyone. 
Im new to Linux and ubuntu.
I just starting out with Linux.
I had an old pc the was running old windows 7.
Wand wanted to use it to play with Linux and ubuntu. 
Because to be totally honest I hate windows lol.
The mother board is a nforce-a939 ver 1.
Works absolutely fine with windows.
But when I install ubuntu with rufus build stick.
The installation goes through ok.
But on final reboot.
The pc hangs on the bios screen detecting drives and will not go any further.
Unplug the hdd and the bios boots ok 
Plug the hdd back in and stick on detecting drives. 
I have to plug the hdd in to another pc and this other pc dosent see the drive  till  I  go into disk management delete the drive then create again 
.then my other pc will see the drive.
I tried lots of other drives and exactly same problem.
And advice would be appreciated

---

### Post by oldfred on 2024-03-17
That old of a system probably will not run Ubuntu.
I have an old 64 bit XP era laptop with 1.5GB of RAM, and it would  not work with Ubuntu. 
I was able to install server version, and add a lightweight gui.
Bit surprised as I also was able to load Kubuntu which is more of a mid-weight flavor.
But also found using an external SSD made system functional as Limited RAM went to swap on old slow HDD, if I loaded more than one large app.

[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, Xubuntu, Ubuntu MATE, Budgie
Flavors of Ubuntu only come with three years of supported life (five years applies to Ubuntu Desktop, Ubuntu Server but not flavors)

---

### Post by tonyr55 on 2024-03-17
Im not shore about the system not running ubuntu.
Because I don't even get past the bios screen. 

> **oldfred said:**
> That old of a system probably will not run Ubuntu.
I have an old 64 bit XP era laptop with 1.5GB of RAM, and it would  not work with Ubuntu. 
I was able to install server version, and add a lightweight gui.
Bit surprised as I also was able to load Kubuntu which is more of a mid-weight flavor.
But also found using an external SSD made system functional as Limited RAM went to swap on old slow HDD, if I loaded more than one large app.

[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, Xubuntu, Ubuntu MATE, Budgie
Flavors of Ubuntu only come with three years of supported life (five years applies to Ubuntu Desktop, Ubuntu Server but not flavors)

---

### Post by Rubi1200 on 2024-03-17
An older computer that ran Windows 7 will almost certainly not be able to run a recent version of Ubuntu. I know this because I tested it to see what happens and the experiment failed.

Granted, your situation seems a bit unusual.

I would try another Linux distro and boot the computer to see if it will work/recognize your drive etc.

My recommendations to try are Bodhi Linux, AntiX, possibly MX Linux.

You can find a whole list of distros at Distrowatch and can even filter for your preferences e.g. Debian/Ubuntu based, Arch based etc.

---

### Post by tonyr55 on 2024-03-17
Yea it's very strange I having trouble understanding why it stops the bios from booting.
I have tried other distros.
Can't remember witch ones now.
But I have a lap top that came with vista when that first came out and I can load any Linux on that and it's older then the pc.
Also if I duel boot the hdd as long as I put windows on first doesn't matter which version of Windows I install.
I can install Any version of Linux and the pc and it  will work and run any Linux no problem.
Its just when I try to install a Linux on the the pc  only that the hdd holds the bios boot.
Its doing my head in as to why lol
> **Rubi1200 said:**
> An older computer that ran Windows 7 will almost certainly not be able to run a recent version of Ubuntu. I know this because I tested it to see what happens and the experiment failed.

Granted, your situation seems a bit unusual.

I would try another Linux distro and boot the computer to see if it will work/recognize your drive etc.

My recommendations to try are Bodhi Linux, AntiX, possibly MX Linux.

You can find a whole list of distros at Distrowatch and can even filter for your preferences e.g. Debian/Ubuntu based, Arch based etc.

---

### Post by MAFoElffen on 2024-03-17
Welcome to Ubuntu Forums!

Lets back up a bit...

We are talking 2004 to 2005... That board maxes out at 2GB RAM. It supports 4 IDE PATA drives and 2 SATA drives. The CPU slot is Socket 939. It and the BIOS supports AMD Athlon&#8482; 64 X2 Dual-Core/ Athlon&#8482; 64/ Athlon&#8482; 64 FX processor... The Graphics slot is AGP 8X/4X and it has 4 PCI slots. It is solely Legacy BIOS Boot. And IDE PATA drives haven't been available for many years... Nor can you find any PCI or AGP option cards, except old used cards on EBay...

Which CPU are you using? What graphics GPU? What (type) drives are you using?

Curious that it is having a drive issue. I ran those AMD NVidia NForce chipped boards in the mid-2000's with Solaris and Linux. (20 some years ago) But I had to make sure I updated the firmware for both the BIOS and the NForce chipset for it to work. (Dang. yes, I've been around for awhile.) Boards and CPU's like that had issues later for newer versions of Windows (version 8 on), because the series of CPU didn't have some capabilities that their Windows kernel started to require, but it still ran Ubuntu fine... That is, until after Ubuntu LTS 16.04, when Ubuntu releases required more memory than those boards originally supported.

Full blown Ubuntu now requires 4GB RAM minimum. It should still run Lubuntu okay.

You could make it run.... But I would seriously budget and save for a (used) newer motherboard, CPU, GPU. I understand it is what you have... I honestly think you would definitely be more satisfied, and enjoy yourself with something more current... Even if it was just from the last decade (2010s). Instead of struggling with something that old. There is the "challenge"... (That is at risk of dying at any moment.) Then there is ensuring you have a sound foundation to build upon.

---

### Post by tonyr55 on 2024-03-18
Hello mate its a and athlon 64 processor 3200+
A old nvidia card can't remember spec.
The thing I am struggling to understand is why does the latest ubuntu and any Linux distos work absolutely perfect if I duel boot get the menu where you choose windows or Linux and works absolutely perfectly so obviously if im Wright the machine runs Linux ok.
Which I have used ubuntu this way
Its just if I want to have Linux on the drive only after the install it holds the bios from booting.
Unplug the hard drive and the bios boots ok 
> **MAFoElffen said:**
> Welcome to Ubuntu Forums!

Lets back up a bit...

We are talking 2004 to 2005... That board maxes out at 2GB RAM. It supports 4 IDE PATA drives and 2 SATA drives. The CPU slot is Socket 939. It and the BIOS supports AMD Athlon™ 64 X2 Dual-Core/ Athlon™ 64/ Athlon™ 64 FX processor... The Graphics slot is AGP 8X/4X and it has 4 PCI slots. It is solely Legacy BIOS Boot. And IDE PATA drives haven't been available for many years... Nor can you find any PCI or AGP option cards, except old used cards on EBay...

Which CPU are you using? What graphics GPU? What (type) drives are you using?

Curious that it is having a drive issue. I ran those AMD NVidia NForce chipped boards in the mid-2000's with Solaris and Linux. (20 some years ago) But I had to make sure I updated the firmware for both the BIOS and the NForce chipset for it to work. (Dang. yes, I've been around for awhile.) Boards and CPU's like that had issues later for newer versions of Windows (version 8 on), because the series of CPU didn't have some capabilities that their Windows kernel started to require, but it still ran Ubuntu fine... That is, until after Ubuntu LTS 16.04, when Ubuntu releases required more memory than those boards originally supported.

Full blown Ubuntu now requires 4GB RAM minimum. It should still run Lubuntu okay.

You could make it run.... But I would seriously budget and save for a (used) newer motherboard, CPU, GPU. I understand it is what you have... I honestly think you would definitely be more satisfied, and enjoy yourself with something more current... Even if it was just from the last decade (2010s). Instead of struggling with something that old. There is the "challenge"... (That is at risk of dying at any moment.) Then there is ensuring you have a sound foundation to build upon.

---

### Post by MAFoElffen on 2024-03-18
> **MAFoElffen said:**
> 
Which CPU are you using? What graphics GPU? What (type) drives are you using?

Asking again... Info please.

---

### Post by tonyr55 on 2024-03-18
I think I have sorted it mate.
Im a bit busy at the moment but will post what it was when I get a mo 
> **MAFoElffen said:**
> Asking again... Info please.

---

### Post by MAFoElffen on 2024-03-18
LOL. No problem. I am very patient.

Another way to gather more info than you will ever need... Is to boot from the Installer LiveUSB > Use "Try" > Run the [UbuntuForums 'system-info' Script]("https://github.com/UbuntuForums/system-info") in my Signature Line. There is [a Sticky]("https://ubuntuforums.org/showthread.php?t=2475931") for it in the Top of this "New To Ubuntu" Section. Then just post the URL of where the report uploads to in a post.

Painless, safe, and fast.

---

### Post by tonyr55 on 2024-03-19
Happy days I sorted it lol.
Im now using ubuntu on said machine and now I'm having a play with ubuntu server lol.
The problem was my hard drives where set to gpt and not mbr.
As they was set to gpt my old machines bios didn't like it and wouldn't boot.
Changed the drives to mbr in disk manager on my other machine and each drive worked OK.
And using ubunto perfect yea &#55357;&#56396;

---

### Post by DuckHook on 2024-03-19
I'm glad that you got things running. However, I am of the same opinion as the other old&#8209;timers who have advised you so far: you will likely not be happy with your Ubuntu experience on that old machine. 2GB RAM is barely enough to run the OS alone. It will choke if you run anything else like a modern web browser or an office suite. If your goal is just to play with Ubuntu, then it will serve. But if you want an actually workable system, then many of the suggestions for lightweight distros that have already been made will serve you better.

I do note that you have Ubuntu Server installed. This is good and will give you many more options. If interested, take a look at my link: ***The Best 'buntu Flavour*** for a bird's eye view of what you can do to lighten the OS and run lightweight apps.

---

### Post by oldfred on 2024-03-19
Probably not a gpt vs MBR issue. You may not have had the bios_grub partition for grub to correctly install in BIOS boot mode.

BIOS only knows to jump to MBR to boot. And gpt has a protective MBR primarily for one partition table entry to say drive is gpt partitioned.
But gpt's MBR can be used for BIOS booting. Grub then has to have a 1 or 2MB unformatted  partition set as bios_grub for grub to correctly install.
I started using gpt with BIOS only desktop system in 2010. And have used gpt with my 2006 BIOS laptop system.

---

