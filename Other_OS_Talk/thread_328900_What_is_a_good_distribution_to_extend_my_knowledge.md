---
title: "What is a good distribution to extend my knowledge of linux?"
date: 2006-12-31
forum: Other OS Talk
---

### Post by Skia_42 on 2006-12-31
I originally switched from Mac OSX to Ubuntu to learn more about how *NIX systems work. I chose Ubuntu because It was the most popular and relativly easy to use. Over the past 6 months I learned an immense amount and I now have a working Ubuntu System that I am never going to leave. I have been looking for a Linux Distribution that is a bit more of challenge installing, configuring and using then Ubuntu that I can work with in my spare time. I have been told that both Slackware and Fedora are powerful OS's that are worth the extra work. Can anyone share their experiences with these or any other Linux Distributions?

---

### Post by towsonu2003 on 2007-01-01
It seems you want to learn more about Linux. Either Gentoo or Slackware would do the job. I'd prefer Slackware, because while you're learning how things work, you won't have to go the extra mile (and cpu time) to compile programs. 

I started with Slackware, and I know the basics (from file permissions to recovering from X failures) thanks to that distro.

---

### Post by neowolf on 2007-01-01
Fedora will teach you quite abit about the Redhat way of doing things, RPM and YUM, useflu if you wanted to get a job as a Linux System Admin as lots of people use RHEL/Fedora in enterprise (Wikimedia uses Fedora on its servers alot).
Gentoo will teach you alot but has little actual use IMO.

---

### Post by 3rdalbum on 2007-01-02
I know this sounds like a cop-out, but you could try developing your own distribution. Or, you could load Slackware or Fluxbuntu, where there are few if any GUI configuration tools.

---

### Post by jdhore on 2007-01-03
i'd recommend Debian, it gives you some of the great features of Ubuntu like apt-get, but it's lighter, faster and a bit more difficult to use, but you do learn a lot...i'm VERY glad i learned most of what i know about Linux on Debian...kept me away from using some of the noobish things in Ubuntu...i learned A LOT...

---

### Post by Celeborn74 on 2007-01-03
FULL ACK with jdhore. Debian has been my distribution where I learned loads from installation to configuration. For example, Debian is much more restrictive on user rights after first install, and you have to finetune a little bit to get the user rights you need. That's a big difference to Ubuntu. And you KNOW about your settings then.

Don't know Gentoo but all the compiling might be more than you would like to know...

---

### Post by jdhore on 2007-01-03
> **Celeborn74 said:**
> FULL ACK with jdhore. Debian has been my distribution where I learned loads from installation to configuration. For example, Debian is much more restrictive on user rights after first install, and you have to finetune a little bit to get the user rights you need. That's a big difference to Ubuntu. And you KNOW about your settings then.

Don't know Gentoo but all the compiling might be more than you would like to know...

Yeah...i tried Gentoo...it took more than twice as long to install anything (including the base system) and i really didn't feel like i was learning anything or that it was faster...if you want to get into learning how to compile and stuff, go with Debian or Ubuntu and install most of your apps from their sources (.tar.gz files)

---

### Post by Kindred on 2007-01-03
I learned a lot by using Arch, and to a lesser extent Debian (on Debian you'll still probably end up using the helper utilities and very specific ways of doing things).  For learning i'd lean toward Arch or Slackware I think.

---

### Post by earobinson on 2007-01-03
ubuntu is a good as any yet lots of people think slackware and gentoo are more "hardcore"

---

### Post by K.Mandla on 2007-01-05
I started on Ubuntu, gave Slack a very, very brief try, then moved to Arch. That taught me a lot. After that I went to Gentoo for a little while, but it wasn't nearly as gratifying as I thought it would be. Now I'm back here, and only briefly foray into other realms. :)

---

### Post by xoai on 2007-01-05
from my friend's quote
> If u learn RedHat,u learn RH. If u learn SuSE,u learn SuSE. But if u learn Slackware,u learn Linux

---

### Post by RAV TUX on 2007-01-05
KNOPPIX & Sabayon

---

### Post by manmower on 2007-01-05
+1 for Arch, sadly it's not in the poll, goes to show it is one of the lesser known distros. Arch is dead simple once you get the hang of it, yet you will be in touch with the OS on a much less abstract level than in Ubuntu. It is the distro that has kept me motivated to dig deeper so I wholeheartedly recommend it.

---

### Post by null0 on 2007-01-08
ubuntu or gentoo. 
in fact any debian-based distro will teach you a lot about linux. 
what makes the big diference is the paper. the books and tuts you read.

---

### Post by SunnyRabbiera on 2007-01-08
Most of my lessions came with Mepis linux, Mepis was easy to use for me and easy to learn.
Mepis to me is a lot better for newbies then Ubuntu or kubuntu, I personally think mepis is a great starter system.
As for other distro's I have tried most of them were soso, I like debian quite a bit as its pretty streightforward after you install it... of course the installer itself is rather hard.
I also like Sabayon, Arch, slackware and a few others but I have had mixed results.

---

