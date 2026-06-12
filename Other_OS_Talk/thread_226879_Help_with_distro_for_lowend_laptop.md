---
title: "Help with distro for lowend laptop"
date: 2006-07-31
forum: Other OS Talk
---

### Post by rattlerviper on 2006-07-31
Allright my mother would like me to install Linux on her laptop.  Specs are meager! 64 mb of ram, it's a P2 operating at? (haven't even looked yet).  It has NO cd drive.  It does have a floppy. 
What is the best Distro that I can slam into this thing to get it up and working?  Will I be able to give it wifi support with that distro once she chooses to buy a card after it is working? She is fed up with the windows 98 that is on it(and not functioning).  
I'd like to make it my project tonight so suggest away!:p

---

### Post by RAV TUX on 2006-07-31
puppy

---

### Post by rattlerviper on 2006-07-31
> **yozef said:**
> puppy
Yozef, was just getting ready to pm you to ask this question. Don't you have to burn puppy to cd otr use a pen drive to boot from?  This stupid toshiba laptob can't boot from USB.

---

### Post by richbarna on 2006-07-31
Linux on a Floppy disk distros, anybody wanna test 'em :)
[http://www.linuxlinks.com/Distributions/Floppy/](http://www.linuxlinks.com/Distributions/Floppy/)

---

### Post by rattlerviper on 2006-07-31
> **richbarna said:**
> Linux on a Floppy disk distros, anybody wanna test 'em :)
[http://www.linuxlinks.com/Distributions/Floppy/](http://www.linuxlinks.com/Distributions/Floppy/)

Well looks like I will end up testing them whether I want to or not.;-) Not that I won't enjoy it.  It does have usb, but it is not usb bootable, wonder if I could make up a bootdisk like they use to use to boot from cdrom before they were bootable.  I also have a network card for it, and it is network bootable, but without the driver installed it does not seem to be network bootable from this card.  First thing that went through my mind was add 64mb more of ram, and try a network install of Xubuntu...Got to thinking about it and I think it would be VERY slow though.  

Thanks for the link to the floppy distros, looks like I'm off to see if there are any good ones.  If I test them out I shall report.

---

### Post by richbarna on 2006-08-01
If you succeed, it would make a great "Howto", as I know that there are a lot of people with older Pc's/Laptops out there.

---

### Post by John.Michael.Kane on 2006-08-01
rattlerviper if the laptop has an eth port. you could try a network install  .There should then be no need to make floppies or a cd.

---

### Post by rattlerviper on 2006-08-01
> **SD-Plissken said:**
> rattlerviper if the laptop has an eth port. you could try a network install  .There should then be no need to make floppies or a cd.

The laptop has a PMCIA Etho network card.  It has the option in bios to boot from network.  But since it is a PMCIA wouldn't it require a driver to work?   I am clueless as to whether it would work without a driver or not???:confused: 

Hopefully I can find out that it will work, as I have tried MuLinux and it is totally unacceptable!  It was written in 1998-1999 and has never been updated.  It is very rudimentery, No wifi support, no etho support as far as I can tell all it really has is a GUI desktop (required a extra floppy) and VERY minamalistic software options.  No package manager, no apt-get, no nothing.  Reminds me of installing Windows 3.1 back in the day.

---

### Post by RavenOfOdin on 2006-08-01
Debian has a network installation method from two floppies which may come in useful.

[http://www.us.debian.org/distrib/netinst](http://www.us.debian.org/distrib/netinst)

I'm running Sarge on an iMac G3 with 333 MHz and 32 MB of RAM and its actually useable, sans slowdown and with graphical goodies, in a major desktop environment such as KDE.  Therefore, double that amount of RAM shouldn't be any trouble for you.

Just run aptitude instead of kpackage when you want to upgrade, otherwise you're in for a headache since the default settings set you up for downloads of BSD/Gentoo/Slackware package lists in addition to RPM and .deb.

---

### Post by richbarna on 2006-08-01
> **RavenOfOdin said:**
> Debian has a network installation method from two floppies which may come in useful.

[http://www.us.debian.org/distrib/netinst](http://www.us.debian.org/distrib/netinst)

I'm running Sarge on an iMac G3 with 333 MHz and 32 MB of RAM and its actually useable, sans slowdown and with graphical goodies, in a major desktop environment such as KDE.  Therefore, double that amount of RAM shouldn't be any trouble for you.

Just run aptitude instead of kpackage when you want to upgrade, otherwise you're in for a headache since the default settings set you up for downloads of BSD/Gentoo/Slackware package lists in addition to RPM and .deb.

Nice link, I've put that in favourites for future reference, Thanks :)

---

### Post by rattlerviper on 2006-08-01
> **RavenOfOdin said:**
> Debian has a network installation method from two floppies which may come in useful.

[http://www.us.debian.org/distrib/netinst](http://www.us.debian.org/distrib/netinst)

I'm running Sarge on an iMac G3 with 333 MHz and 32 MB of RAM and its actually useable, sans slowdown and with graphical goodies, in a major desktop environment such as KDE.  Therefore, double that amount of RAM shouldn't be any trouble for you.

Just run aptitude instead of kpackage when you want to upgrade, otherwise you're in for a headache since the default settings set you up for downloads of BSD/Gentoo/Slackware package lists in addition to RPM and .deb.

Looks like we have a winner! I booked marked and will definantly do the install after I research everything that I will need to do.  This is great!!! thank you so much. Once again the Ubuntu community has proven to be the most best at knowing thier distros and the friendliest forums on the web!=D>

---

### Post by rattlerviper on 2006-08-01
Oops, I am feeling REALLY stupid. I cannot find the link to download the floppies antwhere on that page...or even on the debian website.

---

### Post by rattlerviper on 2006-08-02
Found the boot disks! can't find a cat5 cord off to wal....that really big store that stays open 24hrs I shall go!

---

### Post by rattlerviper on 2006-08-03
Well I got Debian Sarge up and working on the laptop through a network install, it was actually very easy.  Tried to install Xubuntu through a network install by using debootstrap but I just couldn't secceed.  My mother has now decided to purchase a cdrom to add to the laptop as she wants "that Ubuntu thing like on your computer".;)  Well I wish she would of decided that first, but at least I learned something.

---

### Post by 1101 on 2006-08-04
DSL!!! (Damn Small Linux)

I can't get my head around this not being suggested to you, DSL rules at keeping old machines going.

[www.damnsmalllinux.org](www.damnsmalllinux.org) - have a look

you can make a boot disk that will let yo boot from USB, the entire OS is 50mb and thats with a ton of programs (like firefox, xmms, see website) included. It also has a kick-*** "MYDSL" function - basically a lot like a repository where all the files will auto-install from a menu.

I really like the DSL team, they seem to stab problems right in the heart and then twist.

Alternatly you can install from multiple floppies, this method can work with many OS's - but having done it once with DSL (a small OS) it really wasn't much fun.

Good luck, i hope you get a lot more use out of the old thing.

---

### Post by rattlerviper on 2006-08-04
> **1101 said:**
> DSL!!! (Damn Small Linux)

I can't get my head around this not being suggested to you, DSL rules at keeping old machines going.

[www.damnsmalllinux.org](www.damnsmalllinux.org) - have a look

you can make a boot disk that will let yo boot from USB, the entire OS is 50mb and thats with a ton of programs (like firefox, xmms, see website) included. It also has a kick-*** "MYDSL" function - basically a lot like a repository where all the files will auto-install from a menu.

I really like the DSL team, they seem to stab problems right in the heart and then twist.

Alternatly you can install from multiple floppies, this method can work with many OS's - but having done it once with DSL (a small OS) it really wasn't much fun.

Good luck, i hope you get a lot more use out of the old thing.

How would one find the install disks for the multiple floppies?  I also didn't realize that it would be possible to make a floppy so that it would boot from USB, so that might be an intresting route also.  If this works out with my mothers laptop, I might have to visit ebay and make a purchase of my own as it has only been the price to performance ratio keeping me out of the laptop market.(I'm a truckdriver, so one would come in REALLY handy).

If you could point me in the right direction for the multiple floppy install I would much apreciate it.

---

