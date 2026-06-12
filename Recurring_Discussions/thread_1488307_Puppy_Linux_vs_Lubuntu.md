---
title: "Puppy Linux vs Lubuntu"
date: 2010-05-19
forum: Recurring Discussions
---

### Post by TheNerdAL on 2010-05-19
Which is better and why?

---

### Post by madjr on 2010-05-20
havent tried either lol

---

### Post by WinterRain on 2010-05-20
I like both of them. I think puppy is a bit lighter, but both are well done and work good on many computers.

---

### Post by TheNerdAL on 2010-05-20
> **WinterRain said:**
> I like both of them. I think puppy is a bit lighter, but both are well done and work good on many computers.

I liked Puppy but I found a really hard time to install it to my cousin's hard drive, I don't know how. :(

---

### Post by WinterRain on 2010-05-20
> **TheNerdAL said:**
> I liked Puppy but I found a really hard time to install it to my cousin's hard drive, I don't know how. :(

Practice in virtualbox. ;)

---

### Post by Guitar John on 2010-05-20
Haven't tried Lubuntu yet, but I am curious.  

I did a frugal install (Pup431) on my old Dell 3500.  It came with Win98, 366 Mz,6GB HDD, 32MB RAM.  Now it has a 60GB HDD and 256 MB RAM, which is all it will hold.  

It took a bit of tweaking, but I got everything including sound working on it.  It will even play YouTube videos, as long as you don't mind a frame rate of something like one-per-second.  :-\"

Puppy is fast on a more modern computer, but care must be taken.  You are always logged in as root.

---

### Post by Khakilang on 2010-05-20
I use Lubuntu because of its huge software repositories. Easy installation and my Wifi usb adapter works.

---

### Post by WinterRain on 2010-05-21
> **Koh Kook Loon said:**
> I use Lubuntu because of its huge software repositories. Easy installation and my Wifi usb adapter works.

You can now use ubuntu repositories in puppy.
:guitar:

---

### Post by oleink on 2010-06-05
> **WinterRain said:**
> You can now use ubuntu repositories in puppy.
:guitar:

How?  And btw I like lubuntu just because I like it more haha

---

### Post by DougieFresh4U on 2010-06-05
> **oleink said:**
> How? 
When you open package manager, you can select which repo's you would like.
I think it let you only select 4. There were Debian  repo's avail.

---

### Post by oleink on 2010-06-05
> **DougieFresh4U said:**
> When you open package manager, you can select which repo's you would like.
I think it let you only select 4. There were Debian  repo's avail.

sweet thanks!

---

### Post by OldHW on 2010-06-16
I've used Puppy Linux off and on (mostly on) for several years and the latest official versions are very well done.  However, although Puppy was originally designed for very old hardware I've had many difficulties getting it installed on my two old laptops - due to the install routine not liking my PCMCIA CD drive on one laptop and the install routine freezing on the other.  If I removed the laptop batteries so nothing was left in memory when shut down, and kept trying to install using wubi and other contortions, I was eventually able to get it installed.  Lately I've simply gotten pissed off, and that's why I turned to Lubuntu.

Once installed, Puppy is a great OS except for wireless support, which completely sucks.  I found I needed to step through the wireless wizard every time a laptop was booted, and usually after about 8 hours of use.  Puppy has been in development for many years but somehow the developers never thought the poor wireless support was important.  This, despite many hundreds (thousands?) of posts in the user forums asking for assistance or simply complaining.  User support in the forums is generally excellent.  Perhaps with the new repositories available, including those for Ubuntu, WICD could be installed in Puppy.  Not sure.

Aside from wireless issues, Puppy development is mired in anarchy.  No apparent guidelines or goals and with so many release variations it gets very confusing.  The anarchy is also reflected in their multiple websites and how the websites are (not) organized.  I don't mean to bash Puppy - I like it a lot.  But if you want to simply install and use Puppy, you're likely out of luck unless you're on a newer computer (5-6 years?) with an ethernet web connection.  If you have the time to invest, Puppy is definitely worth checking out - even for a newbee.  Among other things, you can easily install it on a memory stick and boot from that stick.  And yes, it is very fast.

As for Lubuntu -  I installed it with no issues on one of my old laptops and - wireless just works.  It's not as fast as Puppy, but it's very impressive.  I loaded the Seamonkey browser to compare with Chromium and it seemed a bit faster but not enough to force a decision.  I like the layout of Chromium, but I also like the many available plugins for Seamonkey and the easy way they can be installed and managed.  I have yet to decide which one I'll use.

You may want to try dual-booting Lubuntu and Puppy.  Install Lubuntu first and then Puppy.  Most of the Puppy ISOs are between 195 and 220MB is size, so disk space shouldn't be a concern.  Puppy will install on the same partition as Lubuntu and then install or modify GRUB so you can dual-boot.  Removing Puppy is as easy as deleting a few files and modifying the GRUB menu.

I suggest that if you just want something that works with a minimum amount of tweaking and research, go with Lubuntu.

---

### Post by kerry_s on 2010-06-16
between those 2, i'd go with lubuntu.
i find lubuntu is just so easy to tweak.

i'm using lubuntu now, just installed before i went to bed, so now i'm just setting it up.

i'm currently working on the lubuntu netbook session, i removed lxlauncher & put netbook-launcher-efl. now i'm just tweaking openbox & lxde to behave the netbook way. :p

---

### Post by squilookle on 2010-06-16
Puppy has been okay the few times I've tried it, but I would probably go with Lubuntu. I'm ore familiar with the underlying system than I am Puppy.

---

### Post by ubunterooster on 2010-06-16
[quote=Lubutu]Lubuntu is targeted at "normal" PC users running on  low-spec hardware. Such users may not know how to use command line  tools, and in most cases they just don't have enough resources for all  the bells and whistles of the "full-featured" mainstream distributions. A Pentium II or Celeron system with [COLOR=Red]128 Mb RAM is  probably a bottom-line configuration[/COLOR] that may yield slow yet usable  system with Lubuntu. It should be possible to install and run Lubuntu  with less memory, but the result will likely not be suitable for  practical use. If you have less than 160 Mb RAM, you will need to use  the minimal installation instructions at [https://wiki.ubuntu.com/Lubuntu/DocumentationHelp#Minimal  Install]("https://wiki.ubuntu.com/Lubuntu/DocumentationHelp#Minimal%20Install")[/quote]


[quote=Wikipedia]When the operating system boots, everything in the Puppy package  uncompresses into a RAM area, the "[ramdisk]("http://en.wikipedia.org/wiki/Ramdisk")". The PC needs to have at least 128 MB  of RAM (with no more than 8 MB shared video) for all of Puppy to load  into the ramdisk. However, [COLOR=Red]it is possible for it to run on a PC with  only about 48 MB of RAM [/COLOR]because part of the system can be kept on the  hard drive, or in the worst case, left on the CD.[/quote]


So puppy is lighter and can run completely in RAM; sounds like a win (plus, "Puppy" sounds a lot better than does "Lubuntu" ;) ). If only one came in a 64-bit flavor so I could use all of my RAM...

