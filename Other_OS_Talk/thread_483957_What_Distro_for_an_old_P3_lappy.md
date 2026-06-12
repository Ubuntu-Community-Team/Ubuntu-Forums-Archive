---
title: "What Distro for an old P3 lappy?"
date: 2007-06-25
forum: Other OS Talk
---

### Post by DR_K13 on 2007-06-25
I have an old 800 mhz P3 lappy with 256 of ram. I have tried to install Ubuntu on it , the GUI would freeze up the whole install. I havnt tried the non-Gui install yet though.

I was looking at Zenwalk. I have heard some good things on here about it. 

What would you guys run? I was thinking of installing Damn Small Linux but it is going to be used by mostly windows people and I dont think it would be a good idea!

Thanks !

---

### Post by ThinkBuntu on 2007-06-25
I recommend Zenwalk, but also consider SAM and Xubuntu. You cant go wrong with any of those three, although wireless can be a pain in Zenwalk, while it's easy in SAM and Xubuntu.

---

### Post by DR_K13 on 2007-06-25
> **ThinkBuntu said:**
> I recommend Zenwalk, but also consider SAM and Xubuntu. You cant go wrong with any of those three, although wireless can be a pain in Zenwalk, while it's easy in SAM and Xubuntu.

I was looking at Xubuntu too, and it is going to be wireless using a USB adapter. I am worried about the Heavy GUI at install. I tried 4 times with 4 different ISOs on the regular Ubuntu side of things. Will the Xubuntu install be more light weight?

---

### Post by ThinkBuntu on 2007-06-25
> **DR_K13 said:**
> I was looking at Xubuntu too, and it is going to be wireless using a USB adapter. I am worried about the Heavy GUI at install. I tried 4 times with 4 different ISOs on the regular Ubuntu side of things. Will the Xubuntu install be more light weight?
Yes, but in the Ubuntu "compatibility" style, it loads many modules and services that may weigh down your machine. SAM does this, but to a lesser degree, and I think you'll do well with it. And I can guarantee that Zenwalk will work well, as well as Debian or Arch with Xfce. Debian is very flexible and shold work very well if you're willing to put in an hour or two getting it "just right." They offer Xfce-only install discs as well. Arch will require more work, but could be a good solution for a light system.

---

### Post by DR_K13 on 2007-06-25
So how do you think Regular Ubuntu would do on this system. I am going to do the alternative install no matter what but what will run better?

---

### Post by ThinkBuntu on 2007-06-25
> **DR_K13 said:**
> So how do you think Regular Ubuntu would do on this system. I am going to do the alternative install no matter what but what will run better?
Regular Ubuntu's not a good idea for that machine, although technically it will run. I believe that GNOME would be too heavy a desktop environment when coupled with Ubuntu, and I can only imagine it working well with Debian.

---

### Post by DR_K13 on 2007-06-25
> **ThinkBuntu said:**
> Regular Ubuntu's not a good idea for that machine, although technically it will run. I believe that GNOME would be too heavy a desktop environment when coupled with Ubuntu, and I can only imagine it working well with Debian.
 ok, how do you like Xubuntu?  I have never used XFCE.  Will 686mb fit on a CD or do I need to use a DVD?

---

### Post by Kobalt on 2007-06-25
It will fit on a CD (all official Ubuntu ISOs are made to fit on a 700Mo CD). 
Xubuntu is getting very polished now. It can possibly fit your needs but in order to keep a smooth system running I'd stay away from Firefox and Thunderbird for example, as they both are quite heavy in terms or RAM.

---

### Post by mips on 2007-06-25
Fluxbuntu, Sidux, PCBSD etc Take your pick as it is not such a bad spec machine if you ask me.

---

### Post by DR_K13 on 2007-06-27
Put Xbuntu on it, runs very well, not as fast as a DSL HD install but its way more stable! I even got the Zyxel G-220 wireless USB  working on it.

---

### Post by swoll1980 on 2007-06-29
> **DR_K13 said:**
> ok, how do you like Xubuntu?  I have never used XFCE.  Will 686mb fit on a CD or do I need to use a DVD?

I have a dell with a 2.6 celoron and 256mb I originally went with xubuntu because of my system specs. I never found out why, but xubuntu ran horably slow. I Switched to Ubuntu and it works smooth as silk. Go figure

---

### Post by izizzle on 2007-06-29
I have a Dell Inspiron 2100 laptop 700 mhz and 256 RAM. Right now it's running windows XP very slowly and I was considering installing Linux on it. It has a Zyxel G-102 internet adapter. Any ideas on what distro I should run on it? .....I was considering Xubuntu.....

