---
title: "detailed ugrade questions"
date: 2011-12-31
forum: New to Ubuntu
---

### Post by degarb on 2011-12-31
I have a machine running 9.10 since dec 09. It runs great, still, doing video (over network and streaming) office, browser, stream tuner, music over network.  The machine specs are low: 600 mhz, 500 meg ram and 6 gig hardrive, and sysop that feels more at home in windows and lost in Ubuntu.  It took me two days of trying to install my wireless card (no wired ethernet card); I finally installed the gui for wireless windows drivers and installed the xp driver to get wireless card working.  I did a sudo apt-get upgrade.  It said I would loose 6 megs, but lost 300 of my 580 megs of free disk space.  I ran apt clean, got 24 megs, then bleach bit to get 300 megs back.  This made me weary of the competency of the upgrade programmers.

Still, 10.04 lts is available in the upgrade manager. 

1. Will 500 megs of space be enough?

2. What will I gain?

3. Will I need to change my repo list ?

4. Will I need to reinstall my software?

5. Will I loose my wireless card?

6.  Could I brick the machine?

7.  Will there be a performance hit by upgrading?

8. What will the final loss of space be after cleanup?

9.  How long will upgrading take: both in my time and bench time?

10. I was a little under specs for  Ubuntu 9.10, but it runs fine even faster and better than xubuntu.  Have other's installed 10.04 on this type of system-p3 generation.

---

### Post by LowSky on 2011-12-31
With so low specs you should really look at other releases. Lubuntu would be great if it will even run. Honestly anything under 1Ghz these days is cringe-worthy for nearly any operating system created in the last 5 years.

You should really back up your personal data and do a fresh install.

If I were you look to smaller releases like Puppy or Damn small Linux.

---

### Post by grahammechanical on 2011-12-31
So, the hardware is working fine and the OS is doing its stuff, why change anything?

Wait until something in the machine breaks. Then may be you will find that you cannot buy a replacement part because they are no longer sold or those that are available are not compatible with your remaining hardware. At some point you will decide to buy a new machine, then upgrade the OS.

Regards.

---

### Post by degarb on 2011-12-31
> **grahammechanical said:**
> So, the hardware is working fine and the OS is doing its stuff, why change anything?

Wait until something in the machine breaks. Then may be you will find that you cannot buy a replacement part because they are no longer sold or those that are available are not compatible with your remaining hardware. At some point you will decide to buy a new machine, then upgrade the OS.

Regards.


This makes sense, since, obviously changing to lubuntu or puppy would be far more painful than staying with same working OS.  Just trying to reconfigure and reinstall my aps alone would take weeks.  In windows it a true reinstall takes me about 21 to 30 hours reinstalling drivers, programs and reconfiguring 80 plus programs.  I tried in 09 and 10, puppy, vector, crunchbang, slitaz, and xubuntu;  honestly, didn't like any over ubuntu 9.10. All were broken oSes that would take weeks to get to a productive state, for me at least. Slitaz was the only standout, with impressive performance, but steep learning curve, especially if you didn't speak polish. 

I would upgrade to 10-04 , only if is feasible and the 10 posted points were a go.

---

### Post by Karlchen on 2011-12-31
Hello, degarb.

[U]Summary:
[/U]Let me start by giving the summary at the beginning: With this machine, in particular with a tiny 6 GB HDD, you would have been much much better off by installing Ubuntu 10.04 Desktop 32-bit from the very start and keep it running till either the LTS period (long term support) expires or your machine retires for good, whichever will happen first.
Lucid Lynx (Ubuntu 10.04) will run fine on any machine which can run Karmic Koala (Ubuntu 9.10). I.e. the minimum system specifications are more or less identical.
The difference is that Karmic Koala passed away in April 2011 and will not receive any security updates or bugfixes whereas Lucid Lynx will expire at the end of April 2013.

> 1. Will 500 megs of space be enough?The distribution update from Karmic Koala to Lucid Lynx will pull almost a complete operating system to your disk - or at least it will try to do so - before starting to perform the update steps.
In short words: with just 500 MB of available disk space, I tend to reply, "Forget it."

> 2. What will I gain?Security updates and bugfixes until April 2013. Due to the lack of available disk space, however, you are almost guaranteed to gain a lot of trouble during the upgrade process. 

> 3. Will I need to change my repo list ?Good news: unless you have added repositories to the list manually the updater will take care of the Ubuntu default repositories and update the list automatically.

> 4. Will I need to reinstall my software?*Unambiguous* response: this depends. The software which has been installed from the Canonical repositories will be updated in the course of the distribution upgrade. Software which you have installed yourself using third party repositories or manually may need a manual update afterwards.

