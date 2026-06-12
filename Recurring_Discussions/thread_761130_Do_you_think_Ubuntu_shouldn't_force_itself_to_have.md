---
title: "Do you think Ubuntu shouldn't force itself to have release every six month?"
date: 2008-04-20
forum: Recurring Discussions
---

### Post by Ioky on 2008-04-20
Yeah, as the title say, what do you think? 

I mean as such great OS, don't you think it would be much better to have a solid release each time? And Include the most solid software at the time instead include some bate version as default? 

especially for LTS version, people will expect to use it for a few years, you know for developer or business people who don't want to keep upgrading/reinstall the computer and get it a risk. 

I mean when it can't make it, give a it a week or maybe even a month, if needed. It is good to have solid system for 5 months, then have a not as solid system for six months, don't you think?

---

### Post by Saya on 2008-04-20
If I may refer you to [http://ubuntuforums.org/showpost.php?p=4750607&postcount=139](http://ubuntuforums.org/showpost.php?p=4750607&postcount=139)

---

### Post by LaRoza on 2008-04-20
It may slow down in the future, but I think once things are "up", the changes will be less obvious. 

The difference between Dapper and Hardy is great, but I doubt that is going to be a trend among future versions.

Perhaps a "update release", instead of revolutionary will be happening.

---

### Post by swoll1980 on 2008-04-20
I don't think there forced into anything, and the user doesn't have to upgrade with every release It's a matter of choice for them (Ubuntu) and us (the user)

---

### Post by SunnyRabbiera on 2008-04-20
well I think backporting should be a bit better yes as I want the applications to remain updated no matter what instead of being forced to the next release.

---

### Post by mrsteveman1 on 2008-04-21
I think Ubuntu releases should be somewhere in between Arch and Suse in how they work. EG somewhere between a year long release, where stuff is updated significantly in the mean time but users have to wait, and arch, where updates are pushed out immediately, even new kernels.

I think Ubuntu should sync to the releases of the major components, for instance the 2.6.25 kernel just came out, i would be fine with ubuntu delaying by a few weeks to include it, because right now kernel updates are a huge deal because of the pace of development, and because some things are broken when used with older kernels, certain drivers don't work and can't be upgraded without ripping out the entire kernel for a new one.

But that brings the discussion to a more significant problem, once a release is made, the kernel is stuck at the version used at the time. This should not be necessary and causes significant driver problems due to the way the linux driver architecture works. Upgrading the kernel should be possible on existing systems, as should updating drivers which come with the kernel. If updating the kernel like that isn't possible, then the kernel architecture needs to change. I realize the Ubuntu developers can backport drivers, but they don't always do that and it shouldn't be necessary.

---

### Post by Whiffle on 2008-04-21
I think its pretty much fine as is.  I think the ubuntu bugfix policy needs attention, but the 6 month cycle ain't bad.   In contrast with other distros, it seems to have a nice middle ground between bleeding edge new (gentoo/arch), and almost *old* (slackware, debian stable).  The 6 month cycle is a nice solid number too, too much flexibility and you may end up with something like Slackwares release schedule, ie, whenever Pat feels its ready.  

Maybe its just the "i've been using linux too long" in me, but to me it really isn't that big a deal that new software isn't backported immediately.  If the old software is doing its job (and not flat out broken like the aumix bug), then theres no real reason to update it, especially since doing so consumes resources that are needed for building the next version.  Besides, its not that hard to get updated packages from other sources or build them yourself.  Same goes for the kernel as well... up until recently I had feisty running with a kernel newer than gutsy has, maybe even hardy.  If new software is really that important to you, its really worth it to learn to compile it.

---

### Post by saulgoode on 2008-04-21
> **Whiffle said:**
> I think its pretty much fine as is.  I think the ubuntu bugfix policy needs attention, but the 6 month cycle ain't bad.   In contrast with other distros, it seems to have a nice middle ground between bleeding edge new (gentoo/arch), and almost *old* (slackware, debian stable).  The 6 month cycle is a nice solid number too, too much flexibility and you may end up with something like Slackwares release schedule, ie, whenever Pat feels its ready.

"almost *old*"? :confused:

Slackware's packages are just as up-to-date as Ubuntu's -- sometimes newer, sometimes older; rarely differing by much. Slackware typically has more recent versions of core libraries and utilities, while Ubuntu might include the occasional beta version of a package (Firefox3 beta as an example). But overall, packages from the two distros are pretty well in sync "age-wise".

And just for the record, Slackware's releases have averaged out to one every 9 months over the period of Ubuntu's existence with actual intervals of 8, 7, 12, 9, and 10 months.

---

### Post by Whiffle on 2008-04-21
> **saulgoode said:**
> "almost *old*"? :confused:

Slackware's packages are just as up-to-date as Ubuntu's -- sometimes newer, sometimes older; rarely differing by much. Slackware typically has more recent versions of core libraries and utilities, while Ubuntu might include the occasional beta version of a package (Firefox3 beta as an example). But overall, packages from the two distros are pretty well in sync "age-wise".

And just for the record, Slackware's releases have averaged out to one every 9 months over the period of Ubuntu's existence with actual intervals of 8, 7, 12, 9, and 10 months.

Yeah I suppose slackware packages are a little more recent than debian stable.  But relative to something like arch, they're old.  

Yeah slackware has a nice release schedule :)  If it had a package manager for lazy people like me, I'd still use it.

