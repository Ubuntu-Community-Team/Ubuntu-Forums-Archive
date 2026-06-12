---
title: "Whichis more bleeding edge? Gentoo Linux or Arch?"
date: 2009-06-30
forum: Recurring Discussions
---

### Post by the8thstar on 2009-06-30
Hello, I've read that Gentoo Linux is very bleeding edge compared to Ubuntu. I have also heard that Arch is very bleeding edge too because of its rolling updates.

So, which is bleeding edge? Arch? Gentoo? Both? How are they different? Is there one I should consider more than the other? Thanks for your feedback.

---

### Post by schauerlich on 2009-06-30
I don't know how gentoo's system works, but with arch, there is a community maintained repo (AUR, Arch User Repository) which is optional. This repo get packages as soon as someone uploads them. Popular packages are then voted into the official repos. Packages make it into the official repo much quicker in arch than they do on ubuntu.

---

### Post by monsterstack on 2009-06-30
I too would like to know how Gentoo and Arch stack up in terms of shiny newness. And are either of them shinier or newer than Debian Sid with the experimental repositories enabled?

---

### Post by Skripka on 2009-06-30
Do you want to compile everything?

Then you would like Gentoo.

Arch uses pre-compiled binaries. 

FWIW-Arch had KDE4.2 final before it was even announced on KDE's website.

---

### Post by rookcifer on 2009-06-30
Gentoo is not "bleeding edge" in the sense of having the latest packages.  In fact, the stable Gentoo tree usually has older packages (much like Debian).  I believe the stable tree is still using KDE 3.5.9, for instance.  However, you can compile the latest packages by using "overlays" which are basically community run repos.  Gentoo's advantage is the compiling gives you optimization for your hardware and allows you to install only the packages you see fit (no unnecessary dependencies).

Arch is basically a binary version of Gentoo (although Arch also has an alternative package manager that allows you to compile from source).

---

### Post by .Maleficus. on 2009-06-30
Arch and Gentoo are apples and oranges really.  Arch is bleeding edge because as soon as a developer deems a program "stable", it gets pushed to a stable repo and replaces your old version.  Gentoo is bleeding edge in the sense that no system will really be faster than it (assuming you compile your own kernel and don't go the genkernel route).  Everything in Gentoo is compiled, save for a few packages with precompiled binaries that are too large for most users to want to compile.  Because everything is compiled, you need to know your system pretty well, and you need to know how you want to run it (ie, do you want support for Qt apps?  Do you want DVD support?  Do you want GTK 1.x support?  Little things like that).

Arch has ABS (Arch Build System) and the AUR (Arch User Repository).  These two tools essentially allow you to compile any program from source if you want and adds thousands of extra packages.  In this sense, Gentoo and Arch don't differ very much.

If you have a weekend to kill, try out both.  Arch is my current main system but Gentoo had a year or so of complete use and I like both in different ways.  Arch tends to have more broken updates (that have fixes within hours) but Gentoo tends to take longer to get a simple package.  Both will be quicker than Ubuntu for sure and you'll no doubt learn something about A) your system, B) Linux in general or C) both.

---

### Post by dragos240 on 2009-06-30
I would say gentoo...... you do everything from scratch with a guide, and gentoo adapts to your system and "builds INTO your system", according to your hardware, compared to pre-compiled binaries.

---

### Post by juancarlospaco on 2009-06-30
bleeding edge = really Unstable
:)

---

### Post by jeffathehutt on 2009-06-30
If you just want to compare package versions, check out these two lists from distrowatch.com:

[http://distrowatch.com/table.php?distribution=arch](http://distrowatch.com/table.php?distribution=arch)
[http://distrowatch.com/table.php?distribution=gentoo](http://distrowatch.com/table.php?distribution=gentoo)

Black numbers mean the package is an old stable version, green numbers mean the package is the current stable version, red means it is a beta or development version.

Currently there is more green in arch than gentoo, but keep in mind those are not all the packages offered, only the most popular ones, so it is hard to draw a conclusion about the entire distribution.;)

---

### Post by kk0sse54 on 2009-06-30
The stable branch of Arch is more bleeding edge than the stable branch of Gentoo which is imo rock stable. Personally I used the testing branch in Gentoo which is more along the lines of Arch which for me has been perfectly fine.

---

### Post by LowSky on 2009-06-30
Im using Arch right now, and wouldn't touch Gentoo with a 10 meter pole.
Arch is pretty bleeding edge with the AUR w/ youart you get new stuff as soon as anyone uploads the code. Sure it might not alway be stable but if you like learning then its great fun...
Gentoo is too much work compiling by hand is not fun. waint Days and/or hours for something to be up and usable is not for me

---

### Post by PurposeOfReason on 2009-06-30
I use the testing branch of gentoo and it is more stable than the stable branch in arch, at least in my experience.

---

### Post by the8thstar on 2009-07-01
Thank you all for your replies. I will explore the links you posted with interest! It's encouraging to know that I can improve on computer speed and personal knowledge at the same time.

---

### Post by zolookas on 2009-07-01
Arch provides latest software, but keeps updates in testing repo for a while (to test them :)) If you have noticed any outdated package, flag it here: [http://www.archlinux.org/packages/](http://www.archlinux.org/packages/)

Also Arch has a nice build system and community page ([http://aur.archlinux.org/](http://aur.archlinux.org/)) where you will find build files (if there is no binary package provided in repo, you will most likely find it there).

---

### Post by thisllub on 2009-07-02
> **juancarlospaco said:**
> bleeding edge = really Unstable
:)

Not necessarily.
During the development lifecycle bugfixes are released far more frequently than new features. Keeping up to date can sometimes mean a more reliable system.

What would really be strong was a release model and package manager that restricted new features to a major release cycle i.e. 0.1 and bug fixes to a 0.01 release.
The package manager could mask out all updates that introduced new features and only allow updates including bug fixes.

---

### Post by sayems on 2009-07-04
I've been happily using Arch Linux for the last six month and It has become my favorite distro. Click on the link below to read some of the Ubuntu user who's trying to make Ubuntu run like Arch Linux

[http://ubuntuforums.org/showthread.php?t=206022]("http://ubuntuforums.org/showthread.php?t=206022")

---

### Post by doorknob60 on 2009-07-04
Probably Arch. When a new version of a package is released, it gets updated pretty quickly, especially if you use the [testing] repository. And if you don't like a version you can use ABS AUR or yaourt to compile things your way easily. Also pacman is *a lot* faster than apt-get :) I like Debian and Ubuntu, but compared to Arch, no comparison.

---

### Post by handy on 2009-07-04
From what I have read, the speed benefits of compiling everything to suit your hardware, have been eroded as the Linux dev' tools have evolved.

There really is very little to be gained, & an enormous amount of time to be invested by those who go down the compile it all route.

Apparently the kernel is a whole lot smarter than it was a couple of years ago.

This is what I have read, I can't back it up from experience.  

Except to say that I have been using Arch for the last 15 months & it is fast to upgrade, & fast to use & uses by far the simplest architecture that I have seen in any Linux distro', & its package management is absolutely superb.  

The only complaint I have currently is that living somewhere near the cutting edge has been causing me pain due to the crappy work that AMD/ATi have been doing on their GPU drivers.  They take a step forward, then a step back, two steps forward, followed by another step forward, then four back...  It is starting to irritate me.  I'm thinking of going back from kernel 2.6.30-5 to 2.6.29, so I can then downgrade the ATi Catalyst driver to the previous version which worked fine on my machine & then stay there until ATi get there drivers reliable.

---

### Post by hessiess on 2009-07-04
Recently I have played around with Gentoo in a Virtualbox and to be onest i am not that impressed, the install prosess is basically a less automated verson of the arch install, compiling everything takes *ages* and there is no obvious speed improvement. Im sticking with arch for the time being.

---

### Post by handy on 2009-07-04
3 days seems to be the common amount of time required to set up Gentoo.

Following are some very worthwhile installation tips for Gentoo:

[I]
The next time you decide to give gentoo a try, use any live CD/DVD other than the gentoo one... knoppix or systemrescuecd are good choices.

Next, unless you aren't particularly fond of your existing partitions on all of your disks, avoid the automatic installer. In the long run, it is faster to do it manually.

Finally, don't use a stage3 file from one of the official mirrors. They are already out of date and you'll have some very difficult upgrades to deal with if you do. Instead, get your stage3 file from Daniel Robbin's [***_funtoo.org_***]("http://www.funtoo.org/") website. (he was the founder of gentoo) He has an automated system that builds up to date stage3 files every week.[/I]

Courtesy of **yabbadabbadont** from the now closed U.F's. OOST forum.

---

### Post by calrogman on 2009-07-04
I think [this feed]("http://www.archlinux.org/feeds/packages/") (Arch) versus [this feed]("http://packages.gentoo.org/feed/") (Gentoo) will help you decide which is updated faster and which is  more bleeding edge.

---

### Post by PurposeOfReason on 2009-07-04
> **handy said:**
> 3 days seems to be the common amount of time required to set up Gentoo.

Following are some very worthwhile installation tips for Gentoo:

[I]
The next time you decide to give gentoo a try, use any live CD/DVD other than the gentoo one... knoppix or systemrescuecd are good choices.

Next, unless you aren't particularly fond of your existing partitions on all of your disks, avoid the automatic installer. In the long run, it is faster to do it manually.

Finally, don't use a stage3 file from one of the official mirrors. They are already out of date and you'll have some very difficult upgrades to deal with if you do. Instead, get your stage3 file from Daniel Robbin's [***_funtoo.org_***]("http://www.funtoo.org/") website. (he was the founder of gentoo) He has an automated system that builds up to date stage3 files every week.[/I]

Courtesy of **yabbadabbadont** from the now closed U.F's. OOST forum.
Who takes three days?! I'm done in 12 hours max. That is evilwm though and all my configs already done.

---

### Post by handy on 2009-07-05
> **PurposeOfReason said:**
> Who takes three days?! I'm done in 12 hours max. That is evilwm though and all my configs already done.

Good for you.

From personal experience & talking to Gentoo old hands in the past, they also called it 3 days.

Perhaps it depends on different setups?

---

### Post by PurposeOfReason on 2009-07-05
I'd assume so. Gnome and KDE would take quite a bit to compile and if you had a weaker processor even more so. So a 2.4Ghz core 2 duo doing all of KDE I'd hazard at 2 days assuming it compiles through the night.

---

### Post by sertse on 2009-07-05
nvm

---

### Post by kk0sse54 on 2009-07-05
> **handy said:**
> 3 days seems to be the common amount of time required to set up Gentoo.

Like PurposeOfReason said, it depends on your setup and processor but for me depending on what time I start it usually takes a full day to do a complete install and compile KDE4.

> Finally, don't use a stage3 file from one of the official mirrors. They are already out of date and you'll have some very difficult upgrades to deal with if you do. Instead, get your stage3 file from Daniel Robbin's [***_funtoo.org_***]("http://www.funtoo.org/") website. (he was the founder of gentoo) He has an automated system that builds up to date stage3 files every week.[/I]

Courtesy of **yabbadabbadont** from the now closed U.F's. OOST forum.

While this used to be a relevant point, gentoo has been offering weekly built stage3's for a while now to cut down on the amount of time for updates. However funtoo remains an excellent site and some people prefer their stage3's.

---

### Post by the8thstar on 2009-07-05
Well, here is my experience so far...

I downloaded and installed Chakra because I wanted an easy install and setup. I encountered three problems : my synaptics touchpad is recognized in the LiveCD, but not in the actual installation. And my HDA Intel is not recognized, while it works just fine in Ubuntu. And finally, no wireless for my Intel 3945 ABG. I am not used to the KDE interface, so I just ditched Chakra... maybe if they come up with a Gnome version I could reconsider. On the upside, the system was very reactive and fast, which is a huge plus.

Then I downloaded the latest Arch install CD. I have no idea what packages I should install but I'll google around in search for answers. If Arch is beyond my skill I'll try Fedora next.

---

### Post by HappyFeet on 2009-07-05
.

---

### Post by WatchingThePain on 2009-07-05
The trouble with rolling updates is that they can roll over your system (and flatten it).

Rely heavily on backups.

Any Linux distro can be customised.

Bleeding edge means more bugs.

Why do ppl keep saying Gentoo takes 3 days to set up?.
3 days of what?, hard labour?.
I am interested in Gentoo but is it a ballbreaker or something?.

---

### Post by Pogeymanz on 2009-07-05
Gentoo takes a long time because you have to wait for every package to compile. When they say 3 days, 90% of that time can be away from your computer while it compiles.

---

### Post by kk0sse54 on 2009-07-05
> **the8thstar said:**
> Well, here is my experience so far...

I downloaded and installed Chakra because I wanted an easy install and setup. I encountered three problems : my synaptics touchpad is recognized in the LiveCD, but not in the actual installation. And my HDA Intel is not recognized, while it works just fine in Ubuntu. And finally, no wireless for my Intel 3945 ABG. I am not used to the KDE interface, so I just ditched Chakra... maybe if they come up with a Gnome version I could reconsider. On the upside, the system was very reactive and fast, which is a huge plus.

Then I downloaded the latest Arch install CD. I have no idea what packages I should install but I'll google around in search for answers. If Arch is beyond my skill I'll try Fedora next.

For most people if you're going to try and install Arch just go with the normal Arch iso, it's not nearly as difficult as some would say it is as long as you have the ability to read. Chakra imo sort of defeats the purpose of installing Arch and as far as I know is still in alpha. That being said my HDA intel works flawlessly with Arch and was as simple as installing alsa and picking out the right driver. Goodluck with the plain Arch install though, remember the [Beginners Guide]("http://wiki.archlinux.org/index.php/Beginners_Guide") is always your best friend :)

---

### Post by Skripka on 2009-07-05
> **the8thstar said:**
> Well, here is my experience so far...

I downloaded and installed Chakra because I wanted an easy install and setup. I encountered three problems : my synaptics touchpad is recognized in the LiveCD, but not in the actual installation. And my HDA Intel is not recognized, while it works just fine in Ubuntu. And finally, no wireless for my Intel 3945 ABG. I am not used to the KDE interface, so I just ditched Chakra... maybe if they come up with a Gnome version I could reconsider. On the upside, the system was very reactive and fast, which is a huge plus.

Then I downloaded the latest Arch install CD. I have no idea what packages I should install but I'll google around in search for answers. If Arch is beyond my skill I'll try Fedora next.

Chakra is just Arch with a modular KDE.  That is it.  You can use any old window manager/DE you want with Arch-including Gnome it is ALL there in the Wiki 99% of the time.

---

### Post by WatchingThePain on 2009-07-05
Sorry can I just ask where Chakra can be obtained?. Anyone know the homepage.

edit:got it.
[http://chakra-project.org/about-faq.html](http://chakra-project.org/about-faq.html)

---

### Post by handy on 2009-07-05
I also agree that the best way to use Arch, is to go with the standard Arch install following the Beginners Guide to the letter.  Only a few unlucky people get stopped by wireless hardware problems going this route.

The huge benefits of installing Arch in the standard fashion, is that you get introduced to the way Arch works, which is really much simpler than any other distro I have seen.  So much happens in just one file called /etc/rc.conf which is really quite easy to edit & use.  

There is fantastic information available on the Arch wiki, which is the best I have seen for any distro', though the Gentoo wiki is also excellent.

I've been using Arch for 15 months or so on one machine & a bit less on another, & have struck 5 problems that came through upgrades.  

What is worth noting for those unfamiliar with Arch & the rolling release system, is that because it is so simple & quick to do a total system upgrade, (especially if you do them everyday) I have done at least 400 total system upgrades on just one of my machines in that 15 months or so, with (as previously stated) only 5 system upgrades that caused me any problem, I really don't think that the rolling release system is something to shy away from I consider it to be one of the variety of Arch's strong points, without a doubt.

I think that the Arch package management system is the best I have ever encountered in near 24 years of computing & the rolling release system has allowed me to have a daily up to date system for around 15 months without having to go through the drama of a re-installation type of upgrade.

My main gripe currently is with the poor AMD/ATi closed source drivers that lately have been giving my ATi card a rough ride.  This is not Arch's fault, but for me it has really been the only problem that wasn't easy to fix that has come along due to Arch living somewhere near the cutting edge.  My no.2. machine uses an nVidia GPU & has had no problems due to nVidia closed source driver upgrades.

For a growing list of How-To's which currently include; downgrading Arch packages, accessing & installing previous versions of the Arch kernel, safe removal of orphan Arch packages, the installation of Arch on an iMac & more, have a look at the [***_OSTalk.org_***]("http://ostalk.org/") forum in the [***_Howto's & Guides_***]("http://www.noost.org/forumdisplay.php?fid=18") section?

---

### Post by the8thstar on 2009-07-07
I am giving the whole Gentoo/Arch experiment a rest for now. It is too frustrating for me to go through wikis and manuals just to get a system to run. Eventually, I would recreate the Gnome environment I *ALREADY* have with Ubuntu anyway, with similar applications. The hypothetical speed gain between Arch and Ubuntu is not worth the considerable and tangible waste of time I have ahead of me with this endeavor. 

Right now Ubuntu works and it delivers what I need.

PS : I wiped out both my Windows 7 RC1 and my OSX86 partitions. In all honesty, Ubuntu is ALL I need right now.

---

### Post by sertse on 2009-07-07
That's because you asked for a gentoo vs arch comparsion...

Personally I'll suggest sidux. It uses debian sid, (the area new new/updated apps first arrive in debian) which is pretty updated, and is a rolling release. 

It's main advantage is that, like Ubuntu and other general purpose distros, it's a Live CD ready to installed with a working desktop right away. The main difference sidux and debian sid (and for that matter Karmic, Fedora Rawhide, Mandriva Cooker etc etc), is that sidux has a dedicated team focusing on running sid on a daily basis, so you'll be well informed on the changes, advice/workarounds and fixes if some bleeding edge app has major issues, and know where to go for support. 

For full disclosure, sidux doesn't have the level of customisability or optimisation as gentoo or arch, (gentoo optimises to your computer by compiling from source, arch has a more minimalist basic design than debian) but you're just looking for a distro that has the latest apps, consider sidux.

---

### Post by handy on 2009-07-07
I say use whatever does it for you.

It's great to have so many choices. :)

---

### Post by CJ Master on 2009-07-07
> **the8thstar said:**
> I am giving the whole Gentoo/Arch experiment a rest for now. It is too frustrating for me to go through wikis and manuals just to get a system to run. Eventually, I would recreate the Gnome environment I *ALREADY* have with Ubuntu anyway, with similar applications. The hypothetical speed gain between Arch and Ubuntu is not worth the considerable and tangible waste of time I have ahead of me with this endeavor. 

Right now Ubuntu works and it delivers what I need.

PS : I wiped out both my Windows 7 RC1 and my OSX86 partitions. In all honesty, Ubuntu is ALL I need right now.

Well that's fine, obviously neither are for you then. Use whatever works for you the best. :)

(oh, and as a side note, you would have many more advantages besides speed, but that doesn't really matter if your happy with Ubuntu.)

---

### Post by Pogeymanz on 2009-07-08
If you want something like Ubuntu, but more up-to-date, you should try Sidux as mentioned above.

It installs just as quickly as Ubuntu or any other "easy" distro and it is rolling release style. I used it for a short time and really prefered it to Ubuntu.

---

### Post by handy on 2009-07-17
I just found the most amazing new distro' buried in the lists of distrowatch.  It's called StArch.

It uses the pacman & AUR package management system, BUT, it also needs people using it, to believe that the aforementioned systems are absolutely the best systems of their type, that are available to humanity.

---

### Post by HeadHunter00 on 2010-01-23
Gentoo is actually more bleeding edge than arch, its just that the compilation process makes the softwares more stable. Basically,  it looks up all the software and hardware you have, and builds the program according to that. But, it's real slow.

---

### Post by ~sHyLoCk~ on 2010-01-23
Arch is the best. ;-)

---

### Post by dragos240 on 2010-01-23
Gentoo rocks.

---

### Post by PurposeOfReason on 2010-01-24
> **HeadHunter00 said:**
> Gentoo is actually more bleeding edge than arch, its just that the compilation process makes the softwares more stable. Basically,  it looks up all the software and hardware you have, and builds the program according to that. But, it's real slow.
Do you just type without thinking? Gentoo does not look up anything for you. Compiling does not make anything more stable. Read a book.

---

### Post by falconindy on 2010-01-24
Here OP, this is [just for you](http://funroll-loops.info/).

---

### Post by MisfitI38 on 2010-01-24
> **HeadHunter00 said:**
> Gentoo is actually more bleeding edge than arch, its just that the compilation process makes the softwares more stable. Basically,  it looks up all the software and hardware you have, and builds the program according to that. But, it's real slow.

Heh, I lol'd.

[Arch has always been at the top]("http://oswatershed.org/") of the watershed.

---

### Post by chucky chuckaluck on 2010-01-24
> **HeadHunter00 said:**
> Gentoo is actually more bleeding edge than arch, its just that the compilation process makes the softwares more stable. Basically,  it looks up all the software and hardware you have, and builds the program according to that. But, it's real slow.

gentoo is bleeding edge when you start and older than debian when you finish.

---

### Post by ~sHyLoCk~ on 2010-01-24
> **chucky chuckaluck said:**
> gentoo is bleeding edge when you start and older than debian when you finish.

ROFL! 

> **HeadHunter00 said:**
>  Basically,  it looks up all the software and hardware you have, and builds the program according to that. But, it's real slow.

Never tried gentoo have you? :P

---

