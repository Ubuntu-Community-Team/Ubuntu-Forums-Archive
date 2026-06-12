---
title: "PPC Lubuntu - I need some help"
date: 2013-03-08
forum: New to Ubuntu
---

### Post by WilliamP99 on 2013-03-08
Hi,

This is my first time installing a Linux distribution on a PowerPC Mac (I have done installs of Linux and other OSes on x86 machines, for a few years now). Please be patient, i am a total noob.

I am trying to install Lubuntu 12.10 PowerPC Edition on my 2005 Mac Mini G4.

I successfully got to YaBoot, and i hit enter, which it goes to "live", but it just hanged on "loading ramdisk". I then tried what it said if it wouldn't work, which was "live video[FONT=arial]=ofonly", which got me to the Lubuntu bootscreen, but was in 8 bit colors, and it just hung on the Lubuntu boot screen.

Can somebody please help me out here? Is there a certain command i should try to use?


Oh BTW, here are my specs

Model: 2005 Apple Mac Mini G4 (obviously)
RAM: 512MB DDR - Never upgraded
HDD: 40GB - Never Upgraded
CPU: PowerPC G4 - Never upgraded
Graphics: Some kind of ATI Raedon - Never upgraded
Optical Drive: DVD reader/CD writer - Never Upgraded


Thank you in advance![/FONT]

---

### Post by Rodney9 on 2013-03-08
Some hints here may help - [http://powerpcliberation.blogspot.com.au/2012/10/lubuntu-install-guide.html](http://powerpcliberation.blogspot.com.au/2012/10/lubuntu-install-guide.html)

---

### Post by mikef7635 on 2013-04-17
> **WilliamP99 said:**
> Hi,

This is my first time installing a Linux distribution on a PowerPC Mac (I have done installs of Linux and other OSes on x86 machines, for a few years now). Please be patient, i am a total noob.

I am trying to install Lubuntu 12.10 PowerPC Edition on my 2005 Mac Mini G4.

I successfully got to YaBoot, and i hit enter, which it goes to "live", but it just hanged on "loading ramdisk". I then tried what it said if it wouldn't work, which was "live video[FONT=arial]=ofonly", which got me to the Lubuntu bootscreen, but was in 8 bit colors, and it just hung on the Lubuntu boot screen.

Can somebody please help me out here? Is there a certain command i should try to use?


Oh BTW, here are my specs

Model: 2005 Apple Mac Mini G4 (obviously)
RAM: 512MB DDR - Never upgraded
HDD: 40GB - Never Upgraded
CPU: PowerPC G4 - Never upgraded
Graphics: Some kind of ATI Raedon - Never upgraded
Optical Drive: DVD reader/CD writer - Never Upgraded

Thank you in advance![/FONT]


I use Lubuntu 12.10. This command works for me:

live video=radeonfb:1280x854-32

The video resolution is covered on:
[https://wiki.ubuntu.com/PowerPCFAQ#Radeon_cards](https://wiki.ubuntu.com/PowerPCFAQ#Radeon_cards)

under the heading:
What yaboot parameters should I use for graphics problems?

where it says:
Linux radeon.modeset=0 video=radeonfb:1024x768-32@60

Note the resolution of the PowerBook G4 I have is 1280x854 not 1024x768

---

