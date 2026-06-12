---
title: "Installing the latest ubuntu on a celeron with 256k memory?"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by HeyLynx on 2008-08-30
Hello

Have an old celeron laptop running windows 2000.  Was thinking of having a linux experiment to see what having a Linux laptop was like.

The laptop will be used for the internet and open office stuff.

Would it be worthwhile to list all the bits of the laptop, such as screen motherboard drivers etc so I would know it would work with the old hardware?

I've run an old version of unbuntu live cd on the laptop and it seem to work fine.

What do you guys think?

---

### Post by Elfy on 2008-08-30
The newest version has a minimum ram requirement of 384MB ram for the livecd and the alternate 256MB.

I would either go for the alternate, which is a text based installer rather than livecd or xubuntu.

Alternatively install with the older version you have and upgrade from there, depends on the version you have.

---

### Post by Tom--d on 2008-08-30
Please use Xubuntu as that requires less memory :)

---

### Post by billgoldberg on 2008-08-30
The live cd is off limits, you'll need the alternate cd.

The gnome DE might be too much for you pc to handle.

I would suggest fluxbox as a WM (use fluxbuntu) or Xubuntu.

Fluxbuntu will be a lot faster than Xubuntu, but Xubuntu might be easier to use if you are new to Linux.

---

### Post by RedSquirrel on 2008-08-30
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by k3lt01 on 2008-08-30
Take a look at my signature below for my laptop's specs. I run Hardy and have done since it come out. Until yesterday I always installed it with the LiveCD without any difficulty. However yesterday I upgraded my Hdd from 40 GB to 250 GB and the laptop with the 250 installed would not take the LiveCD at all, it just hung at the opening screen. So I downloaded the alternate cd and installed Hardy (plain Ubuntu with Gnome) from that.

The only suggestion I would make is that you need to have some idea about your network. When I got to the install network screen it asked about dhcp and all so I just clicked ignore and went on to the next part and installed my network components (ndiswrapper and driver) when Hardy was running.

---

### Post by HeyLynx on 2008-08-31
ahh the version I have the cd for is version 5.04.

Also the celeron processor i have is a 466, the one thats around the pentium two area, i think.  Hence thinking that linux might be a way to keep it going.

---

### Post by halitech on 2008-08-31
You are going to want to get a newer version personally and I would go with Xubuntu as opposed to Ubuntu unless you can bump the memory up to at least 512. I have both running on my old compaq (p3 750 with 256meg of ram) and Xubuntu works better as far as system speed but is missing a few network tools that Ubuntu has.

