---
title: "Lubuntu newbie"
date: 2021-05-22
forum: New to Ubuntu
---

### Post by dpeddle66 on 2021-05-22
Hi,

New to installing different operating systems.
I have only used Windows, and not really into programming.

I have an old Vista laptop, and would like to try Lubuntu. 
I downloaded Lubuntu 18.04, and have the iso on my USB stick.

I managed to get the USB stick to load first, and got the Lubuntu display screen, with all the options listed.

I have really a basic question, does the first option listed " Install Lubuntu" permanently install the the system on my computer, or does it run from the USB stick?  I don't want to install it on my laptop; just trying the whole thing out. I was under the impression you could install it on the stick, and run it from there.

---

### Post by yancek on 2021-05-22
The install option will install to the hard drive.  There should be an option to Try Lubuntu which you can select to try Lubuntu and run it from the usb without making changes to your hard drive.

---

### Post by Impavidus on 2021-05-22
There should be an option to try Lubuntu before installing, whatever the words are exactly. That will start a live session. When you wish to install Lubuntu, you can start the installer from there. Simply running the live session won't change anything on your computer. Depending on how you created the live disk (with or without persistence), it may be possible for changes in your live session to be saved on the live disk.

Lubuntu 18.04 is no longer supported. LTS releases of Lubuntu only get 3 years of support (same for Xubuntu, Kubuntu, ..; only regular Ubuntu gets 5 years). The parts it has in common with regular Ubuntu are still supported, so it's not that bad, but still. Lubuntu 18.04 cannot be reliably upgraded to 20.04, so I suggest you start with Lubuntu 20.04. System requirements are about the same.

---

### Post by dpeddle66 on 2021-05-22
Thanks,
I wanted to try the latest version of Lubuntu, but I could only get a download for a 32 bit version; the latest being 18.04.
Are there other versions out there that currently supported for a 32 bit system? 
I just tried the Lubuntu version because it was suggested it was good for beginners, and not too complicated.

---

### Post by GhX6GZMB on 2021-05-22
First: from where did you get your Lubuntu .ISO file?
lubuntu.net is a cybersquatter, lubuntu.me is the official site.

Second: Ubuntu 32-bit is dead after 18.04. If you really have 32-bit hardware, lubuntu is the wrong choice.

---

### Post by dpeddle66 on 2021-05-22
It was .net.

Yes, I really do have 32 bit hardware...not sure what to do with it.
Wouldn't mind trying another operating system, but I have no idea what to try.

---

### Post by guiverc on 2021-05-22
I would bet your box is x86_64 (*amd64*), but sold with 32-bit windows as it was a $5 cheaper license from Microsoft, and makers understood most consumers understood $5 far more than 32-bit versus 64-bit, thus selling it with the 32-bit windows.

Lubuntu did have a later release than 18.04, but 18.04 outlived 18.10/19.04 due to being a LTS release, so later i386 releases make less sense than 18.04.

