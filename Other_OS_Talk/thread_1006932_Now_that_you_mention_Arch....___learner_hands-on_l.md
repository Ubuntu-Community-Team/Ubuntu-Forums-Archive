---
title: "Now that you mention Arch....   learner hands-on linux?"
date: 2008-12-09
forum: Other OS Talk
---

### Post by xarte on 2008-12-09
Would that be a good distro to learn 'real' linux on? 

Arch sounds nice, and the instructions on the website are amazingly clear. I really like the idea of installing ground-up and actually knowing where things are going and what they are doing.

 I suspect Ubuntu, however pretty and fun it is, isn't going to help me learn to actually use Linux itself. Command line fixes tend to be executed with crossed fingers that I've copied it right.

What would be a good, uber-lean Linux distro to play with? 

Will I be able to get my head around this with a bit of tinkering like I did with BASIC and MS-DOS or is it all getting too complicated these days? Maybe I should just get SuSE and leave the techy stuff to the pros....

---

### Post by kerry_s on 2008-12-09
real linux? :lolflag:

linux is linux, you can learn it from the gui or cli it doesn't matter.

sure, starting with a base install you can learn what parts you need and it's fun to see what you would do.

i personally do a base install of debian, then work my way up from there.
arch is okay to, you just need to follow the wiki to get the wording right.

---

### Post by kk0sse54 on 2008-12-09
I agree there's no real linux. As for wanting to be challenged and to learn a bit more about Linux I'd go for Slackware. Install from the minimal cd and you'll get a pretty sweet system which you'll learn a lot during the process of configuration.

---

### Post by xarte on 2008-12-09
I guess saying 'real' linux is a bit like a red rag to a bull, isn't it. I'm not saying one distro is 'more real' than another - what I mean is, I want to get my head under the bonnet. 

My experience of Ubuntu so far isn't much different to installing Windows - plug the disks in and off you go. Tried tinkering with some command line things till I discovered that there were utilities to fix those things right on the desktop.

Which was really nice... but not all that satisfying for my inner geek, you know!

---

### Post by Tatty on 2008-12-09
> **xarte said:**
> My experience of Ubuntu so far isn't much different to installing Windows - plug the disks in and off you go. Tried tinkering with some command line things till I discovered that there were utilities to fix those things right on the desktop.

You should have tried installing ubuntu a couple of years ago.  I remember installing dapper (might even have been hoary - I hadnt grasped the Ubuntu naming system at this point), banging my head on the keyboard several times with various terminals and text editors open, cursing that it couldnt just configure itself. 
lol:popcorn:

---

### Post by cardinals_fan on 2008-12-09
Absolutely Slackware.  Nothing will teach you more (except maybe LFS).  It's minimal, manual, and vanilla.  And who knows - you just might stick with it.  I did.

---

### Post by zmjjmz on 2008-12-09
I always recommend digging up an old machine and using a lightwieght distro such as Damn Small Linux, DeLi, or Basic Linux.

This has given me a ton of experience in Linux.

---

### Post by Tatty on 2008-12-09
You could always try Gentoo.  Lots of manual compilation to do there.

---

### Post by kerry_s on 2008-12-09
> **xarte said:**
> I guess saying 'real' linux is a bit like a red rag to a bull, isn't it. I'm not saying one distro is 'more real' than another - what I mean is, I want to get my head under the bonnet. 

My experience of Ubuntu so far isn't much different to installing Windows - plug the disks in and off you go. Tried tinkering with some command line things till I discovered that there were utilities to fix those things right on the desktop.

Which was really nice... but not all that satisfying for my inner geek, you know!

here's the debian net installer, if you uncheck everything at package selection, you'll get just a base install, it will be command line, no gui yet.
to start from there, the first thing you will want is X:
**apt-get install xorg**

next you'll need to decide what gui you want to work in, i'm a jwm guy, it's what i use:
**apt-get install jwm**