---

### Post by FredB on 2008-04-21
Ah, beta software. I think you're talking about Firefox 3 beta... Please try to remember than Firefox 3.0 is due to be released in june, and so, Firefox 2.0.0.x will see its end of life in december 2008.

Is it good to provide a software which will not be security updated for at least 2/3 of the LTS lifetime ?

---

### Post by mrsteveman1 on 2008-04-21
Yes you CAN upgrade the kernel if you want, but ubuntu is supposed to be the easy one for most people. The minute you start talking about compiling stuff to overcome some problem, you limit the usefulness of the solution to that problem.

Drivers are the real issue, you shouldn't have to compile a new kernel or install a release candidate kernel from the next release just to get new drivers. It should be possible to update the kernel when a new one is released on kernel.org, without significantly changing the system or requiring the user to compile stuff.

Maybe the ubuntu devs need to put out packages for the newest kernel, that way if necessary you can tell a user to install a specific package. By package i mean one compiled specifically for the current release, not using a kernel meant for hardy on gutsy, because there can be problems there.

---

### Post by saulgoode on 2008-04-28
> **Whiffle said:**
> Yeah I suppose slackware packages are a little more recent than debian stable.  But relative to something like arch, they're old. 

Actually, if you compare the versions of [Slackware packages](http://distrowatch.com/table.php?distribution=slackware) to [Arch packages](http://distrowatch.com/table.php?distribution=arch), Arch seems to consistently trail SW by a just bit. (EDIT: looking at some more packages, I realize that this assessment is not quite accurate; but again SW & Arch seem to both be quite up-to-date.)

Not that I place much stock in the difference of a release cycle or two (or even a minor version, for that matter); but it is a mistake to characterize Slackware as anything but one of the most consistently up-to-date distributions. Just because Pat Volkerding still provides support for all versions of Slackware dating back to 2001 does not mean the current versions are out-of-date.

---

### Post by cardinals_fan on 2008-04-29
> **saulgoode said:**
> Just because Pat Volkerding still provides support for all versions of Slackware dating back to 2001 does not mean the current versions are out-of-date.
It just means that he is a living god ;)

---

### Post by SomeGuyDude on 2008-04-29
I've said there should be a compromise. One release should be kind of a "beta" type thing that's all bleeding edge, and one should be the stable version of everything that was tested out on the one before it. Still every six months, but the "releases" come out once a year.

That way the "new new new!" people always have something, but the people who tend to bitch about a new release that doesn't work very well know to stay away half the time. I realize there are LTS's now and all, but given that there does seem to be a lot of new stuff with Hardy, I don't think so.

For example: Hardy would be the "half-way release" because it has a Firefox beta, it's trying out all these new features in Nautilus, it's got Pulse instead of ALSA for the first time, etc. Then Intrepid would be the "stabilized" version that basically takes everything we tried out in Hardy and makes sure it works seamlessly.

Yay? Nay?

---

### Post by mrsteveman1 on 2008-04-29
I don't think you even need to use the releases of the distro itself to test things though.

We already HAVE beta periods and alpha test releases for each one that massive numbers of people try out and report bugs with, by the time hardy came out with its new sound server, new VFS layer, etc, there shouldn't be a need for any such long term beta period.