> 5. Will I loose my wireless card?As far as the hardware is concerned: definitely no. With respect to the driver software: cannot give any warranty.  Several scenarios are imaginable: 
[LIST]
[*]the update software does not touch your wireless software and Lucid likes it as well. You have been lucky.
[*]the update software updates your wireless software correctly and Lucid likes it. You have been lucky.
[*]the update software simply disables your wireless software or updates it incorrectly. Bad luck. Searching for the right driver software will start all over.
[/LIST]
> 6.  Could I brick the machine?No.

> 7.  Will there be a performance hit by upgrading?No. Having performed the upgrade from Karmic Koala to Lucid Lynx I have not noticed any change in performance at all. But this may depend on the specific machine.

> 8. What will the final loss of space be after cleanup?Cannot tell. Have not checked. Yet, my harddisk had a total capacity of 160 GB, not 6 GB. I tend to think that Karmic Koala and Lucid Lynx require almost the same amount of disk space, plus/minus some hundreds MB.

> 9.  How long will upgrading take: both in my time and bench time?This largely depends on the processor speed and on the harddisk speed. So if I were you I would expect half a working day. If it is anything below 4 hours then rejoice and grant a larger hard disk to your poor old machine as a reward.

> 10. I was a little under specs for  Ubuntu 9.10, but it runs fine even faster and better than xubuntu.  Have other's installed 10.04 on this type of system-p3 generation.Sorry. No. My ancient PIII had only 256 MB of RAM and it would not accept more, so no chance. By the way, it had a *gigantic* 20 GB EIDE harddisk. If I had not disposed of it and of the whole machine I would gladly send it over to you, because with just 20 GB of disk space the main problem which will make any dist-upgrade fail would simply be gone: lack of disk space.

_Essence:_
If you can spare the time to do a clean install, install Lucid and live happily ever after until April 2013, in particular in case Lucid should bring better built-in support for your WIFI card.
If you cannot stick with Karmic Koala and live almost as happily ever after.

Happy New Year and kind regards,
Karl

---

### Post by degarb on 2011-12-31
Karlchen, the quality of your response is another reason I chose Ubuntu, and will recommend it to other real people.  I just need to be careful to push only lts releases in future.

---

### Post by snowpine on 2011-12-31
Hi degarb, why are you starting so many threads asking the same question?

[http://ubuntuforums.org/showthread.php?t=1901447](http://ubuntuforums.org/showthread.php?t=1901447)
[http://ubuntuforums.org/showthread.php?t=1901032](http://ubuntuforums.org/showthread.php?t=1901032)
[http://ubuntuforums.org/showthread.php?t=1902424](http://ubuntuforums.org/showthread.php?t=1902424)

9.10 is no longer supported, and 15gb is the recommended minimum hard drive for Ubuntu. If you are not willing to upgrade your hardware, then I think your best bet is a fresh install of a lightweight, long-term support release such as Lubuntu or Xubuntu 10.04.

---

### Post by degarb on 2011-12-31
> **snowpine said:**
> Hi degarb, why are you starting so many threads asking the same question?

[http://ubuntuforums.org/showthread.php?t=1901447](http://ubuntuforums.org/showthread.php?t=1901447)
[http://ubuntuforums.org/showthread.php?t=1901032](http://ubuntuforums.org/showthread.php?t=1901032)
[http://ubuntuforums.org/showthread.php?t=1902424](http://ubuntuforums.org/showthread.php?t=1902424)

9.10 is no longer supported, and 15gb is the recommended minimum hard drive for Ubuntu. I think your best bet is a fresh install of a lightweight, long-term support release such as Lubuntu or Xubuntu 10.04.

One thread was about subversion and repo list, one in cafe wasn't support but why the upgrade issue prevents the wider acceptance of linux via computer shops, I believe the subversion thread caused me to get locked out of machine, since since the package managers don't auto cleanup.   This thread outlines ten questions that needed essential answers, not clearly outlined in other threads. The clear answer give above here is what wass needed to decide if pulling the upgrade trigger is worth the risk.

I think if I have another machine with these hardware specs, the clear winner to me and my tests and preference is not a stripped down OS that you must just un-strip-down to get productive, rather 10.04 per this thread.  Also, note, I can run xp fine on external usb drive with 6 gig partition under ubuntu, using virtual box.  You probably can tell, I didn't buy the hardware specs given for ubuntu 9.10, and thankfully so. It would be nice to have 15 gigs, but this isn't apple and windows 7 with new hardware land.  I still must admit, xp works great, I don't get windows 7 or the need.  A newer Ubuntu, may have more hardware support and could be easier; I get that. Security updates in Ubuntu, not so much.

---

