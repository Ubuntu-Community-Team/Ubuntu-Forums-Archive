---
title: "Is there a non-freezing OS out there?"
date: 2007-01-28
forum: Other OS Talk
---

### Post by Nda on 2007-01-28
Oh dear, another complete freeze-up in Ubuntu 6.06 this morning.  No mouse, trackpad or keyboard input possible so I had to do a hard reset, then restart.  

Two apps I'd added to Sessions/Startup didn't start, so I deleted them, restarted, added them back in, restarted, but one - DevilsPie - won't start at all, so my nicely centred windows are all opening top left again. :mad:

It's not a hardware problem as it didn't happen when Windows was on this machine (Thinkpad T30, P4 1.8Ghz, 512 MB ram).  I don't have any fancy graphics stuff or video drivers installed.  It's just a standard machine with a standard Dapper setup.  Apart from freezing up randomly, Ubuntu works well, including hibernate and screensaver.

I'm getting a bit weary of this though, and thinking it might be time to move on.  I've done a search and it seems that the problem still happens in Edgy so that's not an option for me.

The question is therfore, is there a more reliable version of Linux that won't keep freezing?  Is there a distro that has a reputation for reliability and stability?  Have any of you had the same problem with Ubuntu but not with a different OS on the same machine?

My needs are straightforward: internet, email, office apps, photo editing.  I don't play games and I'm not interested in flashy 3D graphics effects.  I just want a system that is functional and reliable and doesn't require a high level of command-line knowledge.  Ideally it would have forums as good as these, but I doubt I'll find that!

Any recommendations would be appreciated.

Nda

---

### Post by Rodneyck on 2007-01-28
It actually could be a hardware problem and two things come to mind right off the bat, a failing hard drive and/or failing memory. You might want to run scans for both just to be sure.

I always thought Ubuntu Dapper was suppose to be the stable version.  I am running Kubuntu edgy at the moment and have never experienced any problems. You could try a lighter desktop environment and fewer installed apps in a distro, such as Xubuntu, Vectorlinux, Dreamlinux or Debian itself. 

What I would advise is to just start downloading the livecds and giving them a try. [www.distrowatch.com](www.distrowatch.com) is a good place to start.

---

### Post by Nda on 2007-01-28
Rodney,

I'm fairly confident it's not the hardware as I had Breezy on this machine first and that never froze, whereas Dapper has done since I installed it six months ago.  I have Dapper on my desktop machine as well, and that freezes sometimes.  I am also not the only one with this difficulty as this 40 page thread: [http://www.ubuntuforums.org/showthread.php?t=193283&highlight=dapper+freezes ]("http://www.ubuntuforums.org/showthread.php?t=193283&highlight=dapper+freezes")
and others show.  I will run a memtest tonight though as I've never done that.

I'll have a look at the OSs you mention.  I am aware of Distrowatch and check on it regularly but there are so many distro's that I don't know which to try.  That's why I was hoping someone who had suffered Ubuntu freezes could point me at one that didn't keep locking up.

Nda

---

### Post by mips on 2007-01-28
Maybe try Debian or Sabayon ?

---

### Post by Lord Illidan on 2007-01-28
Sabayon is rumoured to be quite unstable. Try Zenwalk Linux.

---

### Post by Rodneyck on 2007-01-28
Another thing you might want to check out is the video card driver which can cause lockups. Not quite sure which one it is installing for your system or what you are using.

---

### Post by Nda on 2007-01-28
I've just been off having a look at the forums for Vector, Dream, Debian, Sabayon and Zenwalk and searching for 'freeze' in each of them (except Dream as I don't speak Portugese!)

They all have entries for 'freeze', and at first glance Debian seems to have fewer recent ones.  I'll have to do this more scientifically though - perhaps a ratio of forum freeze posts to monthly download figures from Distrowatch or something. :)

Nda

---

### Post by Rab22 on 2007-01-28
I would say, that if you haven't had problems with Breezy, to stick with that for now.

---

### Post by Nda on 2007-01-28
> **Rab22 said:**
> I would say, that if you haven't had problems with Breezy, to stick with that for now.

Can't argue with the logic there, Rab.  I still have the installation disk too, so I might do that.

Sniffing around these other distro's is whetting my appetite though...

Nda

---

### Post by igknighted on 2007-01-28
> **Nda said:**
> I've just been off having a look at the forums for Vector, Dream, Debian, Sabayon and Zenwalk and searching for 'freeze' in each of them (except Dream as I don't speak Portugese!)