### Post by grinby on 2007-01-08
Arch really helped me.  I had been using other distros successfully, but I didn't understand what I could do with linux until I installed Arch.  It actually changed the way I used other distros.

---

### Post by montgoej on 2007-01-09
If you wanna learn a lot, try Linux From Scratch.  It looks like a whole lotta work but I plan on trying it later.  Basically, you build it from the ground up. You gotta partition the drives, compile all the software, etc.  So you will learn a ton, but it will take a long time too.
~Montgoej

---

### Post by Rumor on 2007-01-09
I'll add another voice for Arch. That was the first distro to get me tinkering under the hood to learn why things work the way they work.

---

### Post by truthfatal on 2007-01-11
I vote Slackware. Because it's what I learned on :) It's definately good for learning how to manually configure programs through text files. The .conf files are usually incredibly well documented.

You won't learn SysV init, or dpkg/apt with slackware, but RPM is available if you want to learn it. You'll learn how to manually handle dependancies and how to scour the internets for obsure libraries :)

Slack is (IMO) the best distro for tweaking (I think of LFS as a book/guide, not a distro). because it doesn't hold your hand through *anything* If you wan't to compile something, you compile it. if you want to use a binary, it's probably kicking around somewhere on the internet. in rpm or tgz format (rpm2tgz is a great tool :) ) Most of Slackware's packages are installed as close to 'Vanilla' as Mr. Volkerding can get away with... no obsure patches that make generic documentation incorrect (Not unuseable, just not nessecarily what the developer of the program intended.) I could probably go on... but I won't.

---

### Post by happy-and-lost on 2007-01-17
Debian's great, I'll be returning to it once 4.0 is out (I need proper hardware support which 3.1 just doesn't offer, especially for graphics and wireless). I always use a netinstall, which installs the bare bones for you from packages fetched from the net, it's then up to you to apt-get what you want, and only what you want/need. The only frustrating bit is the fact that many of the packages you know and love in Ubuntu have slightly different names in the Deb repos, but once you've figured out that sudo won't work out of the box and that "apt-get install gnome" installs gnome+unnecessary fluff, but no Xorg, it's great fun to play with, and solid as a rock.

---

### Post by j800r on 2008-07-07
i burned a slackware install pc and tried installing it, it would freeze install when it got to a python package every time. :\ anyone know what the problem would be? I also want to largely expand my linux knowledge.

---

### Post by cardinals_fan on 2008-07-07
Slackware.  No contest.

---

### Post by ericdsr on 2008-07-10
My rather odd journey through UNIXland took the following path: Coherent UNIX, DEC Ultrix, Soft Landing Systems Linux, Slackware, Debian, Red Hat, Fedora, back to Debian and (UKX)buntu. I'd have to say Debian for the Linux OS's since I've stayed with it or a derivative the longest. Debian, et al just seem to do things *right****...***

---

### Post by VCSkier on 2008-07-11
Keep in mind that I haven't used Slackware or Linux from Scratch so the value of my opinion may be limited, but this is my impression of good learning distributions that I would recommend to someone.  I have left out ones like OpenSUSE, Gentoo, and Sabayon because I think these are better for learning purposes.  Their order is based on amount of automation so the ones to the left will generally do things for you that ones to the right would require you to do.  You can still learn from the ones to the left, but the ones to the right will force it.

MEPIS > Mint > Ubuntu > Fedora > Debian > Arch > Slackware > LFS
(feel free to correct me)

I would specifically recommend Arch, because I think it's a good balance and it's well documented; it really helps you learn.  Aside from that, I would encourage some who wants to learn to try whichever one they think best suits them.  When deciding, you need to consider your goals, the amount of time you want to commit to it, your degree of patience and diligence, and your prior experience.

---

### Post by cprofitt on 2008-07-11
Unlisted...

Arch.

---

### Post by cardinals_fan on 2008-07-11
> **PrivateVoid said:**
> Unlisted...

Arch.
I really don't get how people learn from Arch.  It's about the easiest distro I've used - just "pacman -S *appname*" to install and "pacman -Syu" to upgrade.  All dependencies are handled behind the scenes.

---

### Post by Joshuwa on 2008-07-11
There's a saying:

If you learn Red Hat, you'll know Red Hat.

If you learn Slackware, you'll know Linux.

---

### Post by perlluver on 2008-07-11
I would say Slackware, or FreeBSD.  Gentoo is just alot of compiling time.  Arch is pretty simple too.  I am in love with Slackware, so stable and very close to Unix.

---

### Post by mikjp on 2008-07-11
One can learn equally much with any distro as long as one is willing to learn and read documentation. Some distros force you to learn, some distros like Ubuntu try to make learning and studying unnecessary.

---

### Post by atomkarinca on 2008-07-11
> **cardinals_fan said:**
> I really don't get how people learn from Arch.  It's about the easiest distro I've used - just "pacman -S *appname*" to install and "pacman -Syu" to upgrade.  All dependencies are handled behind the scenes.

Since when did learning Linux become equal with compiling packages? With Arch you learn how you should work with daemons, you learn how to keep it simple (K.I.S.S.) and so on. Basically you rip what you saw. You learn those with Gentoo too, AND you have to compile your packages. I know one could say "But you can compile it for a better performance" and you work for ages to compile just for a placebo effect.

---

### Post by cardinals_fan on 2008-07-11
> **atomkarinca said:**
> Since when did learning Linux become equal with compiling packages? With Arch you learn how you should work with daemons, you learn how to keep it simple (K.I.S.S.) and so on. Basically you rip what you saw. You learn those with Gentoo too, AND you have to compile your packages. I know one could say "But you can compile it for a better performance" and you work for ages to compile just for a placebo effect.
I don't mean compiling, I mean manual dependency handling.  With Slackware, you handle package management manually and learn an enormous amount about it.

I'm not insulting Arch - it's a fabulous distro.  But I really didn't learn how to do anything when I used it.

---

### Post by SunnyRabbiera on 2008-07-11
I learned a lot from using Mepis personally,
Even though it was very easy to use and operate I still learned a lot, like basic terminal commands, how apt and repositories worked and how to use the linux OS in general...
Later I learned a few tricks on ubuntu but not as much as I did Mepis.

---

### Post by MattBD on 2008-07-12
I'm really enamoured of Sidux at the moment. Like Ubuntu, it's based on Debian, but it's somewhat closer to it than Ubuntu is. It's certainly a little bit tougher, but it's well worth a try. However, it's not as good for out of the box functionality as they have a stricter policy on including non-free drivers.

---

### Post by will1911a1 on 2008-07-12
None of those.  I learned the most from Arch.  I might try Linux from scratch to get my hands even dirtier...

---

### Post by Dr Small on 2008-07-12
> **PrivateVoid said:**
> Unlisted...

Arch.
+2 for Arch :)

