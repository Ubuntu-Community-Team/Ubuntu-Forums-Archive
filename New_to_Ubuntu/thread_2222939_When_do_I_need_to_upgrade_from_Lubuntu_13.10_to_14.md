---
title: "When do I need to upgrade from Lubuntu 13.10 to 14.04 LTS?"
date: 2014-05-08
forum: New to Ubuntu
---

### Post by AbleTassie on 2014-05-08
Wikipedia says 13.10 is supported until June, other sources say until July. Anybody know the exact date? It will probably take some time for me to upgrade, so I am putting it off.

I assume it is best to do a "clean upgrade," i.e., download and burn a CD or DVD, save files, install 14.04, install needed apps, etc. Any comments on this?

Can 14.04 LTS be put on a CD? Or is it too large?

Thanks,

R.

---

### Post by monkeybrain20122 on 2014-05-08
13.10 is supported til late July. Clean install all the way. "upgrade" is unreliable and takes hours to finish, a fresh install of 14.04 takes about 15 minutes. 

14.04 is ok but there are glitches at this point. If 13.10 is working why trade it off for something barely out of beta? (not having many updates since released, many updates are now sitting in "proposed"), 14.04.1 will come out around the same time 13.10 reaches end of life, I will wait til then.

P.S. No it can't be put in a CD, best way is to use a live usb, forget about DVD and burning, it is 2014. :)

---

### Post by kansasnoob on 2014-05-08
> **monkeybrain20122 said:**
> 13.10 is supported til late July. Clean install all the way. "upgrade" is unreliable and takes hours to finish, a fresh install of 14.04 takes about 15 minutes. 

14.04 is ok but there are glitches at this point. If 13.10 is working why trade it off for something barely out of beta? (not having many updates since released, many updates are now sitting in "proposed"), 14.04.1 will come out around the same time 13.10 reaches end of life, I will wait til then.

P.S. No it can't be put in a CD, best way is to use a live usb, forget about DVD and burning, it is 2014. :)

Other than PowerPC the Lubuntu images are still CD size :)

[http://cdimage.ubuntu.com/lubuntu/releases/14.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/14.04/release/)

---

### Post by AbleTassie on 2014-05-08
Thanks Monkeybrain and Kansas Noob, 

I wonder if 14.04.1 will fit on a CD? My machine is old, I can't burn a DVD or boot from a USB port.

Thanks,
R.

---

### Post by Redalien0304 on 2014-05-08
No 14.04.1 wil not fit on CD Need to be Dvd.

---

### Post by kansasnoob on 2014-05-08
> **Redalien0304 said:**
> No 14.04.1 wil not fit on CD Need to be Dvd.

How do you know that?

Lubuntu strives very hard to not break 700MB.

Regardless the original 14.04 images will be archived so they could still be used, then there would just be a lot of updates to apply after installing.

---

### Post by ian-weisser on 2014-05-08
> **monkeybrain20122 said:**
> Clean install all the way. "upgrade" is unreliable and takes hours to finish, a fresh install of 14.04 takes about 15 minutes.

I think that's misleading. The upgrade path is tested and supported.
I find upgrading to be more convenient, very reliable, and faster than a fresh install.
I've been installing, upgrading, and customizing on various machines since 2006. The one serious upgrade problem I experienced was patched and fixed within a couple days.

---

### Post by monkeybrain20122 on 2014-05-08
> **ian-weisser said:**
> I think that's misleading. The upgrade path is tested and supported.
I find upgrading to be more convenient, very reliable, and faster than a fresh install.
I've been installing, upgrading, and customizing on various machines since 2006. The one serious upgrade problem I experienced was patched and fixed within a couple days.

Upgrade takes a few hours, how is it going to be faster than a fresh install? You need to spend more time to configure your system before upgrade to a pristine state for it to be successful (removing proprietary drivers ppa etc) I find it misleading to present it to users as if they just press a button and everything is ok only to leave them with a broken/messed up system.

---

### Post by Don_Tai on 2014-05-10
The standard desktop install iso for Lubuntu and Ubuntu are close to 700mb and I could not burn it to a CD. If you have no dvd player, like I don't, you will need to install the alternative iso, which, at 620mb, does fit onto a CD, and works well.

---

### Post by mörgæs on 2014-05-10
Then you are doing something wrong. Lubuntu (both standard and alternate) fits to a CD, X/Ubuntu don't. 

Regardless of size, installing from USB is a safer way provided the computer supports it.

---

### Post by Vladlenin5000 on 2014-05-10
> **mörgæs said:**
> Regardless of size, installing from USB is a safer way provided the computer supports it.

If it doesn't support boot from USB then use a PloP CD to boot and from its menu select USB (with the installer USB already connected). It's currently the only solution for standard installations in machines that don't have a DVD drive and can't boot from USB. Note: By "standard installation" I mean using a full installer media, not the minimal CD or server versions.

---

### Post by AbleTassie on 2014-05-10
> **mörgæs said:**
> Then you are doing something wrong. Lubuntu (both standard and alternate) fits to a CD, X/Ubuntu don't. 

Regardless of size, installing from USB is a safer way provided the computer supports it.

Thanks Morgaes,

I cannot boot from a USB port. Do you (or anybody else) have any thoughts about which is superior, an upgrade or clean install? Or neither?

Thanks,

R.

---

### Post by craig10x on 2014-05-10
Upgrading doesn't take a few hours if you do it directly from the iso installer, and if he only runs one version of lubuntu, then the installer should offer the option of upgrading in addition to just wiping and replacing...and that should only take about the time a clean install takes...well, perhaps a little longer since it has to bring over all your data, personal settings, and usually is able to bring over most of your installed apps...

important to remember to turn off any ppas you have prior to beginning it (in the software souces)...then it should go very smoothly...i have used that method about 5x now and had excellent results...i think the longest the whole process took was maybe 35 minutes (and i have a LOT of data to bring over...lol) :D

I never did it using the software updater but i'd imagine that way must take a lot longer since it has to keep going to the internet to get the stuff? where as the iso has it right on there already...

---

### Post by AbleTassie on 2014-05-10
> **Vladlenin5000 said:**
> If it doesn't support boot from USB then use a PloP CD to boot and from its menu select USB (with the installer USB already connected). It's currently the only solution for standard installations in machines that don't have a DVD drive and can't boot from USB. Note: By "standard installation" I mean using a full installer media, not the minimal CD or server versions.

Thanks Vlad. Where do I get a PloP CD? Why is it so important to install using a USB port, rather than using a CD or DVD? I've always used a CD or DVD before without problems.

Thanks,

R.

---

### Post by monkeybrain20122 on 2014-05-10
Sounds like you need to upgrade your hardware. :)

