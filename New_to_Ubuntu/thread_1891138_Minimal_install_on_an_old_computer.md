---
title: "Minimal install on an old computer?"
date: 2011-12-05
forum: New to Ubuntu
---

### Post by cshin9 on 2011-12-05
Hi, I want to know if I can do a minimal install of Ubuntu on a very old computer. I'm not sure when I got it, but it's probably at least 12 years old. I'm not sure about the specs either (because I'm away from home), but I know it runs Windows 98 (and you can guess how small the minimum requirements for that was). I'm having some doubts as to whether it can do a minimal install at all.

Does anyone know what the "minimum requirements" for a minimal install of Ubuntu is, and for those who have done a minimal install on old computers, how low the specs can go? And if I can't do a minimal install of Ubuntu, what other distros should I consider that's not DSL, Puppy Linux, or Macpup?

Thanks in advance!

---

### Post by mastablasta on 2011-12-05
You will need to give more info about computer (CPU, graphics, RAM and disk size).

Ubuntu needs 384 MB to run and a good processor with it.

if computer is really old you can try Lubuntu (but you still need about 256 MB ram to get much out of it). Lubuntu itself will take up close to 80MB RAM. then you still need memorry for the progammes to load.

DSL is not maintained anymore. It would be then better to try Slitaz or Puppy. 
There are a couple of others like Bodhi linux, TinyCore etc.

Just don't expect too much :)

---

### Post by cshin9 on 2011-12-05
I was thinking of doing a minimal install, then installing lubuntu-core using CLI. I know the hardware requirements for a full install of Ubuntu or Lubuntu, but what are the requirements for minimal install? And as I've said, I don't have the computer with me to give you the specs.

---

### Post by quadproc on 2011-12-05
To do a really minimal install you would need to install the server version of Ubuntu and omit as much as you can.  The graphical software eats a lot of memory.

Ubuntu claims that you can install amd run in 256 MB but my experience was that it isn't so; I have an old Dell GX110 that has 256 MB RAM and both Ubuntu and Xubuntu would run impossibly slowly while most applications crashed.  I settled on Puppy Linux and it works well on that system; its biggest drawback is that it is a single user system and that user is (necessarily) root so there is no protection.

Newer versions of Ubuntu require that the CPU be able to execute the cmov instruction.  This instruction appeared in the middle of the 686 processor lifetime.  If your CPU does not have that instruction then your only Ubuntu options are to use an older release that does not require cmov.

quadproc

---

### Post by mastablasta on 2011-12-05
> **cshin9 said:**
> I was thinking of doing a minimal install, then installing lubuntu-core using CLI. I know the hardware requirements for a full install of Ubuntu or Lubuntu, but what are the requirements for minimal install? And as I've said, I don't have the computer with me to give you the specs.

use the mini iso for that isntall. but as soon a syou go graphics you should have about 190 MB at least. problem is also programmes. running lighter ones should reduce the load. e.g. abi word instead of libre/open office.

if you go mini be prepared that a lot of stuff will be missing and must be installed. unless you know what exactly you need you might only find out later when you actually need it :)

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

you also need to have good internet conneciton to download the stuff you need.

server is not necessary to be installed ;)

---

### Post by cortman on 2011-12-05
I was real impressed with [Slax]("http://www.slax.org/") (even though it uses KDE and I'm a gnome fan), but I don't know if you can install it onto a PC HD or not. I always used it on a bootable flash drive.

---

### Post by snowpine on 2011-12-05
The Ubuntu hardware requirements are well-documented here:

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Minimal Install has the same hardware requirements as Server Install:

> Ubuntu Server (CLI) Installation

    300 MHz x86 processor
    128 MiB of system memory (RAM)
    1 GB of disk space
    Graphics card and monitor capable of 640x480
    CD drive

This is before you add any graphical user interface or applications. You need to budget for that on top of the minimum specs above. I agree with the following recommendation and would not personally attempt to install Linux on a computer that didn't meet this minimum:

> 1 GHz CPU (x86 processor (Pentium 4 or better))
1 GiB RAM (system memory)
15 GB of hard-drive space (or USB stick, memory card or external drive but see LiveCD for an alternative approach)
800 by 600 screen resolution
Either a CD/DVD drive or a USB port for the installer media
Internet access is helpful

Where I live (New  York) you can get a Pentium 4 with 1gb ram for under $100 on Craigslist.

So the next step for you is to figure out what your hardware specs are, and then decide whether to keep it or recycle it and upgrade to a computer from this millennium. :)