They all have entries for 'freeze', and at first glance Debian seems to have fewer recent ones.  I'll have to do this more scientifically though - perhaps a ratio of forum freeze posts to monthly download figures from Distrowatch or something. :)

Nda

Any linux distro can be pefectly stable or bery unstable, it depends on what programs you try to install.  If you start to break dependancies you will get lockups.  Also, you said you havent installed any fancy graphics drivers... that might be the problem.  Sometimes the generic ones just don't do the job.  Finally, if you want a linux distro that is rock solid then look at Slackware.  The packages are old, but the stability is unmatched.

---

### Post by tito2502 on 2007-01-28
I've had an Ubuntu mahine running for 8 months without a single restart.

PEBKAC I say

---

### Post by Nda on 2007-01-28
> **igknighted said:**
> .  Also, you said you havent installed any fancy graphics drivers... that might be the problem. 

The graphics chip is a Radeon (7500, I think.  I checked it once but can't remember the command now.), so I'll see what drivers I can find for that.

I'm off for a look at Slackware now.  Thank you all for your comments.

Nda

---

### Post by cowlip on 2007-01-28
> **Nda said:**
> Oh dear, another complete freeze-up in Ubuntu 6.06 this morning.  No mouse, trackpad or keyboard input possible so I had to do a hard reset, then restart.  

Two apps I'd added to Sessions/Startup didn't start, so I deleted them, restarted, added them back in, restarted, but one - DevilsPie - won't start at all, so my nicely centred windows are all opening top left again. :mad:

It's not a hardware problem as it didn't happen when Windows was on this machine (Thinkpad T30, P4 1.8Ghz, 512 MB ram).  I don't have any fancy graphics stuff or video drivers installed.  It's just a standard machine with a standard Dapper setup.  Apart from freezing up randomly, Ubuntu works well, including hibernate and screensaver.

I'm getting a bit weary of this though, and thinking it might be time to move on.  I've done a search and it seems that the problem still happens in Edgy so that's not an option for me.

The question is therfore, is there a more reliable version of Linux that won't keep freezing?  Is there a distro that has a reputation for reliability and stability?  Have any of you had the same problem with Ubuntu but not with a different OS on the same machine?

My needs are straightforward: internet, email, office apps, photo editing.  I don't play games and I'm not interested in flashy 3D graphics effects.  I just want a system that is functional and reliable and doesn't require a high level of command-line knowledge.  Ideally it would have forums as good as these, but I doubt I'll find that!

Any recommendations would be appreciated.

Nda

I have definitely had freezes with Ubuntu, up to Dapper Drake (I didn't use Edgy Eft so can't comment).  Hoary Hedgehog and Warty Warthog were particularly freezy, IIRC, and the only drivers I had were the ones default in the kernel (gfx card was an old ATI "All in wonder" Radeon, 7200 or 7500).  If you want to check, I think Ubuntu in later version has a hardware device list under system...

Windows XP has definitely beat Ubuntu in that regard for me :)  But I can't argue with free.

---

### Post by Grey on 2007-01-28
You might want to take a look at BSD.  It's probably more stable than Linux.  If you want to stick with Linux though, you might want to try Debian stable, or Slackware.  Both run fairly old, but stable and reliable software.

---

### Post by chipmonk010 on 2007-01-28
I have a feeling its graphics card related every computer i have ever installed linux on with an ATI graphics card has been a hassle. The problem would be non-existant if ATI could just support there own hardware but they choose not to, hence I only buy nvidia.ANYWAY i would try installing accelerated graphics drivers for your card and see if that helps.

On a related note theres no reason not to try other distros. Sometimes you can more easily spot the problem in another environment then apply the knowledge to whatever distro you like.

---

### Post by SunnyRabbiera on 2007-01-28
there is no such thing as a non freezing OS, all of them freeze for some reason or another, I have had windows freeze on me, Linux freeze, BSD freeze, OSX....

---

### Post by kerry_s on 2007-01-28
Try some PCLinuxOS, it's dirt simple and pretty at the same time.-> [http://distrowatch.com/index.php?distribution=pclinuxos&month=all&year=all](http://distrowatch.com/index.php?distribution=pclinuxos&month=all&year=all)

---

### Post by RAV TUX on 2007-01-28
> **Nda said:**
> Oh dear, another complete freeze-up in Ubuntu 6.06 this morning.  No mouse, trackpad or keyboard input possible so I had to do a hard reset, then restart.  