---

### Post by seanc7 on 2008-07-13
Well between using Fedora at work on servers and Debian at home, I'd say I've learned a lot of Linux from both of them. Probably a slight nod to Fedora though since the servers are mainly CLI, no GUI to fall back on.

---

### Post by kk0sse54 on 2008-07-13
For me it has been Slackware which I originally planned just to test and learn linux with but it ended up replacing Ubuntu for me :-D

---

### Post by jgrabham on 2008-07-13
Add another one for Arch.

---

### Post by MisfitI38 on 2008-07-14
> **cardinals_fan said:**
> I don't mean compiling, I mean manual dependency handling.  With Slackware, you handle package management manually and learn an enormous amount about it.

I'm not insulting Arch - it's a fabulous distro.  But I really didn't learn how to do anything when I used it.
First, let me say I have the highest regard for Slack.

Perseonally, I learned the most from Arch, because it is the most comfortably laid out, and the system is installed from the ground-up.
When installing Slackware from DVD, I am left with 3+ gigs of software, including a desktop environment that is chosen for me. Using Slackware, I adopted a 'top-down' learning method; KDE is there, but in order to get to the base system, I needed to tear out what I didn't want, and then use slackbuilds to get what I needed afterward. Doing the configure, make, make install sequence taught me a little bit about how to manipulate source tarballs..but doing this every time I needed something became a chore and an exercise rather than a learning experience.

Manual dependency resolution didn't really leave me well equipped for transferring such a skillset to any other distro or OS, especially since most consider it a trivial task that a package manager should handle, and therefore, I would need to re-learn said packaging method anyway after coming from Slack.
Advantages to Slack:
It is very clean
It is very simple. 
BSD-style init. Clearly superior to the old System V.
Adding daemons to default runlevel involves simply a chmod +x of the script under /etc/rc.d/
It is rock solid.

With Arch, I get the same advantages and spend more time learning other more useful stuff, while I let pacman chase down packages.

---

### Post by cardinals_fan on 2008-07-14
> **MisfitI38 said:**
> First, let me say I have the highest regard for Slack.

Perseonally, I learned the most from Arch, because it is the most comfortably laid out, and the system is installed from the ground-up.
When installing Slackware from DVD, I am left with 3+ gigs of software, including a desktop environment that is chosen for me. Using Slackware, I adopted a 'top-down' learning method; KDE is there, but in order to get to the base system, I needed to tear out what I didn't want, and then use slackbuilds to get what I needed afterward. Doing the configure, make, make install sequence taught me a little bit about how to manipulate source tarballs..but doing this every time I needed something became a chore and an exercise rather than a learning experience.

Manual dependency resolution didn't really leave me well equipped for transferring such a skillset to any other distro or OS, especially since most consider it a trivial task that a package manager should handle, and therefore, I would need to re-learn said packaging method anyway after coming from Slack.
Advantages to Slack:
It is very clean
It is very simple. 
BSD-style init. Clearly superior to the old System V.
Adding daemons to default runlevel involves simply a chmod +x of the script under /etc/rc.d/
It is rock solid.

With Arch, I get the same advantages and spend more time learning other more useful stuff, while I let pacman chase down packages.
I just installed a minimal Slack system from CD #1 ;)

---

