---
title: "The common question - Low Resource Distro?"
date: 2008-05-15
forum: Other OS Talk
---

### Post by The Joe on 2008-05-15
I'm trying to look for a (very) low resource Distro.
**The Specs**
128MB RAM (will soon upgrade add 256MB, removing 32MB, cba to work it out)
Intel Pentium II Processor - 331MHz
40GB HDD (formerly 8GB with jumper set to 3GB)
S3 Trio3D graphics card
Some obscure and old Creative sound card
Slow (40 something x?) CD Drive
Windows XP Professional SP3 (heavily cut down to Windows 2000 size with nLite and SP3 was slipstreamed so don't worry about the post-SP3 installation problems)

**The Model**
IBM Personal Computer 300GL (1998)

**What I've tried**
DSL - It was good but... It wasn't good enough. I guess it was because at the time I had no internet
Slackware - Did not install, and it's covered in "Bob" and I won't have anything to do with SubGenius.

**The Question**
So can anyone suggest a low resource distro? I would prefer something with C interpreters so I can build software, or .deb support

I think I'm more likely to try DSL-n next, but I would like some advice from the experts. When I used Xubuntu my graphics card simply wouldn't play with it.

---

### Post by wolfen69 on 2008-05-15
Puppy linux runs well on my laptop with only 160ram. it comes with alot of apps and looks good too. it will fly with 256ram. highly recommended.

---

### Post by smoker on 2008-05-15
i'll second puppy:
[http://www.puppylinux.com/](http://www.puppylinux.com/)

---

### Post by cardinals_fan on 2008-05-15
Zenwalk is great.  Run it with a minimal WM.

---

### Post by will1911a1 on 2008-05-15
Might want to consider Arch Linux as well. :)

---

### Post by chris4585 on 2008-05-15
ubuntu base, make your own system.  

Install xorg first, then a WM/DE and then your apps and tada, you have a fast computer on your hands

---

### Post by MONODA on 2008-05-16
zenwalk is nice but doesnt have a large package repo, I would recommend arch linux.

---

### Post by Midwest-Linux on 2008-05-16
Xubuntu - Use the "alternate desktop installer" as it will install on 128 MB Ram. Later when you upgrade to 256 MB you will notice how quick it is on so little hardware. I use it on two on my older 300 Mhz and 500 Mhz machines and it works good. 

Probably the best installable Linux out there that includes pretty much everything that you could want that runs great on older machines.


[http://cdimages.ubuntu.com/xubuntu/releases/hardy/release/xubuntu-8.04-alternate-i386.iso](http://cdimages.ubuntu.com/xubuntu/releases/hardy/release/xubuntu-8.04-alternate-i386.iso)



Alternate install CD

The alternate install CD allows you to perform certain specialist installations of Xubuntu. It provides for the following situations:

    * creating pre-configured OEM systems;
    * setting up automated deployments;
    * upgrading from older installations without network access;
    * LVM and/or RAID partitioning;
    * installs on systems with less than about 128MB of RAM (although note that low-memory systems may not be able to run a full desktop environment reasonably). 


[http://xubuntu.org/home](http://xubuntu.org/home)

---

### Post by volkswagner on 2008-05-16
Slax, based on slackware works great.  It is one of the few distros that handles ACPI on older bios out of the box.  It is installable.  I did have a problem with the install because I did not use the suggested LILO.  I installed it in a multiboot.  I installed ubuntu afterwards expecting grub to pick it up.  Grub did pick it up, but it does not log directly to GUI.  It booted to CLI first.

I think slax 5 is better for older hardware vs. slax 6.

Others to consider, especially with 256meg,

Xubuntu
Fluxbuntu

Ubuntu 7.10 works great on my pent2 400mhz with 386meg ram.  I could not believe it.  I still have to sort out ACPI to properly shutdown without hitting power button.

---

### Post by icecruncher on 2008-05-16
try tinyme. a pclinuxos deriviative using the openbox window manger. goes nicely for my PII on 192 mb ram. 
still in test 7 though, with an new version on it's way. (haven't run into any problems though)

---

### Post by DJiNN on 2008-05-16
+1 for Arch & TinyMe (Although i would only go with Arch if you're prepared to put some work in)  TinyMe is great, and runs really well on lower spec machines, with a nice desktop etc.

But i would also strongly suggest you check out [antiX]("http://www.antix.mepis.org") - i'm running it here on several machines, one of which is a P3, 450mhz with 128mb ram, and it's flying along. Debian based, so plenty of apps to choose from, and a very helpful community. :)

---

### Post by RumorsOfWar on 2008-05-16
I've tried Puppy, its good, but Ubuntu repositories are a big factor. 
I would try Fluxbuntu. (or ubuntu base, add Flux)  Once you get used to Flux, you may really like it, but unless you have 256 ram, use the ALTERNATE INSTALL disk ! ( I think this applies to any Ubuntu based install: 192 MB ram, unless shared video, then 256. Or alt install can work with 64 MB)

---

### Post by rlcomstock3 on 2008-05-16
I like Slackware, many people don't like it because of it's lack of package managment but I grew up on it, so it is just fine for me.  Also FreeBSD might be a good choice.  Also I second, third or fouth (whichever number I am) Arch linux.  They are all good choices.  

Linux Rules!  (I should say *nix Rules!)

PS Also debian... it is rather light.

---

### Post by Aearenda on 2008-05-16
I'd go for Debian with XFCE. It's way faster than Xubuntu on smaller machines, and you can use apt/aptitude/synaptic for package management just like on Ubuntu. There's a special setup CD for XFCE on Debian.

---

### Post by Ripfox on 2008-05-16
I have Puppy4 installed with xfce4 and it is freakin awesome on my 600mhz/256ram

I mean FAST.

---

### Post by CREEPING DEATH on 2008-05-16
> **Aearenda said:**
> I'd go for Debian with XFCE. It's way faster than Xubuntu on smaller machines, and you can use apt/aptitude/synaptic for package management just like on Ubuntu. There's a special setup CD for XFCE on Debian.

I'll second that, I've used that on much lesser machines.

CD

---

### Post by Twitch6000 on 2008-05-16
Debain or Arch.

---

### Post by Ripfox on 2008-05-17
What about this [http://debian.tu-bs.de/project/cpx-mini/](http://debian.tu-bs.de/project/cpx-mini/)

---

### Post by linuxlizard on 2008-05-18
I've got an older desktop running about those specs- 333 mhz, 128mb ram.

Highly recommend pcfluxboxos.

It's as fast as puppy, but has hundreds of full featured, modern apps in it's repositories like ubuntu. Instead of seamonkey, abiword and gnumeric as is found in puppy, I can run the latest firefox, open office and gimp and run them fast. I can also install hundreds of other apps with a click in synaptic (for example I use the machine for gizmo).

---

### Post by NightwishFan on 2008-05-18
Install Ubuntu minimal then:
```
sudo apt-get update && sudo apt-get install xorg xterm fluxbox xdm firefox synaptic
```
Then add apps as you will. You can leave out fluxbox and add xfce4 or icewm, etc it is your choice.

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by MaxIBoy on 2008-05-18
I've heard good things about MINIX 3.

---

### Post by MONODA on 2008-05-18
> I've heard good things about MINIX 3. yeah but that isnt exactly linux, or stable (currently) or eeasy to use. It also only has like 600 packages avalable to install.

---

### Post by MaxIBoy on 2008-05-18
He just asked for an OS, he didn't say what kernal.

And MINIX is *very* low-resource. No games released for it, but come on, you're not going to do much gaming on 256 megs of ram anyway, besides maybe solitaire. I should know, the school computers all have 256 megs.:(

---

### Post by Half-Left on 2008-05-18
Puppy linux is insanely fast.

---

### Post by exploder on 2008-05-18
AntiX is a good choice for a low resource pc. Anticapitalista has done a fine job refining Antix. I installed AntiX on a PIII 933 with 256 MB of RAM, the machine runs very nice. Only using 38 MB of RAM at startup!

The ISO is light, great choice of default applications and the default artwork is decent. Both Fluxbox and IceWM are set up well and the system is very usable from a default load.

I did have to clean up the residual config files but that was the only configuration I had to do. The old PIII system is now a perfectly usable machine now.

AntiX is a very good choice for a low resource pc!

---

### Post by Ripfox on 2008-05-19
> **exploder said:**
> AntiX is a good choice for a low resource pc. Anticapitalista has done a fine job refining Antix. I installed AntiX on a PIII 933 with 256 MB of RAM, the machine runs very nice. Only using 38 MB of RAM at startup!

The ISO is light, great choice of default applications and the default artwork is decent. Both Fluxbox and IceWM are set up well and the system is very usable from a default load.

I did have to clean up the residual config files but that was the only configuration I had to do. The old PIII system is now a perfectly usable machine now.

AntiX is a very good choice for a low resource pc!

P3 isn't exactly slow...I was talking about a P1 166mhz with Puppy4 working really good on it. Jwm is actually usable for a new user vs Fluxbox which is less new user friendly. Puppy4 would SCREAM on that machine...:)

---

### Post by Ripfox on 2008-05-19
Just tried the latest Antix on my P1

> Panic! This CPU is too old for this kernel

Bummer

---

### Post by DJiNN on 2008-05-19
> **Ripfox said:**
> Just tried the latest Antix on my P1
Bummer

Which release of Puppy 4 did you try? There are two different releases of Puppy, one with a newer (up to date) kernel and one with a slightly older kernel for older machines.  I'm not saying that it'll work, but it could be worth a try.?? :)

To the original poster - you could also perhaps check out "Grafpup" which is based on Puppy but uses Openbox as the WM (at least the newer version does). It's small, light, VERY fast, and has a great selection of apps. Otherwise try the last release of Puppy, (3.01?) or maybe even one of the slightly older "Community Editions" which work exceptionally well, and will almost undoubtedly work on that machine. :)

---

### Post by Ripfox on 2008-05-20
Dingo...the standard one not the 2.5 (?) kernel one.

---

### Post by The Joe on 2008-08-24
Woah I never really looked at this topic, sorry!

Those that said Xubuntu, I tried that. For some strange reason it simply "doesn't work" and I can't define "doesn't work" because I can't really explain what happened.

Ubuntu base.... hmm... I just -can't-.

Puppy Linux sounds like a good choice. A few of you said that.

Upgraded the RAM too - It's now 384MB.

But thank you all for your responses, I'll think I'll look into Puppy.

> **MaxIBoy said:**
> He just asked for an OS, he didn't say what kernal.
But I did mean a Linux OS ;)

---

### Post by zmjjmz on 2008-08-24
antiX would be great.

---

### Post by confused57 on 2008-08-24
Absolute linux might also be an option:
[http://www.pcbypaul.com/absolute/](http://www.pcbypaul.com/absolute/)

---

### Post by chris4585 on 2008-08-24
maybe Slitaz?

---

### Post by tel93 on 2008-08-24
> **will1911a1 said:**
> might want to consider arch linux as well. :)

+1. With icewm, wmaker, fvwm or openbox (not the SLOW fluxbox)

---

### Post by kaiju on 2008-08-24
+1 for arch.

many apps available from the official repositories + the arch user repository;
constantly up-to-date software (rolling release system);
no defaults except for the core system - you get to use whatever daemons/gui/apps you like;
one-word resume: genius.

---

### Post by ArtF10 on 2008-08-24
Arch Linux.

---

### Post by cardinals_fan on 2008-08-24
SliTaz.

---

### Post by kspncr on 2008-08-24
Here's a thread worth mentioning: [http://ubuntuforums.org/showthread.php?t=575456](http://ubuntuforums.org/showthread.php?t=575456)

I'm all for Puppy in terms of low-resources, by the way.

---

### Post by Sorivenul on 2008-08-25
Puppy or SliTaz.

---

### Post by mips on 2008-08-25
Arch or I have heard good things about SliTaz.

---

