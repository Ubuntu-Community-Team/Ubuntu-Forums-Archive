---
title: "Ubuntu vs PCLOS"
date: 2007-08-12
forum: Other OS Talk
---

### Post by OrcusFelinus on 2007-08-12
If Ubuntu ever manages to make wireless installation and configuration as simple as PCLOS did, i'd switch in a heartbeat. 

On initial installation PCLOS detected my Dell draft-n card, offered an ndiswrapper solution,  prompted me to supply the (windows driver) .inf file and my WPA key, then it just plain WORKED. 

How come Ubuntu, as popular as it is, can't do this?

Several hours of forum reading, and a couple more tinkering at the command line and i'm no further ahead... My Inspiron 6400 just sits here sans internet connection. Everything else works just fine... but i'm beginning to realize why the average user will never accept Linux as a mainstream alternative to Windows.

---

### Post by por100pre1 on 2007-08-12
You get no argument from me. You're not the only person saying that PCLOS beats Ubuntu!

---

### Post by ron999 on 2007-08-12
Hi
I've used PCLinuxOS too.
I found that the installation went more smoothly than Ubuntu. Also the LiveCD has a toram opton.
But I've come back to Ubuntu. I prefer Gnome to KDE. And Ubuntu works well. 
:cool:

---

### Post by laidback on 2007-08-12
Agree with sentiment, I often wish (and wonder why don't) all the Linux OS teams work on one super OS that really does cut it. Choice is often the answer; not much good if it doesn't work and turns people away.

Look here for hardware info on wifi:-
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

Stick with it, it really is worth the effort.

---

### Post by aysiu on 2007-08-12
Since this isn't really a support request, I'm moving it to a discussion part of the forums.

---

### Post by viking777 on 2007-08-12
> **ron999 said:**
> Hi
I prefer Gnome to KDE.
:cool:

Never mind I am sure you can get treatment for that.:):)

---

### Post by viking777 on 2007-08-12
> **OrcusFelinus said:**
> If Ubuntu ever manages to make wireless installation and configuration as simple as PCLOS did, i'd switch in a heartbeat. 

On initial installation PCLOS detected my Dell draft-n card, offered an ndiswrapper solution,  prompted me to supply the (windows driver) .inf file and my WPA key, then it just plain WORKED. 

How come Ubuntu, as popular as it is, can't do this?

Several hours of forum reading, and a couple more tinkering at the command line and i'm no further ahead... My Inspiron 6400 just sits here sans internet connection. Everything else works just fine... but i'm beginning to realize why the average user will never accept Linux as a mainstream alternative to Windows.

I use both, but at the moment at least I prefer Ubuntu. Well that is not strictly true, I prefer Kubuntu as KDE is the only sensible window manager there is (look out incoming fire!!). The pace of development in Kubuntu is faster than PClos, for instance I am using Gutsy as it has the latest kernel and in some ways works much better with my new laptop than PCLos, though it still is far from perfect, for instance, with PCLOS I have no sound, with Kubuntu I do, on the other hand with PClOS I have desktop graphic effects (because it uses the old beryl) with Kubuntu I have none (because it uses compiz which at the moment is useless). This doesn't bother me because eye candy is not my thing, but overall I think that Kubuntu will catch up with the technology on my laptop before PCLOS will.
However I will still continue to run both.

---

### Post by SunnyRabbiera on 2007-08-12
> **OrcusFelinus said:**
> If Ubuntu ever manages to make wireless installation and configuration as simple as PCLOS did, i'd switch in a heartbeat. 

On initial installation PCLOS detected my Dell draft-n card, offered an ndiswrapper solution,  prompted me to supply the (windows driver) .inf file and my WPA key, then it just plain WORKED. 

How come Ubuntu, as popular as it is, can't do this?

Several hours of forum reading, and a couple more tinkering at the command line and i'm no further ahead... My Inspiron 6400 just sits here sans internet connection. Everything else works just fine... but i'm beginning to realize why the average user will never accept Linux as a mainstream alternative to Windows.