If there aren't enough developers to fix things in time then thats another problem entirely.

---

### Post by Ioky on 2008-05-02
Feels like, Linux is always in it's way to get better, I love this fact so much. but which also make me feels like it is never there. haha, it is like once for a while, I get a super strong stable release, for it 7.04 is one of those release, and when I get into 7.10 a lot problems occur, then when 8.04 come out, it is getting better. Maybe Ubuntu II (not 2) seem like will be one of those super release again to me. It also come with a lot super powerful cut edge software come along with it such as, firefox 3, openoffice.org 3, wine 1.0, Gnome 2.4, KDE 4.1, and many others, which every one looking forward to, and we will get it all at once, at Ubuntu II

---

### Post by Foster Grant on 2008-05-02
> **Ioky said:**
> Yeah, as the title say, what do you think? 

I mean as such great OS, don't you think it would be much better to have a solid release each time? And Include the most solid software at the time instead include some bate version as default? 

especially for LTS version, people will expect to use it for a few years, you know for developer or business people who don't want to keep upgrading/reinstall the computer and get it a risk. 

I mean when it can't make it, give a it a week or maybe even a month, if needed. It is good to have solid system for 5 months, then have a not as solid system for six months, don't you think?

Why have "releases" at all? Why not follow the Gentoo/Arch plan of rolling releases, continually updating the repositories and continuous evolution?

---

### Post by 23meg on 2008-05-02
[QUOTE=Foster Grant]Why have "releases" at all? Why not follow the Gentoo/Arch plan of rolling releases, continually updating the repositories and continuous evolution?[/QUOTE]

In rolling release distributions, things tend to break to an extent and in ways that's not going to be fixable by Ubuntu's target audience. 

[QUOTE=mrsteveman1]If there aren't enough developers to fix things in time then thats another problem entirely.[/QUOTE]

For now, I would go so far as to say that's almost *the entire problem*.

---

### Post by tw3k on 2008-05-02
[FU]("http://en.wikipedia.org/wiki/Friedman_(unit)")!

---

### Post by cardinals_fan on 2008-05-03
> **23meg said:**
> In rolling release distributions, things tend to break to an extent and in ways that's not going to be fixable by Ubuntu's target audience. 

Rolling release is as stable as you choose to make it - simply don't add packages to the stable repos until they have been thoroughly tested in a number of scenarios.

---

### Post by madjr on 2008-05-03
> **cardinals_fan said:**
> Rolling release is as stable as you choose to make it - simply don't add packages to the stable repos until they have been thoroughly tested in a number of scenarios.

exactly rolling releases are stable.

usually the packages that would break parts of the system would be:

new kernel.
new desktop manager version (gnome, kde, etc.).

just **hiding these packages to a new user** in a rolling release would do the trick.

also a rolling release could be possible

---

### Post by AndyCooll on 2008-05-03
> **SomeGuyDude said:**
> I've said there should be a compromise. One release should be kind of a "beta" type thing that's all bleeding edge, and one should be the stable version of everything that was tested out on the one before it. Still every six months, but the "releases" come out once a year.
The Ubuntu releases already follow that type of pattern, hence their names It may not be immediately obvious however there is some logic to the names given. Following Dapper there has been Edgy, Feisty, Gutsy and Hardy. Although they're not static, the aim has been to make each release more stable than the previous one with the view that LTS releases should be the most solid and stable versions.

:cool:

---

### Post by articpenguin on 2008-05-03
pclinuxos i a rolling distro.

---

### Post by qazwsx on 2008-05-04
rolling release != bleeding edge

It can be it as well though. I love sidux but it is not suitable for big masses. PCLOS is rolling release and it is suitable for wide user base.

Problem in rolling release is backward compatibility. It breaks if you are not updating it for long time depending on update frequency

---

### Post by mrsteveman1 on 2008-05-05
Heres the problem though, the Ubuntu devs have the source for EVERYTHING in those repos, if something breaks they can fix it before it is even released to the public.

Even the kernel, you can set dependencies for things that rely on newer kernel functionality. Say you update the kernel to 2.6.25 and some interface somewhere no longer works, you make updating that other software a condition of updating to the kernel.

These are problems the repo model solved a long time ago.

The advantages of being able to utilize the newest kernel when it comes out outweigh the possible breakage, which can be fixed by the devs.

---

