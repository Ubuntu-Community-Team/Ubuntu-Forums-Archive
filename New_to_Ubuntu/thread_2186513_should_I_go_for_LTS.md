---
title: "should I go for LTS?"
date: 2013-11-07
forum: New to Ubuntu
---

### Post by LinuxVirgin2000 on 2013-11-07
Hi, just trying to decide which release of ubuntu to use. once the support is no longer available for an opperating system what are the main problems that occur? Is there more chance of getting a virus or something? 

I guess what I'm trying to get at is there any reason I should consider installing 12.04 LTS as opposed to 13.10?

---

### Post by rburkartjo on 2013-11-07
lin  12.04LTS is a more stable release and will be supported for 5 years. depends what you want

---

### Post by Iowan on 2013-11-07
I have older hardware. As the revision numbers climb, the responsiveness declines. I've converted one machine to Lubuntu, another may follow at next upgrade.
I also have one server running 8.04 (shhh).
I might try a workstation on a new release - the rest go from LTS to LTS. Most of my machines are on 12.04, so I don't know what goodies have appeared in recent versions.
None of my machines are mission-critical, so an OS re-load isn't catastrophic.

---

### Post by newb85 on 2013-11-07
To the point, yes there are much higher security risks to running an unsupported release or not keeping your current release updated.  These risks are inconsequential if you run the machine in a vacuum (no internet connection or interaction with other machines via removable media).  Otherwise, stick with something supported and keep it updated.

You may want to install 13.10 and then upgrade to 14.04 (LTS) [s]when it's released next April[/s].  You'll have five years of support from there.

Edit: It's often best to wait a month or two after the initial stable release for a few more bugs to be worked out.

---

### Post by buzzingrobot on 2013-11-07
When a release goes out of support, no more bug fixes and security patched are released.  The repositories where other updates are made available go offline.  If you don't upgrade, you are on your own.

The differences between the 12.04 LTS and the current 13.10 release aren't terribly apparent to the casual user, I think. You might consider grabbing live images of both, booting and checking them out before making the call.

Many, many folks are happily using 12.04 and avoiding the churn of the non-LTS releases.  If you don't like the idea of re-installing or upgrade often, then LTS is for you.

12.04 is supported until 2017.  The next LTS will be 14.04, arriving in about 6 months.