wireless has always been an issue with linux, PCLOS's advantage over ubuntu in this field as its based on Mandrake/ Mandriva, a distro that has a LOT of good hardware support under its hood even moreso then Ubuntu.
Ubuntu got ahead of Mandriva on websites like distrowatch for many reasons:
1: the shipit free CD's, by offering free live CD's it gained vast interest
during its time.
2: Mandriva's cost, plus mandriva club memberships have been a burden on it. getting proprietary stuff is much easier on ubuntu.
3: installation of packages are a pain on Mandriva, apt and synaptic are infinately better then anything offered on mandriva.
but this is all personal opinion, I still give great thanks to mandriva as it was the start of great desktop linux distros, before mandriva the majority of linux was for servers only and not even close to workable for the desktop user.
Now where PCLOS comes in is that Texstar used to be a developer for Mandriva when it was still Mandrake.
He had a falling out at some point with them but he took his knowledge and started to make PCLOS its own distro.
PCLOS now is still mandriva at heart as it is compatible with a good amount of mandriva's packages though I would not try a lot of them if I were you as it could break the system.
PCLOS and ubuntu have different goals in the end, PCLOS is meant for all around general desktop use, Ubuntu does the same but it chooses to leave a lot out due to "legal" issues concerning certain apps, drivers, codecs, etc.

---

### Post by basenvironment on 2007-08-12
> **OrcusFelinus said:**
> 

How come Ubuntu, as popular as it is, can't do this?

Good question to ask dell or whomever made the card. 

Just a guess but possibly has to do with some firmware/driver that is non-free and PCLOS includes it but ubuntu doesn't.

---

### Post by OrcusFelinus on 2007-08-12
> **basenvironment said:**
> Good question to ask dell or whomever made the card. 

Just a guess but possibly has to do with some firmware/driver that is non-free and PCLOS includes it but ubuntu doesn't.

Not really. Neither OS supply the (windows) driver, but PCLOS has ndiswrapper installed by default and correctly identifies the card (in this case a Dell 1500 draft-n). It prompts you to configure the card via ndiswrapper and gives you the opportunity to supply the windows driver during the install and then takes it from there. Ubuntu does none of this. Ndiswrapper is in the Ubuntu repository but is not installed by default. Ubuntu merely ignores the card.

I'd be interested in hearing from anyone who has successfully managed to get their draft-n wireless card working on a Dell Inspiron 6400 under Feisty. :confused:

---

### Post by vexorian on 2007-08-12
It is a RPM distro and that's enough reason for me not to use it.

But hey it is all a matter of opinion, people make too much of a drama in distro/wm discussions... 

As long as it isn't harmful MSLinux distros that want to screw Linux up it is all good stuff, isn't it?

---

### Post by SunnyRabbiera on 2007-08-12
yeh but for a RPM based distro its pretty good, it pretty much none of the dependency hell of fedora or suse.
its apt that makes the real difference on it, if more RPM distros had apt they would look better.

---

### Post by darksong on 2007-08-12
PClinuxOS makes me pay for free software. So i don't use it anymore.

---

### Post by SunnyRabbiera on 2007-08-12
Yeh the pass server is annoying

---

### Post by cobrn1 on 2007-08-12
There's a thread in the gutsy dev ideas forum asking to include ndiswrapper in ubuntu by default - I think I see why now... ;)

Other thant the wireless issue (which sounds like it could be easily fixed) are there any other issues with ubuntu?

Anyway, I really like ubuntu, and respect it for being the rock solid usable distro it is, but it's missing a few nifty features that other distros include that are leaving it tailling a little.

for instance, (i think) Mepis includes the options to fix your installation, and crucially, fix your MBR by reinstalling GRUB when windows gone and f*ed it up. The ndiswrapper thing is another good example. fully installed compiz-fusion is another, but that'll be there in gutsy, so that's ok. It'd be nice to see a backup MBR option, encryption by default, etc.

