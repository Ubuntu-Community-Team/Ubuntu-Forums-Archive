---
title: "Where to begin?"
date: 2013-08-03
forum: New to Ubuntu
---

### Post by GirlFromMars on 2013-08-03
I have a dell inspiron 1721 which came with windows vista and after several complete crashes is now running windows 7 very poorly. It's 6 years old and I hate the laptop and am ready to drop kick it but I though I might as well try some sort of Linux as an experiment and since I have a little experience with unix (very basic commands only). But I don't know where to begin to get it installed.  Is it even possible on this laptop as I have a RAID and windows 7 wasn't even supported for it.  Where do people get drivers for ubuntu?

---

### Post by grahammechanical on 2013-08-03
Where to start? Download an ISO image of Ubuntu and burn it to DVD or USB. Note the heading in this link Help with installing Ubuntu. There is a section for Windows. If your CPU is 64bit, then you need Ubuntu amd64. This is true even if your CPU is an Intel CPU.

 [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

Ubuntu 12.04 LTS has support for about 4 more years. Which means that you can upgrade in May 2014 to Ubuntu 14.04 LTS (with 5 years support) or wait to May 2016 to upgrade to Ubuntu 16.04 LTS (with 5 years support).

Ubuntu 13.04 has support until December 2013. If you choose 13.04 you will have to upgrade to Ubuntu 13.10 before 13.04 reaches End of Life. But Ubuntu 13.10 will only have support for 9 nine months. So, you will have to again upgrade to Ubuntu 14.04 before 13.10 reaches End of Life. It is your choice.


Once you have Ubuntu on a DVD or USB you can run a live session to test if your hardware is detected and to see if your are happy with Ubuntu. The live session runs slower than an installation to hard disk. So, keep that in mind.

That I think is enough for now. Drivers for Linux are included in the core part of the operating system (called the Linux kernel). If the live session runs well and activates the hardware then all the drivers are present. What you will need to check is the wireless adapter. That is one area where there may be issues with drivers but there are ways to fix things. Wait until you find out if that is an issue.

This link has images of what you will see when you run the live session and choose the Install Ubuntu option

[http://www.ubuntu.com/download/desktop/install-desktop-long-term-support](http://www.ubuntu.com/download/desktop/install-desktop-long-term-support)

Regards and welcome to the Ubuntu Forum Community

---

### Post by ibjsb4 on 2013-08-03
There are different flavors of ubuntu, some are made to run better on older equipment.  Whats your lappy specs?  Dual core? Gig of ram? What kind of video support do you need?

---

### Post by purak2 on 2013-08-03
Welcome GirlFromMars,

You should read a beginner guide like the following before installing Ubuntu to learn some ideas and key features about Ubuntu.

[http://www.makeuseof.com/pages/ubuntu-an-absolute-beginners-guide](http://www.makeuseof.com/pages/ubuntu-an-absolute-beginners-guide)

Good Luck

---

### Post by Rob Sayer on 2013-08-03
Without knowing why the system crashed, all I can suggest is downloading (torrent method is best) a ubuntu install iso image of one of the desktop versions and booting from that.  I prefer installing it to a usb drive.  It's much faster.  But you can boot it from cd or dvd as well.

That will boot ubuntu linux on your machine and you can see how well it runs.

If it's a 2Gb ram or less computer, which I suspect, I wouldn't recommend ubuntu with the unity desktop.  It won't run very well.  I had it on an i3 based laptop with 4Gb ram and found it too slow.

For 2Gb I'd recommend kubuntu.  Actually I run kubuntu on a 1Gb netbook and it runs fine for me but many would recommend xubuntu for a 1Gb ram laptop.  Less than 1Gb, definitely xubuntu or maybe lubuntu.

I'd try version 12.04, which is the long term support version (length depending upon desktop version).

---

### Post by Buntu Bunny on 2013-08-03
Welcome!

With an older laptop you may want to try Xubuntu 12.04 LTS. Another advantage is that it may seem more familiar to you, coming from Vista and Win 7.

---

### Post by BBQdave on 2013-08-03
> **GirlFromMars said:**
> I have a dell inspiron 1721...

If I understand your hardware correctly, it is 64-bit, with max memory of 4 Gigs. You will increase your choices of Linux distros by maxing out your memory to 4 Gigs. If you have 2 Gigs of memory, that should allow most Linux distros to function fine.

As suggested before, burn a live *64-bit* iso, and test your hardware for compatability - and it also gives you a chance to *test drive* the desk top environment :)

---

### Post by waynefoutz2 on 2013-08-03
This Laptop has the ATI Xpress 1270. I had one of those. You're stuck with the open source driver, and I never had much luck with the Unity Desktop or Gnome-Shell. Your best bet on that machine is Lubuntu, especially with only 2 gigs of RAM. I wouldn't wast my time with the main edition, it's not going to work with your GPU. 

If I owned that particular machine, I would put Legacy OS on it. It's a flavor of Puppy Linux, with an older Kernel and older version of xserver, then install Catalyst version 9.3 on it. It would perform really well, but there's a learning curve....I'd start with Lubuntu to get my feet wet in the Linux world first.

---

### Post by craig10x on 2013-08-03
Oh yes...not sure if this was mentioned, if you burn an iso dvd to try it, then don't forget to go into your bios settings (when you are initially booting up your computer) and change the sequence to have it boot off the cd/dvd drive first (rather then the hard drive first which is the default)...Then, after you burn the iso dvd...put it in your dvd drawer after you are in your regular system and then you will restart your computer and you will go right into booting off the ubuntu dvd...try the live session first (when the screen for that comes up and says "try" or "install")...

Keep in mind it take a few minutes to go into the session, so be patient...and if your computer is 64 bit...then best to get the 64 bit version...
Try ubuntu 13.04 first i would say...see if it runs properly on your hardware (including the unity desk top)...if not, then you can always live run the other variations such as xubuntu or lubuntu to see if they will work better for you...but no harm in trying the regular ubuntu first...

---

### Post by kurt18947 on 2013-08-03
Girl from Mars, 
> It's 6 years old and I hate the laptop and am ready to drop kick it 
don't drop-kick the machine,  it probably didn't do anything wrong and you'll likely hurt your foot.  Rip Windows out and drop kick that, it's likely the guilty party and deserving:P.  The advice above is good.  My laptop is a Thinkpad of similar vintage.  It works well with Ubuntu & gnome-shell though I have Intel graphics so no older ATI issues.  Perhaps the most difficult thing is to remember that Ubuntu is not Windows.  There are similarities but there are likely more differences.  Drivers are a whole different ballgame in Ubuntu/Linux for starters.

There are a number of different distro choices.  One I haven't seen mentioned is Linux Mint.  It's built on Ubuntu but has some tweaks and differences that might make it more familiar to Windows users.  I find the Cinnamon desktop fairly intuitive and software to play media e.g. flash for Youtube videos is included in Mint but must be installed separately in Ubuntu and its variants.

---

### Post by GirlFromMars on 2013-08-04
I managed to install ubuntu 64 bit but it's a bit slow.  I have 2gb of ram.  Can I install one of these lighter versions over the top or is it a full install again to do lubuntu or kubuntu or whatever else is easier?  It took a full day to do ubuntu (various partitioning issues due to the laptop using raid) so changing it now is putting me off.

---

### Post by ibjsb4 on 2013-08-04
You can cheat :)

Xubuntu is a lighter but full featured desktop.  You could install it to you current Ubuntu desktop and then remove the Ubuntu (Unity) desktop.  

To install Xubuntu desktop, [open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and ..

```
sudo apt-get install xubuntu-desktop
```

Then reboot and at the login window choose xubuntu by clicking on the icon.

Then to remove ubuntu ..

[http://www.psychocats.net/ubuntu/purexubuntu](http://www.psychocats.net/ubuntu/purexubuntu)

---

### Post by kurt18947 on 2013-08-04
I think I installed XFCE-panel & XFCE-goodies.  I prefer the gnome apps over the default Xubuntu-desktop apps,  didn't care for Abiword much though gnumeric seemed okay and I'm not a Thunar fan.  I presume you could do similar with LXDE but have never tried it.  You select your preferred desktop when you log in by clicking the little round thingy to the right of your name on the login screen.

---

### Post by kevdog on 2013-08-04
I'd just skip Ubuntu and go right to Arch of Gentoo

/s

---

### Post by kurt18947 on 2013-08-04
> **kevdog said:**
> I'd just skip Ubuntu and go right to Arch of Gentoo

/s

For someone brand new to linux?

---

### Post by Bucky Ball on 2013-08-04
DON'T install Xubuntu-desktop. You only want the desktop environment so ... install xfce4, log out, choose 'xfce session' or something like it from the 'Sessions' pop-up, log in.

Installing xubuntu-desktop will drag everything in and you will end up will all default xubuntu apps along with all default ubuntu apps, regardless of which desktop environment you are using. Duplication, redundancy and you don't want that.

If you have enough space on the hard drive, burn off an Xubuntu ISO, boot from that and install it to another partition, say 15Gb, by choosing 'Something Else' at the partitioning section of the install. Mark the existing /swap to 'use' but NOT ticked to format. Same with the existing /home partition, if you have one. They will be used by the new install by default, but the data in the /home partition will not be erased.

Good luck.

---

### Post by craig10x on 2013-08-04
By the way...i wouldn't do kubuntu as one person suggested...it is NOT going to be lighter then Unity desktop...xubuntu or lubuntu i would say but not kubuntu..

---

### Post by ibjsb4 on 2013-08-04
> **Bucky Ball said:**
> DON'T install Xubuntu-desktop. You only want the desktop environment so ... install xfce4, log out, choose 'xfce session' or something like it from the 'Sessions' pop-up, log in.

Don't  know about that Bucky.  Can you get the true xubuntu experience without removing ubuntu?

---

### Post by Bucky Ball on 2013-08-04
> **ibjsb4 said:**
> Don't  know about that Bucky.  Can you get the true xubuntu experience without removing ubuntu?

The true Xubuntu experience is a clean Xubuntu install. If you have Ubuntu with xubuntu-desktop installed, you will have tons of apps, some of which will be the Ubuntu defaults and requiring Gnome. This is Xubuntu puffed up and not the true experience.

Clean Xubuntu better, minimal install with xfce4 and just the apps you want better still. But horses for courses. ;)

PS: If you want to use Ubuntu default apps, don't mind having duplicate and redundant apps in the drop downs and Gnome running, then installing xubuntu-desktop is fine. A clean Xubuntu install does not bloat with Gnome and has far fewer apps than Ubuntu.

---

### Post by ibjsb4 on 2013-08-04
I think were saying the same thing.  A fresh install or remove ubuntu (post#12).  At any rate, I think we need to hear from Mars :)

---

### Post by GirlFromMars on 2013-08-05
I might just do a fresh install as I seem to have lost my wifi following some application updates then lost all internet trying to follow the instructions to fix the wifi :(

---

### Post by kurt18947 on 2013-08-05
If you're have a good internet connection, you might consider trying some live CD/DVD/USBs to sample the 'feel' of different 'flavors'.  That should be quicker than doing multiple installs.  Ubuntu, Ubuntu-gnome, KDE, Lubuntu, Mint, Xubuntu are all in the Ubuntu family.

---

### Post by BBQdave on 2013-08-05
> **kurt18947 said:**
> If you're have a good internet connection, you might consider trying some live CD/DVD/USBs to sample the 'feel' of different 'flavors'.

+1

And I humbly offer that **Ubuntu Unity 12.04LTS** - 64bit and **Xubuntu 12.04LTS** - 64bit, are two good distros to try :)

with Xubuntu most likely being faster on your hardware.

---

### Post by waynefoutz2 on 2013-08-05
> **craig10x said:**
> By the way...i wouldn't do kubuntu as one person suggested...it is NOT going to be lighter then Unity desktop...xubuntu or lubuntu i would say but not kubuntu..
KDE gets along better with those ancient ATI cards. I had a Dell laptop with the same GPU as hers, mine had twice the RAM though, It ran KDE flawlessly with all the eye candy. Unuty and Gnome-shell, all I got was a garbled mess.

At any rate, I would go Lubuntu over Xubuntu. Xfce isn't really that much lighter these days.

---

### Post by GirlFromMars on 2013-08-10
I just installed Mint 15 cinnamon and it seems _a lot_ faster. It's also a bit easier for me to use as well...so far anyway lol.

---

### Post by BBQdave on 2013-08-10
> **GirlFromMars said:**
> I just installed Mint 15 cinnamon and it seems _a lot_ faster.

Cinnamon is cool DE, nice nod to the style of Gnome 2 - accept evolved :D

If you are looking for a nice LTS, Linux Mint 13 - Maya is LTS. And you can backport newer Cinnamon DE to Maya :)

---