Note that the latest version bump of 12.04 LTS is 12.04.03, available here: [http://releases.ubuntu.com/12.04.3/](http://releases.ubuntu.com/12.04.3/).

---

### Post by Impavidus on 2013-11-07
Running an end-of-live release has several disadvantages. In order of importance:
1: Bugs and security holes won't get fixed any more, which leaves your computer more vulnerable.
2: Without the repositories and other people using the same version, solving problems gets more complicated.
3: New add-ons and extensions that you have to download and install separately and manually may no longer work on the outdated software you have.
4: You won't get the new features of new releases of software. You won't get them by staying with a supported release either, but you will by upgrading to the next supported release. This is not so much an argument against running obsolete releases, but more for upgrading in general.

Usually I recommend people who don't want to update too often to use the LTS release. This half year it's somewhat different. Many people jump from one LTS release to the next as soon as the next is released. As the next release will be an LTS release this means that whether you install 13.10 or 12.04 now, in both cases you may want to upgrade next April or May anyway.

---

### Post by monkeybrain20122 on 2013-11-07
If you have relatively old hardware go for 12.04. Otherwise I would install 13.10 and update to the next LTS (14.04) next July (it is not essential that you upgrade your OS in step with Canonical's release tempo. It is usually better to wait a bit for post release bug fixes and ppas to be set up etc. My main system is 13.04, there is no compelling reason to upgrade in oct, will probably do it during Christmas)

I find Unity 7 in 13.04 and 13.10 faster and more optimized than 12.04, also you get more up to date software with 13.10, the repo in 12.04 is getting quite stale by now unless you use ppas. BTW with 12.04.3 you will have to upgrade your graphic stack comes April 2014.

P.S. A main difference between 12.04 and  13.04 onwards (12.10 onwards?) is the absence of internet search in the dash. If you don't feel comfortable about the idea you can disable it in 13. XX by going to System Settings > Piracy Settings and turn off online search (the System Settings button is on the upper right corner next to the clock)

---

### Post by monkeybrain20122 on 2013-11-07
> **Impavidus said:**
> Running an end-of-live release has several disadvantages. In order of importance:
1: Bugs and security holes won't get fixed any more, which leaves your computer more vulnerable.
2: Without the repositories and other people using the same version, solving problems gets more complicated.
3: New add-ons and extensions that you have to download and install separately and manually may no longer work on the outdated software you have.
4: You won't get the new features of new releases of software. You won't get them by staying with a supported release either, but you will by upgrading to the next supported release. This is not so much an argument against running obsolete releases, but more for upgrading in general.

Usually I recommend people who don't want to update too often to use the LTS release. This half year it's somewhat different. Many people jump from one LTS release to the next as soon as the next is released. As the next release will be an LTS release this means that whether you install 13.10 or 12.04 now, in both cases you may want to upgrade next April or May anyway.

About 4. You can add ppas to your sources list, IMO this is not so much a reason to upgrade the whole OS.

---

### Post by Buntu Bunny on 2013-11-07
> **monkeybrain20122 said:**
> ... System Settings > Piracy Settings ....

Ah, so that's the problem with Unity, it has piracy settings! ;)

LinuxVirgin2000, firstly, welcome to the Ubuntu Forums. If you have newer hardware, like tinkering around with your computer and OS, and don't mind upgrading frequently, you may enjoy the non-LTS versions. If you don't have time for that or aren't comfortable with it, then go for LTS.

---

### Post by elliotn on 2013-11-07
me I like new staff thus I upgrade every time a  new release is available

---

### Post by scottbomb on 2013-11-08
For servers, the only sane choice is LTS for rock-solid stability.

On my workstations, I like bleeding-edge new so I upgrade immediately. This does come with some problems though, as Monkeybrain has eluded to. If your tolerance level for bugs is low, it's always a good idea to wait a few months after every release. Otherwise, go with the latest release.

---

### Post by mastablasta on 2013-11-08
you need newer release only if you have very new hardware and don't want to mess arorund with installing new kernel and such on older release. same with applications. you get new versions out of the box. 

there are also usually some new features added.

but all in all it's ok to just stick with LTS. i plan to do so. i already have one like that, another one has 13.10 and i am hoping 14.04 LTS will also be as compatible as thi sone and then i willprobably switch the XP maschine to dualboot it with 14.04.

---

### Post by Bucky Ball on 2013-11-08
LTS is a perfect place to start with Ubuntu. Stable and long-term support. Once you get the hang of it, install whatever suits. I always stick with LTS for my main squeeze and have a couple of spare partitions for 'playthings'. ;)

---

### Post by Nr90 on 2013-11-08
upgrading from one 6 month release to the next also brings along some risk that your install will break.
Keep this in mind when picking a release.

Personally I run LTS for two reasons:
- The aforementioned annoyance of upgrading so regularly
- Some software like ROS is much easier to install on LTS releases

---

### Post by newb85 on 2013-11-08
> **Nr90 said:**
> upgrading from one 6 month release to the next also brings along some risk that your install will break.
Keep this in mind when picking a release.

Indeed.   One upgrade is pretty safe. Six is not.   I recently saw someone's source list that still had leftovers from karmic.   I was more than a little surprised.

---

### Post by buzzingrobot on 2013-11-08
I play around so much that it's unusual for anything to last six months.

That said, I don't upgrade in place.  Why?  Because I change things along the way.  The software that does the updating isn't magic.  The more my system has been altered from the baseline it expects, the more the chance for something going wrong.

So, I keep /home on a separate partition on a separate drive, do regular backups, and stash a copy of every config file I edit on Dropbox with notes indicating what the change does.  I don't keep a list of every app on a system, but I do know what I routinely install.  Re-installing them all takes one command. That approach does not prevent problems. An app. for example, might change the location of its configuration data from one folder in /home to another.

---

### Post by angelsimon on 2013-11-08
If you get the LTS version you will have a more stable SO and support for 5 years. On the other hand if you get the latest version available (13.10) you will get all the updates and new features of a brand new operating system. Your choice.

PS: I got 13.04 LTS :)