---

### Post by TBABill on 2010-06-16
Puppy is probably quicker because it resides in RAM. But Lubuntu is super fast and being based on Ubuntu you would feel right at home with it. Plus you can still get answers to issues here with instructions that should work with either your Ubuntu install or Lubuntu.

---

### Post by ubunterooster on 2010-06-16
> **TBABill said:**
> Puppy is probably quicker because it resides in RAM. But Lubuntu is super fast and being based on Ubuntu you would feel right at home with it. Plus you can still get answers to issues here with instructions that should work with either your Ubuntu install or Lubuntu.
Both are Ubuntu-Based. (Puppy 5 is now a Ubuntu spinoff unlike Puppy 4)

---

### Post by OldHW on 2010-06-16
Here's a quick overview of Puppy Linux:
[http://distro.ibiblio.org/pub/linux/distributions/puppylinux/puppy-5.0/release-500.htm](http://distro.ibiblio.org/pub/linux/distributions/puppylinux/puppy-5.0/release-500.htm)

---

### Post by ParadoxBlue on 2010-06-19
The Lubuntu screenshot looks nice...the blue is great :)

---

### Post by AthanasiusKircher on 2010-08-01
I recently have spent some time trying both distros on an old Dell laptop (about 6 years old).

Puppy is undeniably much faster -- it may have to do with the specs of my hardware, but I've never seen this computer run this fast.  It's not as polished-looking as Lubuntu, but all the apps work well and are lightning fast, even on an underpowered old laptop.

As for configuration problems that some have noted, I had no difficulties whatsoever.  There were two options for wireless config, and it took me about 3 minutes to figure out that one of them worked with my network and the other didn't.  Everything else ran perfectly immediately -- within 10 minutes of booting up, I had it installed on my hard drive, with sound, monitor, etc. detected automatically.  Network printer setup was a snap.  And it's configured with flash and such things out of the box, so no hunting for non-free audio/video codecs (as in most canonical Ubuntu variants, including Lubuntu).

Honestly, Puppy was up and running much faster than any other Linux distro I've ever tried.  Every single version of Ubuntu and even Mint has always had some weird config problem on install for me, but Puppy ran perfectly smooth.