As a side note, i'd like to have the option to dropinto the terminal in the liveCD boot menu, without loading the liveCD - basically, I'd like to see the cd have the basic tools you need to recover the system (live windows does - truen we can boot into the live CD gui, but some pc's cant and could do with e command line recovery mode like XP gives on the cd - just a thought).

Basically, there are quite a few things that ubuntu should really integrate as soon as possible, and obviously (looking at this thread) ndiswrapper is one of them...

Is any of this likely to happen (8.04's going to be LTS, so they won't want to go too wild, but it'd be good to see these small, but important improvements for the next LTS)

---

### Post by cmat on 2007-08-12
ndiswrapper needs to be integrated with the network manager, complete with documentation. It's just silly for it not to be. How many users do you think installed Ubuntu, the wireless doesn't work? What are they going to do, download ndiswrapper and find out how it works off the internet? What internet?

---

### Post by aysiu on 2007-08-12
> **cmat said:**
> ndiswrapper needs to be integrated with the network manager, complete with documentation. It's just silly for it not to be. How many users do you think installed Ubuntu, the wireless doesn't work? What are they going to do, download ndiswrapper and find out how it works off the internet? What internet?
How do people have wireless connections without a wired one too? To configure a router, aren't you supposed to have a wired connection to it? Or are people just stealing their neighbors' wireless connections?

---

### Post by cmat on 2007-08-12
My router is in the basement. Where my my cable connection comes in set up by the ISP. I'm not one to bring my desktop downstairs, set it up on the concrete floor and fiddling around on sites I never thought to be on and learning how command line works.

---

### Post by aysiu on 2007-08-12
> **cmat said:**
> My router is in the basement. Where my my cable connection comes in set up by the ISP. I'm not one to bring my desktop downstairs, set it up on the concrete floor and fiddling around on sites I never thought to be on and learning how command line works.
So you have a desktop upstairs with wireless and a router downstairs? I can't imagine this is a common scenario. I'm sorry you're in that situation, though.

Isn't there a GUI frontend for *ndiswrapper*? Something like *ndisgtk*?

---

### Post by cmat on 2007-08-12
> **aysiu said:**
> So you have a desktop upstairs with wireless and a router downstairs? I can't imagine this is a common scenario. I'm sorry you're in that situation, though.

Isn't there a GUI frontend for *ndiswrapper*? Something like *ndisgtk*?

Ya I used that, but at first when I was new to linux I followed the guide on NDISWrapper's source forge homepage. Also the reason me and a lot of people I know have wireless routers in their basements because it's very difficult to run wires and CAT5 cables. My computer is upstairs, I got a small ethernet cable to configure it, then I reconnect it downstairs. But the configuration can be done over the wireless. I just plugged it in, installed the drivers, connected to my router and configured it on Windows.

---

### Post by aysiu on 2007-08-12
I guess what I'm saying is that wireless is usually in a laptop, no? In which case, walking down to the basement and plugging in the laptop isn't that big a deal.

Nevertheless, I do agree that *ndiswrapper* (and, in fact, *ndisgtk*) should both be included in Ubuntu by default. Removing *ndiswrapper* from the Feisty CD was a **big** mistake on the part of the Ubuntu devs (it was on the Edgy and Dapper CDs--though not installed by default).

---

### Post by cmat on 2007-08-12
Some people don't have laptops. :) I didn't have one at the time. And if like 12,000,000 people use linux there is a great chance there are at least 500-5000 (guessing) people that have had my problem. I guess this is something we must sway developers into.

---

### Post by aysiu on 2007-08-12
> **cmat said:**
> Some people don't have laptops. :) I didn't have one at the time. And if like 12,000,000 people use linux there is a great chance there are at least 500-5000 (guessing) people that have had my problem. I guess this is something we must sway developers into.
Well, it's just weird to me that they *used* to include *ndiswrapper* and then removed it later.

---

### Post by cmat on 2007-08-12
I guess they are just trying to reduce the amount of proprietary drivers being used. Which would makes little sense and probably not the reason. But that's the only one I can think of.

---

### Post by DreamcastJack on 2007-08-12
I currently use both, I really dont know which I like the best. both do exactly what I need.. and the wireless issue on ubuntu was easy for me (but different cards different issues). I like both just fine. but if you want a OS that finds cards pretty much instantly..try out freespire.. i'm not too big of a fan..but it found my card using the LiveCD.

---

### Post by misfitpierce on 2007-08-12
I like Ubuntu better than PCLOS.. to be honest I liked Mandriva better than PCLOS... Kubuntu all the way for me.

---

### Post by jrusso2 on 2007-08-13
> **OrcusFelinus said:**
> If Ubuntu ever manages to make wireless installation and configuration as simple as PCLOS did, i'd switch in a heartbeat. 

On initial installation PCLOS detected my Dell draft-n card, offered an ndiswrapper solution,  prompted me to supply the (windows driver) .inf file and my WPA key, then it just plain WORKED. 

How come Ubuntu, as popular as it is, can't do this?

Several hours of forum reading, and a couple more tinkering at the command line and i'm no further ahead... My Inspiron 6400 just sits here sans internet connection. Everything else works just fine... but i'm beginning to realize why the average user will never accept Linux as a mainstream alternative to Windows.

Ubuntu would need to back off on its free software only dream if they ever want usability to be anywhere near that of PCLinuxOS.

You can talk until your blue in the fact but people want an operating system that works out of the box.  And if you won't include wireless firmware because its not open enough then thats a big problem.

---

### Post by vexorian on 2007-08-13
It is just configuration of a single hardware piece to make it a defining factor of how usable something is and how of a "dream" some philosophy is, that's just an overstatement.

> You can talk until your blue in the fact but people want an operating system that works out of the box.

no operating system as of today does that.

---

### Post by Ozeuss on 2007-08-13
> **jrusso2 said:**
> Ubuntu would need to back off on its free software only dream if they ever want usability to be anywhere near that of PCLinuxOS.

You can talk until your blue in the fact but people want an operating system that works out of the box.  And if you won't include wireless firmware because its not open enough then thats a big problem.

the free software dream is a common for *every* GNU/Linux distro. some take the hard-line, and some make more compromises (ubuntu does a lot).
Ubuntu works very well out of the box if you know what you're doing. in fact, it does much much better than windows ootb. and i would sacrifice a bit of functionality for a whole lot of freedom. that's just me, and it's good that there are distros that make more compromises and make it easier for new GNU/Linux users.

oh, and what's the deal people seem to have with media formats? i had a harder time making them work in windows (wmv might work natively, but not other codecs) than even in dapper, and feisty does it infinitely easier. and it makes the user think about the effect of proprietary formats, and the option of not using them if there's a legal issue in his country.

---

### Post by jrusso2 on 2007-08-13
> **Ozeuss said:**
> the free software dream is a common for *every* GNU/Linux distro. some take the hard-line, and some make more compromises (ubuntu does a lot).
Ubuntu works very well out of the box if you know what you're doing. in fact, it does much much better than windows ootb. and i would sacrifice a bit of functionality for a whole lot of freedom. that's just me, and it's good that there are distros that make more compromises and make it easier for new GNU/Linux users.

oh, and what's the deal people seem to have with media formats? i had a harder time making them work in windows (wmv might work natively, but not other codecs) than even in dapper, and feisty does it infinitely easier. and it makes the user think about the effect of proprietary formats, and the option of not using them if there's a legal issue in his country.

The average user does not care about the Free Software Movement.  They want their wireless to work, they want to play their media and they want it all to work without having to become a sysadmin.

When you buy a computer with WIndows on it the wireless is working.  With Ubuntu you need to install it and then make it work.  If you don't have a wired way to connect thats a real problem and a deal killer for most people.

With PCLinuxOS at least you have a chance the firmware for your atheros/intel/broadcom card is on the cd, and you have a nice gui if you need to try to do NDISWRAPPER.

With Ubuntu's stance they refuse to even provide these needed firmwares.  Thats why you have Freespire, Mephis,and LinuxMint that are willing to soften their stand and provide these features.

---

### Post by aysiu on 2007-08-13
> **jrusso2 said:**
> 
When you buy a computer with WIndows on it the wireless is working.  With Ubuntu you need to install it and then make it work. Interesting how you don't start your second sentence *When you buy a computer with Ubuntu...*

---

### Post by jrusso2 on 2007-08-13
Well considering most windows users buy a computer with Windows on it but most Linux users download an image and install it I thought it was accurate.

---

### Post by aysiu on 2007-08-13
> **jrusso2 said:**
> Well considering most windows users buy a computer with Windows on it but most Linux users download an image and install it I thought it was accurate.
But then that doesn't really have anything to do with Windows v. Ubuntu in terms of functionality. It has more to do with preinstalled v. not preinstalled.

---

### Post by jrusso2 on 2007-08-13
The point is why Ubuntu will never be truly easy to use if they take such a firm stand on Free Software to not allow people to even set up wireless from the CD.

---

### Post by darksong on 2007-08-13
> **jrusso2 said:**
> The point is why Ubuntu will never be truly easy to use if they take such a firm stand on Free Software to not allow people to even set up wireless from the CD.

The same with all linux distros. A few are realising that a firm stand of free software is not helping, after they changed that they are taking off - PClinuxOS and Sabayon  are examples of this.

---

### Post by vexorian on 2007-08-13
You said it, the average user does not care about it , they only want things to work out of the bugs, the problem with your assertions is that ubuntu does work out of the box on some hardware. Of course not all, but no OS really works out of the box for everything. Restricted drivers have dealt with my hardware nicely.

---

### Post by jrusso2 on 2007-08-13
> **vexorian said:**
> You said it, the average user does not care about it , they only want things to work out of the bugs, the problem with your assertions is that ubuntu does work out of the box on some hardware. Of course not all, but no OS really works out of the box for everything. Restricted drivers have dealt with my hardware nicely.

My point is for people who don't have another way to connect other then wireless and there appears to be lots of those.  Search for forums for people who can't get their wireless working.

Most wireless chipsets are Intel, Atheros or Broadcom, and Ubuntu doesn't have the drivers on the cd for any of them.

PCLINUXOS does that  makes it much easier for people to deal with.  There is no reason other then a philosophy for Ubuntu not to do this.

---

### Post by jrusso2 on 2007-08-13
> **darksong said:**
> The same with all linux distros. A few are realising that a firm stand of free software is not helping, after they changed that they are taking off - PClinuxOS and Sabayon  are examples of this.
 

So are Linux Mint and Freespire 2.0, and even Sam Linux.  This is my point.  There should be some flexibility there.

---

### Post by kellemes on 2007-08-13
> **darksong said:**
> The same with all linux distros. A few are realising that a firm stand of free software is not helping, after they changed that they are taking off - PClinuxOS and Sabayon  are examples of this.

Not helping what?!
You seem to be stuck (like a lot of folks lately) in thinking there should be a clear goal for GNU/Linux, a specific piece of the market or something..
Some comfort-oriented distro's will probably have this in mind, but GNU/Linux is so much more powerful then having n00bs point-click-setup there wireless.
If you want the comfort of Windows and the power/performance/security/stability of Linux.. get a mac.

---

### Post by igknighted on 2007-08-13
> **kellemes said:**
> Not helping what?!
You seem to be stuck (like a lot of folks lately) in thinking there should be a clear goal for GNU/Linux, a specific piece of the market or something..
Some comfort-oriented distro's will probably have this in mind, but GNU/Linux is so much more powerful then having n00bs point-click-setup there wireless.
If you want the comfort of Windows and the power/performance/security/stability of Linux.. get a mac.

I think he meant that a strict adherence to GNU/Free Software wasn't getting that particular distro anywhere, but once they adopted some non-free things they took off.  And I don't think its bad to have some non "free software only" distros, nor do I think it will kill the free ones.  There is a demand for both so it is reasonable to expect a supply for both.

EDIT: If you want to be able to tell the computer how you want it to do things as opposed to being given one option (even if it is "easy"), then you should never look at a mac.  You are hardly a computer "user", the computer knows how to do everything and you are along for the ride.  Some may like that, but it is the opposite of linux where you have control over EVERYTHING.

---

### Post by kelvin spratt on 2007-08-13
I use a desktop and to be honest Ubuntu and all the Debian based distros work straight from the box even with my ATi card, their is not one
RPM, based distro that does including Pclinux and i install on my PCs  hardrive. Pclinux did not find my ATI card my USB mouse, sound card or my Ethernet,also Feisty by default sets up my network so i can share files from my wifes windows based laptops shared folder,

---

### Post by igknighted on 2007-08-13
> **kelvin spratt said:**
> I use a desktop and to be honest Ubuntu and all the Debian based distros work straight from the box even with my ATi card, their is not one
RPM, based distro that does including Pclinux and i install on my PCs  hardrive. Pclinux did not find my ATI card my USB mouse, sound card or my Ethernet,also Feisty by default sets up my network so i can share files from my wifes windows based laptops shared folder,

This is just chance, not an inherent difference between deb and rpm.  The package format has nothing to do with what is recognized.  Don't assume that in the future RPM distros will not recognize your HW because of this reason.

That said, since Ubuntu recognizes your hardware, keep using it!  It's always nice to find a distro that recognizes everything :).

EDIT: PS, out of curiosity, what RPM distro's did you try?

---

### Post by darksong on 2007-08-13
> **igknighted said:**
> This is just chance, not an inherent difference between deb and rpm.  The package format has nothing to do with what is recognized.  Don't assume that in the future RPM distros will not recognize your HW because of this reason.

That said, since Ubuntu recognizes your hardware, keep using it!  It's always nice to find a distro that recognizes everything :).

EDIT: PS, out of curiosity, what RPM distro's did you try?


Personally i have had a much better time with .deb's than RPM's. Debs allow me to download application and install it like an exe. RPM's in PClinuxOS has never been able to do that for me. Every RPM i download will not install. PClinuxOS major downfall is its packaging - the repos are poor and RPM does not work.

---

### Post by aysiu on 2007-08-13
> **igknighted said:**
> I think he meant that a strict adherence to GNU/Free Software wasn't getting that particular distro anywhere, but once they adopted some non-free things they took off. I haven't seen that to be the case at all. Examples?

Mepis was around longer than Ubuntu and had proprietary stuff from the very start. Ubuntu is still ahead of Mepis in almost every measure (hype, forum membership, DistroWatch ranking). Blag and Linspire also fall into that category (proprietary stuff... not as popular as Ubuntu).

---

### Post by igknighted on 2007-08-13
> **aysiu said:**
> I haven't seen that to be the case at all. Examples?

Mepis was around longer than Ubuntu and had proprietary stuff from the very start. Ubuntu is still ahead of Mepis in almost every measure (hype, forum membership, DistroWatch ranking). Blag and Linspire also fall into that category (proprietary stuff... not as popular as Ubuntu).

I was just clarifying what another poster meant, not agreeing with him.  He suggested that Sabayon and PCLOS were his examples.  I do think that Ubuntu is a poor example to compare to, as they do include non-free code (madwifi and the intel firmware IIRC).  In this light, the rapid rise of PCLOS and Sabayon versus the drop of Suse, Fedora and Debian could support that claim.

The DW top 10 for the last 6 mo:

1) Ubuntu (some non-free code, but very little... neither group would really claim Ubuntu)
2) PCLOS (non-free, rising)
3) OpenSuse (free, dropping)
4) Fedora (free, dropping)
5) Sabayon (non-free, rising)
6) Debian (free, down from its heyday but fairly stable ATM)
7) Mepis (non-free, down but has had so much other "stuff" going on with changing base so much that there are extra circumstances)
8) Mint (non-free, rising)
9) Mandriva (free and non-free versions, falling due to poor business and quality choices)
10) DSL (unknown free/nonfree status, niche distro wouldn't really fit analysis anyways)

Given that list, I think you could make the arguement the previous poster was trying to make.  Overall, I think there is a market for both free and non-free distros.  I also think the extraordinary growth seen from these distros might be because there wasn't much in the non-free market until recently.  So this might explain the recent shift rather than a "non-free always trumps free" mentatility.

---

### Post by basenvironment on 2007-08-13
> **igknighted said:**
> 
Given that list, I think you could make the arguement the previous poster was trying to make.  
I dont. :)

