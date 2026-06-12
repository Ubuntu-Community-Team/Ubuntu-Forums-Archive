---
title: "What distro will work in a Toshiba Libretto 70CT?"
date: 2007-09-22
forum: Other OS Talk
---

### Post by tico on 2007-09-22
I've got an old Toshiba Libretto 70CT (mini-notebook) with Windows 98 installed and runing MS Office 2000 (works a bit slow, but's ok, nothing terrible). I'd like to install Linux (no dual boot, I will format my Windows partition), but it's a pretty old hardware. So, what distro could be installed into this computer? I need a GUI and would like to be able to use Writer (Openoffice). This computer doesn't have a CDRom driver, just a floppy (and I can connect it to another computer through laplink to transfer big files). This is its hardware:

Pentium
16 Mb ram
1,2 Gb HDD
video memory 1 or 2 Mbs, I thing
Floppy
No CD driver.

Any suggestion about a good distro?

Thanks.

---

### Post by Kingsley on 2007-09-22
I suggest Puppy Linux. It's a lightweight distro.

---

### Post by tico on 2007-09-22
I know Puppy Linux. It's nice, but is there a way to install it without a CDRom drive?

---

### Post by irieken on 2007-09-27
> **tico said:**
> I know Puppy Linux. It's nice, but is there a way to install it without a CDRom drive?

Here are a few routes that I recommend:

1.) If you have another laptop that does have a CD drive, move the hard drive into that computer, and install normally. Transplant the hard drive back into the Libretto, and you'll be all set.

2.) You can buy a 2.5in-->3.5in adapter, and use a desktop computer in the same manner.

3.) If you have a USB-->IDE 2.5in HD adapter, you can use VirtualBox to install Linux to the HD by creating a VMDK raw disk for your Libretto's HD.

I'm not sure what you'll be able to do with only 16MB of RAM, but the best of luck to you:)

---

### Post by timetrap on 2007-10-09
I have one of these also . . . I managed to get openbsd 4.1 running without too much trouble; It is one of the few modern operating systems that can still be installed with a floppy (and a NIC).

It is funny how much hardware that I have accumulated for this thing. Of course all of the PCMCIA devices must be 16bit . . .

Floppy drive
NIC
Wireless 802.11b
CDROM

They all work great, just the CDROM won't work.

Oh yeah, and a 40GB hard drive . . . not that I use it, just had it laying around.

I think I am going to try and install Ubuntu Server next.

---

### Post by Sef on 2007-10-09
[Linux Floppy Distros]("http://www.linuxlinks.com/Distributions/Floppy/")

---

### Post by 900donuts on 2007-10-09
again linux links is terrible every thing is outdated if you want floppies and don't want to put the drive in a big computer try either 

basic linux 3.5 (a 2 floppy distro with gui)
deli linux (a light weight distro with installation floppies)
debian (this is what i plan to use on my omnibook800ct and can be installed with floppies)

also see this thread [http://ubuntuforums.org/showthread.php?t=569167](http://ubuntuforums.org/showthread.php?t=569167) i'm trying some thing similar (i know nothing i have tried yet has worked for me but i have a odd mouse you could be different)

if you want to put it in a big computer try dsl

p.s. are you sure its 16mb of ram hat seems to small for 98 with office 2000

---

### Post by jaqie on 2008-01-12
I found this thread trying to find more information on 70CT hardware hacking and wifi drivers, thus I expect others find it as well. On topic - this old minilaptop is just too low spec to handle ubuntu, plain and simple. It does not even have PCI, the video card is a chips & tech 65555 1MB VLB card, the internal hard drive controller is not even DMA, it is on the ISA bus as is everything except video. And even that, the system can only be upgraded to 32MB ram total, and the CPU is an intel Pentium 166 or 200 MMX underclocked to 120Mhz.

The only real options are the extreme low end linuxes, here is a list for anyone else wanting to know of good distros to try on their little libretto 70CT or similar.

Puppy Linux
DSL
DSL-N
FreeBSD (and the other BSDs, not including FreeSBIE and PCBSD, they are way too heavy)
ZipSlack (outdated, meant to fit on and run on a ZIP100MB disc)
Vector Linux

I myself am a fangirl of FreeBSD so I run that on my 70CT. It is very much a do it yourself *nix OS... which means if you do it yourself (and can learn how as you go) you can make a very lean, mean install.  A few hints if you decide to go fBSD route:
1) recompile kernel without any modules you won't need. no AGP no PCI no USB in the CT70, no SCSI cards so you can nix most of those, same with almost all the network drivers... google and find out what all you can nick out of that.
2) install a very light windowmanager, never ever use KDE, the heaviest WM you should use on the little 70CT is XFCE. there are much lighter ones you can try, again google for them.
3) buildworld and buildkernel *WILL* take a long time, be ready to just set the thing down for a few days (almost a week) and let it do its thing while you do other stuff. this will also be a very, very good way to make sure the hardware is good - a kernel compile will definitely bomb out if your hardware is in any way marginal, especially on such old hardware.
4) [http://dfwlpiki.dfwlp.org/index.php/Installing_FreeBSD_6.2](http://dfwlpiki.dfwlp.org/index.php/Installing_FreeBSD_6.2) use this as a guide for how to install.
5) at the above link, there is a tutorial on how to set up another machine to compile ports for this machine to fetch instead of you compiling all things local on the little P120MMX CPU. it will save an absolute ton of time, and look up some optimizations while you are at it, that will help a lot on such a low stat system.

---

