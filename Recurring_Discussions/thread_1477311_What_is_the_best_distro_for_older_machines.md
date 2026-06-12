---
title: "What is the best distro for older machines?"
date: 2010-05-08
forum: Recurring Discussions
---

### Post by freshprints on 2010-05-08
Hey, 
first of all I'm a very new user of ubuntu (or any variant of linux for that matter) so please keep that in mind when responding to my question :P

im looking for the best distro for a Packard bell iExtreme 6003 which i bought in 2003, the only thing it would be used for is browsing the internet and maybe some im. anyway here are the details and i look forward to any help :)

Core

	Quasar (MS6786) V1.0 µATX motherboard
Name: Quasar (MS6786 KM400 Ver 1.0)
Type: µATX motherboard
Manufacturer: MSI 

	
		CPU

AMD Athlon XP 2600+

	Storage Components

	HLDS GDR-8162B DVD Drive
Name: GDR-8162B
Type: 16x DVD-ROM/40 xCD-ROM Drive
Manufacturer: LG / HITACHI, HLDS group
			

	HLDS GCE-8483B CD-R/-RW Drive
Product Name:GCE-8483B
Type: 48x CD-R/24xCD-RW Writer (for high speed CDRW media)/48x CD-ROM Player
Manufacturer: Hitachi-LG Data Storage
		

	HDD Seagate U9 series
Manufacturer: Seagate
Name: U9
Type: 3.5-inch IDE
Speed: 5400 RPM
			

	HDD Maxtor Falcon series
Manufacturer: Maxtor
Name: Falcon - Diamond Max 16
Type: 3.5-inch IDE
Speed: 5400 RPM

Modem

	Aztech CNR2900-W (C1) SEC modem
08-05-2003

---

### Post by spiky001 on 2010-05-08
Ubuntu will run on that fine karmic or lucid

---

### Post by snowpine on 2010-05-08
[The Ubuntu system requirements are published here.]("https://help.ubuntu.com/community/Installation/SystemRequirements") As long as you have at least 512mb of ram, you should have no problem. Take a Live CD for a test drive to be sure. :)

---

### Post by freshprints on 2010-05-08
> **spiky001 said:**
> Ubuntu will run on that fine karmic or lucid
 


> **snowpine said:**
> [The Ubuntu system requirements are published here.]("https://help.ubuntu.com/community/Installation/SystemRequirements") As long as you have at least 512mb of ram, you should have no problem. Take a Live CD for a test drive to be sure. :)

Thanks guys :) i'll be trying it out tomorrow as i have no monitor for it atm haha will post on whether it works with the live cd i made for this laptop tomorrow :P

---

### Post by ranch hand on 2010-05-08
Yes, ram is the real question here.  You need to know that.

If you have low ram you have a couple choices.

Get more ram.  Should be fairly cheap for a box that old.

Try Lubuntu 10.04.  It is pretty nice.  I have an install on my box.  I like it and it is very fast on my box (see my signature for box specs) but it is aimed at boxes with very little ram.  A lot of distros say they are light but most that are have a very poor gui.  This is a very light release wit ha nice gui.

Zenix is an Ubuntu respin that is also pretty light.  Not as light as Lubuntu but it is still down there pretty low on ram needs.  I think the gui is nicer on it.  Yes I have an install of it too (I have lots, it is fun).

---

### Post by -humanaut- on 2010-05-08
You don't need a super-light distro for that machine. I'd recommend VectorLinux or Salix (slackware based distros run excellent on older hardware) or if you wanted to stay in the Debian family tree why not Debian Squeeze with Xfce?

---

### Post by Swatfoot on 2010-05-08
You might want to check out Antix which uses fluxbox or icewm both are lightweight and look good but require intermediate linux knowledge. But out of the two my opinion is icewm is a little easier to config.

---

### Post by BT1 on 2010-05-08
In order from least to most resource hungry (to my knowledge):

Lubuntu
Xubuntu
Ubuntu - Kubuntu