---

### Post by cobrn1 on 2007-08-13
I think there may be other factors -ie other nifty features that are drawing people to them... For instance:

PCLOS - inclusion of more uptodate packages, features, etc. Also has a few nifty things up its sleeve, ie, on the live vd you can boot into the live environment, or you can boot straight into a commandline, giving you the best of both...

Sabayon - thrying to be pretty, so it attracts people. Interest may well subside when  compiz is included by default in most distros

Mint - lost of press and does a few things differently, ie the start menue, etc.

Overall, people like to experiment. But having to download the codecs isn't generally a problem, and it's made much easier by the autodownload feature in feisty... I doubt the added bonus of plying mp3s out of the box really matters that much to most people.

EDIT: i know that's not the only non-free bit of software, but it's the most hotly debated one...

---

### Post by kelvin spratt on 2007-08-13
Ignighted
I do not wish to name as it would sound like flaming but i have over 30
distros stored on my computer all under 3months old, the reason trying to find a distro that all the software that i need to use works on one distro,and this is how i came to discover that all the Debian distros on my standard PC, work better straight from the box. Ubuntu is certainly not the best of the bunch look at my other Distro now that's something else as everything may not be cutting edge but it all works like it says on the box.

---

### Post by igknighted on 2007-08-13
> **basenvironment said:**
> I dont. :)