Two apps I'd added to Sessions/Startup didn't start, so I deleted them, restarted, added them back in, restarted, but one - DevilsPie - won't start at all, so my nicely centred windows are all opening top left again. :mad:

It's not a hardware problem as it didn't happen when Windows was on this machine (Thinkpad T30, P4 1.8Ghz, 512 MB ram).  I don't have any fancy graphics stuff or video drivers installed.  It's just a standard machine with a standard Dapper setup.  Apart from freezing up randomly, Ubuntu works well, including hibernate and screensaver.

I'm getting a bit weary of this though, and thinking it might be time to move on.  I've done a search and it seems that the problem still happens in Edgy so that's not an option for me.

The question is therfore, is there a more reliable version of Linux that won't keep freezing?  Is there a distro that has a reputation for reliability and stability?  Have any of you had the same problem with Ubuntu but not with a different OS on the same machine?

My needs are straightforward: internet, email, office apps, photo editing.  I don't play games and I'm not interested in flashy 3D graphics effects.  I just want a system that is functional and reliable and doesn't require a high level of command-line knowledge.  Ideally it would have forums as good as these, but I doubt I'll find that!

Any recommendations would be appreciated.

Nda

Nepalinux
rPath
Wolvix
KNOPPIX
Sabayon

start with these,...highly recommend Nepalinux if you want to stay with a Debian enviroment

Stay away from:

PCLinuxOS 
SimplyMepis
SUSE

---