---

### Post by Vladlenin5000 on 2014-05-10
You can use a DVD if you can boot from one. Meaning... You need at least a DVD-ROM drive (reader only) if you can burn the media somewhere else. The USB method is faster and usually safer - you can make many mistakes burning optical media. 

A PloP "boot manager" CD can be used to boot from a USB flash memory for those old computers that can boot from a CD but not from an external drive. 
[http://www.plop.at/en/bootmanager/download.html](http://www.plop.at/en/bootmanager/download.html) 
Just download the latest version. It's a ZIP file which contains an ISO inside. For the time being and for the aforementioned purpose all you need is the ISO. Create the bootable CD from that ISO - rewritable media is fine - just like you would with the Ubuntu's ISOs.

---

### Post by mörgæs on 2014-05-11
> **RMcGinnis said:**
> I've always used a CD or DVD before without problems.


Then just use the method again. Sorry for adding to the confusion. 
Please post back and tell how it proceeds.

---

### Post by AbleTassie on 2014-05-12
> **craig10x said:**
> Upgrading doesn't take a few hours if you do it directly from the iso installer, **and if he only runs one version of lubuntu, then the installer should offer the option of upgrading in addition to just wiping and replacing**...and that should only take about the time a clean install takes...well, perhaps a little longer since it has to bring over all your data, personal settings, and usually is able to bring over most of your installed apps...

important to remember to turn off any ppas you have prior to beginning it (in the software souces)...then it should go very smoothly...i have used that method about 5x now and had excellent results...i think the longest the whole process took was maybe 35 minutes (and i have a LOT of data to bring over...lol) :D

I never did it using the software updater but i'd imagine that way must take a lot longer since it has to keep going to the internet to get the stuff? where as the iso has it right on there already...

[B]Thanks to everybody, Craig, Morgaes, Monkeybrain, Vlad and others,
[/B]
**Re: Upgrade vs Reinstall:** _QUESTION:_ From what Craig says above, it sounds like if I use the Lubuntu 14.04 LTS (or 14.04.1 LTS) iso it gives me the option to upgrade,_** is that correct?**_ **(**Rather than forcing me to do a complete "clean install" (and then add back backed-up files, reinstall apps such as WINE, Libre Office, Pdf Shuffler, Kazam, Foxit Reader for Windows, maybe a JAVA plug-in, etc.)**)**. **I am presently dual-booting Lubuntu and Windows XP.**

**Re: Media for installation: **I can burn a CD, but not a DVD. But I can read DVDs. I can boot off a CD or DVD, but not a USB port. The method Vlad describes of burning a PloP "boot manager" CD that allows booting off a USB port sounds real interesting and possibly "safer." I think I may give that a try. Although having a Lubuntu 14.04 LTS CD or DVD for occasionally doing a live CD or DVD boot might be handy (I'd have to burn a DVD at the library though). 

**Re: upgrading my hardware:** As suggested by Monkeybrain, one of the great things about Lubuntu is that it can run on older hardware. My budget is kind of limited right now. And if I do a hardware upgrade in the future, I guess I could buy older, cheaper hardware (maybe refurbished) and just use the latest appropriate version of Ubuntu.

ANY OTHER COMMENTS ANYBODY HAS WILL BE WELCOMED. I am close to marking this thread as "SOLVED," although I will probably wait until July (as suggested by Monkeybrain) to do the upgrade or reinstall.

Thanks again,

R.

---

### Post by mörgæs on 2014-05-12
Upgrade is always a theoretical option, but in reality it often gives trouble. 

If you install Lubuntu 14.04 the good news is that you don't have to do it again before april 2017.

---

### Post by Danger_Monkey on 2014-05-12
I just updated my old ThinkPad T61, I run Kali and Ubuntu on it.  I upgraded it it in about 35 minutes.  I spent most of the time drinking coffee.

---

### Post by AbleTassie on 2014-05-13
Again, thanks to everybody. I just noticed that Morgaes is from Iceland. This intrigues me very much. I have never been to Iceland, but would like to visit someday. I know somebody who visited Iceland recently and liked it very much. I am in the Western U.S.; I will now mark this thread as SOLVED.

R.

---