---

### Post by mastablasta on 2011-12-06
you mean Ubuntu linux? because chrunchbang linux works rather well with 256MB ram, though it uses Debian stable...
 
yah for new, up to date, linux 1GB ram is what they need. Maybe 512Mb with Xubuntu and similar.

---

### Post by lykwydchykyn on 2011-12-06
If you're lucky that thing has 128 MB of RAM in it.  If it's built for Win98 I doubt it's much more than that, possibly as low as 32.

My short answer would be to look at slitaz, but check the link in my signature for the long answer :).

---

### Post by N00b-un-2 on 2011-12-06
if your computer has less than 128MB of ram, you may want to try out one of the 'boxes (fluxbox, openbox, IceWM, JWM, etc).  Otherwise, I would recommend Lubuntu.  A fresh install of Lubuntu uses around 80mb of RAM in my experience.  Otherwise, depending on your level of ability perhaps a CLI system might be best.  But definitely give Lubuntu a try.

---

### Post by Paqman on 2011-12-06
If you want a script to run that can help you out with building a system from the minimal install, check out my sig. The one thing it can't do for you is remove packages or DEs you decide you don't want, but it does log the stuff it installs so that you can remove it yourself.

Switching DE on an old machine will make a some difference, but it's worth bearing in mind that this won't help you unless you use lightweight apps as well. Gnome core running Abiword will be snappier than Xubuntu or Lubuntu running Libre Office, for example.

---

### Post by Paqman on 2011-12-06
> **mastablasta said:**
> 
yah for new, up to date, linux 1GB ram is what they need. Maybe 512Mb with Xubuntu and similar.

Not necessarily. A lightweight install of Ubuntu will run quite happily on 512MB. A Gnome-core install of an older version like 10.04 will idle at about 100MB of memory use.

---

### Post by mastablasta on 2011-12-07
> **Paqman said:**
> Not necessarily. A lightweight install of Ubuntu will run quite happily on 512MB. A Gnome-core install of an older version like 10.04 will idle at about 100MB of memory use.
 
 
yes you can see my other thread on how that ended. 256 Mb, 10.04 - works nicely until.... updates and then works like crap. extensivelly using swap eventhoguh free mem is available etc.
 
It all depends on what applicaitons you are using. for modern applicaitons and for quick work you need 1GB. of course 512MB should also work normal with Gnome and probably Unity 2D (unless GPU has good support).
 
but just think abotu it. Mozilla can easilly take 120+ MB, open a few open office docs, some MP3 music in background, add some other programmes and 512 Mb is really not enough anymore. though it should be fine to do most things.

---

### Post by DapperMe17 on 2011-12-07
Yes, Puppy sure can be configured with a user name/password at startup, as protection.