OK, im not disagreeing with you, but what about it makes you come to another conclusion?  I didn't even AGREE with the conclusion, I just looking at the data, I can see where someone COULD draw that conclusion.

---

### Post by OrcusFelinus on 2007-08-13
> **kellemes said:**
> Not helping what?!
You seem to be stuck (like a lot of folks lately) in thinking there should be a clear goal for GNU/Linux, a specific piece of the market or something..
Some comfort-oriented distro's will probably have this in mind, but GNU/Linux is so much more powerful then having n00bs point-click-setup there wireless.
If you want the comfort of Windows and the power/performance/security/stability of Linux.. get a mac.

Geez, why *shouldn't* there be a clear goal? Why wouldn't you want Linux to gain a *real* foothold in the retail market? Wouldn't it be nice to actually have a choice when you buy a PC as opposed to Billy shoving his latest piece of crapware down your throat? Wouldn't it be nice to cruise the local store and actually be able to buy a game or app that ran natively under Linux? And what would be wrong with Linux being both easy to set up initially *and* powerful/configurable behind the scenes for those who want to wind 'er up?

Linux is arguably the most versatile OS out there, but it'll never gain acceptance with the masses as long as it remains clique'ish and a niche OS used mainly by command line guru's who look down their nose at others who may only be looking for an alternative to the Windows monopoly.