The manual for modern Lubuntu can be found at [https://manual.lubuntu.me/stable/](https://manual.lubuntu.me/stable/)

(to see the LTS release of the manual; ie. 20.04, you change "*stable*" to "*lts", ie. *[https://manual.lubuntu.me/lts/](https://manual.lubuntu.me/lts/) as the stable manual refers to latest 21.04)

32-bit hardware was made & sold into 2007 yes, but it was all cheap intel atom (before the atom itself became *amd64* as well during 2007), and to my knowledge x86 only atoms came with either Ubuntu or windows XP (*resurrected from sale-death as Vista wouldn't install on the 32-bit hardware which is what Ubuntu had used to be sold on netbooks*)

Given you grabbed your ISO from a non-Lubuntu, non-Ubuntu site (3rd party) I hope you verified the ISO using checksums from a legitimate site.

I'd suggest checking out you do need 32-bit,  If you need an alternative, personally I'd opt for Debian (i386) but if it came with Vista it'll be *amd64* I'm sure.  You can explore how much support Lubuntu 18.04 LTS has (ie. `ubuntu-support-status`), and read some of my 2c on alternatives at [https://discourse.lubuntu.me/t/lubuntu-18-04-lts-end-of-life-30-april-2021/2466/4](https://discourse.lubuntu.me/t/lubuntu-18-04-lts-end-of-life-30-april-2021/2466/4)

(Note: *amd64* is because AMD created x86-64, intel wanted the market to move to an backwards-incompatible IA64 architecture which failed to sell given there was an upward compatible alternative... intel's IA64 is now dead & intel use *amd64* ; don't be scared of *amd64* as it's correct even for intel cpus)

---

### Post by grahammechanical on 2021-05-22
The issue of 32 bit hardware needing a 32 bit operating system that is still supported is discussed in this thread. It might contain some useful information.

[https://ubuntuforums.org/showthread.php?t=2461998](https://ubuntuforums.org/showthread.php?t=2461998)

All computer operating systems do the same thing but in different ways and with a different user interface. I would not describe Lubuntu as "good for beginners." Just as I would not describe Ubuntu as designed for the expert. We use to say Ubuntu is for humans. Meaning a user does not need to learn lots of commands in order to keep the operating system in working order. The same is true for the various types of user interface that are available. Although it was not always the case.

In my opinion your biggest challenge is the installation. Even those of us who have done it before do not consider ourselves experts because it is not something we do all that often. Unless we like to try out different Linux distributions.

You have one thing in your favour. You will not want to dual boot Linux with Microsoft Windows on that machine. If the installation does not go as you would wish you can always try again from the beginning.

Lubuntu is built on Ubuntu which is built on Debian which is supporting 32 bit OS at least until 2024 and might continue longer. Her eis the link to their ISO image.

[https://www.debian.org/CD/live/](https://www.debian.org/CD/live/)

[https://cdimage.debian.org/debian-cd/current-live/i386/iso-hybrid/](https://cdimage.debian.org/debian-cd/current-live/i386/iso-hybrid/)

With Debian you can choose the User Interface that suits you. It appears that Debian offers two installers - Calamares installer and Debian Installer

[https://calamares.io/](https://calamares.io/)

You might find the Debian installer less helpful than Calamares. So, be prepared to try installing more than once.

Regards

---

### Post by Impavidus on 2021-05-23
I can't say that Lubuntu is easier for beginners. Not all people, not even all beginners, find the same things easy. But if that laptop originally came with Windows Vista, it must be at least 12 years old, so rather weak by modern standards. Lubuntu has the lowest system requirements of all Ubuntu flavours, so that's probably the right choice. Here's the official site: [https://lubuntu.me](https://lubuntu.me)

As stated above, it may be able to handle 64 bit, despite having a 32 bit Windows system. Would you mind sharing some hardware details with us? CPU, RAM, graphics. That may tell what's the best OS for that laptop.

---

### Post by dpeddle66 on 2021-05-23
Thanks for responding.

It's a Toshiba laptop, Intel Core 2 Duo CPU T5450 @ 1.66 GHz  1.67 GHz
2.00 GB Ram
As for the graphics, all that I can find is "Intel Graphics Media Accelerator Driver for mobile"
I realise this laptop is pretty old, didn't bother upgrading it, either.
I am currently using the Maxthon 5 browser on my laptop, still stable and fairly safe to use.
I can't see a link to attach a file from here, so I'll use cut and paste of a diagnostic report on my graphics.

	Intel(R) Graphics Media Accelerator Driver for Mobile Report




Report Date:		05/23/2021
Report Time[hr:mm:ss]:	13:33:12
Driver Version:		7.14.10.1329
Operating System:		Windows Vista (TM) Home Premium* , Service Pack 2 (6.0.6003)
Default Language:		English
DirectX* Version:		10.0
Physical Memory:		2037 MB
Minimum Graphics Memory:	8 MB
Maximum Graphics Memory:	358 MB
Graphics Memory in Use:	154 MB
Processor:		x86 family 6 Model 15 Stepping 13
Processor Speed:		1662 MHZ
Vendor ID:		8086
Device ID:		2A02
Device Revision:		0C




*   Accelerator Information   *


Accelerator in Use:		Mobile Intel(R) 965 Express Chipset Family
Video BIOS:		1436
Current Graphics Mode:	1280 by 800 True Color (60 Hz)






*   Devices Connected to the Graphics Accelerator   *




Active Notebook Displays: 1




*   Notebook   *


Monitor Name:		
Display Type:		Digital
Gamma Value:		2.20
DDC2 Protocol:		Supported
Maximum Image Size:	Horizontal: Not Available
			Vertical:   Not Available
Monitor Supported Modes:
1280 by 800 (60 Hz)
Display Power Management Support:
	Standby Mode:	Not Supported
	Suspend Mode:	Not Supported
	Active Off Mode: Not Supported
Raw EDID:
00 ff ff ff ff ff ff 00 32 0c 00 dc 00 00 00 00
00 10 01 03 80 21 15 78 0a b3 40 99 59 53 8d 27
25 50 54 00 00 00 01 01 01 01 01 01 01 01 01 01
01 01 01 01 01 01 bc 1b 00 a0 50 20 17 30 30 20
36 00 4b cf 10 00 00 19 00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00 00 00 00 00 00 fe 00 4c
47 50 68 69 6c 69 70 73 4c 43 44 0a 00 00 00 fe
00 4c 50 31 35 34 57 58 34 2d 54 4c 44 32 00 43


                                                                                                                                                                                            

thanks

---

### Post by Holger_Gehrke on 2021-05-23
According to [Intel]("https://ark.intel.com/content/www/us/en/ark/products/30787/intel-core-2-duo-processor-t5450-2m-cache-1-66-ghz-667-mhz-fsb.html") that's a 64bit CPU. The only potential problem I see with that system is the amount of RAM, especially since integrated graphics use some of that. Lubuntu either 64 or 32 bit should run with 2GByte, but you should look into getting more since some applications - the major browsers for example - really want more than that.

Holger

---

### Post by GhX6GZMB on 2021-05-23
Yes, the T5450 is 64-bit.
I run a couple of old laptops with 2 GB RAM on Lubuntu 20.04. Nice and fast, no problems with the memory size.

And stay away from lubuntu.NET !!
If in doubt, go to ubuntu.com at the bottom you'll find "Downloads", "Ubuntu flavours".

---

### Post by guiverc on 2021-05-24
The closest box I have to what you listed (and used in QA-testing) is

```
lenovo thinkpad sl510 (c2d-t6570, 2gb ram, i915)
```

and I've used it to run up to the current *development* release which currently is *impish* but will be Lubuntu 21.10 when released (in 2021-October).

Because of the limited RAM, I use that thinkpad sl510 differently to this my current desktop (which has 8GB of RAM), in that I tend to have fewer apps in RAM at the same time, and mentally consider how they'll interact with each other before I load them,  eg. on this box I'm happily running some GTK programs in the background, causing GTK libraries to be in memory for those apps, but Qt libs for the desktop & other programs; which I'd try and avoid if using my sl510 (with its 2GB), either using one program at a time, or not using any GTK apps and using a  Qt5 app instead.

I for sure would have swap enabled (partition or swap file, I'd probably say swap file is easier to deal with for newbies). Lubuntu 20.04 LTS doesn't offer to create a swapfile during install (later releases do with a checkbox), so I'll offer [https://discourse.lubuntu.me/t/how-to-create-a-swapfile-in-lubuntu-20-04-20-10/1959](https://discourse.lubuntu.me/t/how-to-create-a-swapfile-in-lubuntu-20-04-20-10/1959)

Lubuntu 18.04 LTS however installed with a swap partition by default; so if you re-install, you can re-use that too (depending on installation choices made; as you're new & its a new system, I'd probably forget about swap during installation and set it up post-install using the link I've provided in this post if it wasn't setup during install).

---

### Post by mastablasta on 2021-05-25
i am using Kubuntu on 2 GB laptop that takes away 0.5 Gb for graphics chip. it works but it is slow. system takes about 0.5 Gb so that leaves 900mb-1Gb free for applications. running browser and Libre office at the same time is a challenge. one app at a time works relatively well. if i have time & money i might still uprgade to at least 6 GB. it will make huge difference. laptops (older ones) have a lot slower hard disks than desktops so when they need to swap it is even slower than on desktop. and they need to swap when they are out of memorry. ideal upgrade would be RAM+SSD, but ram alone will brin in major difference. maybe oyu can get a good used one to upgrade to 4GB or 6 GB?

if you don't want to spent money on it (investing in new one or a newer used one would be better), then Lubutnu or Xubuntu should be quite light. if it's not your workhorse and you are willing to experiment a bit then try something like Antix (using IceWM - look a bit like windows 98) or Bunsenlabs linux (which uses openbox - you do things with right click on desktop). both are super light, debian based and consume very little resources.

another a bit unusual one is Bodhi linux which is ubuntu based and uses Moksha desktop. depending how you use the PC and for what it might be good enough for your usage.

---

### Post by dpeddle66 on 2021-05-26
I just had Lubuntu 20.04.2 running on my laptop. 
I could not create the ISO file on my USB with Rufus, however. So, I tried Universal-USB-Installer 2.0.0.4.
The load to my laptop started automatically, after a few seconds...didn't know what to expect, really.
Everything looks just fine, getting sound, and the connection to my wireless internet was very simple...just a password request.
One odd thing I just noticed, the time on my laptop is off by a few hours when I switched back to my Windows system.

thanks for all the help and suggestions

---

### Post by Holger_Gehrke on 2021-05-26
> **dpeddle66 said:**
> 
One odd thing I just noticed, the time on my laptop is off by a few hours when I switched back to my Windows system.


All Unix-like Operating Systems expect the hardware clock of the system to keep UTC and will set it that way after getting the time through ntp (network time protocol). Windows expects the hardware clock to keep local time. There are many tutorials on the net to make either system do it the way the other does it. Search either for 'make windows use UTC' or 'make Linux use local time'.

Holger

---

### Post by CharlesA on 2021-05-26
> **dpeddle66 said:**
> I just had Lubuntu 20.04.2 running on my laptop. 
I could not create the ISO file on my USB with Rufus, however. So, I tried Universal-USB-Installer 2.0.0.4.
The load to my laptop started automatically, after a few seconds...didn't know what to expect, really.
Everything looks just fine, getting sound, and the connection to my wireless internet was very simple...just a password request.
One odd thing I just noticed, the time on my laptop is off by a few hours when I switched back to my Windows system.

thanks for all the help and suggestions

You can either do what has been suggested or just force the clock to sync via NTP after you boot back into Windows.

---

### Post by dpeddle66 on 2021-05-27
Hi,
Just checking out online how to use Ubuntu with Persistence; a bit confused as to whether I can do this from the running USB.
There is a suggestion of LinuxLive USB Creator for Windows, but I read it will not work for the latest version of Ubuntu. Is this true?

---

### Post by ajgreeny on 2021-05-27
Normally a "live"system loses everything at reboot but if you create a persistent live system (still live, ie, not installed to the computer) any files you save after reboot will still be there in the system.

It is still a faIrly limited system however, and will probably run slower than an installed version, it is certainly a great way to test the OS.

---

### Post by CharlesA on 2021-05-27
> **ajgreeny said:**
> Normally a "live"system loses everything at reboot but if you create a persistent live system (still live, ie, not installed to the computer) any files you save after reboot will still be there in the system.

It is still a faIrly limited system however, and will probably run slower than an installed version, it is certainly a great way to test the OS.

Just to add to this... last I checked, it uses squashfs to store the persistent data.

I've made the mistake of trying to update a persistent live system before and it ended up using all the available space. I don't know why that was the case, but if I need an updated version, I do a new install of it.

---

