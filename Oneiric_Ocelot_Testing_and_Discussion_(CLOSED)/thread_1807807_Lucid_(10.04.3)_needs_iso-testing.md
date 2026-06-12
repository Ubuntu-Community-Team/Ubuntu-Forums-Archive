---
title: "Lucid (10.04.3) needs iso-testing"
date: 2011-07-19
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2011-07-19
I realize this is totally OT (not a Oneiric problem) but I just received a NEW notice regarding the upcoming Lucid point release:

[http://iso.qa.ubuntu.com/qatracker/](http://iso.qa.ubuntu.com/qatracker/)

I'd even been a bit slow testing the initial image but with no more than 48 hours remaining before it's released I thought I'd give those who are bored something to do, if they're so inclined :D

Apologies for going OT but I know there are a few other iso-testing junkies hanging out here ;)

---

### Post by kansasnoob on 2011-07-19
Ouch, they're rebuilding some images again already:

[http://iso.qa.ubuntu.com/qatracker/](http://iso.qa.ubuntu.com/qatracker/)

Scary stuff for an LTS :(

The i386 Ubuntu live worked fine for me, now for some test installs.

---

### Post by ranch hand on 2011-07-19
Can't help with this one, too scary for me.  Every Ubuntu release from 10.04 (rc was fine) makes my HDD make terrible noises.

Sounds very destructive.

Xubuntu and Lubuntu seem to boot fine but I just don't feel like risking my HDDs on any of them.

---

### Post by dino99 on 2011-07-20
hdd noise; have uninstall hddtemp to silent this problem. Have been reported long time ago but never fixed.

---

### Post by VMC on 2011-07-20
Actually, this is the only news of late that interest me. I plan to stick with Lucid to the bitter end.

I'll be interested to see how the next LTS develops. I don't much care for Unity, gnome2 is all I need.

I'm waiting for Kubuntu and KDE 4.7.

---

### Post by kansasnoob on 2011-07-20
It's probably not a big deal anyway, but they've done a couple of rebuilds so I'm retesting today :)

I did decide to skip the upgrade testing though. Thinking that there would be no more Karmic --> Lucid or Hardy --> Lucid upgrade testing, since both Karmic and Hardy have reached end-of-life, when I moved my office I tossed nearly all of my old live media that's no longer supported :(

I know that I could find the old images and perform the installations, etc. But it seems almost pointless to me since it would be impossible AFAIK to completely update either Karmic or Hardy.

---

### Post by kansasnoob on 2011-07-20
> **VMC said:**
> Actually, this is the only news of late that interest me. I plan to stick with Lucid to the bitter end.

I'll be interested to see how the next LTS develops. I don't much care for Unity, gnome2 is all I need.

**I'm waiting for Kubuntu** and KDE 4.7.

I'm pretty well sold on Lubuntu ATM, but I'm dieing to have a look at the new "low-fat" Kubuntu spoken of some time ago.

One of the things I really like about Lubuntu is the ability to install only "lubuntu-core" to an existing Ubuntu install, thereby not installing a whole raft of unneeded packages :)

Things should settle down here soon so I can start playing more. I miss being able to play on the puter, but having a roof over my head had to take precedence ATM :(

---

### Post by cipherboy_loc on 2011-07-20
What do you want tested, and will installing it in VirtualBox work for testing purposes? 


Cipherboy

---

### Post by seeker5528 on 2011-07-20
> **kansasnoob said:**
> Ouch, they're rebuilding some images again already:

[http://iso.qa.ubuntu.com/qatracker/](http://iso.qa.ubuntu.com/qatracker/)

Scary stuff for an LTS :(

The i386 Ubuntu live worked fine for me, now for some test installs.

Scary that they are re-building or did you mean one of these?

> Lucid 10.04.3	 
813143	Ubuntu	Fix Committed	Critical	wubi 10.04.3 rev191 fails with: TypeError: __init__() got an unexpected keyword argument 'metalink3'
812744	Ubuntu Translations	Triaged	Low	Ubiquity long German translation doesn't fit
656486	xserver-xorg-video-ati	Confirmed	Medium	error de Video - [DRM: radeon_ttm_backend_bind] * * ERROR no pudo enlazar 1.772 páginas
645818	usb-creator	Triaged	Medium	Unknown keyword in configuration file: gfxboot
771485	ubiquity	Triaged	Medium	oem-config desktop icon and confirmation dialog are not transtated
812232	tzsetup	Triaged	Medium	lucid debian-installer: timezone screen not translated
365157	casper	Confirmed	Undecided	Kubuntu live session has open TTY's left when Stopping
812738	apport	New	Undecided	No permission to /var/log/installer/casper.log
813056	ubiquity	New	Undecided	OEM install: "incomplete language support" shown twice
813065	ubiquity	New	Undecided	Live sesssion switches to VT console briefly
Lucid 10.04.2	 
656486	xserver-xorg-video-ati	Confirmed	Medium	error de Video - [DRM: radeon_ttm_backend_bind] * * ERROR no pudo enlazar 1.772 páginas
718671	ubiquity	Confirmed	Medium	hitting "Enter" during slideshow closes it/skip the current task without confirmation
227869	base-installer	Triaged	Medium	Server installer should not use -server kernel for non-PAE CPU's
645818	usb-creator	Triaged	Medium	Unknown keyword in configuration file: gfxboot


Later, Seeker

---

### Post by kansasnoob on 2011-07-20
> **seeker5528 said:**
> Scary that they are re-building or did you mean one of these?



Later, Seeker

Any of the above :)

Only those hiding under a rock somewhere would imagine that less than a significant number of Ubuntu users dislike Unity enough to want to use the LTS for a while.

I just want to be sure they can install the LTS w/o any huge problems. I've tested three potential images ATM w/o any problems (on two different sets of hardware) so I think we're OK :D

The LTS still has about 21 months of support left for the DE version and 2 years more than that for the server version so, contrary to some statements, it's hardly prehistoric. And 12.04 will be nearly due for it's second "point release" when 10.04 reaches EOL, so IMHO Ubuntu is in fine shape.

---

### Post by kansasnoob on 2011-07-20
> **cipherboy_loc said:**
> What do you want tested, and will installing it in VirtualBox work for testing purposes? 


Cipherboy

You can read all about it here:

[https://wiki.ubuntu.com/Testing/ISO/Procedures](https://wiki.ubuntu.com/Testing/ISO/Procedures)

It releases tomorrow so it's probably too late now, but more iso-testers are always welcome :D

---

### Post by seeker5528 on 2011-07-20
> **kansasnoob said:**
> I just want to be sure they can install the LTS w/o any huge problems. I've tested three potential images ATM w/o any problems (on two different sets of hardware) so I think we're OK :D

I have not actually tried to install it, but I did use usb-creator to set up 10.04.2 on a flash drive and running from the live session there didn't seem to be any big issues. None of the 10.04.2/10.04.3 issues listed seem all "scary" to me.

There is always potential for regressions, in particular with hardware support as drivers are updated, but the expectation is that changes will be conservative and more stuff is fixed than broken.

I'll have to zsync my ISO, the last time I had an issue that required me to have 2 ISOs, one in '/boot-isos/' on one of my partitions so I could use a super grub 2 disk to loop boot the ISO, then another on a different partition because I couldn't access the ISO on the partition that contained the '/boot-isos/' directory when booted from an ISO stored there.  

I thought is was because of usb-creator in Oneric not doing something correctly for the older version of the distribution, but it turned out there was some issue that required me to wipe the flash drive, so may not have been the fault of usb-creator, if nothing else it's probably at least worth testing if usb-creator in Oneiric will create a bootable flash drive when pointed at the iso for 10.04.3. 

Was trying to get Avast to work from the flash drive, but the Linux version seems broken, tried Natty, Lucid, and a recent version of System Rescue CD, and Avast starts initally, but after updating the definitions, it no longer works. 

Later, Seeker

---

### Post by tlcstat on 2011-07-21
Greetings,
Yesterday, July 29, I did a full install of 10.04 from my older CD onto a thumb drive for a friend to try out. The install downloaded 336meg of updates due to its age, including a couple of kernel updates. It skipped the first kernel and installed the second. Could it have updated to the new release? Just a question.
tlcstat

---

### Post by Bucky Ball on 2011-07-21
> **tlcstat said:**
>  Could it have updated to the new release? Just a question.
tlcstat

If it's not released until tomorrow, I doubt that. ;)

---

### Post by seeker5528 on 2011-07-21
> **tlcstat said:**
> Could it have updated to the new release? Just a question.
tlcstat

If you installed from an earlier 10.04/10.04.x install CD, and keep up to date, then you will have the same thing as if you install 10.04.3 and keep it up to date.

Later, Seeker

---

### Post by tlcstat on 2011-07-21
Greetings,
Thanks Seeker, actually I gave that other installation to a friend but I'm about 20 minutes from having the new version downloaded at this moment. Will probably wait until Monday to install. 
tlcstat

---

### Post by cariboo on 2011-07-21
It would be nice if we could test the iso using testdrive-gtk

---

### Post by kansasnoob on 2011-07-21
> **tlcstat said:**
> Greetings,
Thanks Seeker, actually I gave that other installation to a friend but I'm about 20 minutes from having the new version downloaded at this moment. Will probably wait until Monday to install. 
tlcstat

Just to be totally clear; 10.04.3 is only a "point release" of 10.04. If you have 10.04 installed and properly updated you'll have 10.04.3 soon :)

AFAIK the only two reasons for LTS point releases is to allow installation w/o so many updates and to be able to create a more "up-to-date" live CD or USB.

My concern was being certain that no major br4eakage was present in this point release. I think 10.04 will remain very popular throughout it's lifespan.

I have Natty classic running perfectly but when I boot into Lucid and use it for a day or two I honestly can't tell the difference, other than a slight change in boot :)

---

### Post by drs305 on 2011-07-21
I received the email saying it's been released, and sure enough, there it was:
[http://releases.ubuntu.com/]("http://releases.ubuntu.com/")

---

### Post by kansasnoob on 2011-07-21
> **drs305 said:**
> I received the email saying it's been released, and sure enough, there it was:
[http://releases.ubuntu.com/]("http://releases.ubuntu.com/")

Cool!

Good to see you around :)

Hopefully in a couple of weeks I'll be able to resume my normal activities.

---

### Post by kansasnoob on 2011-07-21
> **drs305 said:**
> I received the email saying it's been released, and sure enough, there it was:
[http://releases.ubuntu.com/]("http://releases.ubuntu.com/")

BTW, the md5sum was the same as the last of the images I tested :)

---

### Post by VMC on 2011-07-22
> **kansasnoob said:**
> BTW, the md5sum was the same as the last of the images I tested :)

Yes, your correct. I wondered why the iso wasn't updated for today. Odd, I haven't been checking Lucid's progress, and the first mention of the point issue, is the release issue, I downloaded.

I have been keeping Lucid updated all along, but the generic change was being held back, so I needed to issued a "dist-upgrade" to get the latest. The 10.04.3 has the correct generic already there, as it should.

---

### Post by jerrylamos on 2011-07-22
Installed 10.04.3 along with Ocelot, Narwhal, and Meerkat.  Went O.K. except for taking ages to install "language packs" I'll never use.  This tower is not about to travel to different countries.

Haven't done the "update" yet.

Jerry

BTW. 10.04.3 boots nice and fast and has very crisp screen response compared to sludgy Unity....

---

### Post by jerrylamos on 2011-07-22
Just updated Ocelot, chose Unity 2D, and screen action is a lot faster.  Snap, snap instead of smudgy snail fades.  I'm happy.

Jerry

---

### Post by VMC on 2011-07-22
> **jerrylamos said:**
> ... **except for taking ages to install "language packs" I'll never use**.  This tower is not about to travel to different countries.

Haven't done the "update" yet.

Jerry

BTW. 10.04.3 boots nice and fast and has very crisp screen response compared to sludgy Unity....

The trick to stopping it from installing language packs, is to unplug the internet right after it finds you clock location and just begins installing. It takes me only 5 minutes for a complete install using that method. I've done it that way for a very long time without any trouble.

---