(ps. I'm guessing you meant 256Meg of ram and not k ;) )

---

### Post by HeyLynx on 2008-08-31
Ok the system details

Motherboard - Clevo Co 320 series
Proccesor - x86 family 6 model 6 stepping 
Memory 261,616kb
Screen-Digital flat panel 1024x768
Adaptor-ATI Rage mobility P\M Mobility AGP2x
CD Rom - Toshiba Cd Rom XM-7002B
Soundcard Yamaha native DS1
Hard Drive- Toshiba MK1214GAP 11.23GB
Network card - FE574B 3COM 10/100 LAN pccard Fast ethernet 
USB - Intel 82371 AB/EB pci to USB universal host controller.

Is there any where I can check which would be the best Ubuntu to use with these parts.

Thanks for the help

---

### Post by Elfy on 2008-08-31
You will be better using xubuntu with that amount of ram.

[http://www.xubuntu.org/get](http://www.xubuntu.org/get)

---

### Post by halitech on 2008-08-31
you can find info here: [http://www.psychocats.net/ubuntu/whichbuntu](http://www.psychocats.net/ubuntu/whichbuntu)

go to the section on Desktop CD, Alternate CD, or Server CD?

basically your 2 main concerns are the speed of your processor and the amount of ram so personally I would go Xubuntu as it should work fine on your system.

---

### Post by t0p on 2008-08-31
My desktop computer has 256MB RAM and a Pentium 4 processor.  I have always installed Ubuntu with Live CD, and have always used the latest Ubuntu (ie with Gnome desktop) with no problems.

The computer isn't the fastest box around, but it's certainly usable.  I have also run it with Xfce, and I don't take that much of a speed hit using Gnome.

---

### Post by lazyart on 2008-08-31
With a 466 mhz processor--  correction, with a 466 mhz CELERON processor, the laptop makes a better doorstop than a Ubuntu candidate.  Try Puppy Linux or DSL (Damn Small Linux).  You will be disappointed with the performance otherwise.  A 466 mhz processor is a FAR CRY from a P4.

You might also want to verify that you can boot from a CD.  A machine of that era might only boot from floppy disk.

Good luck in your endeavor.

---

### Post by dai_vernon on 2008-08-31
If you are proficient with linux (or just don't mind spending the time) I'd go with fluxbuntu over xubuntu; those hardware specs are in the vicinity of 'crazy low' and I think fluxbox is more suited to them.

Plus its prettier. :P

edit: Damn or Puppy Linux would probably be somewhat more suited, but if you have any experience with *buntu I'd say still go with fluxbuntu because it will work in a way you're used to (package manager etc.).

---

### Post by lisati on 2008-08-31
My older laptop has 256Mb ram and a Celeron - the initial installation went smoother with the "alternate" cd than with the "Live" CD.  It currently runs Ubuntu 7.04, gui and all, no major hassles. Apart from a tweak to get the USB mouse working reliably there wasn't any hassle.

---

### Post by egalvan on 2008-08-31
> **lazyart said:**
> -  correction, with a 466 mhz CELERON processor,.  Try Puppy Linux or DSL (Damn Small Linux).  You will be disappointed with the performance otherwise.  A 466 mhz processor is a FAR CRY from a P4.

You might also want to verify that you can boot from a CD.  A machine of that era might only boot from floppy disk.

Good luck in your endeavor.

+1

I vote for Puppy Linux. The latest version (v4.x) is very nice, and works well on limited hardware.

Also, Puppy might be easier to set up than DammSmallLinux. YMMV

ErnestG

:popcorn:

---

### Post by lazyart on 2008-08-31
> **lisati said:**
> My older laptop has 256Mb ram and a Celeron - the initial installation went smoother with the "alternate" cd than with the "Live" CD.  It currently runs Ubuntu 7.04, gui and all, no major hassles. Apart from a tweak to get the USB mouse working reliably there wasn't any hassle.

Before you suggest that this will work on the OP's computer, what speed is your Celeron?

466 mhz is really, really slow.  We're speaking Pentium 2 speeds.  And being a Celeron, it's likely equivalent to a 266 or 300 mhz Pentium 2.

---

### Post by pi.boy.travis on 2008-08-31
I tried running Ubuntu 8.04 on a similar machine.  It was an old Dell, and it was horribly slow.  I still get nightmares. . .  I could have used Xubuntu, but I ended up buying a 1GB upgrade instead.  You can install Ubuntu via the alternate CD, and it should work. . . just very, VERY slowly.

---

### Post by egalvan on 2008-09-01
> **lazyart said:**
> Before you suggest that this will work on the OP's computer, what speed is your Celeron?

466 mhz is really, really slow.  We're speaking Pentium 2 speeds.  And being a Celeron, it's likely equivalent to a 266 or 300 mhz Pentium 2.

Yeah, Intel has used the Celeron label for everything from that useless C300 (with no cache) - what a dog), up to a 3.GHZ cpu (that still only has 128k)

That said, I have used Puppy on under-powered rigs, 500Mhz-PII with 256M.
Xubuntu ran OK,. Firefox was slow.

Puppy was much peppier.

And   big +1 to your tag-line

[SIZE="3"][COLOR="Red"]It's all about choice, right? Then stop flaming Windows users.[/COLOR][/SIZE]


Cannot agree more, and I'm a Microsoft hater.

ErnestG

:popcorn:

---

### Post by dai_vernon on 2008-09-01
It's not just the window manager that is important here, the apps are just as much so.  Fluxbuntu uses the non-java AbiWord/Gnumeric suite and Kasehakase for its browser - both have a much smaller footprint than OOo or Firefox.

---

### Post by snowpine on 2008-09-01
> **HeyLynx said:**
> Hello

Have an old celeron laptop running windows 2000.  Was thinking of having a linux experiment to see what having a Linux laptop was like.

The laptop will be used for the internet and open office stuff.

Would it be worthwhile to list all the bits of the laptop, such as screen motherboard drivers etc so I would know it would work with the old hardware?

I've run an old version of unbuntu live cd on the laptop and it seem to work fine.

What do you guys think?

If you want the latest version of Ubuntu (8.04 Hardy Heron), my recommendation for an older system is Crunchbang. It uses Openbox as the windows manager and is full-featured (OpenOffice, lots of multimedia apps, etc.). 

Fluxbuntu is about a year old (7.10 Gutsy Gibbon) and is fast both because of the Fluxbox windows manager and its suite of lightweight apps (Abiword, Gnumeric, Kazehakase, Rox-Filer, etc). You can easily install "heavier" apps from the Ubuntu repositories if you need them (and if your computer can handle them). 

SliTaz is not part of Ubuntu, but it's tiny and incredibly fast. The latest "cooking" version uses Openbox and feels amazingly "modern" for such a lightweight distro. There are tradeoffs, though--it really runs best as a Live CD (which you can easily remaster) and its repositories are limited (no OpenOffice for example).

---