---

### Post by Ozeuss on 2007-08-14
> **igknighted said:**
> I think he meant that a strict adherence to GNU/Free Software wasn't getting that particular distro anywhere, but once they adopted some non-free things they took off.  And I don't think its bad to have some non "free software only" distros, nor do I think it will kill the free ones.  There is a demand for both so it is reasonable to expect a supply for both.

I agree that there's a lot of room for distro that are more compromising, but the reason GNU/Linux got its momentum is from its adherence to freedom. if it weren't for the concepts of freedom, ubuntu would be just another proprietary os, that would go into oblivion. freedom of software is more important than ad-hoc ease of use, because it will advance REAL interoperability, functionality, and ease of use.

In my experience, ubuntu works much much better ootb than windows. if it doesn't for someone, it's the fault of the hardware manufactures, and they should make the adjustment, not ubuntu or fedora. or anyone. 
distros will get nowhere trying to gain popularity by acting like a slutty cheerleader and putting out just for one-minute ease of use.

---

### Post by OrcusFelinus on 2007-08-14
Well, two days of reading and configuration attempts... but it finally WORKS! Got the 1500 draft-n card working finally. Now 6 of my 7 machines are running Ubuntu (my daughter steadfastly refuses to budge from her Windows machine... games... ugh!) :):):)