---

### Post by mips on 2007-07-01
> **izizzle said:**
> It has a Zyxel G-102 internet adapter. 

[http://madwifi.org/](http://madwifi.org/)

---

### Post by HermanAB on 2007-07-01
The problem with that laptop of yours is not so much the processor speed as the lack of RAM.  I ran KDE on a 600MHz stinkpad for a few years, but it had 512MB RAM.

I suggest that you stay away from KDE and Gnome and use a fast desktop based on IceWM and Rox.  As a test, go to PuppyOS.org and try their live CD.  You may like it better than DSL.

Cheers,

Herman

---

### Post by steveneddy on 2007-07-01
With those specs, install another stick of 256 mb RAM. Ubuntu will run well on that machine with 512 MB RAM installed.

RAM is cheap and makes everything run better.

---

### Post by Bachstelze on 2007-07-01
> **DR_K13 said:**
> What would you guys run?

If the Windows people are only going to *use* it (i.e. not going to go "under the hood"), Slackware is the first Linux that comes to mind.

---

### Post by izizzle on 2007-07-01
I think  will install Xubuntu with 256 RAM...Maybe I'll install another stick of ram.....

---

### Post by deanlinkous on 2007-07-01
my laptop is 700mhz with 256mb ram and it does fine, I usually use debian as well as gnewsense right now...

---

### Post by izizzle on 2007-07-02
I might look into gnewsense a bit more....seems interesting........

---

### Post by timzak on 2007-07-03
I'm using Xubuntu on a Celeron 466 with 256MB ram and i810 graphics.  Granted, the box only plays mp3s and Streamtuner, but it does so admirably.  After a fresh bootup the system uses about 85MB ram with no apps running, and with Rhythmbox and/or XMMS/Streamtuner open and playing songs I'm at about 120 MB and 25% cpu utilization.  Rarely does the swap disk get touched.

I also have Xubuntu on a Dell Inspiron 8000 with P3 650Mhz and 384MB ram and it runs fine.  Sure, the cpu is pegged at 100% usage a lot of the time (like when doing a search in Synaptic or loading most any app), but the system is very usable.  

Other distros worth looking at are SAM and Mint Lite.  I think both utilize Xfce.  There's also antiX (still in development...based off of Mepis), and the old MepisLite.  I'm looking forward to trying out Fluxbuntu.

---

### Post by kerry_s on 2007-07-03
debian custom install with fluxbox. go light if you want to maximize your resources.

---

### Post by marsmissionaries on 2007-07-04
i reccomend slackware. I ran slack on a 800mhz pIII desktop, it was VERY stable. Never crashed.


that was with kde.

---

### Post by izizzle on 2007-07-04
Wow. So many new and lightweight distros that I've never really looked into before. Keep it up guys!

---

### Post by rustybronco on 2007-07-14
ubuntu works fine on my toshiba p3 650 mhz with 384 megs, wireless card and running firefox. it boots about 15% slower than xp sp2 did, but when its up and running it's stable as a rock. 
I have sabayon on my desktop and am currently downloading linux mint 3.0 to try on the desktop and this laptop.
one thing nice about linux you can download a lot of distros and try them all for the price of a few cd's.

---

### Post by RAV TUX on 2007-07-15
> **DR_K13 said:**
> I have an old 800 mhz P3 lappy with 256 of ram. I have tried to install Ubuntu on it , the GUI would freeze up the whole install. I havnt tried the non-Gui install yet though.

I was looking at Zenwalk. I have heard some good things on here about it. 

What would you guys run? I was thinking of installing Damn Small Linux but it is going to be used by mostly windows people and I dont think it would be a good idea!

Thanks !

[Wolvix]("http://wolvix.org/")

&

[Wolvix Cub]("http://wolvix.org/")

---

### Post by izizzle on 2007-07-15
~~A POST COMPLETELY OFF TOPIC~~

Hey Rav, nice display image. I saw that movie, funny as hell man!

---

### Post by RAV TUX on 2007-07-15
> **izizzle said:**
> ~~A POST COMPLETELY OFF TOPIC~~

Hey Rav, nice display image. I saw that movie, funny as hell man!

BEST MOVIE OF THE YEAR!......thanks Remy is cool....LOL

---

### Post by izizzle on 2007-07-18
Remy is a mouse with Betty Crocker's IQ...LOL!

---