having those 2 things is enough to get you into gui:
type> **exit**
now log in as your normal user
type> **startx**

from there you open a terminal and continue adding stuff you want.
example:
[B]su
apt-get install pcmanfm leafpad[/B]

su, gives you root.
pcmanfm is a filemanager
leafpad is a text editor

the first thing i do, when i get into gui is grab synaptic, so i can browse packages easily and take my time deciding what i want to try.
example:
[B]su
apt-get install synaptic
synaptic[/B]

---

### Post by dizee on 2008-12-09
Definitely something like Slackware if you want to learn. Did the Debian netinstall myself and, while I like it, it's pretty straightforward if you have some Ubuntu CLI experience (apt-get is still apt-get, after all).

---

### Post by Sorivenul on 2008-12-09
There are many paths to try here, each with something slightly different to offer.

Arch is a good system, and with the BSD-style init (which probably doesn't concern you much at the moment) configuration is relatively easy, especially with the Arch Beginner's Guide.  However, most of what Arch taught me was how to use pacman, the Arch package manager, which in itself is enough reason to try Arch.

Slackware is as basic as it comes.  Vanilla packages, manual configuration, manual... um...  pretty much everything, if you want.  A lot of knowledge can be gained from Slackware maintenance, configuration, and package management (which can be done manually, or with the help of tools like slapt-get/gslapt).

A minimal (netinstall) of Debian is always my suggestion for those seriously looking beyond Ubuntu.  The basics of Ubuntu are still there, but differences are also evident from time you start the install.  Manual configuration, possible handling of some drivers/firmware, good to learn about the init systems present in Debian-based, and also Ubuntu-based distributions.  

There are many other options, and [INX]("http://inx.maincontent.net/"), an Ubuntu-based command-line system may help prepare you for the journey ahead, wherever it may take you.

---

### Post by cardinals_fan on 2008-12-09
> **Sorivenul said:**
> 
Arch is a good system, and with the BSD-style init (which probably doesn't concern you much at the moment) configuration is relatively easy, especially with the Arch Beginner's Guide.  However, most of what Arch taught me was how to use pacman, the Arch package manager, which in itself is enough reason to try Arch.
Arch is a good distro, but pacman + copy/paste from the wiki makes learning very optional.
> **Sorivenul said:**
> 
Slackware is as basic as it comes.  Vanilla packages, manual configuration, manual... um...  pretty much everything, if you want.  A lot of knowledge can be gained from Slackware maintenance, configuration, and package management (which can be done manually, or with the help of tools like slapt-get/gslapt).
I strongly recommend manually managing dependencies, at least at first.  It gives you a real feel for how packages fit together, and encourages you to become more involved in keeping your system secure/up-to-date.
> **Sorivenul said:**
> 
There are many other options, and [INX]("http://inx.maincontent.net/"), an Ubuntu-based command-line system may help prepare you for the journey ahead, wherever it may take you.
INX is very good for gently learning about the CLI.

It won't teach you 'Linux', but a BSD (I recommend NetBSD) can be a great learning experience.

---

### Post by ryaxnb on 2008-12-09
> **xarte said:**
> Would that be a good distro to learn 'real' linux on? 

Arch sounds nice, and the instructions on the website are amazingly clear. I really like the idea of installing ground-up and actually knowing where things are going and what they are doing.

 I suspect Ubuntu, however pretty and fun it is, isn't going to help me learn to actually use Linux itself. Command line fixes tend to be executed with crossed fingers that I've copied it right.

What would be a good, uber-lean Linux distro to play with? 

Will I be able to get my head around this with a bit of tinkering like I did with BASIC and MS-DOS or is it all getting too complicated these days? Maybe I should just get SuSE and leave the techy stuff to the pros....
Ubuntu has plenty of room to grow to the CLI. The full set of tools are in the repositories, the basic set is included, you'll be up and compiling and using emacs or vim in no time. :D Linux is most certainly Linux on GUI, and Linux on the CLI is seriously available in Ubuntu, and Ubuntu does it very well. It has SSH, SFTP, NFS, Apache, and the weight of basically a modified Debian repo behind it. Debian is the standard for free as in beer as well as speech FOSS servers (non-paid). Debian is the standard, and Ubuntu is gaining traction in FOSS enterprise computing.  
Of course, there is the question of whether you want to have "real" as in LSB Linux. That requires SuSE or Red Hat or Mandriva, and is unrelated to GUI issues. If you learn LSB Linux with yum, Redhat/Fedora/CentOS style, you prepare for a future as a Red Hat IT tech.

---

### Post by xarte on 2008-12-09
> **kerry_s said:**
> here's the debian net installer, if you uncheck everything at package selection, you'll get just a base install, it will be command line, no gui yet.
to start from there, the first thing you will want is X:
**apt-get install xorg**

<snip>

[/B]

This is perfect - thanks, Kerry. I'll have a look at Slackware too - might be interesting to go through the same process and see how they compare.

Sounds like the Arch tools will be a little too tempting - cut and paste is handy but does short-circuit your learning. Mind you that's how I learned HTML - copying and pasting other people's markup.


I'm hearing you Tatty - my first attempts with Linux a while ago were insanely frustrating. 

I think I might have to grab a cheapo machine from Ebay to play with, so I can keep the ubuntu laptop for actual work. (Dangit, doncha hate having to earn a living....)

---

### Post by xarte on 2008-12-10
> **ryaxnb said:**
> Ubuntu has plenty of room to grow to the CLI. The full set of tools are in the repositories, the basic set is included, you'll be up and compiling and using emacs or vim in no time. :D Linux is most certainly Linux on GUI, and Linux on the CLI is seriously available in Ubuntu, and Ubuntu does it very well. It has SSH, SFTP, NFS, Apache, and the weight of basically a modified Debian repo behind it. Debian is the standard for free as in beer as well as speech FOSS servers (non-paid). Debian is the standard, and Ubuntu is gaining traction in FOSS enterprise computing.  
Of course, there is the question of whether you want to have "real" as in LSB Linux. That requires SuSE or Red Hat or Mandriva, and is unrelated to GUI issues. If you learn LSB Linux with yum, Redhat/Fedora/CentOS style, you prepare for a future as a Red Hat IT tech.

Ryan, I'm interested in what you're saying here about the differences between the two, but I don't -quite- understand. Could you elaborate a little? The stuff you said about command line makes a fair bit of sense but LSB not so much. (due to ignorance on my part)

---

### Post by cardinals_fan on 2008-12-10
> **xarte said:**
> Ryan, I'm interested in what you're saying here about the differences between the two, but I don't -quite- understand. Could you elaborate a little? The stuff you said about command line makes a fair bit of sense but LSB not so much. (due to ignorance on my part)
[http://en.wikipedia.org/wiki/Linux_Standard_Base](http://en.wikipedia.org/wiki/Linux_Standard_Base)

Anyway, if you want to be a Red Hat Certified sysadmin in the future, you should use CentOS.  Otherwise, the other systems listed are fine.

---

### Post by kpkeerthi on 2008-12-10
In my opinion, all distros are the same under the hood. The knowledge you will eventually gain depends on which route (command line or GUI) you take to configure things. It really doesn't matter which distro you use.

Gentoo will only teach you how to compile from source.
Slackware will only teach you how to manually track package dependencies.
Neither compiling from source nor tracking deps manually is exciting.

If somebody tells you would learn more from Slackware/Gentoo/Arch, they are lying. You could still use Ubuntu (or any beginner friendly Linux) and learn linux.

---

### Post by cardinals_fan on 2008-12-10
> **kpkeerthi said:**
> In my opinion, all distros are the same under the hood. The knowledge you will eventually gain depends on which route (command line or GUI) you take to configure things. It really doesn't matter which distro you use.

Gentoo will only teach you how to compile from source.
Slackware will only teach you how to manually track package dependencies.
Neither compiling from source nor tracking deps manually is exciting.

If somebody tells you would learn more from Slackware/Gentoo/Arch, they are lying. You could still use Ubuntu (or any beginner friendly Linux) and learn linux.
While a motivated user with Ubuntu will learn more than a slacker with Slackware (sorry, I had to :P), I think that the latter is more conducive to learning.  It has completely vanilla packages and encourages the user to tweak things they may not have known existed.  Could they have searched them out and changed them on Ubuntu?  Yes, but it isn't part of a steadily building process culminating with a desktop that is uniquely yours.  It's the difference between starting with a pile of bricks to build a house and starting with most of the house already built and taking apart what you want to mess with.

---

### Post by ddnev45 on 2008-12-10
Slackware.

---

### Post by kevdog on 2008-12-10
Although Slackware may force you to manually build your system -- you can do the same in Ubuntu if you really want to.  Its just that in one situation you are forced to do --- in the other its optional.  Linux is linux either way.

As far as compiling.  Its is kind of neat, more powerful, etc.  However I would agree it really doesn't teach you "linux".  But I guess that begs the question -- "What really is learning Linux", and for that question I have no real answer.  Compiling packages from source may be one small part of this answer.

---

### Post by cardinals_fan on 2008-12-10
> **kevdog said:**
> Although Slackware may force you to manually build your system -- you can do the same in Ubuntu if you really want to.  Its just that in one situation you are forced to do --- in the other its optional.  Linux is linux either way.
Well, even an Ubuntu minimal install won't require the same configuration as Slack.  You'd have to literally rip down what's there.
> **kevdog said:**
> 
As far as compiling.  Its is kind of neat, more powerful, etc.  However I would agree it really doesn't teach you "linux".  But I guess that begs the question -- "What really is learning Linux", and for that question I have no real answer.  Compiling packages from source may be one small part of this answer.
Is compiling software educational?  I think so.  Is using a source-based packaging system such as Portage or Pkgsrc educational?  I have my doubts.

---

### Post by Rokurosv on 2008-12-10
The latest minimal distro I've heard is [Crux]("http://crux.nu/")
> CRUX is a lightweight, i686-optimized Linux distribution targeted at experienced Linux users. The primary focus of this distribution is keep it simple, which is reflected in a straightforward tar.gz-based package system, BSD-style initscripts, and a relatively small collection of trimmed packages. The secondary focus is utilization of new Linux features and recent tools and libraries. CRUX also has a ports system which makes it easy to install and upgrade applications. 

I've downloaded it but I haven't installed it yet, I'll try it on an old pc one of this days.

---

### Post by handy on 2008-12-10
> **xarte said:**
> Would that be a good distro to learn 'real' linux on? 

Arch sounds nice, and the instructions on the website are amazingly clear. I really like the idea of installing ground-up and actually knowing where things are going and what they are doing.

 I suspect Ubuntu, however pretty and fun it is, isn't going to help me learn to actually use Linux itself. Command line fixes tend to be executed with crossed fingers that I've copied it right.

What would be a good, uber-lean Linux distro to play with? 

Will I be able to get my head around this with a bit of tinkering like I did with BASIC and MS-DOS or is it all getting too complicated these days? Maybe I should just get SuSE and leave the techy stuff to the pros....

Go to the evil [***_distrowatch_***]("http://distrowatch.com/") & get a little familiar with what's available & distro hop around to your hearts content.  There is no race to learn as much as you can in the shortest time possible.  Every distro has got things to teach us.

Enjoy exploring the distros & BSD's.

---

### Post by Icehuck on 2008-12-10
I've thought about trying out Slackware before but its reputation intimidates me. Though it seems that you can install a full ready to go system now? At least at 3.8 gigs or so I would assume this is what they are referring to.

---

### Post by Sorivenul on 2008-12-10
> **Icehuck said:**
> I've thought about trying out Slackware before but its reputation intimidates me. Though it seems that you can install a full ready to go system now? At least at 3.8 gigs or so I would assume this is what they are referring to.

You can install as much or as little as you wish.  Using the DVD you can select which packages (or groups of packages) you wish to install.  It eliminates some of the early hassle of setting up your base system.  If you install your comfortable GUI to begin with, adding on becomes much more friendly and fun.  It also slightly defeats the purpose of learning Slackware from the ground up.  However, if you want to start with a full GUI, there are plenty of Slackware-based systems available in addition to Slackware itself - Zenwalk, Slax, and Absolute come to mind right now.  There's no right or wrong way to do what you want, so have a good time!

---

### Post by nothingspecial on 2008-12-10
> **Sorivenul said:**
>  
There are many other options, and [INX]("http://inx.maincontent.net/"), an Ubuntu-based command-line system may help prepare you for the journey ahead, wherever it may take you.

Start with inx, it`s silly but excellent. It`s more like a beginners guide to the command line than an actual distro, but it`s fun. You can install it on a usb stick and boot into it on any computer whenever you like, a little os in your pocket.

---

### Post by xarte on 2008-12-10
Reading with interest - great to hear the various thoughts, thank you.

Inx sounds fun, so do the little versions of Slack. PUppy too.

Wish I'd kept that old computer.I think a couple of bigger thumbdrives might be in order.

woooah actually falling asleep at the computer. Gonna have to cave and get some sleep...

---

### Post by eldragon on 2008-12-10
what you are actually doing wrong is the copy/pasting bit.

it doesnt matter what distro you use, as long as fixes are not applied blindly... use the man pages to get some insight on what you are doing, search the wiki...

or else, you will find yourself using arch, and applying much more blind chunks of text into a terminal, you will only learn to type fast....

---

### Post by billgoldberg on 2008-12-10
> **xarte said:**
> I guess saying 'real' linux is a bit like a red rag to a bull, isn't it. I'm not saying one distro is 'more real' than another - what I mean is, I want to get my head under the bonnet. 

My experience of Ubuntu so far isn't much different to installing Windows - plug the disks in and off you go. Tried tinkering with some command line things till I discovered that there were utilities to fix those things right on the desktop.

Which was really nice... but not all that satisfying for my inner geek, you know!

You can do a command line install of Ubuntu.

That will just installed the bare bones.

Then you can install X and the packages you want yourself.

That would be a good exercise.

Or you could try Arch or Gentoo.

And if you feel you really know Linux, try Linux From Scratch.

---

### Post by bapoumba on 2008-12-10
Moved to Other OS Talk.

---

### Post by xarte on 2008-12-10
> **eldragon said:**
> what you are actually doing wrong is the copy/pasting bit.

it doesnt matter what distro you use, as long as fixes are not applied blindly... use the man pages to get some insight on what you are doing, search the wiki...

or else, you will find yourself using arch, and applying much more blind chunks of text into a terminal, you will only learn to type fast....

Excellent point. Taken on board, thanks.

---

### Post by MisfitI38 on 2008-12-10
> **cardinals_fan said:**
> Arch is a good distro, but ...copy/paste from the wiki makes learning very optional..

The same can be said for LFS, or a stage 3 Gentoo install.
I think this can be viewed as a testament to good documentation..not being read.

Arch, LFS and Gentoo all have excellent documentation resources, while I would rate Slack's docs as mediocre, (and scattered) at best.

---

### Post by cardinals_fan on 2008-12-10
> **MisfitI38 said:**
> The same can be said for LFS, or a stage 3 Gentoo install.
I think this can be viewed as a testament to good documentation..not being read.

Arch, LFS and Gentoo all have excellent documentation resources, while I would rate Slack's docs as mediocre, (and scattered) at best.
Of course.  I'm simply pointing out that following the beginner's guide will essentially automate your entire install.  To truly learn from Arch, the wiki should only be used in extreme cases.

---

### Post by chucky chuckaluck on 2008-12-11
there are definitely ways around learning when you use arch. my guess is that, if you want to learn more about linux, you can do that on purpose with any distro, rather than hoping a distro will force understanding into your head.

---

### Post by handy on 2008-12-11
> **chucky chuckaluck said:**
> there are definitely ways around learning when you use arch. my guess is that, if you want to learn more about linux, you can do that on purpose with any distro, rather than hoping a distro will force understanding into your head.

I agree.

Still, I have learned far more about Linux since I've been using Arch, than any other distro, & I'm starting to become more drawn to app's that have editable configuration files than those that point & click for everything.

Hell, I might end up with distro bulimia like you chucky! :lolflag:

---

### Post by chucky chuckaluck on 2008-12-11
distro bullimia? me? i'd say i have wm bullimia, but not distro bullimia. :popcorn:

---

### Post by handy on 2008-12-11
You do seem to like to make everything as skinny as can be.

I think you may have caught a Terminal illness. ;-)

---

### Post by xarte on 2008-12-11
> **chucky chuckaluck said:**
> there are definitely ways around learning when you use arch. my guess is that, if you want to learn more about linux, you can do that on purpose with any distro, rather than hoping a distro will force understanding into your head.

Perhaps some need learning forced upon them, but in my case it's more that I'm looking for as lean and uncluttered an experience as possible (within reason). Extra bells and whistles just muddy the waters when you are trying to understand how something works. ( How's that for a mixed metaphor?)

Though in retrospect I've really asked the wrong question. A better question might be

"How do I go about learning to use and administer linux effectively, and what are the best tools to help me do this?"

I've done a bit of both DIY and formal education, and know that there are many ways to aquire knowledge - some more fun than others, some more effective than others.

Some sort of Linux Sysadmin direction sounds appealing but I couldn't spend another four years at university... not sure that my maths was good enough for computing anyway, even before 20 years passed....:-k

---

### Post by bonzodog on 2008-12-11
Yes, I would say Slackware for the definitive Linux Learning Curve. Its where I started in 2000 (Slack 7.0), and I stuck with it for 5 years.

I now use Arch Linux, and I nearly always have a terminal session open somewhere, as Slack taught me the sheer raw power of the CLI in Linux. Slack also teaches you about dependency resolution, which most other distros do by default, including Arch. Even now, when pacman tells me it need X,X,X to install this, I will often say to myself "no, it doesnt *need* that library or progam, but it provides the full feature set...."

Also, I am still quite addicted to compiling stuff manually, though I am a big fan of AUR, which still will manually build stuff, but removes the command sequence, you just issue makepkg -ci, and watch it work.....

---

### Post by notwen on 2008-12-11
> **kerry_s said:**
> here's the debian net installer, if you uncheck everything at package selection, you'll get just a base install, it will be command line, no gui yet.
to start from there, the first thing you will want is X:
**apt-get install xorg**

next you'll need to decide what gui you want to work in, i'm a jwm guy, it's what i use:
**apt-get install jwm**

having those 2 things is enough to get you into gui:
type> **exit**
now log in as your normal user
type> **startx**

from there you open a terminal and continue adding stuff you want.
example:
[B]su
apt-get install pcmanfm leafpad[/B]

su, gives you root.
pcmanfm is a filemanager
leafpad is a text editor

the first thing i do, when i get into gui is grab synaptic, so i can browse packages easily and take my time deciding what i want to try.
example:
[B]su
apt-get install synaptic
synaptic[/B]

+1 Debian.  Debian has taught me more than any other distro and along w/ Ubuntu, Debian has made me a apt-get fiend.  As much as Arch intrigues me, I always seem to end up using any Debian-based distro over the others.  I'd recommend Debian as a stepping stone to other distros, as it has it's similarities to Ubuntu, while also having enough differences to make it clear you're not using Ubuntu.  Hope that makes sense.  =p

---

### Post by cardinals_fan on 2008-12-11
> **xarte said:**
> Perhaps some need learning forced upon them, but in my case it's more that I'm looking for as lean and uncluttered an experience as possible (within reason). Extra bells and whistles just muddy the waters when you are trying to understand how something works. ( How's that for a mixed metaphor?)

Though in retrospect I've really asked the wrong question. A better question might be

"How do I go about learning to use and administer linux effectively, and what are the best tools to help me do this?"

I've done a bit of both DIY and formal education, and know that there are many ways to aquire knowledge - some more fun than others, some more effective than others.

Some sort of Linux Sysadmin direction sounds appealing but I couldn't spend another four years at university... not sure that my maths was good enough for computing anyway, even before 20 years passed....:-k
It depends on what "using and administering Linux" entails for you.  To administer Linux systems in the enterprise, you should really use CentOS since Red Hat is pretty much the standard.
> **bonzodog said:**
> Yes, I would say Slackware for the definitive Linux Learning Curve. Its where I started in 2000 (Slack 7.0), and I stuck with it for 5 years.

I now use Arch Linux, and I nearly always have a terminal session open somewhere, as Slack taught me the sheer raw power of the CLI in Linux. Slack also teaches you about dependency resolution, which most other distros do by default, including Arch. Even now, when pacman tells me it need X,X,X to install this, I will often say to myself "no, it doesnt *need* that library or progam, but it provides the full feature set...."

Also, I am still quite addicted to compiling stuff manually, though I am a big fan of AUR, which still will manually build stuff, but removes the command sequence, you just issue makepkg -ci, and watch it work.....
+1

---

### Post by xarte on 2008-12-11
> **cardinals_fan said:**
> It depends on what "using and administering Linux" entails for you.  To administer Linux systems in the enterprise, you should really use CentOS since Red Hat is pretty much the standard.

+1

I  had a bit of a look at listings on a job site and I don't see myself fitting well into many of them - especially with my complete lack of project management - heck any sort of management - skills. Can't organize my home office paperwork! I was thinking more along the lines of - I don't know - a local help desk? Consulting for local computer shops, now that desktop linux is becoming more popular...

Probably not all that realistic at this stage... just toying with some ideas and seeing if I can come up with something achievable.

In terms of use/administer I mean as a tool at home - being able to use and customize it, and know what it's actually doing, and troubleshoot it myself, and to be able to undo buggy updates and keep crapware off my machine. I want to be the driver and mechanic, not a passenger.

 It's so fascinating to me - it's a bit like when you see those cutaway working models of engines.

> 
Even now, when pacman tells me it need X,X,X to install this, I will often say to myself "no, it doesnt need that library or progam, but it provides the full feature set...."

Also, I am still quite addicted to compiling stuff manually, though I am a big fan of AUR, which still will manually build stuff, but removes the command sequence, you just issue makepkg -ci, and watch it work.....


YES !!! Exactly !!!! That's what I want!

---

### Post by MisfitI38 on 2008-12-13
> **chucky chuckaluck said:**
> there are definitely ways around learning when you use arch. my guess is that, if you want to learn more about linux, you can do that on purpose with any distro, rather than hoping a distro will force understanding into your head.

Well said.
In my case, I need a distro to guide me to learn, since so many of them focus on abstraction and avoiding the underlying base..I just played along.
With Arch, I sort of got my hands dirtier from the installation onwards, and just stuck with the basic methodology put forth in the Official Installation Guide.

---

### Post by simtaalo on 2008-12-13
going through this guide will teach you alot [http://tille.garrels.be/training/tldp/index.html](http://tille.garrels.be/training/tldp/index.html)

its pretty in-depth.

---