---

### Post by dptxp on 2007-08-14
> **OrcusFelinus said:**
> 
Linux is arguably the most versatile OS out there, but it'll never gain acceptance with the masses as long as it remains clique'ish and a niche OS used mainly by command line guru's who look down their nose at others who may only be looking for an alternative to the Windows monopoly.

First there was Command Line. Then came GUI. The generation that never used command line is a spoiled generation that wants to be spoon fed (some, not everyone). There is a reason why everything is not under GUI in Linux and I think that the more serious user understands it.

I had started with Windows 3.1 (actually have even punched cards for mainframes), I am not yet much used to command line yet, but can sense that Linux should stay this way. After all command line is not needed for daily use and the functions one normally uses command line for should be carried out by those who have a bit of knowledge. One can always learn a few simple ones with just a bit of effort and wish.

Linux is not Windows and we do not want Linux to be Windows.

---

### Post by jrusso2 on 2007-08-14
At this point I can't really see Linux being a major player on the desktop, its way too political.  In order to compete it needs to be able to embrace some proprietary components to make it usable for most users.

With the present political climate this appears to be impossible.

So I am just happy to be able to use it myself as I have been doing for 11 years.

I agree with Linus that open source is just a better way to develop software but its not a political calling.  We need to be able to use what works until their are  open source alternatives that are viable and usable.

