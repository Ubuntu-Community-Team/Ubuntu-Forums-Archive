---
title: "Kubuntu 15.04 Memory issues"
date: 2015-08-02
forum: New to Ubuntu
---

### Post by arieleoar on 2015-08-02
Hi everyone!

I've got some memory issues with the new Kubuntu 15.04 (kde5); since i've made the actualization from 14.04 (the last week) it's been using a lots of memory, from 0,4Gb that was using in 14.04, it uses 0,8 ~ 0.9 Gb now with kubuntu 15.04. I can't identify what program/app uses that amount of memory because i'm not too "familiarized" with ksysguard (i left some snapshots)

[ATTACH=CONFIG]263588[/ATTACH][ATTACH=CONFIG]263587[/ATTACH]

The PC is pentium4 dualcore 3.0ghz, 1,256Gb of ram, 2Gb of swap, 512Mb geforce 6200 vcard

In the other hand i have some issues with plasmashell and my vcard, it crashes no matter what (privative/noveau) driver i use qhen i select opengl in the compositor, i've to use it with xrender but it becomes slower sometimes.

if you need some info i'll post it, Regards!

---

### Post by NathanRodriguez on 2015-08-03
This user reported the same on KDE forum:
[https://forum.kde.org/viewtopic.php?f=289&t=125251](https://forum.kde.org/viewtopic.php?f=289&t=125251)

Looks like there's a memory leak waiting for correction.

---

### Post by mastablasta on 2015-08-03
> **NathanRodriguez said:**
> This user reported the same on KDE forum:
[https://forum.kde.org/viewtopic.php?f=289&t=125251](https://forum.kde.org/viewtopic.php?f=289&t=125251)

Looks like there's a memory leak waiting for correction.

15.04 while "stable" (i.e. not changing= frozen)  it's Plasma 5 is actually still under heavy development. so you can expect more issues like this. If you are using the computer then it is better to stay with 14.04. 

another option would be disabling various special effects.

with 15.04 Ubuntu and other variants it might not be such an issue. though sitll considered to be a bit more testing grounds they do not introduce some major changes like plasma 5 is.

looks like plasma is leaking memorry. also you have Mozilla Firefox taking up 100MB.

---

### Post by buzzingrobot on 2015-08-03
Watch the figure for PlasmaShell (more or less the core of KDE) over time and see if it keeps increasing. It should be smallest immediately after a reboot and launching KDE.  If there is a substantial memory leak, its memory consumption will continue to grow until you quit KDE or shut down the machine. (Programs and processes grab memory all the time, and then release it for use by something else. If that release does not occur correctly, then that portion of memory won't be available for anything else.  That's a memory leak.) (So, it's normal to see KDE's memory allocation increase as you do things like open apps and windows in KDE, but when you close those apps and windows the memory should be released.)

The figure for Firefox seems OK from my experience.  I'll guess you had only one tab open.  Here, Firefox with a few tabs open is typically at 350-400k.

---

### Post by arieleoar on 2015-08-03
Thanks for the answers!

I've been reading the report in kdeforum and the bugtrace they posted, seems that i've the same problem, worst, because they have lots of memory (16Gb) and i have only 1,2Gb, so plasmashell increases everytime and not only loads the memory it loads the swap, and the system becomes more slower every time, the weird is that i'd not any freezes or hangs-up, but seems nearly when some app crashes and even i can't how me the report bug dialog because kde says to me "insufficient memory to make traceback".

So now on i'm using plasmashell without any widget or panel, no clock and notifiers, nothing. even i disabled the efects and the lock screen. it reduces the memory consumption and leak but i'm still having more consumption than older version of kde (now ~0,2Mb more). I can't downgrade because i'd to do a fresh install of the system, i haven't a good internet connection in my home, so i downloaded a iso image, bad for me, i hadn't read the bugs before :P

Now, i need a little more memory, how i can disable desktop searchs, akonadi (if kde5 uses it) or some other background app that consumes memory? i've to use blender for an engineering work and it becomes slower... -.-

Ahh, > looks like plasma is leaking memorry. also you have Mozilla Firefox taking up 100MB. Yes firefox and any other webbrowser takes the same amount or more when i use it, i don't know why, but i don't use webbrowsers everytime so is fine to me :P

How i contribute to fix/help in this memory bug on plasmashell? does it will take much time to be fixed? as i was reading posts of this memory leaks nobody has a solution, it can only be fixed by the devs of kde?

---

### Post by mastablasta on 2015-08-04
> **arieleoar said:**
> 

Now, i need a little more memory, how i can disable desktop searchs, akonadi (if kde5 uses it) or some other background app that consumes memory? i've to use blender for an engineering work and it becomes slower... -.-


It's in system settings I think. another option is to leave it overnight so it indexes the disk. it then calms down. but this problem was solved in plasma 4. it depends how many files you have and all. mine took about 2 hours to index and then it's not really noticeable.

> 
Ahh,  Yes firefox and any other webbrowser takes the same amount or more when i use it, i don't know why, but i don't use webbrowsers everytime so is fine to me :P

I though it was stuck in memory after you closed it. if you were using it at the time of screenshot then it's ok.

> 
How i contribute to fix/help in this memory bug on plasmashell? does it will take much time to be fixed? as i was reading posts of this memory leaks nobody has a solution, it can only be fixed by the devs of kde?
[/QUOTE]

if you think it's a bug post it on Launchpad or if you know which app then [https://wiki.kubuntu.org/Kubuntu/Bugs/Reporting](https://wiki.kubuntu.org/Kubuntu/Bugs/Reporting)

to gain more RAM:
you can add only a windows manager and use that when you work. suggest you use icewm.

you can disable various special effects. there used to be kubuntu low fat package I am not sure if they have that for plasma 5 - it gave kind of 2D desktop but worked wonders on old PCs. make sure disk is indexed or disable indexing.

your ram is low for blender. if you can I would upgrade it at least a a little bit. I used to have 1.2 as well. I've moved it to 2 GB DDR2 and replaced the iDE disk with sata. noticeable improvement I must say. i would upgrade it more if i could but mobo can only handle 2 GB max. I was only sad as I couldn't get the new GT 730 Nvidia card to work. so I returned the card and I am using the ancient old Radeon 9600 which seems to have some drivers problem (they do not spin up the fan when it get's hot- sometimes they do, sometimes they don't).

More ram is always good. it can make even old PC fly. I have a single core with winXP. I pumped it 4 GB ram. it can run many games. some even from 2012... :-). it takes time to boot but once it boots it works nice.

---

### Post by arieleoar on 2015-08-06
First is first thanks for answering mastablasta!

> if you think it's a bug post it on Launchpad or if you know which app then [https://wiki.kubuntu.org/Kubuntu/Bugs/Reporting](https://wiki.kubuntu.org/Kubuntu/Bugs/Reporting)

The bug is already reported, so it's time to stand by for fix :S

> you can add only a windows manager and use that when you work. suggest you use icewm.

A question about that: IceWM is a desktop environment like Kde's Plasma 5 or Ubuntu's Unity?  or is a manager like Kwin? what specifically does Kwin? (i mean, i'm usually relating plasmashell/plasma in Kde4 with the analog explorer.exe in winxp, that's where i come from, but what/why kwin? what is it?)

> you can disable various special effects. there used to be kubuntu low  fat package I am not sure if they have that for plasma 5 - it gave kind  of 2D desktop but worked wonders on old PCs. make sure disk is indexed  or disable indexing.

Everything is disabled, every effect and even the compositor and the disk indexation, and kubuntu-low-fat-settings package does not exist since Kde4.

> your ram is low for blender. if you can I would upgrade it at least a a  little bit. I used to have 1.2 as well. I've moved it to 2 GB DDR2 and  replaced the iDE disk with sata. noticeable improvement I must say.

this is the worst, this motherboard is all "dual channel" and whatever it wants but is ASRock 775g, only 2 DDR2 slots with a max of 2Gb like yours, no PCIE slot. It's a shame on me if i try to upgrade this archaic machine instead save money to buy a new. Too bad was had to bought it a geforce 6200 because it burned a geforce 6600 (begun to show artifacts and then died).

It already has a sata disk, was one of the upgrades I've made (and the 1Gb memory ram card at the same time), and i don't regret that, it's notably more speedy than before. i've managed once to run in winxp DMC5 so i think this machine have a lot to give.

---

### Post by mastablasta on 2015-08-07
> **arieleoar said:**
> 
A question about that: IceWM is a desktop environment like Kde's Plasma 5 or Ubuntu's Unity?  or is a manager like Kwin? what specifically does Kwin? (i mean, i'm usually relating plasmashell/plasma in Kde4 with the analog explorer.exe in winxp, that's where i come from, but what/why kwin? what is it?)

yes and no. it's a separate windows manager. it's not a DE as it by itself have all the extra stuff a DE would have (e.g. network manager, maybe keyboard, system settings etc. I am not sure what stuff go into DE).
you won't be in Kubuntu anymore but you will have plenty of RAM. ToriOS (made by forum members here) uses jwm only and on boot it uses about 60 MB ram. desktop doesn't looks as nice but get's the job done.

if you add a desktop - say you install Xubuntu-dektop or just XFCE4 packages to your current install - they might pull in other things that you don't need - eg. if you already have network manager you might end up with 2 of them etc. but with window manager it's just that. they are also pretty basic & look like win 98. have a look at antix to see how icewm looks like. once install you will have option to select at login if you want to start KDE or windows manger or another de.

> Everything is disabled, every effect and even the compositor and the disk indexation, and kubuntu-low-fat-settings package does not exist since Kde4.

issue is KDE5 then. it is still in development stage not really ment for production PCs. new version of Kubuntu is due in Oct.

> this is the worst, this motherboard is all "dual channel" and whatever it wants but is ASRock 775g, only 2 DDR2 slots with a max of 2Gb like yours, no PCIE slot. It's a shame on me if i try to upgrade this archaic machine instead save money to buy a new. Too bad was had to bought it a geforce 6200 because it burned a geforce 6600 (begun to show artifacts and then died).

I think mine is Asrock too. yes if you can save then it's better to save for newer one. I saw they sell descent i3 PC's with 1 TB disk and 4 GB ram , intel GPU for 350 EUR. thins kind of stuff might be cheaper in US if you are there. if you have good case and PSU unit then you should be able to upgrade well and get the upgrade even cheaper. I planned AMD A8 APU (the reduced price now it seems), but some A6 seem good as well. AMD motherboards and CPU's are a bit cheaper. and they might be slower but their GPU is stronger than Intel. anyway I was calculating I should be able to upgrade to a descent PC for about 250 EUR, but unfortunately I had less so I decided to do a RAM, disk and GPU upgrade instead. I had to return the GPU (twice) as it didn't want to recognise it.
> 
It already has a sata disk, was one of the upgrades I've made (and the 1Gb memory ram card at the same time), and i don't regret that, it's notably more speedy than before. i've managed once to run in winxp DMC5 so i think this machine have a lot to give.

save up the money (at least 350 EUR for a descent PC maybe a bit more for good GPU if you do videos), use lighter DE for now (maybe windows manager only or go with Xubuntu and use 2D desktop there) you can use this PC later as server for data backup or to share videos you make and pictures with family using piwigo galery or something. or create your cloud with owncloud.

---

