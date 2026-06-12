---
title: "Dual Boot Help Please!"
date: 2013-05-26
forum: New to Ubuntu
---

### Post by jim89 on 2013-05-26
Hi all,

First post here. I'll summarise:

I was a long time Windows user but decided to give Ubuntu a go at the start of this year. After some teething problems (caused, I think, by having an SSD and a UEFI motherboard rather than standard BIOS) After some messing about re-formating and creating the necessary partitions with a gParted LiveDisk I managed to get Windows 7 installed along side Ubuntu on my 120GB SSD. At the time, I simply installed Windows, went back and installed Ubuntu and then never felt the need to go back to Windows as I had no need for anything it offered.

Cut to now - I wanted to go back in to Windows to play some games that won't run on Ubuntu (at least not without faffing about with Wine for a very long time) so hopped back in to my other partition. Turns out that because I'd never used it the Windows install had expired and so I did a re-format and re-install of/into the Windows NTFS partition. I then lost my Ubuntu installation (as Windows overwrote my MBR - yay) and had to use EasyBCD to add Ubuntu to my Windows boot options and then re-enable Grub2, which I did successfully.

However, once that had been done I went back in to Windows to install updates/drivers/anti-virus etc before I could game on it. I have an ATI HD7970 card so went to download the proprietary drivers, which is where I encountered a problem. When I installed the drivers, I'd load in to Windows and be presented with just my desktop background present, explorer.exe did not seem to have loaded and I couldn't even Ctrl-Alt-Del to open up the task manager and start explorer afresh. After a bit of google-ing I found the driver release notes ([http://support.amd.com/us/kbarticles/Pages/AMDCatalyst13-4WINReleaseNotes.aspx](http://support.amd.com/us/kbarticles/Pages/AMDCatalyst13-4WINReleaseNotes.aspx)) which say I need to install SP1 and .Net SP1 before installing the drivers.

So, I restored Windows to pre-driver installation and fully updated eveything with Windows Update and made sure the mb chipset drivers were installed, too. I then re-installed the drivers and encountered the same problem. 

So now. I can get in to and use perfectly my Ubuntu installation (12.04) just fine (which is where I'm writing this from!) but Windows seems to be screwed. Could this be anything to do with also having Ubuntu installed at the same time? I'm guessing not as Windows essentially doesn't see Ubuntu and just sees its own 60GB partition, but I thought I'd check.

If I can't find a fix for this I'm wondering if a complete wipe of the SSD in gParted would be a sensible option? Then a full re-install of Windows followed by Ubuntu along side and hopefully I'll be good to go.

It doesn't seem like my Ubuntu installation is messed up, so I'd like to avoid that option as it seems that it's Windows being the problem here. Would love to hear your thoughts, though. Thanks a lot for any helpful advice!

J.

---

### Post by Paqman on 2013-05-26
> **jim89 said:**
> Could this be anything to do with also having Ubuntu installed at the same time?

Highly unlikely. As you say, there isn't really any connection between the two. A fresh start will probably work, as it's a bit hard to say what's wrong with Windows. I'd say go ahead with the reinstall, get Windows up and running properly, then stick Ubuntu back on and you should be good to go.

---

### Post by jim89 on 2013-05-26
Eurgh, that's not what I wanted to hear :P

Ok, just run my gParted LiveCD again to re-familiarise myself with the options in there and have run in to another problem. When I try to run from the LiveCD I get all the way through the various options and loads and then my screen just turns off, seemingly just as gParted starts. When I say turns off I mean it suddenly shows the "no signal" flashing LED rather than the "On and receiving data" static-on LED, so it's not just a blank screen, it's like my screen suddenly becomes disconnected from the machine. Thoughts? Are there options I can configure in gParted LiveCD before I try to boot in to the GUI to re-format and re-partition everything?

---

### Post by Paqman on 2013-05-26
Does you graphics card need drivers to work in Linux? If you can boot up an Ubuntu LiveCD or USB you can use Gparted from there (it's preinstalled), you don't necessarily need to use the Gparted LiveCD if it won't boot on your machine.

---

### Post by jim89 on 2013-05-26
Not sure if the graphics card needs drivers to work in Linux - how might I find that out?

---

### Post by Paqman on 2013-05-26
> **jim89 said:**
> Not sure if the graphics card needs drivers to work in Linux - how might I find that out?

If it boots and you can use the screen, you don't need drivers.

I suspect the Gparted LiveCD may be based on an older kernel or doesn't include some of the stuff you get on the Ubuntu disk, and that's why it isn't working. Since you know Ubuntu will boot up into a live session (because that's how you installed it) just use that. Gparted on an Ubuntu disk is exactly the same as Gparted on a Gparted disk.

---

### Post by jim89 on 2013-05-26
Ok so the Ubuntu disk is now giving me the same problem. No video signal once I get past the initial splash and code screen(s). Basically once it gets to the point of actually loading in to the desktop environment on either gParted or Ubuntu liveCD the video signal cuts out. Should I try running video from the CPU/onboard graphics rather than the GPU, or do you think there is a work around?

---

### Post by as2000 on 2013-05-26
Did you do an MD5 after creating the Ubuntu cd? Just a thought...

My experience with dual booting is to defrag the Windows partition before you run Ubuntu setup.

---

### Post by jim89 on 2013-05-28
I did not do an MD5, no. How do I do one in Ubuntu?

---

