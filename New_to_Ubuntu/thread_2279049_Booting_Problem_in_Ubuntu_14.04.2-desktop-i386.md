---
title: "Booting Problem in Ubuntu 14.04.2-desktop-i386"
date: 2015-05-20
forum: New to Ubuntu
---

### Post by alfred9 on 2015-05-20
Hi,

I have a problem booting my Ubuntu using a bootable USB, When I choose install the ubuntu what happened is automatic restart my desktop it is not continuing to boot and install the ubuntu, My desktop is Dell Optiplex 740, OS windows XP Dual core

Please help me what was the problem.

Thank You
Alfred Galit

---

### Post by alfred9 on 2015-05-20
Hi,

What is the system requirements for Ubuntu 14.04.2 desktop i386 ?

My system specs is:

Win Xp pro 32 bit
AMD athlong 64x2 dual core processor
2 GB Ram

Can I run ubuntu with that specs ? Please reply asap

Thank You
Alfred Galit

---

### Post by newb85 on 2015-05-20
Welcome!

My last desktop PC had similar specs (though you didn't say anything about your graphics card/chip).  It's been a couple years since the motherboard gave up the ghost, but she was pretty slow with regular Ubuntu.  It ran, but not very impressively.

I'm guessing you would need a lighter variant, like Xubuntu or Lubuntu, with Lubuntu being the lightest.

I recommend that you create the installation media and simply try each one out, and see how well they run and how well you like the interface.  If your BIOS will let you boot from a USB, go that route.  Otherwise, you'll have to create DVDs/CDs.

Best of luck!

---

### Post by alfred9 on 2015-05-20
Hi,

Actually I use USB, When I boot on my desktop I see the Ubuntu logon and the choices after I choose any of the choices it is automatic restart my computer it is not continue to boot. What was the problem ?


Primary Chipset GEForce 6150 LE.

Thank You
Alfred Galit

---

### Post by newb85 on 2015-05-20
You mean that after you select "Try Ubuntu" or "Install Ubuntu", it automatically reboots the machine?  How did you create this USB, and how did you download the .iso?

---

### Post by v3.xx on 2015-05-20
My first guess would be that your trying to run Ubuntu, which is resource demanding and your dell is not up to the demands.

There are options if this is the case:
Ubuntu Mate
Lubuntu
Xubuntu

---

### Post by sandyd on 2015-05-20
**Threads merged**

---

### Post by alfred9 on 2015-05-21
Hi,

I download the .iso to ubuntu site and there's a step by step how to create bootable usb. I use universal usb installer. Here's the link.

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop), [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

Regards,
Alfred F. Galit

---

### Post by leunam12 on 2015-05-21
Did you try booting from a DVD? Sometimes a live session that won't boot from USB will boot from DVD and the other way around.

---

### Post by alfred9 on 2015-05-21
Hi,

No not yet, No other solution for that ? Only boot on CD is the alternative solution ?

Thank You

---

### Post by mattharris4 on 2015-05-21
> **alfred9 said:**
> Hi,

I download the .iso to ubuntu site and there's a step by step how to create bootable usb. I use universal usb installer. Here's the link.

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop), [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

Regards,
Alfred F. Galit

Forget that method.  Download UNetbootin on another computer (there are versions that work on Linux, Mac and Windows) and use that to download whatever version of Linux you want.  Using Canonical OSes it can be downloaded through the Ubuntu Software Center.  If you need to do this on a Windows or Mac machine here is the website:  [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Also, you can download almost any Linux OS using UNetbootin, not just Canonical OSes.  Make sure you are downloading to your USB and not to your hard drive, the program is usually good about that but I suppose stranger things have happened.  Also, be sure to use version 14.04 Live USB if you use a Canonical OS (Ubuntu, Xubuntu, Kubuntu, Lubuntu).  Also, be sure to download the 32 bit version, if the CPU isn't 64 bit that version will not even boot.

Ubuntu will run on your computer but resource-intensive websites will cause you to dip into swap area which slows your computer to a crawl.  I recommend Xubuntu which is a medium-weight OS although Lubuntu (the lightest of Canonical OSes) is also an option if you are willing to download the Ubuntu Software Center and whatever else you use that is missing from it (Lubuntu uses its own Software Center which doesn't have many of the programs people like but the full Ubuntu version can be downloaded from it).

Specs to run different Canonical OSes (from personal experience):
Ubuntu/Edubuntu:  2.5GB RAM, a Pentium 4 or faster CPU
Xubuntu:  1.5GB RAM, a Celeron/A4 or faster CPU
Kubuntu:  Same as Xubuntu
Lubuntu:  1.25GB RAM, a Celeron/A4 or faster CPU

Supposedly Puppy Linux will run and surf the web/run Libre Office on 256MB RAM and a Pentium 3 processor but I don't have experience with that OS on such hardware.  I did try a live USB boot of it and just at idle it used about 64MB RAM.  Puppy Linux is not a Canonical OS and has limited support if something were to go wrong.  Fortunately with your computer's specs you don't have to go there.

You don't say which model of that type processor you have but with the 4200+ the Passmark is 1101 which is fine for any Canonical OS, if you can increase the RAM to 3GB you could run Ubuntu or Edubuntu just fine.  It is a 32 bit processor so there is a 3.25GB cap on recognizable RAM.

---

### Post by newb85 on 2015-05-22
> **mattharris4 said:**
> Forget that method.  Download UNetbootin on another computer (there are versions that work on Linux, Mac and Windows) and use that to download whatever version of Linux you want.  Using Canonical OSes it can be downloaded through the Ubuntu Software Center.  If you need to do this on a Windows or Mac machine here is the website:  [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Actually, the surest way for a good download is using a bittorrent client.

> **mattharris4 said:**
> ...Lubuntu (the lightest of Canonical OSes) is also an option if you are willing to download the Ubuntu Software Center and whatever else you use that is missing from it (Lubuntu uses its own Software Center which doesn't have many of the programs people like but the full Ubuntu version can be downloaded from it).

Wait...what?  Where did you get that?  Regardless of whether you use Lubuntu Software Center, Ubuntu Software Center, or apt-get, you'll be using the sources in /etc/apt/sources.list, which in a default Lubuntu install is an exact copy of the sources.list file used in Ubuntu.  LSC doesn't pull from smaller repos.

> **mattharris4 said:**
> Specs to run different Canonical OSes (from personal experience):
Ubuntu/Edubuntu:  2.5GB RAM, a Pentium 4 or faster CPU
Xubuntu:  1.5GB RAM, a Celeron/A4 or faster CPU
Kubuntu:  Same as Xubuntu
Lubuntu:  1.25GB RAM, a Celeron/A4 or faster CPU


Where did these specs come from?  The Lubuntu website says 512MB would be a usable system, and I can vouch that it runs great in a VM with only 1GB.

---

### Post by mattharris4 on 2015-05-23
> **newb85 said:**
> . . . Where did these specs come from?  The Lubuntu website says 512MB would be a usable system, and I can vouch that it runs great in a VM with only 1GB.

These specs come from personal experience.  I tend to have 6-8 tabs open while reading SFGate.com and those specs are the approximate RAM usage of my computer (rounded up to the nearest half GB) when I read that site.  I also take into account that in my experience once a Linux computer goes into swap it slows down drastically so that is to be avoided at all costs.  This is obviously worst-case scenario but I want people to have a good experience with Linux and feel that it is fair to tell people to choose an OS (or a computer) based on this usage.  Obviously if someone never uses the internet on whatever computer they need advice for the RAM and processor required to run an OS is less than someone like me which uses a computer mainly for internet.

As for Virtual Box I have never used one so I do not have knowledge of the specifics of that use.

Lastly, I recommend UNetbootin because it is easy and almost fool-proof.  I don't like sending people to Bittorent sites because I am not familiar with their use myself other than that I know unscrupulous people sometimes use them to spread malware to unsuspecting users and because many people requesting assistance don't have the greatest computer skills and need a solution closer to fool-proof (which UNetbootin provides).  I have a concern that telling a Linux noob to use a Bittorent site to get an OS will cause them to have difficulty installing Linux and scare them away (and may even wreck some component of their computer with malware).  You may be unaware of this but most of the Bittorent sites where people can get a download of a Canonical OS are not directly managed by Canonical which affects my advice to people here as well.  I know Canonical does not manage UNetbootin either but it have been around for several years and no one has ever posted about malware coming from that program -- unfortunately more than I can say for Bittorent sites.

---

### Post by Diandra on 2015-05-23
YOu say that you are using bootable usb, what software you are using to create bootable? I recomends YUMI or rufus if you still got error

---

### Post by newb85 on 2015-05-24
How did you download the .iso?  Did you use checksum or a bit torrent client?

---

### Post by mattharris4 on 2015-05-25
> **Diandra said:**
> YOu say that you are using bootable usb, what software you are using to create bootable? I recomends YUMI or rufus if you still got error


Diandra, I just took a quick look at the website supporting YUMI.  It appears that its purpose is to use Linux in a live USB environment and not for installs.  Here is the pertinent paragraph from their site as of 25 May 2015:  "**[COLOR=#800000]Important Note:[/COLOR]**  YUMI was intended to be used to try to run various "LIVE Linux"  Operating Systems from USB. Installing Linux from the YUMI created USB  Drive to a Hard Drive is not officially supported. If the installer portion of any Live Linux distro does work, consider it a bonus".  That takes them out of the running for most people as they will eventually want to install an OS to hard disk.

Rufus looks interesting but from looking at their website (I haven't used it) it doesn't sound as intuitive as UNetbootin.  It appears to be faster, however.  It may be a good choice for more tech-savvy people but without actually using it a few times I could not say for certain whether it is appropriate for the masses of new Linux users.

---