---

### Post by craig10x on 2013-11-08
Actually, 13.04 is not LTS....LTS is only every 2 years in the even numbered years...so, 12.04 is LTS 14.04 will be LTS...16.06 and so on....

For anyone installing now, i'd suggest 13.10 so you will still have 8 months of updates left (13.04 will run out in January)...and then UPGRADE to 14.04 in April....from that point, you could go LTS to LTS if you prefer (which would mean upgrading only every 2 years...of course you could actually run an LTS for 5 years but most of your apps won't be updated of course)...

@buzzingrobot: i agree...upgrades work well for me because i don't modify my system much (just some of the standard stuff that system settings allows you to do and carry over fine in the upgrades) and very few ppas...but if one does make lots of big changes and had lot of ppas then it's probably better to clean install as you do...

---

### Post by monkeybrain20122 on 2013-11-08
> **craig10x said:**
> 
For anyone installing now, i'd suggest 13.10 so you will still have 8 months of updates left (13.04 will run out in January)...and then UPGRADE to 14.04 in April...
.

No reason to upgrade in April. 13.10 is supported til July. I suggest to wait  a month to two after release to install the new system for post release bug fixes, especially if you use proprietary drivers.

---

### Post by Bucky Ball on 2013-11-08
> **monkeybrain20122 said:**
> No reason to upgrade in April. 13.10 is supported til July. I suggest to wait  a month to two after release to install the new system for post release bug fixes, especially if you use proprietary drivers.

+1.

---

### Post by newb85 on 2013-11-09
+1.  I'm editing my earlier post to reflect this point.

---

### Post by joyousjake on 2013-11-09
I'd say 12.04 is not as advanced as 13.10, and it would be worth it to give 13.10 a try. You can always upgrade to 14.04 in a few months. With web apps, more social integration, this release is much more useful.

---

### Post by ibjsb4 on 2013-11-09
> **rburkartjo said:**
> lin  12.04LTS is a more stable release and will be supported for 5 years. depends what you want

I agree and would add that newer is not always better :)

---

### Post by monkeybrain20122 on 2013-11-09
> **ibjsb4 said:**
> I agree and would add that newer is not always better :)

Yeah but in this case newer (13.xx) is better. :)

---

### Post by ibjsb4 on 2013-11-09
> **monkeybrain20122 said:**
> Yeah but in this case newer (13.xx) is better. :)

Yes, Unity has improved and if thats your choice, then joyousjake has a good answer for you.

> give 13.10 a try. You can always upgrade to 14.04 in a few months

But there are also differences in packages.  User options are being removed.  One example is Nautilus.  When it comes time for me to do a version upgrade I will install Nemo instead.  The list of what I call degraded packages is not long, but enough of a difference for me to stick with 12.04 and ..

Myself, when I get my system tweaked out the way I want it, I just want to be able to use it for a few years.  Really the tweaking never stops, thats what my testbox is for, but my just to use everyday machine is 12.04, I got it set up the way I want it and its nice to know that if I want to, I can  use it till 2017.

---

### Post by Remten on 2013-11-09
I really, really wanted to just run LTS (specifically, xubuntu 12.04 lts) because I wanted to install something that had been thoroughly tested and I didn't want to have to go through the whole re-do in just a few months. But I had a lot of problems with drivers for my new laptop with LTS. So after struggling with LTS for weeks, I ended up installing 13.10, and so far, things have been working out. (although that's still with having had to do a fair amount of tinkering to get things working just right!)

The good thing is that you can try both before committing -- just make a live CD or live USB for each version you are considering. You can test each of them and decide which one works better for you. When you're satisfied, you can do the full install to the hard drive.

---