In the meantime distros like Ubuntu and Fedora would do better to offer these components that are needed in the distro, or at least include an easy and obvious method to install as per my previous suggestion which seems to fall on deaf ears.

---

### Post by vexorian on 2007-08-14
> In the meantime distros like Ubuntu and Fedora would do better to offer these components that are needed in the distro, or at least include an easy and obvious method to install as per my previous suggestion which seems to fall on deaf ears.You seem to be the one with deaf ears, considering that installing proprietary codecs and drivers in Feisty is very easy already.

- OS detects I want to play some mp3 file, it tells me "yo has to download codecs" I click yes, it downloads codecs and then it plays the mp3 file.

- The same with my nvidia card.

The average user can't even configure hardware for windows, making it a big deal is just falling into myths, Linux does not have to be better to install or configure, it must come in more hardware by default, sorry , but that's true...

---

### Post by OrcusFelinus on 2007-08-14
> **dptxp said:**
> 

Linux is not Windows and we do not want Linux to be Windows.

Who is this magical "we" you speak of? 

Bah, looks like this thread is evolving into the usual elitist Linux vs Windows crap. My question that started this thread has long been answered. I'm outta here.

---

### Post by basenvironment on 2007-08-14
Why stop at "some" proprietary components? They should chock it full of proprietary goodness so that it is usable for all users? Those wanting something not chock-full-of-proprietary should have to go some place else and start their own OS. Sure it is a free OS but how dare they expect us to have to install our own proprietary parts - they should do that for us - even if they have reasons for not including those parts. How dare they follow what they believe in, while giving me a totally free product. They should dictate that proprietary to me, they should keep me locked in to using something, they should make it impossible to remove without breaking the system. How dare they only offer me free software for free cost. I am a customer and I will tell them what they are going to give me, not accept what they are offering. I always do that at every business I frequent.


[SIZE="1"]rant over[/SIZE]

---