### Post by phr0ze on 2008-05-05
You still need to improve the CD. And rolling releases just aren't ideal in the corporate world. For home users they are great.

---

### Post by days_of_ruin on 2008-05-05
I think they should keep doing what they are doing only LTS's should
always get an extra two months.

---

### Post by mrsteveman1 on 2008-05-06
Heres the thing though, other operating systems already do rolling releases to some extent. Most software in OS X or Windows doesn't require a recompile by the developer every 6 months, doesn't require drivers to be recompiled for every single kernel update etc.

XP has been the same "release" operating system for years now, there aren't any real "releases" that break stuff the way kernel updates in Linux do. With some exceptions i have seen drivers released as binaries from 2002 work on XP SP3 systems in 2008. This is literally impossible in Linux and you would be lucky to even get a source recompile to work without seriously working on the code to match the kernel you are using.

The same is true of OS X, Apple updates all kinds of stuff continuously, including the kernel, but the system itself has stable ABIs for everything. Linux doesn't in a lot of cases. The driver ABI is anything BUT stable.

---

### Post by gameryoshi600 on 2008-05-06
Yes and no. Yes because I do not like upgrading every 6 months, and No because its beating mac and windows in releases.

---

### Post by Desterie on 2008-05-09
Lets look at one of the few things MS did right.  It came out with Windows ME.  A seemingly nice OS that crashed alot.  They scrapped it and went with Windows 2000.  That lasted a couple of years.  Then they came out with XP in 2002.  It was little glitchy at first, but when you were online you would see a little bubble appear telling you it was downloading updates.  With each update, the programed smoothed out a little more.  It became the dominant OS for the last [B]6 years[B] Even now with Vista, people are still clinging to XP.

Now I only had Gutsy for about 2 weeks before I got Hardy.  The only real difference I see in it so far is that the sound works on my Dell 1521 now with Hardy.  Could that not have been done just as easily in an "update?"  Why produce another new distro to get the latest when you could just simply update the current version to do the same thing??:-|

---

### Post by greghill on 2008-05-09
Sorry to say it, but I really think that at this point in Ubuntu's progression, it may be time to consider reducing the release cycle to maybe once a year instead of every six months. Like a lot of others, I too downloaded Hardy, having gone through the cycle of just getting Gutsy to the point where I thought it was the best release ever. My mistake. For the first time ever (I've used Ubuntu since Warty) I regretted the decision, and have spent the last two days doing away with Hardy and re-installing Gutsy. 
To me at least, Hardy was not quite ready for release. Things just didn't "feel right". Several hangs and freezes at random, and the inclusion of the Beta version of Firefox was nothing less than a total disaster. It might have been better for Canonical to hold off for another few months to get things right before releasing the travesty called Hardy. Don't get me wrong.... I don't mind fiddling and tweaking with Ubuntu, because in the past I have always ended up with a solid working system I could be proud of. Like I said, I've worked exclusively (well, almost) with Ubuntu since the beginning, but Hardy almost sent me searching for another distro. 
I have tried other distros, but I keep coming back to Ubuntu. It has matured so much that it may be time to slow down just a bit and concentrate on improving stability rather than be in a rush because "we have a deadline to meet in October". Personally I rely on Ubuntu so much in my work at the newspaper and in my personal life, that a short delay wouldn't be the end of the world. After all, small updates can be done in increments anyway, right? A major release once a year would be fine with me I guess. But that's just my 2 cents. 
By the way, this was the 64-bit version with Gnome. Some programs just won't work with 64 bit unless you install the 32-bit libraries, as I'm finding out. If you want Adobe Reader (which I still need, by the way) with  Hardy, be prepared for some extra work. I expect this will continue for some time with other applications as well 'til eventually they all run on 64-bit systems. I think I'll stick it out to the end with Gutsy and see what happens with the next offering. It's got be better than Hardy!

---

### Post by buntunub on 2008-05-09
> Sorry to say it, but I really think that at this point in Ubuntu's progression, it may be time to consider reducing the release cycle to maybe once a year instead of every six months

Yes, that statement is indeed, sorry.

> Like a lot of others

That proves it.

Ubuntu is what it is. Its release cycle road map is no big secret and has been in place since the early days. LTS releases supported for 3/5 years -- what is wrong with that?

---