See here...[http://www.murga-linux.com/puppy/viewtopic.php?t=21338](http://www.murga-linux.com/puppy/viewtopic.php?t=21338)

---

### Post by Paqman on 2011-12-07
> **mastablasta said:**
> 
It all depends on what applicaitons you are using.

Totally. Although there are lightweight alternatives to anything.

> 
Mozilla can easilly take 120+ MB, open a few open office docs, some MP3 music in background, add some other programmes and 512 Mb is really not enough anymore.

Well, you obviously won't be able to multitask like on a more powerful machine.

For office docs I'd say avoid Libre/Open Office like the plague. Try the Gnome office apps (Abiword, Gnumeric, etc), or a browser based suite like Google Docs and Zoho (the latter of which actually integrates quite nicely into Ubuntu through [webservice-office-zoho]("apt:webservice-office-zoho")). Of course the command line apps for a lot of stuff like music players are pretty lightweight too.

Browsers are a bit of a stumbling block. If you want a full-featured modern browser it'll chew up a pretty obscene chunk of your memory, but you could make the best of that by simply running everything in the browser a la Chrome OS.

You should expect to swap at times on 512MB, but a modern desktop would definitely be usable if you're a bit cunning about how you do it.

---

### Post by cshin9 on 2011-12-12
I'm back home now, so I was able to find out what the specs on the computer were. It has 64 MB of RAM and a Pentium II processor. Even Windows 98 runs pretty slow on it. Before I do anything, I'm going to have to transfer some photos from the computer.

@lykwydchykyn: That was an informative link. Thanks!

---

### Post by mastablasta on 2011-12-12
that CPU is not supported by ubuntu kernel i believe.
you will need to use Slitaz or one of other distros that are made for older maschines.

---

### Post by yndesai on 2011-12-12
> **cshin9 said:**
> I'm back home now, so I was able to find out what the specs on the computer were. It has 64 MB of RAM and a Pentium II processor. Even Windows 98 runs pretty slow on it. Before I do anything, I'm going to have to transfer some photos from the computer.


Well That seems a reasonable machine. Just check few things. 

1. Does it support booting from CD ? (Chances are it should support)

2. If you want to use it for another 2~3 yrs (not a bad idea). Install max possible RAM on it. With 64MB RAM you will have to use the "Alternative installation CD" which is text based installation. Regular LiveCD will work only if you have @300MB RAM but you can still try.

3. Identify the purpose for which you want it to use. Hence Select the packages that you want to install.

4. Best would be install a light weight Xubuntu or Lubuntu and then add required packages using synaptic. Another way is to use Minimal CD [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) and get your packages. However GNOME will be too much for p2 hence better use XFCE / LXDE.

[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu) gives that P2 should be good enough for a resonable Lubuntu experience.

YNDESAI

---

### Post by lykwydchykyn on 2011-12-12
> **cshin9 said:**
> I'm back home now, so I was able to find out what the specs on the computer were. It has 64 MB of RAM and a Pentium II processor. Even Windows 98 runs pretty slow on it. Before I do anything, I'm going to have to transfer some photos from the computer.

@lykwydchykyn: That was an informative link. Thanks!

You're gonna want a lot more RAM to make that anything but a screaming pain to use.  Most of the Pentium II machines I've revived will go up to 256 Mb (at least), and that's usually enough breathing room to make (for example) Debian with LXDE reasonably usable.

Slitaz or Tinycore might be ok with the machine as-is, but you'll want to stick to lightweight applications.  RAM for machines that age can usually be found if you ask around a bit.

---

### Post by yndesai on 2011-12-13
> **cshin9 said:**
>  I'm going to have to transfer some photos from the computer.


You can use DSL (DamnSmallLinux) liveCD to transfer files from this m/c to a usb generally it supports the hotplug of usb.

---

### Post by MartijnNL on 2011-12-13
I used to run xubuntu (gutsy) on a Pentium 2 (old compaq) butI had acquired some used memory to get it to 256MB. It wasn't working very fast, but it was usable. Using lubuntu would probably make it a bit faster.

I thing the earlier advise to use the minimal CD ([https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)) might be the best way to go, if you're not afraid to install a lot of things manually (and to find out what you need). Otherwise using the alternate installer might be a better solution. I used the alternate installer at the time.

---

### Post by kemtnbkr on 2011-12-14
I was contemplating a similar build earlier, except with a Windows 95-running computer.  I was resigned to a CLI interface but then I found this useful tutorial for a minimal install: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

Also, the old rig I was looking at only has a 2gig HD, so even this minimal of an install takes about half that.  I was going to try to revive the old machine for my little brother to learn C and C++ on, but got distracted.  Now that I think of it, maybe I'll do that this Christmas...

---

### Post by mastablasta on 2011-12-14
^^note that i586 is not supported anymore on latest versions of Ubuntu.

---

### Post by cshin9 on 2012-09-12
Yeah, it's probably not possible on this computer. It doesn't even have an ethernet port. The most urgent thing is getting the data out of it, which includes some of my family's first digital photos. Well, I'll probably get to it when I have the time. And even then, I won't be installing the latest Ubuntu on it. Maybe an old version or a lightweight distro.

---

### Post by lykwydchykyn on 2012-09-12
If you can't get decent performance from Linux, you can try an AROS distribution like Icaros.  They run pretty well on old hardware, and have a surprising amount of software available.

---