### Post by 3rdalbum on 2007-01-29
I'd say, use Slackware, Debian, or Zenwalk. Don't install proprietry ATI drivers, they cause most of the crashes on my computer (I'm guessing).

---

### Post by Nda on 2007-01-29
Thanks for all the helpful suggestions.

I've been busy nosing around following up the leads and this is the current plan:

First, update the ATI drivers.  I'm not wildly optimistic about the results of doing this as many of the respondents in the thread I linked to earlier had done this without any benefit. This will take some time as there are a LOT of threads about trying to get the best setup with a Radeon 7500, with lots of differing methods cited.  Plenty of learning for me to do there.

Then, once that's been done - and whilst I'm testing it - start having a look at other distro's, probably starting with Debian and Zenwalk before looking at some of the rest.  [RAV TUX - your suggestions were certainly very interesting (NepaLinux!!), but aren't they a little er, young, to be classed as stable.  Please correct me if I'm wrong.]

If all else fails, revert to Breezy, which as I stated earlier didn't lock up like Dapper does.  It would be a shame if I finished up doing this as I really like Dapper, but I don't feel comfortable using - and promoting to others - an OS that freezes solid on me far more frequently than Windows ever did.

There is one last hope: that one of the regular posters from the "Dapper freezes 1-3 times a day" thread will read this and tell me what he or she now uses instead, but I suppose they have might already have moved on from Ubuntu because of that...

Nda

---

### Post by kazuya on 2007-01-30
All OS freezes depending on how you use them. I find Windows does more freezing than any other one, hence the reason to reboot the machine most times. Power users of XP, may know something else we do not about how to prevent this, but that is very hard. Ubuntu would not freeze that much. For me I experienced freezing after my third upgrade from breezy to dapper and dapper to edgy. For the most part this is rare.

A distro as simple as debian, slackware, zenwalk, vector linux, and the BSDs would be very difficult to have any freezing. I can say the same for almost all other distros though. But these and Sabayon definitly gets my vote.


From Ravtux:
Nepalinux
rPath
Wolvix
KNOPPIX
Sabayon

start with these,...highly recommend Nepalinux if you want to stay with a Debian enviroment

Stay away from:

PCLinuxOS 
SimplyMepis
SUSE


Reply: Ravtux, why is PClinuxOS & Simply Mepis here. These are supposed to be some of the better ones as well.

---

### Post by RAV TUX on 2007-01-31
> **kazuya said:**
> 
Stay away from:

PCLinuxOS 
SimplyMepis
SUSE


Reply: Ravtux, why is PClinuxOS & Simply Mepis here. These are supposed to be some of the better ones as well.

perhaps for some but not for me....it is just my opinion but I found a lot about these two distros is simply over hype...I abhor them both and find them both as a pathetic excuse for Linux....but to each his own and again it is just my opinion

If these were the only two Linux options available I would use BSD, OS X, or Windows instead.

---

### Post by Rodneyck on 2007-01-31
> **RAV TUX said:**
> perhaps for some but not for me....it is just my opinion but I found a lot about these two distros is simply over hype...I abhor them both and find them both as a pathetic excuse for Linux....but to each his own and again it is just my opinion

If these were the only two Linux options available I would use BSD, OS X, or Windows instead.

This still did not answer the question RAV. Why did you find them over hyped and what about them did you abhor? I have not tried these two but was looking over them the other day on distrowatch, just want to know myself.

---

### Post by RAV TUX on 2007-02-01
> **Rodneyck said:**
> This still did not answer the question RAV. Why did you find them over hyped and what about them did you abhor? I have not tried these two but was looking over them the other day on distrowatch, just want to know myself.Not sure what kinda of answer you are looking for? if you just want to know for yourself then you can PM me. The only true knowledge can be only obtained through experience...simply try them yourself. 

I will not elaborate much more then that I simply don't like them.

---

### Post by igknighted on 2007-02-02
> **Rodneyck said:**
> This still did not answer the question RAV. Why did you find them over hyped and what about them did you abhor? I have not tried these two but was looking over them the other day on distrowatch, just want to know myself.

I share his sentiments, so I'll respond.  PCLOS .93 felt very cheap.  Apt4RPM is junk, and the distro was never stable no matter what I did.  On top of that, the windows-esque logo made me cringe.  I got regular crashes from hardware that has never been troublesome with any other distro.  The new PCLOS is nothing more than Mandriva (which is an OK distro, I guess) with nice artwork and that about it.  Since I customize the look anyway, I would use Mandriva (ha, or not) before PCLOS to give credit to the original.

Mepis is OK, but its old and has really cheap art.  Visually, it is awful.  Plus, packages are very old.  If I really wanted a debian-based KDE distro I would choose Mepis in a heartbeat over Kubuntu.  Also, there is no reason for Mepis to come via DVD, a single CD would certainly have been sufficiant.

The one I don't understand on his list is Suse.  Technologically this is probably the most advanced distro, it has an active community and an increadible distro.  People say they hate Suse because of the Novell/MS deal... but Suse is free GPL software written by the community... hence, Opensuse.  If you hate novell, don't by SLED, but OpenSuse is a terrific, free, community based distro.

---

### Post by slimdog360 on 2007-02-02
freebsd

---

### Post by mips on 2007-02-02
> **slimdog360 said:**
> freebsd

OpenBSD is more secure/stable BUT not as progressive as FreeBSD which could make a very good desktop.

---

### Post by Adamant1988 on 2007-02-02
> **RAV TUX said:**
> perhaps for some but not for me....it is just my opinion but I found a lot about these two distros is simply over hype...I abhor them both and find them both as a pathetic excuse for Linux....but to each his own and again it is just my opinion

If these were the only two Linux options available I would use BSD, OS X, or Windows instead.

I shy from PClinuxOS because it's not developed by a company, but the distribution, for what I can tell, is truly solid.  I've consistently had better luck with it than I have with Ubuntu, but I feel more secure with Ubuntu's future, so I use that instead.  I'm actually downloading the Sabayon DVD right this second though, want to see if it will work on my lappy.

---

### Post by Lord Illidan on 2007-02-02
> **igknighted said:**
> I share his sentiments, so I'll respond.  PCLOS .93 felt very cheap.  Apt4RPM is junk, and the distro was never stable no matter what I did.  On top of that, the windows-esque logo made me cringe.  I got regular crashes from hardware that has never been troublesome with any other distro.  The new PCLOS is nothing more than Mandriva (which is an OK distro, I guess) with nice artwork and that about it.  Since I customize the look anyway, I would use Mandriva (ha, or not) before PCLOS to give credit to the original.

Mepis is OK, but its old and has really cheap art.  Visually, it is awful.  Plus, packages are very old.  If I really wanted a debian-based KDE distro I would choose Mepis in a heartbeat over Kubuntu.  Also, there is no reason for Mepis to come via DVD, a single CD would certainly have been sufficiant.

The one I don't understand on his list is Suse.  Technologically this is probably the most advanced distro, it has an active community and an increadible distro.  People say they hate Suse because of the Novell/MS deal... but Suse is free GPL software written by the community... hence, Opensuse.  If you hate novell, don't by SLED, but OpenSuse is a terrific, free, community based distro.

Doesn't mepis use the ubuntu repositories?? How can it be more outdated than Kubuntu?

I haven't tried Sabayon, but I am already fed up of the hype. :lolflag: Seriously, I need a good link to a .iso as I can't download torrents at more than 0.5 kilobytes per second here... :(

Suse? I don't like it. Used it a few times and it still has a way to go, especially with yast.

PcLinuxOs and Mandriva - boring...

I think I'll try Slackware.

---

### Post by RAV TUX on 2007-02-02
> **igknighted said:**
> I share his sentiments, so I'll respond.  PCLOS .93 felt very cheap.  Apt4RPM is junk, and the distro was never stable no matter what I did.  On top of that, the windows-esque logo made me cringe.  I got regular crashes from hardware that has never been troublesome with any other distro.  The new PCLOS is nothing more than Mandriva (which is an OK distro, I guess) with nice artwork and that about it.  Since I customize the look anyway, I would use Mandriva (ha, or not) before PCLOS to give credit to the original.

Mepis is OK, but its old and has really cheap art.  Visually, it is awful.  Plus, packages are very old.  If I really wanted a debian-based KDE distro I would choose Mepis in a heartbeat over Kubuntu.  Also, there is no reason for Mepis to come via DVD, a single CD would certainly have been sufficiant.

The one I don't understand on his list is Suse.  Technologically this is probably the most advanced distro, it has an active community and an increadible distro.  People say they hate Suse because of the Novell/MS deal... but Suse is free GPL software written by the community... hence, Opensuse.  If you hate novell, don't by SLED, but OpenSuse is a terrific, free, community based distro.

Agreed with most of your points on PCLinuxOS and Mepis...Thanks for the elaboration....I just find the subject matter of these two distros old and boring and I honestly simply do not to dwell deeply in why I don't like them....

After all it is simply my humble opinion....I expect everybody to make up their own mind through experience....try them you might like them...I didn't, the "why?" is not important to me to dwell on...

As for openSUSE 10.2,....I just bought the Linux Pro Mag...that includes the DVD...perhaps I will try once more...I have always liked their mascot...;)

---

### Post by RAV TUX on 2007-02-02
> **mips said:**
> OpenBSD is more secure/stable BUT not as progressive as FreeBSD which could make a very good desktop.

> **slimdog360 said:**
> freebsd

PC-BSD

---

### Post by slimdog360 on 2007-02-02
> **RAV TUX said:**
> PC-BSD

meh, Ive tried it. I didnt much care for it, even though it was about 1000 times easier then freebsd. (and yeah I know that PCBSD is freebsd in disguise)

---

### Post by manmower on 2007-02-02
What turned me off of PC-BSD was their own software installation system, which in the end doesn't play all that nice with ports when updating, etc. I believe of all BSDs OpenBSD is the one most focused on binary packages (as opposed to compiling from source) but I have yet to try it myself.

---

### Post by igknighted on 2007-02-03
> **Lord Illidan said:**
> Doesn't mepis use the ubuntu repositories?? How can it be more outdated than Kubuntu?

Yeah, they do use the ubuntu repo's, and actually I think Debian repo's as well.  The net of repo's is odd.  I consider them old because I am used to X.org 7.1 and other new programs, and Mepis hasn't released since Dapper (although I think they have a release coming up soon).  I know it's only like 8 months, but it feels *really* old to me.

---

### Post by mips on 2007-02-03
> **slimdog360 said:**
> meh, Ive tried it. I didnt much care for it, even though it was about 1000 times easier then freebsd. (and yeah I know that PCBSD is freebsd in disguise)


What about DesktopBSD then ?

---

### Post by ubu fubar on 2007-02-04
> **Nda said:**
> It's not a hardware problem as it didn't happen when Windows was on this machine (Thinkpad T30, P4 1.8Ghz, 512 MB ram).  I don't have any fancy graphics stuff or video drivers installed.  It's just a standard machine with a standard Dapper setup.  Apart from freezing up randomly, Ubuntu works well, including hibernate and screensaver.

I'm getting a bit weary of this though, and thinking it might be time to move on.  I've done a search and it seems that the problem still happens in Edgy so that's not an option for me.

About a month ago I installed Edgy on the T30 I'm using to type this post - identical specs except I have the 1.6Ghz version - and it's been as stable and reliable as my Mac.

$ uptime
 02:12:10 up 22 days,  4:09,  2 users,  load average: 0.06, 0.09, 0.10

I'm guessing you either have a hardware problem, or a b0rked configuration file somewhere. What's in the logfiles after you reboot?

---