### Post by cb951303 on 2008-05-09
I'm not concerned about stability of a 6 month cycle release however I don't like upgrading my os every 6 months. You may say "then don't upgrade" but knowing something newer is out there I always find a way to convince my self to try the new release :lolflag: What can be done is to keep the base system for a year and upgrade end-user packages every six month--not a new release but package upgrade... It's just an idea though...

---

### Post by aysiu on 2008-05-09
How about moving the every six months to a different every six months?

Right now, Ubuntu's release cycle is synched to Gnome's release cycle. So after Gnome has been released, Ubuntu's also released.

It'd make much more sense to have Ubuntu's release be a month after Gnome's release, so that Ubuntu developers have time to work out all the kinks in the new Gnome.

So it'd be Ubuntu 8.11, 9.05, 9.11, 10.05, 10.11 instead of Ubuntu 8.11, 9.04, 9.10, 10.04, 10.10.

---

### Post by Sef on 2008-05-09
> To me at least, Hardy was not quite ready for release. Things just didn't "feel right". Several hangs and freezes at random, and the inclusion of the Beta version of Firefox was nothing less than a total disaster.

It depends on your hardware.  For me, the 64-bit version runs great. It has worked well since the install.

---

### Post by greghill on 2008-05-09
Yes, I suppose you're probably right. The hardware could be an issue, although the motherboard and processor are new (2 months ago). My point being that everything was working so well that I was just looking forward to having maybe a couple of made-in-heaven improvements and was sorely disappointed to find that my system no longer performed the way it used to. Like others have said, then why did I upgrade? Just the urge to have something newer and better, I guess. Fact remains though, Hardy just doesn't impress me as a distro that I want to use, so I choose not to upgrade for now. Like I said, I need a solid reliable distro that works on MY box, complete with nvidia, a customizable browser (the Firefox browser beta isn't, yet, with no themes available) acrobat reader, and so on. I realize that there are many others on whose machines Hardy may work to their liking and may certainly be fine. My box happens to be not one of them. I couldn't help but think that maybe Hardy just was rushed to market because of the 6-month deadline thing, and perhaps it could have used a couple of months more testing before the release. Ubuntu is a great distro with an even greater reputation, If it were me (and it isn't!:(), I would not have but "beta" anything into a top notch product as an LTS release.

---

### Post by 23meg on 2008-05-10
> **aysiu said:**
> 
It'd make much more sense to have Ubuntu's release be a month after Gnome's release, so that Ubuntu developers have time to work out all the kinks in the new Gnome.

Your suggestion describes the actual situation: Ubuntu releases are scheduled to happen a about a month after GNOME releases. GNOME 2.22 was released on March 12th, and Ubuntu 8.04 was released on April 24th.

Besides, new GNOME components are constantly uploaded to the development version in Ubuntu as they are developed during each development cycle, so they get testing all along the way. The whole new GNOME doesn't drop as one piece from the sky towards the end of the cycle.

---

### Post by karellen on 2008-05-10
I think that the problems raised by the OP is somehow redundant. I mean, there are distros for everyone's tastes. distros that are bleeding edge (Fedora), distros that went through much testing and are very stable (Debian stable branch), distros that are rock solid ,suitable for servers (CentOS) and so on. you see, plenty of choices. why should Ubuntu switch to other development model?...
the Linux world is a very heterogeneous one, not a monolith

---

### Post by mrsteveman1 on 2008-05-12
> You may say "then don't upgrade" but knowing something newer is out there I always find a way to convince my self to try the new release

The real problem is that these upgrades are really more of a replacement and not incremental upgrades. They create walled gardens where things substantially change to the point that a lot of the system must be entirely upgraded to remain functional.

For instance, the ABI breaks for a lot of libraries requiring a recompile of certain software, kernel drivers almost always break, which is only offset by the fact that most of them come with the kernel, but its still a broken interface. 

> I think that the problems raised by the OP is somehow redundant. I mean, there are distros for everyone's tastes. distros that are bleeding edge (Fedora), distros that went through much testing and are very stable (Debian stable branch), distros that are rock solid ,suitable for servers (CentOS) and so on.

Fedora shouldn't be considered bleeding edge, they use release software from the various upstream providers like the kernel. If those are unstable they were never really releases anyway. 

There is too much separation and distinction here for sure, you can be stable and up to date at the same time, it doesn't require a year of testing to push new packages out unless you have virtually no developers working on things, which is also a broken situation.

---