I'm not real sure about Kubuntu since I've only tried it seriously for a month and I went back to Ubuntu. Ubuntu is just more newbie friendly to me than Kub is, and this is from my own personal experience of course, and doing my own field trials with people new to Linux (I've had family and friends use both for a couple of weeks and got their opinions). Xubuntu has (in my experience once again), more functionality out of the box than Lubuntu but as far as I've tested, Lubuntu is _fast_. So if you're wanting to stay in the direct Ubuntu family, Lubuntu or Xubuntu would be best for getting the most out of the hardware you have.

---

### Post by mkvnmtr on 2010-05-08
I have been running Ubuntu 9.04 on a box about like that . It runs fine. I am thinking about upgrading to 10.04 and it seems to use a lot more resources. In trying a minimal install of XFCE4 it uses more ram than 9.04. I tried Debian Squeeze with the standard install of XFCE4 and it is much better. It looks like it will be my next upgrade but I am running both in virtual box to see if Ubuntu gets better. It seems to use 3 times as much ram as debian. Really you just have to try them out to see what works on your machine.

---

### Post by Geoff918 on 2010-05-08
Lubuntu -- Not an official distro, but it may very well be once fully tested. This is designed specifically for low spec systems. New with 10.04

FTW

---

### Post by sidzen on 2010-05-08
SLACKWARE
absolute_13-1-0
zenwalk-gnome_6-0

DEBIAN
LinuxMint-8-Fluxbox
lubuntu-10.04

MANDRIVA
pclinuxos-lxde-mini-2010
unity32-2010-rc1_live

My new favorite for old PCs: ultilex-5.0.0
which is not really a distro but a multi-boot utility compilation with Slax, tiny core, puppy and more;
it will run without a hard drive from a bootable USB flash drive or storage device.  I put it on a friend's
Gateway Profile 3 w/o  a hard drive.  Have run the others on a Dell 4100, PIII, 512MB RAM, ATA HD.

---

### Post by ranch hand on 2010-05-08
> **Geoff918 said:**
> Lubuntu -- Not an official distro, but it may very well be once fully tested. This is designed specifically for low spec systems. New with 10.04

FTW
I am sure it will be an official member of the Ubuntu family with 10.10.  It is, right now a "foster" member.

There is actually a 9.10 release too but the 10.04 is a lot better and it is really ready to use.  The 9.10 never really got past the beta stage.

The main reason that I like it is the file manager (pcmanfm2).  I have nothing against xfce and thunar but pcmanfm2 is just a lot better for me.

I also find that, on my box, I can see no difference in resource usage between Xubuntu (xfce) and Ubuntu (gnome).

Do not even think about Kubuntu or any other KDE distro.  I will admit to not liking KDE but even if I did I would have to admit that it does not even try to be a light desktop environment.  I do have it on here with Mandriva so that people can see it if they want to.

I have had Kubuntu on and, frankly, think the Mandriva devs have it integrated better on their system.

---

### Post by BT1 on 2010-05-08
> 

My new favorite for old PCs: ultilex-5.0.0
which is not really a distro but a multi-boot utility compilation with  Slax, tiny core, puppy and more;
it will run without a hard drive from a bootable USB flash drive or  storage device.  I put it on a friend's
Gateway Profile 3 w/o  a hard drive.  Have run the others on a Dell  4100, PIII, 512MB RAM, ATA HD. 	

I currently do that with some computers that were donated to me without drives (Pent 2's, 3s, 4s), and it's really great. I don't use that software though, just use a good ol' fashioned partitioner and some optimized Ubuntu flavored distros. Most people who use the computers for just checking e-mails and stuff don't even notice the difference. Its more energy efficient than having a mechanical hard drive running inside, and less noisy too in many cases. Better than running ubuntu flavors as a live CD as well.

---

### Post by baruch60610 on 2010-05-08
I highly recommend Xubuntu, which is a lightweight distribution of Ubuntu.  I've got Xubuntu running on an old IBM ThinkPad with 128 Meg of memory.  I'm also running it on a 512 Meg eeePC.  They work quite nicely.

The smaller computer can do e-mail, Internet, word processing, many of the more useful tasks.  Probably couldn't run any games on it, but you could use this for basic chores.

---

### Post by coolbrook on 2010-05-08
You may like Arch Linux.  It's well documented.

---

### Post by k3lt01 on 2010-05-09
With 10.04 a full Ubuntu install will have difficulty with anything less than 512 mb of RAM. I have had to try various methods to do a fresh install of 10.04 on my laptop and eventually had to do a clean install of 9.10-alternate and then update, over the net with Update Manager, to 10.04. After I did that I then had to remove a few things to get it to run with 256 mb of RAM. Be very aware that ureadahead will make an absolute massacre of a low RAM system. I still have to remove it to get my system to operate effectively.

---

### Post by freshprints on 2010-05-09
hey guys, im having some problems booting from a cd, ive gone into the BIOS setup an changed it to boot from cd and it has booted so far then restarted and its now stuck on the boot screen before loading into xp again. does the computer have to be connected to the internet for the boot to work? i dont understand what the problem would be. ive tried it with a ubuntu 10.04 disk, lubuntu disk and linux mint with the same results.

---