That said, I'm no longer using it.  First, the always run-as-root thing was just annoying.  It's great for an emergency USB stick where you'll need to do system commands, but when running on a normal installed system, there's no need for it.  I know security folks debate it (and I debated it with a hard-core network admin friend of mine for a while when I first tried Puppy), but it goes against standard industry practice, and I figure... why take the risk?  Multiuser stuff is easy and lightweight, so I just don't understand the Puppy mentality there (even after reading a lot of debate on forums).  It seems that they made the decision early on, and nobody really wants to do the major changes now.  (There is a multiuser version of the previous Puppy version out there, but I haven't tried it.)

But the real deal-breaker is the trouble installing software.  Basically, you have most common software installed in so-called PET packages, which are stripped down to be small and fast.  Those are great.  However, if you're using something beyond a couple dozen most common apps, you'll probably need to go outside the PET package world.  One option Puppy offers is SFS files, which you can load at boot if you're not doing a standard HD install.  Unfortunately, these are not always kept up-to-date, and I had difficulties with backward compatibility between a new Puppy version and an old SFS file.

Supposedly, the new version of Puppy should be able to deal with standard package managers, including DEB and RPM formats.  This is true in theory, and I was able to install some things.  But other things just ended up broken, because dependencies weren't handled correctly, etc.  I really need LaTeX installed on this computer, and I just couldn't get it working in an easy way (and I didn't feel like compiling from source), so finally I just gave up.

I went to Lubuntu.  As I already said, it's better looking, but nowhere near as fast on my computer.  Still better than a heavier distro, but it's not really that light for an older computer.  Unfortunately, there are still annoying bugs, which I didn't see with Puppy (at least not until I tried installing random software on Puppy).  There's the missing terminal title bar, for example, and a few other weird things (slowdowns for no apparent reason, menus stop working sporadically, etc.).  I tried the Mint version using the same window manager, and it was really buggy for whatever reason on my system.

Overall, with a few notable bug exceptions, Lubuntu works as well as most of the Ubuntu family.  It's not perfect, but its package management is more stable than Puppy -- no random dependency errors when I install software now (which is just another thing I don't have to worry about).  I'm willing to put up with a few random bugs and a slightly slower system for that right now.

---

### Post by Legendary_Bibo on 2010-08-01
Puppy was fast, but tended to make it difficult to find useful info. I couldn't get it to install to my hard drive. I tried Lubuntu, and before some updates it was slow to boot up (getting applications going), but once it was going, it was a juggernaut on old hardware. Puppy was slow to boot, and pretty fast, but I preferred Xubuntu. Puppy would definitely be a good choice for children if you could get it to not run in root all the time.

---

### Post by ronnielsen1 on 2010-08-01
> You can now use ubuntu repositories in puppy.

Sure you can, but it's never able to fetch all of the needed files

---

### Post by AthanasiusKircher on 2010-08-01
> **Legendary_Bibo said:**
> Puppy was fast, but tended to make it difficult to find useful info.

That's definitely true.  It's something I left out of my earlier post, but one other potentially annoying thing about Puppy is the lack of documentation.  You only get really basic info with the default install, and you really have to resort to the forums (which are pretty active) to get help.

But a more annoying thing for some users might be the lack of regular installed documentation for packages.  One of the ways Puppy gets its size down is by omitting documentation for standard installs (and PET packages, etc.).  That's a great benefit if you really need an OS that takes up 100 MB or less, but it's kind of annoying when you can't even ask for man pages at the command prompt for common commands....

All these things are trade-offs, though, so this policy may work for a lot of folks.  Personally, I have to use my laptop occasionally in places where I'm not online, and the lack of documentation can get annoying.

---

### Post by markwiering on 2013-02-08
Ubuntu, Linux Mint and Lubuntu all three failed to boot on my computer with the same error. Puppy Linux boots fine, reacts fast, has a nice user interface, is user friendly, and the coolest thing is: I didn't even have to install drivers for it. Everything immediately worked: sound, video, network adapter, and even my external harddrive, which only supports Windows XP, Vista en 7, works in Puppy Linux. And there is another very cool thing about Puppy Linux. Puppy Linux can boot from an USB flash drive. My computer has an old BIOS from 2003 and can't boot from an USB flash drive, but our computer downstairs can. I installed Puppy Linux on the USB flash drive, put it in the computer, I turned the computer on, Puppy Linux booted up, then I removed the USB flash drive, and Puppy still works! Well, THAT is amazing. Another good thing is: Puppy Linux has a EXE-installer which will allow you to install Puppy Linux within Windows.

All these things makes Puppy Linux far better than Lubuntu, because Lubuntu can't even boot on every computer!

---

