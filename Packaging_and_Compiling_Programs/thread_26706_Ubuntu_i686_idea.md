---
title: "Ubuntu i686 idea"
date: 2005-04-13
forum: Packaging and Compiling Programs
---

### Post by Molot on 2005-04-13
Umkay... I don't know where exactly post it, so sorry if it don't belong here...

Me and my friends like Ubuntu. But, comparing to Arch or Gentoo, Ubuntu is sloooow on our machines. As far as we know, it's because all packages are compiled for an i386 architecture. So we want to recompile all base packages (possibly all packages, if we will get support in calculating power).

To do it fast, we will be using Arch linux. It is based on it's own package type (a bit Slack-like), so we don't have any automats to simply manage deb packages for Ubuntu.

So, if anyone has experience in recompiling deb from source packages to binary packages on Arch (eventually Slack or sth like this...), it would be great help for us.

---

### Post by DJ_Max on 2005-04-13
Thats one of the consequences of using a pre-compiled binary Linux distro, you don't get to compile the software to your specific system. There's a program that does something similar called alien, but wouldn't depend on it. Recompiling .deb from the source, to Arch would be tricky & risky.

---

### Post by HungSquirrel on 2005-04-13
> But, comparing to Arch or Gentoo, Ubuntu is sloooow on our machines. As far as we know, it's because all packages are compiled for an i386 architecture.
You can significantly improve the speed of any distro by [prelinking](http://ubuntuforums.org/showthread.php?t=1971).

---

### Post by muzzy on 2005-04-14
[QUOTE=DJ_Max]Thats one of the consequences of using a pre-compiled binary Linux distro, you don't get to compile the software to your specific system. There's a program that does something similar called alien, but wouldn't depend on it. Recompiling .deb from the source, to Arch would be tricky & risky.[/QUOTE]
 DJ_Max, you don't understood something. We don't want to add ubuntu packages to arch. We would like to compile whole ubuntu for i686, but using machines with arch installed.
So we ask if there anybody experienced in compiling debian/ubuntu packages on diffrent distributions. Maybe some advices or sth?
And one more thing. Does anybody have scrripts or sth that were used to compile ubuntu? :D

---

### Post by pip on 2005-04-14
Ubuntu pakages are already optimized for pentium 4.
See this thread: [http://www.ubuntuforums.org/showthread.php?t=13753](http://www.ubuntuforums.org/showthread.php?t=13753)

---

### Post by muzzy on 2005-04-14
[QUOTE=pip]Ubuntu pakages are already optimized for pentium 4.
See this thread: [http://www.ubuntuforums.org/showthread.php?t=13753](http://www.ubuntuforums.org/showthread.php?t=13753)[/QUOTE]
 It's optimized for i486, but it can use pentium4. I don't have such processor and I will never buy it. I'm using AMD, so it will use only 486 instructions. We (me and molot) would like to compile it with march=i686

---

### Post by Molot on 2005-04-14
As Muzzy said, many people don't use pentium4. I'm using athlon cpu, so i486 instruction set and optimizations for pentium may result in slow work. Much, much slower than i686 instruction set {**Added: Ok, with proc-specific optimizations...**} (measured - even 10% on some tasks, usually 2-5% what make difference when compiling large parts of code et cetera). Aslo, as pentium is the default target cpu, we may recompile Ubuntu with athlon/duron as a target. **Added: All cpu'owners shoul have their chance to get perfect OS, don't they? ;)**

I don't know is there any difference for pentium between current ubuntu compilation options and i686 without cpu-specific optimizations... And I don't care, to be honest.

**Added:**
We have enought computing power to do that, so why not?
Aslo, we don't want to force i686 to be a mainstream standard...

---

### Post by Leif on 2005-04-14
To be honest with you, I'm perfectly happy with the performance of both my ubuntu machines, and I doubt that I would really feel it if I were running k7/686smp optimized everything. But I would guess that quite a few people would be interested, so would it be possible to get a community effort, using smt like distcc, to generate a variety of builds ? Or would packages built this way not be trustworthy ?

---

### Post by dusu on 2005-04-14
[QUOTE=Leif]To be honest with you, I'm perfectly happy with the performance of both my ubuntu machines, and I doubt that I would really feel it if I were running k7/686smp optimized everything. But I would guess that quite a few people would be interested, so would it be possible to get a community effort, using smt like distcc, to generate a variety of builds ? Or would packages built this way not be trustworthy ?[/QUOTE]

I think I have to diagree with you Leif.
I now use a 686 kernel, and can feel the difference with the default 386 one, on my pretty old laptop. So I guess (though I'm not sure) that using i686 compiled programs  should make some difference.

---

### Post by Astrophobos on 2005-04-14
How about apt-build ?

apt-cache show apt-build

```
Package: apt-build
Priority: optional
Section: universe/devel
Installed-Size: 160
Maintainer: Julien Danjou <acid@debian.org>
Architecture: all
Version: 0.9.16
Depends: perl, apt (>= 0.5), gcc, g++, dpkg-dev (>= 1.9), libappconfig-perl (>= 1.5), libapt-pkg-perl (>= 0.1.11), debconf, devscripts, apt-utils
Recommends: fakeroot, build-essential
Conflicts: pentium-builder
Filename: pool/universe/a/apt-build/apt-build_0.9.16_all.deb
Size: 26852
MD5sum: a174ac8badb48c9844c34502a907d014
Description: Frontend to apt to build, optimize and install packages
 This is an apt-get front-end for compiling software optimized
 for your architecture by creating a local repository with built packages.
 It can manage system upgrade too.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
```

---

### Post by Molot on 2005-04-14
[QUOTE=Leif]To be honest with you, I'm perfectly happy with the performance of both my ubuntu machines, and I doubt that I would really feel it if I were running k7/686smp optimized everything. But I would guess that quite a few people would be interested, so would it be possible to get a community effort, using smt like distcc, to generate a variety of builds ? Or would packages built this way not be trustworthy ?[/QUOTE]

Did we ask why to do it? No. Did we ask if it's needed? No. Did we asked if anyone but us wants it to be done? No. Do we want anyone to work on it? No, we wan't to do it in our free time...

We will not try to force anyone to use our work, so pleas don't you try to force us to give up ;)

Purpose of this thread was to ask people if anyone have experience in building binary packages on other distros. Anything that's not about that or other compiling / proggraming issues will not make us to look different on it. It would only make the thread longer and harder to read. (After reading this again: looks like a spam definition, don't it?)

---

### Post by Leif on 2005-04-14
[QUOTE=dusu]I think I have to diagree with you Leif.
I now use a 686 kernel, and can feel the difference with the default 386 one, on my pretty old laptop. So I guess (though I'm not sure) that using i686 compiled programs  should make some difference.[/QUOTE]

If things do work faster, I'm all for it. I already use optimized kernels, and if optimized packages existed I would use them too. What I meant was that I'm not too bothered, but if for others this is important it's a great idea, and I would happily contribute spare cpu cycles if I could. There's a similar thread to this going on though, and one objection was that this would lead to hugely increased repository sizes.

---

### Post by Molot on 2005-04-14
[QUOTE=dusu]I think I have to diagree with you Leif.
I now use a 686 kernel, and can feel the difference with the default 386 one, on my pretty old laptop. So I guess (though I'm not sure) that using i686 compiled programs  should make some difference.[/QUOTE]
 **dusu**, nice to know you're on the same side that we ;)

Aslo... We want to make it possible to use i686 packages. If anyone is happy now - great! He don't need us, but why does they wan't us not to do this?... I dunno.

**Astrophobos** - If we can transplant apt-build into Arch (most of our computing power works under Arch), we will try ;)

---

### Post by Molot on 2005-04-14
> **Leif]There's a similar thread to this going on though[/QUOTE]I've read this thread... But it was "if to do it in mainstream", and here is "we decided - we will do it. Now is about how"  said:**
> one objection was that this would lead to hugely increased repository sizes. We will be able to run our own repository.

---

### Post by Leif on 2005-04-14
[QUOTE=Molot]Did we ask why to do it? No. Did we ask if it's needed? No. Did we asked if anyone but us wants it to be done? No. Do we want anyone to work on it? No, we wan't to do it in our free time...

We will not try to force anyone to use our work, so pleas don't you try to force us to give up ;)

Purpose of this thread was to ask people if anyone have experience in building binary packages on other distros. Anything that's not about that or other compiling / proggraming issues will not make us to look different on it. It would only make the thread longer and harder to read. (After reading this again: looks like a spam definition, don't it?)[/QUOTE]

I never said anything about you giving up. Thanks for categorizing my post as spam though. I will stay out of your thread as asked.

---

### Post by dusu on 2005-04-14
[QUOTE=Molot]**dusu**, nice to know you're on the same side that we ;)

Aslo... We want to make it possible to use i686 packages. If anyone is happy now - great! He don't need us, but why does they wan't us not to do this?... I dunno.
[/QUOTE]

I dunno either, but just tell you:
Go straight on, make your dreams real ! :twisted: 
I cannot help you more than this, but I fully support you :D

---

### Post by Molot on 2005-04-16
Oki, situation has changed...

Two of our compiling mashines will work under FreeBSD...

Any advices? ;)

---

### Post by alexp on 2005-04-22
Molot (and others),

you have been pointed to the way to create optimized packages by Astrophobos -- or to be less friendly: ```
man apt-build
``` However, I am not convinced at all.



[list=1]
[*]You don't seem to have *any* proof for what you claim. Before putting such an effort into it (basically recompiling every package with higher optimizations and thoroughly testing interdependencies), I'd like to see rock-solid facts: valid benchmarks on how much performance will be gained for the amount of work required. "It feels faster" just isn't enough.
[*]You don't seem to have the faintest idea on how to do what you want. Alas, you want to build and support your own set of packages along with your own repository, all this on a non-supported architecture (FreeBSD) using cross-compilation -- if at all possible, that is. I cannot see how this is supposed to work.
[*]Being rude to other people (Leif, that is) won't help and does not add to your reputation. Also talking bullsh*t about "transplanting" apt-build to Arch tells the tale about your abilities (or the lack thereof). Granted that you don't seem to know what you are talking about, you make a lot of noise.
[/list]My advice is: Go and get a copy of Gentoo.

If you want, you can uberoptimize and customize it to fit your needs. Maintaining an optional architecture-optimized repository of packages for Ubuntu (or any other distro) is beyond your capabilities -- you even seem to be utterly unable to bring up a simple cross-compilation environment.

So stop ranting. If you have hardware to share, contact the Ubuntu devs. Maybe they need diskspace or whatever. If you want to develop (and support and maintain) packages, do so. When you have a repository up and running, come back and tell us. There will be happy testers who want to try out your shiny new packages.

Until then, please shut the f*ck up.

Regards,
Alexander

---

### Post by Molot on 2005-04-22
FreeBSD computers are only a part of computing power we have acces to. We can agree to loose it if it is not possible to use them. But it would be nice to use all we have. Running complete Ubuntu in virtual mashine (some vmware-like software) would 

man apt-build - does anyone here make apt-build works? I've tried, it doesn't work on my copy of ubuntu (different problems). Aslo, if you try to do man apt-build, you will see that in section **bugs** there is only one word: **many**!

About noise or sth - as I wroted, it's only a idea...

About "transplantation" - working on chroot from Arch is possible... Then, we don't have to have kernel image in folder we chroot to, nor many other files... just as an example. So what's your problem?

About my roodnes - this is a technical/programming forum. There already was a thread in a proper forum about need (or not) of optimizations. This one was only about some possibilities. What I think is that putting here sth like a copy of a previous thread was an unneded noise.

Hardware and internet connections I have acces to - it's something I can use, but it is all about trust - I can't grant acces to a borrowed computing power.


As you would see if you would look on a posting times, I wasn't posting from some time, I just wanted to make the job started before next post. You made me to post the answer, but that's it...

---

### Post by alexp on 2005-04-23
Molot,

[QUOTE=Molot]FreeBSD computers are only a part of computing power we have acces to. We can agree to loose it if it is not possible to use them. But it would be nice to use all we have. Running complete Ubuntu in virtual mashine (some vmware-like software) would[/QUOTE]sorry, but I can't figure out what you are trying to say. What do optimized packages for Ubuntu have to do with virtual machine software?

[QUOTE=Molot] man apt-build - does anyone here make apt-build works? I've tried, it doesn't work on my copy of ubuntu (different problems). Aslo, if you try to do man apt-build, you will see that in section **bugs** there is only one word: **many**![/QUOTE]It works perfectly for many people (including me). And the "BUGS" section of the manpage doesn't really qualify for substantial commenting. It has many bugs, so what?

[QUOTE=Molot] About noise or sth - as I wroted, it's only a idea...[/QUOTE]Yes, and that's exactly where the problem lies. Of course, you have the idea to do it, but obviously you don't seem to have any idea how to do it.

[QUOTE=Molot]About "transplantation" - working on chroot from Arch is possible... Then, we don't have to have kernel image in folder we chroot to, nor many other files... just as an example. So what's your problem?[/QUOTE] What does chroot'ing or the kernel image of your Arch installation have to do with repackaging optimized Ubuntu software?

[QUOTE=Molot] About my roodnes - this is a technical/programming forum. There already was a thread in a proper forum about need (or not) of optimizations. This one was only about some possibilities. What I think is that putting here sth like a copy of a previous thread was an unneded noise.[/QUOTE] Your whole posting is unneeded noise. You were talking about making your own optimized package set, still you are unable to compile apt-build on Arch from scratch (with a simple configure/make/make install cycle). Besides that, you haven't explained why being so keen on using Arch or FreeBSD instead of Ubuntu, which would make much more sense in terms of build management and testing.

[QUOTE=Molot] Hardware and internet connections I have acces to - it's something I can use, but it is all about trust - I can't grant acces to a borrowed computing power.[/QUOTE] That, of course, is entirely your decision.

[QUOTE=Molot] As you would see if you would look on a posting times, I wasn't posting from some time, I just wanted to make the job started before next post. You made me to post the answer, but that's it...[/QUOTE] You couldn't even come up with a roadmap what you are going to do next. I doubt that the "job" will ever start.

Besides all that, you haven't answered on any point of criticism I posted above, especially on the huge performance gains you claim to get. That and your obvious lack of understanding regarding package management allows only one conclusion: you are utterly wasting our time.

Regards,
Alexander

---

### Post by jtopping on 2005-04-24
after running gentoo, it is faster than ubuntu, but i'm back good ol ub cuz it flows so much better. in gentoo, its so fast because of the USE flags and how nothing is installed that doesnt need to be. but this makes your systems so damn unstable trying to find which use flags to set and not set to makes your normal-everyday task work and work well.

gentoo is good, i actually do like it, it just needs to have better stability in regards to mixtures of USE flags...i think vidaOS might be a good idea...but to stop myself from hijacking the thread and turning it into a binary distro vs gentoo war lets just say that ubuntu may be a lil slower, but sooo much more friendly, without turning into a windoze clone.

---

### Post by suoko on 2005-07-23
I'd like to report my experience regarding ubuntu on amd pcs.
I run ubuntu on my amd duron 800 with 384 MB of RAM (using k7 kernel, both gnome and kde desktops and enabling prelinking) and I must sadly say that it runs as fast as the Ubuntu on my PII 300Mhz with 164 MB of RAM.

I can also say that I tried Yoper on the same AMD system and noticed it's MUCH FASTER than Ubuntu.
Maybe the i686 optimization really makes the difference on amd processors...

I hope an i686 version will be provided soon.

---

### Post by LordHunter317 on 2005-07-23
[QUOTE=Molot] Ubuntu is sloooow on our machines. As far as we know, it's because all packages are compiled for an i386 architecture.[/quote]No, it isn't.  99%+ of the packages on your system get no speedup from being compiled this way.

And the few that do are compiled that way, and even installed by default.  That'd be mainly the kernel and libc6.

**You need to go read up on the basics of computer programming, software engineering, and how modern operating systems work before continuing any further on your quest.**

Really.  Because it's clear you're totally incapable of what you'd like to do, nor do you understand the postives or negatives of it.

Moreoever, building a distribution on another distribution is generally a slightly difficult and silly task.  You need the distribution you're building for package manager at least, which would mean a chroot, which would mean you'd bascially have it installed.

[quote=jtopping]. in gentoo, its so fast because of the USE flags and how nothing is installed that doesnt need to be[/quote]No, it isn't.  Code that's compiled in and isn't used isn't even ever loaded in to memory on a modern operating system.  

USE flags have no bearing on performance, >99.9% of the time.  The few cases where they do are corner, special cases.  And even then, the performance loss is insignficant and generally not mesurable.

---

### Post by Kimm on 2005-07-24
Might I suggest, that if you want your system faster, download the source for your most common applications and build them yourselfe, with the --build=i686-linux argument to configure.

if you do that to nautilus and perhaps even GTK itselfe you could probably feel a difference...

> 
No, it isn't. 99%+ of the packages on your system get no speedup from being compiled this way.


I acctually notice a majore differance in the repository Gaim and the Gaim that I compiled from source ;-)

---

### Post by LordHunter317 on 2005-07-24
[QUOTE=Kimm]I acctually notice a majore differance in the repository Gaim and the Gaim that I compiled from source ;-)[/QUOTE]Profile the two and prove it then.

It's almost certainly placebo effect.

---

### Post by wmcbrine on 2005-08-14
I concur with Lord Hunter. But if you really want an optimized Ubuntu for a modern AMD processor:

1. Buy an Athlon 64.
2. Download the AMD64 version of Ubuntu.

Voila, Ubuntu is optimized for your processor. (And this time, it really *does* give you a performance boost.)

---

### Post by npaladin2000 on 2005-08-15
[QUOTE=wmcbrine]I concur with Lord Hunter. But if you really want an optimized Ubuntu for a modern AMD processor:

1. Buy an Athlon 64.
2. Download the AMD64 version of Ubuntu.

Voila, Ubuntu is optimized for your processor. (And this time, it really *does* give you a performance boost.)[/QUOTE]

There's still missing apps for AMD64, like Flash, and I've heard libdvdcss is problematic. Still, they should be using a 32-bit K8 kernel

I'm not advocating seperate distros for i686 and K series chips mind you.  P4s need their optimizations.  But I'm not running a P4, I'm running a Pentium M (Which is a P3/P4 hybrid basically).  A lot of people are running Athlons.  One thing for Fedora installer manages to do is detect the CPU and install an appropriate kernel.  How much space would it cost to include a K7/K8-32 and an i686 kernel on the Ubuntu CD in addition to the fallback i386?  Most of the improvement comes from the kernel anyway.

---

### Post by az on 2005-08-15
[QUOTE=Leif]If things do work faster, I'm all for it. I already use optimized kernels, and if optimized packages existed I would use them too. What I meant was that I'm not too bothered, but if for others this is important it's a great idea, and I would happily contribute spare cpu cycles if I could. There's a similar thread to this going on though, and one objection was that this would lead to hugely increased repository sizes.[/QUOTE]


From what I have read, optimising the packages will provide little benefit.  Probably less than on-fifth of one percent gain in speed.

Now, running a 686 or a k-7 kernel will give you a significant gain, but that is a different story and the packages are already there.

---

### Post by asimon on 2005-08-26
For OpenSUSE there is a new project called SUPER. Aim is to get more performance into SUSE. Most of the hints there could make Ubuntu/Kubuntu faster too. (Note, they don't compile every package because it's wasted time)
[SUPER](http://opensuse.org/index.php/SUPER).

I think the first step for one who want to make Ubuntu somehow faster is to choose some benchmarks. Otherwise it's imposible to measure if what you do is reasonable or not.

---

### Post by Chris on 2005-08-28
Ah, what luck.  I was just searching for i686 build info and this thread is near the top.  ;)

Let me start off by saying that I am not one of those "uber tweaker control freak" kind of people.  I am not new to Linux and have used my Linux systems to get real work done and make real money with them for the last 10+ years and I want my system to "just work".  I hate wasting time tweaking and messing around with OS related issues.   I am a professional developer and use/abuse my systems heavily.  It is somewhat annoying, but if it can be broken I seem to have a knack of breaking it or hitting tons of shortcomings within a short period of time.  I have used and played with just about every distro there is but Debian (now Ubuntu) has been my primary distro for as long as I can remember.  This choice is based on the large number of precompiled, preconfigured packages available and the relatively basic and small base install.

Now in the application development world I have done a huge amount of benchmarking.  Various compilers, flags, systems, processors, you name it.  I can say that without question there is a fairly large performance difference between -march=i386 and -march=i686 when using GCC (version 3 or 4, doesn't matter).  No other tuning makes as much difference (outside of -O2 versus no optimization of course).  Tuning for specific CPU's is a generally waste of time and will sometimes actually produce slower code.  It depends on the application but the difference between march=i386 and march=i686 in performance critical code is usually between 40-60%.  That is not a small amount.  Of course you generally won't see that much performance boost across the whole application because there are other factors at play that are not directly CPU related (like I/O bandwidth).

However, I don't know if the Debian/Ubuntu code is actually compiled with -march=i386, or the default gcc settings (ie. no -march flag), or what.  Does anyone know?  The difference between no -march/cpu flags and -march=i686 is much smaller.  Like 10-15% difference.  If they are using -march=i386 though then there would be a substantial increase in performance by using i686.

Unfortunately I have never taken the time to benchmark a whole Linux system with the various flags set.   One day I plan to but I just have not had time and it would not be a simple task since you would need to test all sorts of things.  However, like I said I have seen real differences in the performance of my own applications when using -march=i686.  Again, most of the other tuning options beyond -Ox settings don't benefit very much (and generally -O2 is safer and not much different than anything above 2).

With that said, empirically I can feel a difference between Debian/Ubuntu and an i686 compiled distro (eg. Arch Linux or something).   Applications start faster and feel snappier when using them.  Sometimes I have a need to boot to Windows XP and I'm always surprised at how snappy and fast it feels compared to Debian/Ubuntu.  i686 distros like Arch Linux feel more like XP does.   Of course all this is not based on any hard numbers.  I'm almost positive there is a difference but I don't have numbers to back that up at this point.

So yes, I would like to see a "binary-i686" directory in with the others.  Just to reiterate, I am not talking about "uber tweaking" the system for special cases.  I am simply talking about using "-march=i686", **nothing** else extra from whatever flags are already used in Ubuntu.  I can't believe there are very many people actually using systems that would even require i386 code.  I know there are some but I don't think it is worthwhile optimizing for 1% of the population when the other 99% are being hampered.  Besides, does using -march=i686 even prevent the code from running on a 386/486/Pentium1 CPU?

---

### Post by npaladin2000 on 2005-08-29
[QUOTE=Chris]So yes, I would like to see a "binary-i686" directory in with the others.  Just to reiterate, I am not talking about "uber tweaking" the system for special cases.  I am simply talking about using "-march=i686", **nothing** else extra from whatever flags are already used in Ubuntu.  I can't believe there are very many people actually using systems that would even require i386 code.  I know there are some but I don't think it is worthwhile optimizing for 1% of the population when the other 99% are being hampered.  Besides, does using -march=i686 even prevent the code from running on a 386/486/Pentium1 CPU?[/QUOTE]

In a word, yes.   Honestly, I don't see the point of compiling  -march=i386 anymore either....if someone's using a 386 or 486 they need to be either dragged into the 21st century or shot. I'm iffy on old Pentium 1 machines...in CLI mode they might still be quite useful.   i686 cuts out the original Pentiums and Pentium MMX chips (it's for Pentium Pro and up). 

If you actually can do those benchmarks, I'd like to see differences between no -march, -march-i386, -march=i586, and -march=i686.  Going P4, K7 or all of those others would be getting way too granular (Besides, do you optimize for P4 or Athlons? What about mobile chips?  could get ugly...leave that granulatity for kernel-only optimization).

---

### Post by LordHunter317 on 2005-08-29
[QUOTE=Chris]I can say that without question there is a fairly large performance difference between -march=i386 and -march=i686 when using GCC (version 3 or 4, doesn't matter).[/quote]Yes, wonderful.  Everyone's known that for ages.

**Demonstrate it provides a user visible or otherwise meaingful speedup**  No one really cares if some function is 10, 20, 1000, etc. cycles faster on modern hardware if you're limited by something else that's much slower.

> With that said, empirically I can feel a difference between Debian/Ubuntu and an i686 compiled distro (eg. Arch Linux or something).Without numbers, it's placebo effect.  Really.  And normally, there are much larger causes than compiler flags.  Almost always.

The other issue that everyone ignores is stability: some of the CPU arch and subarch specific optimizations are simply outright *broken* and generate buggy, or unstable code.

> Besides, does using -march=i686 even prevent the code from running on a 386/486/Pentium1 CPU?It can in very rare circumstances, yes.

---

### Post by Chris on 2005-08-29
Just a couple quick points.  I believe at this point this thread as degenerated and I will not post again.  Someone will just need to go make an i686 Ubuntu distro and see how things go.  In other words prove the point by actually doing something and not just talking about it.

I'm not trying to start a flame war... Why so jumpy?  I'm sorry if my post came off as a personal insult.

[QUOTE=LordHunter317]Yes, wonderful.  Everyone's known that for ages.

**Demonstrate it provides a user visible or otherwise meaingful speedup**  No one really cares if some function is 10, 20, 1000, etc. cycles faster on modern hardware if you're limited by something else that's much slower.[/QUOTE]
Many small improvements can make for a large difference.  No?

> Without numbers, it's placebo effect.  Really.
Unless benchmarks are done it's placebo?

> And normally, there are much larger causes than compiler flags.  Almost always.
Like what?  If you know something we don't then please enlighten us because in the end I think we all just want a system that is as good as it can be.

> The other issue that everyone ignores is stability: some of the CPU arch and subarch specific optimizations are simply outright *broken* and generate buggy, or unstable code.
OK, that's what I said.   I have never seen anyone mention -march=i686 being unstable.  Again, that's the only change I was suggesting.  Otherwise you're just restating what I said.   Maybe that flag causes some problems?  Again, please let me know so everyone can benefit.

---

### Post by npaladin2000 on 2005-08-29
[QUOTE=Chris]Just a couple quick points.  I believe at this point this thread as degenerated and I will not post again.  Someone will just need to go make an i686 Ubuntu distro and see how things go.  In other words prove the point by actually doing something and not just talking about it.[/QUOTE]

Uhh, I thought you had already done some benchmarks?  You created this thread making claims; it's up to you to prove them, not others. Personally, I hope you take the time to do so because I would be very interested in seeing the results.  Maybe others don't believe that it'll make a lot of difference; they're entrenched in their lines of thought, and likely the only thing that will change their minds is hard data.  And no matter how the data works out the comparison should be interesting, and very informative (maybe it IS really time to kiss -march=i386 goodbye).

---

### Post by LordHunter317 on 2005-08-30
> **Chris]In other words prove the point by actually doing something and not just talking about it.[/quote]Or prove the idea has merit, since it rages against rather fundamental CS principals.

> Many small improvements can make for a large difference.  No?Yes, but it's not just **many** it's a huge number.

Let's assume you gain 1 us for each optimization you make.  To see a user-visible improvment, you need to make at least 100ms worth of optimization (100ms is generally the point where humans can distinguish lag in realtime, for example: if there's a 100ms delay between you and I talking on a phone, I can notice it said:**
> Unless benchmarks are done it's placebo?Seeing as most code on your system is I/O bound anyway, and usually to a rather slow device, yes.  There's just not much substantiation for it in the general case.

Moreover, for GUI applications, compiler optimizations usually won't matter at all, because programs that appear slow to the user usually have fundamental design flaws.  Typically, they're doing synchronous I/O on a single thread when they should be doing asynchronous I/O, or using multiple threads.  This causes things like the "grey window of death" when the application is really performing fine, or can't perform any faster because it's waiting on something slower, e.g., the hard disk.

And if you're waiting on the hard disk, no amount of optimization is going to save any time on that.  That's just the cold reality of hardware.

> Like what?Profiling the code and fixing slow sections?  Prelinking?

> If you know something we don't then please enlighten us because in the end I think we all just want a system that is as good as it can be.Oh, I know plently of tricks, but they require development time from the code authors, they are not stunts system administrators or packagers can pull.

Why?  Because there's very little you can do to code that's designed wrong anyway.

---

### Post by deepclutch on 2006-04-30
hmm....ubuntu ppl pls provide us i686 optimized packages,i386 ~obselete now...

---

### Post by lafrad on 2006-05-01
I can understand the argument from both sides:  the i686 people want the "latest and greatest", and the i386 folk say "If it aint broke, why fix it?"

Being new to Ubuntu, I am rather suprised that it still IS based off of i386/i486.

I installed Breezy, and got it running pretty smoothly.  It runs quite a bit smoother than Fedora Core 5 on this laptop... (but FC5 is a bloated pig...) but it is no where near as "snappy" as Fedora Core 4.  Compiling feels slower, and the little that I have done in a fresh build of WINE feels slower too.  If Wine runs noticeably slower because the kernel/wine/clib/xorg/OSS and all the rest of its dependencies don't take advantage of the advanced instructions that my Pentium 4 has, I will be back to fedora again... 10-15% in WoW is enough to make it unplayable.

I guess...  from my point of view...  why *not* go to i686? 

Why would the GNU team put that processor flag into their compiler?

Why would we *not* want to take advantage of MMX, SSE, parallel pipelines, increased registers, larger caches... ?

---

### Post by lafrad on 2006-05-01
I guess the next post that can come out of this is:

How can I build the entire ubuntu package tree from source?  Is there a guide that may at least get me started down the road of getting an i686-tree built?

---

### Post by LordHunter317 on 2006-05-01
[QUOTE=lafrad]I can understand the argument from both sides:  the i686 people want the "latest and greatest", and the i386 folk say "If it aint broke, why fix it?"[/quote]But that's not the argument.  The argument is: **it makes no difference and it can degrade the packages and create bugs, so why do it?**

> Being new to Ubuntu, I am rather suprised that it still IS based off of i386/i486.But that's not the case.  Packages that need to be optimized (e.g., kernel, libc6) are optimized.  It just so happens that's a tiny minority of software on your box.

> Compiling feels slower,Compiling, except for heavy optimization, is an I/O-bound task.  Did you time it?  If not, again, placebo.  A human mind is not an accurate measurement device.

> If Wine runs noticeably slower because the kernel/wine/clib/xorg/OSS and all the rest of its dependencies don't take advantage of the advanced instructions that my Pentium 4 has,Neither does Fedora.  i686 != P4 instruction set, since the P4 bolted on even more stuff.  And newer instructions really has nothing to do with it, believe it or not.

And ironically, if you're going to select anything less than i586, i386 is the best choice because optimized i486 code looks nothing like optimized i386/i586/i686 code.  The fastest ways to accomplish many things on those 3 CPU families are more similiar.

> I guess...  from my point of view...  why *not* go to i686? Because it introduces bugs, makes tracking certain issues harder, and yields no useful benefit.  Why introduce risk?

> Why would the GNU team put that processor flag into their compiler?Because it's useful for certain code and GCC needs to support the widest range of codebases possible.

> Why would we *not* want to take advantage of MMX, SSE,Adding -march=i686 or even -march=p4 doesn't suddenly cause the compiler to spit out MMX or SSE code.  It cannot.

> parallel pipelines, increased registers, larger caches... ?There isn't an increase in the number of registers, and you get to take advantage of the other two for free.

Again, your last several statements show you have no clue what you're talking about in the least, like several people before you in this thread.

---

### Post by ekerazha on 2006-05-06
@LordHunter317

i686 distros are MUCH faster than i386 distros (on modern hardware): *take the facts*

---

### Post by asimon on 2006-05-06
[QUOTE=ekerazha]@LordHunter317

i686 distros are MUCH faster than i386 distros (on modern hardware): *take the facts*[/QUOTE]
Fact would be a benchmark. Nothing else. And nearly all the benchmaks I saw on Gentoo Forums were usually nothing which can be called benchmark at all. It seems to some crowd performance is more an emotional thing which you "feel".

My expierience with march customized Gentoo installations are not good. There was no performance improvement on the Desktop at all. And some timings I did of a complete compilation of a cvs checkout of KDE (yes, back then KDE was still on CVS) differed between Gentoo and Ubuntu Breezy with the same gcc version at less then 1% (i.e. error in measurement). Startup times of desktop apps were usually worse with Gentoo (but never big difference). The only thing which I measured a big difference was in booting, Ubuntu booted in less then half the time then Gentoo.

The SUPER project from SUSE doesn't get much because of 686 optimization too. There is only a very small selection of packages (binutils, zlib, openssl, and some more) which they recompile at all. The big part of their performance increase they get from things like preloading, kernel scheduler patches, mounting file systems with noatime, etc. Thus I think if people feel that some "686 optimized" distro is "much" faster, it's often the result of other things, but not gcc's march option.

EDIT: Anyway, if someone can show with a clear benchmark that some Ubuntu package gets really a singnificant performance boost when recompiling with -march=686 or whatever, please file a bug report at Malone, the devs may include a new i686 package if it's worthwhile.

---

### Post by ekerazha on 2006-05-06
[QUOTE=asimon]Fact would be a benchmark. Nothing else. And nearly all the benchmaks I saw on Gentoo Forums were usually nothing which can be called benchmark at all. It seems to some crowd performance is more an emotional thing which you "feel".
[/QUOTE]
I don't need any unuseful benchmark: just use it.
An "emotional thing"? I don't think so... however, it can be what you want  it to be, maybe it's an "emotional thing" but it appears faster so it's good as it is ;)

---

### Post by asimon on 2006-05-06
[QUOTE=ekerazha]I don't need any unuseful benchmark: just use it.[/quote]
Yes, but perception can betray. Look at the startup of large applications (openoffice for example). Compare the perception of users if a splash screen is shown during startup phase and without splash screen. Users will usually perceive startup time faster because there is some action on the screen and they see that something happens, although the apps starts not faster when timed with the clock.

---

### Post by ekerazha on 2006-05-06
[QUOTE=asimon]Yes, but perception can betray. Look at the startup of large applications (openoffice for example). Compare the perception of users if a splash screen is shown during startup phase and without splash screen. Users will usually perceive startup time faster because there is some action on the screen and they see that something happens, although the apps starts not faster when timed with the clock.[/QUOTE]
I never thought an application loads faster because of the splash screen and I never had this perception. But I think and know that an i686 distro is faster than a i386 one on a >= i686 system. Most of the people I know, know and experimented this :) Are  they all dreamers?

---

### Post by LordHunter317 on 2006-05-06
[QUOTE=ekerazha]But I think and know that an i686 distro is faster than a i386 one on a >= i686 system.[/quote]If you know it is, you have benchmarks.  Where are they?

>  Most of the people I know, know and experimented this :)Then where is the data?

>  Are  they all dreamers?No, they're victims of the placebo effect.

---

### Post by ekerazha on 2006-05-07
[QUOTE=LordHunter317]If you know it is, you have benchmarks.  Where are they?

Then where is the data?
[/quote]
Again :rolleyes: No, I don't need any unuseful benchmark: *just try it*
I'm a "human being", not a stupid and unsure monkey that needs 2 tables with some numbers written on it to understand what is faster and what is slower.

> 
No, they're victims of the placebo effect.
If you like to think this way, I've no problems leaving you to think it :D

---

### Post by LordHunter317 on 2006-05-08
[QUOTE=ekerazha]Again :rolleyes: No, I don't need any unuseful benchmark:[/quote]Yes you do.  Computer performance is deterministic and obseverable.  If the gains are as large as you suggest, then simple benchmarking to verify shouldn't be difficult. 

> I'm a "human being",And measurements taken by humans, especially without a reference point are nortriously inaccurate.

> not a stupid and unsure monkey that needs 2 tables with some numbers written on it to understand what is faster and what is slower.Really?  So if I took you to the highway you could consistently, every time, tell me which car out of a pair was going faster?  I don't think so.

> If you like to think this way, I've no problems leaving you to think it :DI'm sorry you don't understand the importance of science, but that's hardly my problem.

---

### Post by ekerazha on 2006-05-09
> **LordHunter317]Yes you do.  Computer performance is deterministic and obseverable.  If the gains are as large as you suggest, then simple benchmarking to verify shouldn't be difficult.
[/quote]
I already know it is *much* faster... if you have time to lose, then "simple benchmarking" by yourself... I've not time to lose and I've many others interesting things to do  said:**
> 
And measurements taken by humans, especially without a reference point are nortriously inaccurate.

There's a little problem: I didn't take any unuseful measurement :D 

> 
Really?  So if I took you to the highway you could consistently, every time, tell me which car out of a pair was going faster?  I don't think so.

Yes, I do ;)

> 
I'm sorry you don't understand the importance of science, but that's hardly my problem.
I think you don't really know what science is ;)
If you can't understand what is slow and what is fast without "2 tables with some numbers written on it" this is only a your problem and a your limit... science hasn't many to do with your problems ;) And we aren't talking about microseconds.

---

### Post by asimon on 2006-05-09
[QUOTE=ekerazha]But I think and know that an i686 distro is faster than a i386 one on a >= i686 system.[/quote]
I pointed out above that when I compared Ubuntu Breezy with Gentoo that the Breezy was faster in some tests and Gentoo not faster in many of them.

[QUOTE=ekerazha]
Most of the people I know, know and experimented this :) Are  they all dreamers?[/QUOTE]
Why don't we get some proove in the form of benchmarks if so many people seem to "know"? Suspicious isn't it? The number of packages where we actually see worthwhile performance boosts through recompiling for i686 seems to be rather small. And most of them don't have any big impact on a desktop at all.

The topic comes up every now and then. There seem to be (many?) people who think/hope/know that an i686 Ubuntu brings, I dunno, 30% performance boost across the board. Well, these people should just start the project and do some recompiling and benchmark the results. If it's cool and fast you will earn some fame and your images will surely get downloaded by a lot of people. Somehow nobody does it, not worth anybody's time? Ha!

---

### Post by nocturn on 2006-05-09
[QUOTE=Molot]Umkay... I don't know where exactly post it, so sorry if it don't belong here...

Me and my friends like Ubuntu. But, comparing to Arch or Gentoo, Ubuntu is sloooow on our machines. As far as we know, it's because all packages are compiled for an i386 architecture. So we want to recompile all base packages (possibly all packages, if we will get support in calculating power).

To do it fast, we will be using Arch linux. It is based on it's own package type (a bit Slack-like), so we don't have any automats to simply manage deb packages for Ubuntu.

So, if anyone has experience in recompiling deb from source packages to binary packages on Arch (eventually Slack or sth like this...), it would be great help for us.[/QUOTE]

AFAIK, compiling for i386 makes little difference.  Beware that the packages are compiled with optimizations for newer pocessors as long as they do not break i386 compatibility.

Yes, Gentoo was faster, but to be fair, you also only installed programs you use, making less software running on your system (of smaller binaries because you do not compile in all possible options).

Although my Gentoo install was really fast for the hardware I had, this speed was basicly lost and even negative if you consider the constant compiling.

---

### Post by ekerazha on 2006-05-09
[QUOTE=asimon]I pointed out above that when I compared Ubuntu Breezy with Gentoo that the Breezy was faster in some tests and Gentoo not faster in many of them.


Why don't we get some proove in the form of benchmarks if so many people seem to "know"? Suspicious isn't it? The number of packages where we actually see worthwhile performance boosts through recompiling for i686 seems to be rather small. And most of them don't have any big impact on a desktop at all.

The topic comes up every now and then. There seem to be (many?) people who think/hope/know that an i686 Ubuntu brings, I dunno, 30% performance boost across the board. Well, these people should just start the project and do some recompiling and benchmark the results. If it's cool and fast you will earn some fame and your images will surely get downloaded by a lot of people. Somehow nobody does it, not worth anybody's time? Ha![/QUOTE]
I know *many* people who used Debian/Ubuntu and went to Arch ( [http://www.archlinux.org](http://www.archlinux.org) ) because they say it is much faster. They say Ubuntu is a very good distro but it is too slow ("Dapper Drake" too). Now... one of the main differences between Ubuntu and Arch is that Ubuntu is i386-compiled and Arch is i686-compiled.

:)

---

### Post by LordHunter317 on 2006-05-09
> **ekerazha]I already know it is *much* faster...[/quote]I'm not intersted in what you know, I'm interested in what you can prove.

> There's a little problem: I didn't take any unuseful measurement :D Then you don't know.  You have no proof.

> I think you don't really know what science is  said:**
> Yes, I do.  If you don't understand the importance of measurements, you have no merit to post in this thread.

[quote]If you can't understand what is slow and what is fast without "2 tables with some numbers written on it" this is only a your problemIf the difference is small, it may not be apparent to an external observer over a large enough timescale.  If you only observe two cars going 59MPH and 60MPH for 10 feet, you will have a difficult time telling the difference in speed.  Over a mile?  It will be more apparent.  Over 60 miles?   Very apparent.

[quote]And we aren't talking about microseconds.Yes, we are talking about that in 99% of cases, if that.  Why?  Applications are normally *IO-bound*.

> I know *many* people who used Debian/Ubuntu and went to Arch ( [http://www.archlinux.org](http://www.archlinux.org) ) because they say it is much fasterYes, but people like.  And people observe things that aren't true all the time.  Ever hear of fictitutious Centrifugal force?  People without a mechanics background will tell you it exists, your body feels the effects of the apparent "force", but it's not actually real.

[quote=nocturn]Yes, Gentoo was faster, but to be fair, you also only installed programs you use, making less software running on your system (of smaller binaries because you do not compile in all possible options).[/quote]No, that has almost nothing to do with it.  Code that is not actually executed is never read into RAM, unless it's on the same page with code that is.

---

### Post by ekerazha on 2006-05-09
> **LordHunter317]I'm not intersted in what you know, I'm interested in what you can prove.

Then you don't know.  You have no proof.
[/quote]
Ahah... but I'm not interested in proving anything to you, you can butt your head against a wall if you want  said:**
> 
Yes, I do.  If you don't understand the importance of measurements, you have no merit to post in this thread.

Really? I understand the importance of measurements, but I don't understand the importance of stupid and unuseful measurements... sorry :)

> 
If the difference is small, it may not be apparent to an external observer over a large enough timescale.  If you only observe two cars going 59MPH and 60MPH for 10 feet, you will have a difficult time telling the difference in speed.  Over a mile?  It will be more apparent.  Over 60 miles?   Very apparent.

Uhhh... but as I've already said, the difference isn't so small (and the timescale isn't so large).

> 
Yes, we are talking about that in 99% of cases, if that.  Why?  Applications are normally *IO-bound*.

This isn't always true (99%? You must be joking...). Look at this thread: [http://ubuntuforums.org/showthread.php?t=157560](http://ubuntuforums.org/showthread.php?t=157560)

2.6.16-ck3 Patched - 2.12 seconds
2.6.14-ck1 Patched - 4.38 seconds
2.6.12-10-k7 Unpatched - 6.08 seconds

~ 4 seconds only changing & patching the kernel. Not bad. Where's your "IO-bound"?

> 
Yes, but people like.  And people observe things that aren't true all the time.  Ever hear of fictitutious Centrifugal force?  People without a mechanics background will tell you it exists, your body feels the effects of the apparent "force", but it's not actually real.

You are making a rambling speech. This has nothing to do with our situation. Parlerei volentieri con te della forza centrifuga e del perchè l'esempio che hai fatto non ha nulla a che spartire con il discorso che stavamo facendo, ma purtroppo il mio "scarso" inglese non me lo consente.

:)

---

### Post by LordHunter317 on 2006-05-09
> **ekerazha]Ahah... but I'm not interested in proving anything to you, you can butt your head against a wall if you want  said:**
> The burden of proof is on you, not me.  You're the one suggesting/supporting the purposed changes, you have to make the case as to why it should be made.  The standard of proof is repeatable, measurable, verifiable benchmarks.  If you don't have that level of proof, you have no grounds to be making or supporting these requests.

> Really? I understand the importance of measurements, but I don't understand the importance of stupid and unuseful measurements... sorry :)You clearly have no clue what you're talking about. The differences are not major, most of the time.  And when they are, *Ubuntu already provides optimized packages.*

What part of that is hard to understand?

[quote]Uhhh... but as I've already said, the difference isn't so small (and the timescale isn't so large).Yes, it is small.  ls(1) won't see any speedups because it's dependent on your filesystem driver and your disk.  Same with cp(1).  And mv(1).  And sed(1).  And awk(1).  And grep(1).  And bash(1).  And most GUI applications.

They're dependent on things far slower than your CPU for speed.  Speeding up the code being executed helps nothing if the code is going to end up blocking for I/O anyway.

> Look at this thread: [http://ubuntuforums.org/showthread.php?t=157560](http://ubuntuforums.org/showthread.php?t=157560)

2.6.16-ck3 Patched - 2.12 seconds
2.6.14-ck1 Patched - 4.38 seconds
2.6.12-10-k7 Unpatched - 6.08 seconds

~ 4 seconds only changing & patching the kernel.Which makes it an instantenously unfair test. You can't change two variables at once and site one as helping.  This doesn't prove in any, way, shape or form that subarch improvments help *in the general case.*

>  Not bad. Where's your "IO-bound"?Did I ever say the kernel was IO-bound?  No.  I explcitly said eariler that the kernel is one of the things that benefit from architecture-specific optimizations, if you had bothered to read the thread.  This is borderline insulting because this ground was covered before and you're making it apparent you haven't entered this thread in good faith and read what transpired before you did so.  

> You are making a rambling speech. This has nothing to do with our situation.Yes, it does.  Human observations are meaningless if they're not objective and repeatable.  You've provided neither of those things.

> Parlerei volentieri con te della forza centrifuga e del perchè l'esempio che hai fatto non ha nulla a che spartire con il discorso che stavamo facendo, ma purtroppo il mio "scarso" inglese non me lo consente.I don't speak Italian, I believe, but regradless of content, I'm taking that as a personal attack.  Do it again and you will be reported for trolling, as it's against posting guidelines.

---

### Post by asimon on 2006-05-09
[QUOTE=ekerazha]
I know *many* people who used Debian/Ubuntu and went to Arch ( [http://www.archlinux.org](http://www.archlinux.org) ) because they say it is much faster. [/quote]
Assumed it is faster (which I don't know) then the gained speed is propably caused mainly by other things then compiling for i686.

[QUOTE=ekerazha]
2.6.16-ck3 Patched - 2.12 seconds
2.6.14-ck1 Patched - 4.38 seconds
2.6.12-10-k7 Unpatched - 6.08 seconds
[/quote]
As I told you there are options which are much more effective than recompiling with another march setting. But if you look at the times from Grub to working desktop which were posted at that thread too, then the apparent advantage of these patches goes towards zero.

And Ck's kernel patches don't introduce a lower latency because you compile it for i686. But in this regard it's a pointless example anyway because Debian/Ubuntu offer i686 kernels too, it's one of the very small number of packages where it makes actually sense.

[QUOTE=ekerazha]
Parlerei volentieri con te della forza centrifuga e del perchè l'esempio che hai fatto non ha nulla a che spartire con il discorso che stavamo facendo, ma purtroppo il mio "scarso" inglese non me lo consente.
[/QUOTE]
Now this is very impolite. Please stick to english here. Thanks.

---

### Post by ekerazha on 2006-05-09
> **LordHunter317]The burden of proof is on you, not me.
[/quote]
I'll reply with the same sentence: "Ahah... but I'm not interested in proving anything to you, you can butt your head against a wall if you want".  said:**
> 
You're the one suggesting/supporting the purposed changes, you have to make the case as to why it should be made.  The standard of proof is repeatable, measurable, verifiable benchmarks.  If you don't have that level of proof, you have no grounds to be making or supporting these requests.

I'm not suggesting anything. Everyone can do what he want, I've recompiled all my system through apt-build, so this thing doesn't touch me. I'm only supporting the truth. I *could* make benchmarks, but as I've already said I don't want to lose time with an annoying teenager next door :)

> 
You clearly have no clue what you're talking about. The differences are not major, most of the time.  And when they are, *Ubuntu already provides optimized packages.*

What part of that is hard to understand?

I don't understand why you deny the truth of the facts :)

> 
Yes, it is small.  ls(1) won't see any speedups because it's dependent on your filesystem driver and your disk.  Same with cp(1).  And mv(1).  And sed(1).  And awk(1).  And grep(1).  And bash(1).  And most GUI applications.

They're dependent on things far slower than your CPU for speed.  Speeding up the code being executed helps nothing if the code is going to end up blocking for I/O anyway.

Do you really use only cp, mv etc. all day long? That's obvious as they are strictly IO-related... try out applications with more complicated CPU/memory-related algorithms.

> 
Which makes it an instantenously unfair test. You can't change two variables at once and site one as helping.  This doesn't prove in any, way, shape or form that subarch improvments help *in the general case.*

This prove that one of the two things, maybe both, can help. This prove that not everything is IO-related. You seem to be very confused.

> 
Did I ever say the kernel was IO-bound?  No.  I explcitly said eariler that the kernel is one of the things that benefit from architecture-specific optimizations, if you had bothered to read the thread.

Yeah... you've said that i686 optimizations are unuseful because all (not all... 99% :D ) is "IO-bound". I'm trying to explain you this is false: and the one of the kernel is not the only situation.

> 
This is borderline insulting because this ground was covered before and you're making it apparent you haven't entered this thread in good faith and read what transpired before you did so.

You're also pretty paranoid imho. Smile, the life is good!

> 
Yes, it does.  Human observations are meaningless if they're not objective and repeatable.  You've provided neither of those things.

You are making a rambling speech. However... my observations are both objective and repeatable :)

> 
I don't speak Italian, I believe, but regradless of content, I'm taking that as a personal attack.  Do it again and you will be reported for trolling, as it's against posting guidelines.
No personal attacks. Just study Italian or use a good translator ;)

---

### Post by ekerazha on 2006-05-09
[QUOTE=asimon]Assumed it is faster (which I don't know) then the gained speed is propably caused mainly by other things then compiling for i686.


As I told you there are options which are much more effective than recompiling with another march setting. But if you look at the times from Grub to working desktop which were posted at that thread too, then the apparent advantage of these patches goes towards zero.

[...]

But in this regard it's a pointless example anyway because Debian/Ubuntu offer i686 kernels too, it's one of the very small number of packages where it makes actually sense.
[/quote]
Maybe... but with the same packages, the same kernel, the same daemons started on bootup etc.... Arch is still faster. I don't notice other differences :)

> 
And Ck's kernel patches don't introduce a lower latency because you compile it for i686.

I know. That was about the "IO-bound" thing.

> 
Now this is very impolite. Please stick to english here. Thanks.
That was about my bad English... this is why I couldn't explain it in English ;)

---

### Post by LordHunter317 on 2006-05-09
> **ekerazha]I'll reply with the same sentence: "Ahah... but I'm not interested in proving anything to you, you can butt your head against a wall if you want".  said:**
> Repeating it doesn't make it true.

> I'm not suggesting anything.Yes, you are.  You're suggesting there are speed gains to be had by compiling i686.  Don't be deliberately obtuse.

 [quote]I'm only supporting the truth. I *could* make benchmarks, but as I've already said I don't want to lose time with an annoying teenager next door :)If you're not willing to make benchmarks you're not supporting a thing.

> I don't understand why you deny the truth of the facts :)You haven't supplied any.

> Do you really use only cp, mv etc. all day long? That's obvious as they are strictly IO-related... try out applications with more complicated CPU/memory-related algorithms.Such as?  Name a few on an average desktop.  You won't find many.  Most things are not CPU-bound or remotely close to CPU-bound.

> This prove that one of the two things, maybe both, can help.Or their combination.

>  This prove that not everything is IO-related.**I never said *everything* was I/O-bound.**  Never.  ***I mentioned the kernel as an explicit exception.*** 

> Yeah... you've said that i686 optimizations are unuseful because all (not all... 99% :D ) is "IO-bound".Yes, and that is the case.

>  I'm trying to explain you this is false: and the one of the kernel is not the only situation.So what are the other cases?  libc6?  Optimized.  Video codecs?  Optimized.  Audio codecs?  Optimized.  X server drivers?  Optimized.  You've yet to shown a single case that needs to be optimized *that is not that way already.*

Most of those thing are optimized irrespective of the arch you pass to GCC, because they do the detection and work at runtime.  LAME is an example of such things.  So are the nVidia binary drivers.  So is transcode.  So is ffmpeg.   

> You are making a rambling speech. However... my observations are both objective and repeatable :)This statment is contradictory with others and your actions.

---

### Post by souki on 2006-05-09
my personal experience on recompiling on gentoo:

the only optimization usefull for me is -Os (optimize for size) for it hits the L1 and L2 cache more often

maybe this is here again a placebo effect, not only I feel a general speed improvement but also an extra battery life time
ok, I know, I have no measure

is this safe (safer than 686 optimization) ?
does someone knows any measure (speed/battery life) for this flag or this approach (more cache hits) ?

---

### Post by ekerazha on 2006-05-09
> **LordHunter317]Repeating it doesn't make it true.[/quote]
Maybe it will make you understand. Repetita iuvant.

> 
Yes, you are.  You're suggesting there are speed gains to be had by compiling i686.  Don't be deliberately obtuse.

Yeah, there are speed gains, but I'm not suggesting any change  said:**
> 
If you're not willing to make benchmarks you're not supporting a thing.

Repetita iuvant. "I *could* make benchmarks, but as I've already said I don't want to lose time with an annoying teenager next door ".

> 
You haven't supplied any.

Because you can verify these facts by yourself ;)

> 
Such as?  Name a few on an average desktop.  You won't find many.  Most things are not CPU-bound or remotely close to CPU-bound.

X.org? ;) ... others?

> 
Or their combination.

Yeah... I've said "maybe both" :D Please read carefully.

> 
**I never said *everything* was I/O-bound.**  Never.  ***I mentioned the kernel as an explicit exception.*** 

Yes, and that is the case.

You have said "99%" and that's untrue ;) I'd say at least 50%.

> 
So what are the other cases?  libc6?  Optimized.  Video codecs?  Optimized.  Audio codecs?  Optimized.  X server drivers?  Optimized.  You've yet to shown a single case that needs to be optimized *that is not that way already.*

X.org? Gnome? ... others?

> 
This statment is contradictory with others and your actions.
Reaaaally? ... ahah

---

### Post by LordHunter317 on 2006-05-09
> X.org? ;) ... others?***I mentioned X.org.  Learn to read.  Do this again and you will be reported for trolling.***

> Yeah... I've said "maybe both" :D Please read carefully.But if you know it didn't support the position in question, why did you raise it *at all*.  It's disingenious to raise data you know to be irrelevant or invalid.  You're not helping your position.

---

### Post by ekerazha on 2006-05-10
> **LordHunter317]***I mentioned X.org.  Learn to read.  Do this again and you will be reported for trolling.***
[/quote]
Wrong. You mentioned "x.org **drivers**"  said:**
> 
But if you know it didn't support the position in question, why did you raise it *at all*.  It's disingenious to raise data you know to be irrelevant or invalid.  You're not helping your position.
It supports the position that *not* the 99% of applications is IO-bound (you said this).

;)

---

### Post by LordHunter317 on 2006-05-10
> **ekerazha]Wrong. You mentioned "x.org **drivers**"  said:**
> And?  That's where all the heavy lifiting and work is done.  The rest is essentially the code that talks to the network and is network I/O bound.

[quote]It supports the position that *not* the 99% of applications is IO-bound (you said this).One application doesn't support that in the least unless there are less than 100 applications.  I think the package list for Ubuntu alone shows that's clearly not the case and that's not remotely close to it.

So no, it doesn't show anything like that.

---

### Post by ekerazha on 2006-05-10
[QUOTE=LordHunter317]And?  That's where all the heavy lifiting and work is done.  The rest is essentially the code that talks to the network and is network I/O bound.
[/quote]
It's good to optimize every aspect. 

> 
One application doesn't support that in the least unless there are less than 100 applications. 

Not really.

> 
I think the package list for Ubuntu alone shows that's clearly not the case and that's not remotely close to it.

So no, it doesn't show anything like that.
It shows that Ubuntu has optimized kernels and it could also have other optimized packages.

---

### Post by MetalMusicAddict on 2006-05-10
You guys are cute. :)

---

### Post by LordHunter317 on 2006-05-10
[QUOTE=ekerazha]It's good to optimize every aspect. [/quote]No. It isn't.  What good does it do me if it takes 1ms to process a request over the network completely and it takes 40ms for the next request to come in?  The processor will be waiting for 39ms.

Even if I could speed it 1000x, so it takes 1us, the process *will still be waiting for 39.999 ms*

Who cares?  No one.  It doesn't matter.  That extra CPU time isn't going anywhere.  

If the time was that important, you wouldn't be running Linux.  Linux isn't a hard RTOS, so it doesn't matter how fast an IO-bound process is as long as it's faster than the I/O.  It cannot matter, because Linux provides no latency guarantees.


> Not really.Yes, it does.  If you can only name one application out of 1000, then 99.9% of the system doesn't need to be optimized.  This is basic math. 

Seriosuly, stop being obtuse.  I'm treating you like an adult, you're not responding to me like one.  Do it again and you will be reported for trolling.  This is not acceptable behavior.

---

### Post by asimon on 2006-05-10
Just a remark regarding IO and optimization. Just because an app is IO-bound doesn't mean that it's pointless to optimize it. There is sometimes excessive unneeded io (for example during booting as recently investigated by a Red Hat developer), which could be eliminated. Of course it's nothing which can be done via changing some compiler flags or without deeper investigation and measurements.

---

### Post by ubuntu_demon on 2006-05-11
here's a related thread :
[http://www.ubuntuforums.org/showthread.php?t=172962](http://www.ubuntuforums.org/showthread.php?t=172962)

---

### Post by vivekR on 2006-05-14
This website has an actual benchmark comparision of Ubuntu vs Arch Linux (a 686 optimized distribution). 

The benchmark used here is not for any graphics - but there is still a difference! 

[http://www.saral-linux.com/?q=node/40](http://www.saral-linux.com/?q=node/40)

---

### Post by RAOF on 2006-05-26
[QUOTE=vivekR]This website has an actual benchmark comparision of Ubuntu vs Arch Linux (a 686 optimized distribution). 

The benchmark used here is not for any graphics - but there is still a difference! 

[http://www.saral-linux.com/?q=node/40](http://www.saral-linux.com/?q=node/40)[/QUOTE]
And if you notice, there is **no** difference (or, actually from the figures given, a **regression**) between Ubuntu-386 kernel & Ubuntu-686 kernel.  So the difference between Arch & Ubuntu speed must be more complicated than just -march=686.

Just for the record, Ubuntu pakcages (those which **aren't** specifically processor-tuned) are build **without** -march=386 and **with** -mtune=pentium4, for what it's worth.

---

### Post by ekerazha on 2006-05-26
[QUOTE=RAOF]And if you notice, there is **no** difference (or, actually from the figures given, a **regression**) between Ubuntu-386 kernel & Ubuntu-686 kernel.  So the difference between Arch & Ubuntu speed must be more complicated than just -march=686.

Just for the record, Ubuntu pakcages (those which **aren't** specifically processor-tuned) are build **without** -march=386 and **with** -mtune=pentium4, for what it's worth.[/QUOTE]

Yeah... the difference is that Arch is all i686 compiled, not only the kernel :D and -mtune=pentium4 (*if what you say is true*) doesn't optimize much for amd CPUs.

---

### Post by suoko on 2006-05-27
One easy question:

if apt-build worked, would it be difficult to do an "apt-build world" on a PIV pc to create ubuntu packages optimized for 686 and then do the same on an Athlon pc to create ubuntu packages optimized for k7 (after having set apt-build accordingly)?

One difficult question:

is there a chance to create a bittorrent-based repository for the above mentioned 686 and k7 packages so that I don't need super fast ftp servers to share them?

Gabriele

---

### Post by RAOF on 2006-05-28
[QUOTE=ekerazha]Yeah... the difference is that Arch is all i686 compiled, not only the kernel :D and -mtune=pentium4 (*if what you say is true*) doesn't optimize much for amd CPUs.[/QUOTE]
Don't take my word for it - try **apt-get source**.   The **debian/rules** file will have the compile options.

As for arch:  The Ubuntu kernel gets **slower** (in that test) going from standard to -686.  So compiling **everything** for 686 makes things somehow magically faster?  Given how many variables there are changing between Arch & Ubuntu, you really can't make any statement that "-march=686" would speed things up.

Of course, you **could** make that statement, with a bit of effort: apt-build world to build your very own Ubuntu, with the only difference being the compile options.  Run the same benchmark.  Then we can say "-march=686 provides *foo%* performance benefit".

---

### Post by vivekR on 2006-05-30
Like most benchmarks, (and statistical data) there are more than 1 way to read the results

1) We acknowledge that ArchLinux is FASTER than ubuntu for some of the very basic tasks. 
2) We say that there is NO major difference between the averge of the benchmarks tests on ubuntu386, and ubuntu686, so we shut our eyes, continue to build 386 packages, and ignore the fact that new and small distributions such as ArchLinux are getting ahead of our much hyped, agressively promoted, financially backed and much beloved Ubuntu. 

I dont understand the problem in having a 686 optimized repository, looks like most of us would like to use it, if such a thing existed. See [http://ubuntuforums.org/showthread.php?t=172962&highlight=386]("http://ubuntuforums.org/showthread.php?t=172962&highlight=386") - 82% people supported the idea of having 686 optimized packages. 

Those convinced that this doesnt bring any benefits may continue to use 386 packages like before. (but why oppose having 686 packages?)

Any Ideas/pointers on how to actually build 686 optimized packages for Ubuntu/Debian? I tried apt-build, but it didnt work for me. (no -mcpu=i686 was passed to gcc)

---

### Post by 23meg on 2006-05-30
> I dont understand the problem in having a 686 optimized repository, looks like most of us would like to use it, if such a thing existed. See [http://ubuntuforums.org/showthread.p...&highlight=386](http://ubuntuforums.org/showthread.p...&highlight=386) - 82% people supported the idea of having 686 optimized packages.This may very well mean that 82% of the people who voted weren't well informed about this matter and just swallowed the "I want to get the most out of my computer" bait presented tastily in the poll options. 

> (but why oppose having 686 packages?)Because of the weight of extra bugspotting and support it would put on the shoulders of the testers and developers which would slow down Ubuntu development and which doesn't justify the insignificiant benefits. 

You want to do this as an unofficial project, setting up repos and preparing step by step guides? Or as an Ubuntu derivative? You have your own crew and resources? Go ahead and do it. Just don't ask for it to be official.

---

### Post by vivekR on 2006-05-30
> **23meg]This may very well mean that 82% of the people who voted weren't well informed about this matter and just swallowed the "I want to get the most out of my computer" bait presented tastily in the poll options. [/QUOTE]

Yes, it may. 

Maybe, 99 of the 121 people who cared to vote for the 686 and K7 optimzed packages were the uninformed ones, and the 17 who did not need optimized packages were indeed the enlightened ones.  

Or, maybe some of them have played around with some other distributions and have experienced some good things (speed, for example) that they would also like to see in Ubuntu, and the 17 others have not had an obejective and unbiased look at some of the non-debian distributions lately.   

Maybe we should conduct a much better worded poll on this matter? (perhaps you would like it to say, "I would like to use 386 optimized code even on my latest processor, as 686 and other such optimizations do not bring any benefits?")  said:**
> 
Because of the weight of extra bugspotting and support it would put on the shoulders of the testers and developers which would slow down Ubuntu development and which doesn't justify the insignificiant benefits. 


As far as I know, we are NOT talking about having different source trees for 386 and 686 here. We are talking about having a new repository of packages with the SAME SOURCES built and optimized for 686. 

I can understand that there would be overhead involved in having new set of build scripts, and repositories. (I was told debian has build servers on which packages are created by the scripts when new sources are submitted by the maintainers?) But, I dont see why software which is functionally the same would need extra support and bugspotting. 

And I also fail to see how does this slow down ubuntu? if anything, such a step would attract some of ArchLinux and Gentoo users towards Ubuntu. You get some very keen and "performance-minded" testers. 

> 
You want to do this as an unofficial project, setting up repos and preparing step by step guides? Or as an Ubuntu derivative? You have your own crew and resources? Go ahead and do it.


Err.. I, like many people, would like to have 686 optimized packages.  There is also a launchpad project for this idea: [https://wiki.ubuntu.com/ubuntu-i686]("https://wiki.ubuntu.com/ubuntu-i686")

Best option for us -  we have Official Ubuntu repositories for this.  

2nd best option - (If Ubuntu developers are totally opposed to having such repositories).. Some of us get together, and we can create such scripts, and build + share such packages with others. We can start with a small subset of packages. 

3rd best option: Say goodbye to Ubuntu, move to Arch Linux or some such distro. 

I was trying to at least build some packages using apt-build, but have been struggling so far. (does not build with the expected compiler flags)

>  Just don't ask for it to be official.

OK sorry. My fault. I must have missed reading those sections of forum rules which forbid this. :(

---

### Post by 23meg on 2006-05-30
> **vivekR]Yes, it may. 

Maybe, 99 of the 121 people who cared to vote for the 686 and K7 optimzed packages were the uninformed ones, and the 17 who did not need optimized packages were indeed the enlightened ones.  [/quote]Right, based on what I know and the discussion at hand, that's more or less what I'm saying, though I'd rather avoid the terms "uninformed" and "enlightened".

> Maybe we should conduct a much better worded poll on this matter? (perhaps you would like it to say, "I would like to use 386 optimized code even on my latest processor, as 686 and other such optimizations do not bring any benefits?")  said:**
> You're right, that would be nice, especially with an opening post that has a benchmark comparison and some basic dumbed down computer science theory on the matter.

[QUOTE]As far as I know, we are NOT talking about having different source trees for 386 and 686 here. We are talking about having a new repository of packages with the SAME SOURCES built and optimized for 686. 

I can understand that there would be overhead involved in having new set of build scripts, and repositories. (I was told debian has build servers on which packages are created by the scripts when new sources are submitted by the maintainers?) But, I dont see why software which is functionally the same would need extra support and bugspotting. Did you actually read the poll thread? Please read again if you only scanned through it; there are some very informative posts that explain why the overhead won't justify the benefits there, as well as elsewhere on the forums where the same matter was discussed many times.

[QUOTE]And I also fail to see how does this slow down ubuntu? if anything, such a step would attract some of ArchLinux and Gentoo users towards Ubuntu. You get some very keen and "performance-minded" testers. 
What do you think slows down distros that support lots of architechtures such as Debian? Same goes here; more archs, more support load. Again refer to the poll thread for specifics which have already been covered. Agreed about testers but I don't see it as a big benefit.

> 2nd best option - (If Ubuntu developers are totally opposed to having such repositories).. Some of us get together, and we can create such scripts, and build + share such packages with others. We can start with a small subset of packages. 
I see this as your best option. Projects such as Kubuntu that are official today actually began as community efforts, and then matured to a point where they got enough interest from the official folks and became official. I say go ahead and experiment with this and report your findings in solid, measured benchmarks; if all goes as you expect, you'll get official attention. 

> OK sorry. My fault. I must have missed reading those sections of forum rules which forbid this. :(No need for drama; I'm barely stating my stance here. I feel people who want changes with possible impacts as big as this should step out and have a go at making those changes themselves to prove their point first rather than asking for top-down official development and support. You have all you need; what's holding you? Make a 686 Ubuntu derivative and distribute it, get it tested, see the reactions. Or set up some repos with 686 optimized packages that replace the 386 ones and see where you can get with that.

---

### Post by LordHunter317 on 2006-06-01
Anyone who thinks the page vivekR posted is useful is crazy.  Bad math abounds on that page (because the benchmark does it), and the data presented is inconsistent enough in behavior to be questionable.  One must question the data before drawing inferences from it, and the data presented simply does not make any sense.

---

### Post by ekerazha on 2006-06-02
[QUOTE=RAOF]
As for arch:  The Ubuntu kernel gets **slower** (in that test) going from standard to -686.  So compiling **everything** for 686 makes things somehow magically faster?  Given how many variables there are changing between Arch & Ubuntu, you really can't make any statement that "-march=686" would speed things up.
[/quote]
Maybe a 686 kernel doesn't offer much when every other thing is 386 compiled.
Maybe Ubuntu kernel isn't very optimized.

---

### Post by matt_hargett on 2006-06-10
There are definitely some apps that this can help on, including the kernel -- but it takes more than mtune/mcpu to get the maximum benefit.

First, newer instructions can help reduce the size of the binary if -Os is used instead of -O2.  (Newer kernels have an option that uses -Os instead of -O2 during compile, also.) Extra registers enabled via -mmmx and -msse can also help increase performance by avoiding pointer dereference operations. 

The biggest help (even on i386 pkgs) would be to generate a runtime profile via -fprofile-generate, enabling usage of  -freorder-blocks and -freorder-functions options.

<slightly offtopic>
None of these would make support any more difficult than it already is since the existing binary packages mostly produce useless stack traces as-is. If another repo were to be made, I would greatly prefer once that packaged more debuggable libraries. I'm not sure how they were planning to support this distro long term without this being the case.

---

### Post by vinboy on 2006-06-13
if you are going to create such a group, count me in.

I have recently installed Gentoo on my machine, guess wat? It is sleek.
Speed, responsiveness, smoothness and much more.
However I'm not comfortable with Gentoo's package management system, which is why I came back to Ubuntu. I'm currently dual-booting.

We really need to tweak up ubuntu packages, may it won't be as good as Gentoo's performance, but something close to it is good enough.

:D

---

### Post by LordHunter317 on 2006-06-13
[QUOTE=matt_hargett]First, newer instructions can help reduce the size of the binary if -Os is used instead of -O2.]/quote]Which isn't a performance benefit always.  It normally is on GCC, however.  But size vs. speed tradeoffs are usually just that on virtually all other compliers.

>  Extra registers enabled via -mmmx and -msse can also help increase performance by avoiding pointer dereference operations. This doesn't help integer code one bit, except in some situations where they can be vectorized to SSE operations.  MMX isn't interesting anymore (AMD64 doesn't even support it).

> None of these would make support any more difficult than it already is since the existing binary packages mostly produce useless stack traces as-is. Yes, they would.  Mainly because GCC is frequently a less-than-perfect compiler.

> If another repo were to be made, I would greatly prefer once that packaged more debuggable libraries.They are packaged.  Look at -dbg libraries.

---

### Post by deathbyswiftwind on 2006-06-22
I dont really think theres any good way to tell anything. You can benchmark all you want but still no matter what youll get slightly different results everytime. So many factors are involved with a computer. Heat being a major one try benchmarking when your system first boots up then try benchmarking after putting your cpu through some wear. You will notice a difference in the numbers. 

And to sum up this thread in whole it was a waste 99% of it was childish bickering. While 686 packages would be cool it wouldnt be worth it for the ubuntu devs to do it. If you want to do it on your own system or even offer it to others go ahead thats the part that makes running linux great is the sharing.

---

### Post by LordHunter317 on 2006-06-22
[QUOTE=deathbyswiftwind] You can benchmark all you want but still no matter what youll get slightly different results everytime.[/quote]Not statistical meaningful differences.

> Heat being a major one try benchmarking when your system first boots up then try benchmarking after putting your cpu through some wear. You will notice a difference in the numbers. If you see a difference in the numbers due to heat it means you're engaging thermal throttling meaning that your data is instantly invalid. So no, heat doesn't matter.

---

### Post by brandt on 2006-06-28
[QUOTE=LordHunter317]
MMX isn't interesting anymore (AMD64 doesn't even support it).[/QUOTE]

This isn't true (as far as I can tell anyway).

```

model name      : AMD Athlon(tm) 64 Processor 3400+
flags           : ... [COLOR="Red"]mmx[/COLOR] fxsr sse sse2 ...

```

Either way, I don't understand why binaries are built for i386 anyway.  Does anyone actually run a 386 anymore?  Seems like you'd be hard pressed to even find someone using a classic pentium.  Either way, _the majority_ of PC users are gonig to be running on i686 machines, so why not have packages compiled for i686 by default and offer seperate i386 packages?

---

### Post by nous on 2006-07-01
Ok, I've been watching this for a while and didn't see anybody posting *any* benchmarks, for crying out loud! So, I took the respectable dcraw.c (raw-to-png converter) and compiled it several times with different flags into separate executables. Then went to single user mode and killed all procs that resisted init. Then ran I 13MB-12MPixels raw image file from my S7000 3 times through each executable. I created a pure i386 binary, a i386 binary with sse2 support, a i686 binary, a  i386 binary with pentium 4 tuning and a pentium4 binary with sse2 support. I sent all conversion output to /dev/null to avoid disk interference and I previously cp'ed all binaries and the raw image itself to /dev/null to have'em cached. The test machine was a P4/3GHz w/ 1GB of RAM (running Gentoo). Here are the results, the deviation of times in each 3 runs were so insignificant (less than 0.01 sec) that I post only one of each.  [comments follow :) ]

# gcc -o dcraw.p4_sse2 -O3 -march=pentium4 -fomit-frame-pointer -fno-strength-reduce -msse2 -mfpmath=sse -lm -ljpeg dcraw.c
# gcc -o dcraw.i386_sse2 -O3 -march=i386 -fomit-frame-pointer -fno-strength-reduce -msse2 -mfpmath=sse -lm -ljpeg dcraw.c
# gcc -o dcraw.i386 -O3 -march=i386 -fomit-frame-pointer -fno-strength-reduce -lm -ljpeg dcraw.c
# gcc -o dcraw.i686 -O3 -march=i686 -fomit-frame-pointer -fno-strength-reduce -lm -ljpeg dcraw.c
# gcc -o dcraw.ubuntu -O3 -march=i386 -mtune=pentium4 -fomit-frame-pointer -fno-strength-reduce -lm -ljpeg dcraw.c

# time -p ./dcraw.i386 -c dscf0862.raf >/dev/null
real 10.26
user 13.34
sys 0.28
# time -p ./dcraw.ubuntu -c dscf0862.raf >/dev/null
real 10.26
user 13.34
sys 0.28
# time -p ./dcraw.i686 -c dscf0862.raf >/dev/null
real 9.57
user 12.42
sys 0.29
# time -p ./dcraw.p4_sse2 -c dscf0862.raf >/dev/null
real 7.09
user 9.15
sys 0.27
# time -p ./dcraw.i386_sse2 -c dscf0862.raf >/dev/null
real 7.28
user 9.39
sys 0.28

 Comments:
a) The huge boost comes from the sse extensions (more than 30% over pure i386 in both P4 and 386 builds)
b) The i686 binary _is_ almost 10% faster than the i386 one
c) The "i386 binary tuned to P4 arch" is a myth of ubuntuland
d) 10% faster is well perceivable in heavy GUIs and apps
e) In slower machines the speed difference is even more obvious, that's why in my desktop P3/850, XGL runs smoothly in SSE optimized Kororaa and _very_ noticeably slower in Ubuntu.

 My .02 euros.

---

### Post by ekerazha on 2006-07-04
[IMG]http://ubuntuforums.org/images/smilies/eusa_dance.gif[/IMG]

---

### Post by ubuntu_demon on 2006-07-04
Here's a relevant thread :
gen-bun-too (ubuntu + gentoo = genbuntoo)
[http://www.ubuntuforums.org/showthread.php?t=208595](http://www.ubuntuforums.org/showthread.php?t=208595)

---

### Post by brentoboy on 2006-07-04
[QUOTE=nous]
# gcc -o dcraw.p4_sse2 -O3 -march=pentium4 -fomit-frame-pointer -fno-strength-reduce -msse2 -mfpmath=sse -lm -ljpeg dcraw.c
 My .02 euros.[/QUOTE]

what happens if you use -O2 or -O1 optimization settings?
I imagine Ubuntu is compiled using -O2 because it is potentially more stable.
Does that end up making much difference?

---

### Post by brentoboy on 2006-07-04
I did some looking into SSE, and it looks like you need a pIII or newer to use it.  It's kind of a shame, the old pc's that could really use optimized execution dont have the ability to utilize many of the potential optimizations.

The only reason I even started looking into this was for an older PC I have that I want to give a boost to.  What's the point now?

---

### Post by LordHunter317 on 2006-07-04
[QUOTE=brandt]This isn't true (as far as I can tell anyway).[/quote]It is true, if you're running in 64-bit mode.  It doesn't even support x87 FPU code. 

It obviously "supports" them in 32-bit mode, because it must.  But I believe internally they're converted into SSE ops and run that way.

> Either way, I don't understand why binaries are built for i386 anyway.Because arch-specific optimizations are rarely worthwhile.

> Either way, _the majority_ of PC users are gonig to be running on i686 machines, so why not have packages compiled for i686 by default and offer seperate i386 packages?Because it complicates your work effort subtantially for no real gain by anyone.

[quote=nous]d) 10% faster is well perceivable in heavy GUIs and apps[/quote]Actually, it may not.  Most GUIs are I/O-bound.  

[quote=brentoboy]I did some looking into SSE, and it looks like you need a pIII or newer to use it. [/quote]You also need a code author who's familiar with it to get an optimal performance boost.

---

### Post by brentoboy on 2006-07-06
Honestly, all this talk about benchmarking and stuff.

Linux is fun.
To many people it is a toy.

the attraction to arch or gentoo linux is not that it might actually be faster, it is the geeky fealing that comes with thinking it probably is.  There is something to be said for feeling that you have done something that makes it better for your computer.  that feeling alone is enough to make it appeal to enough people that it would be worth wild. (in an unofficial repo of course)

---

### Post by nous on 2006-07-07
> **brentoboy said:**
> what happens if you use -O2 or -O1 optimization settings?
I imagine Ubuntu is compiled using -O2 because it is potentially more stable.
Does that end up making much difference?

 -O2 in full P4/SSE flags was 0.01-0.03 seconds slower than -O3, no big deal. It's the SSE instructions that make the difference (that's why Kororaa XGL is so much sleeker than my Ubuntu XGL setup in the same P3/850 machine).

---

### Post by Strannik on 2007-07-04
after reading this thread just wanted to add some info from myself:
i've been using ubuntu on my office computer since breezy (pentium celeron 2.4, 1 gb of ram, integrated intel graphics - nothing special) and ubuntu starts to reallly break down on the following: kde (or gnome), firefox with about 15-20 tabs open, pidgin, some windows with konqueror or nautilus, a lot of terminals (5 or 6), thunderbird,  open office. With these apps, its already a bit sluggish. After I start Eclipse, it just starts to die...
Arch on the other hand.. didn't have any trouble with running all those apps, no slowness at all (was running the ck patched kernel and kdemod).
And this is not something that only i am saying.. a lot of my friends that use linux have also switched to arch because its just faster.. you don't need any benchmarks when you have the same apps running and your system is a lot more responsive that earlier.

---

### Post by Falconix on 2007-08-22
Ubuntu in i686 build would be like heaven if it's getting fast like Arch.

But how much work is it to get the whole Ubuntu to work properly in i686 without any bugs? are there any drawback?

you are able to download the deb-src and compile it for you self if you want. Is that any routine to install Ubuntu totally from source? then it's easy to do a benchmark on Ubuntu i686 and i386.

In my point of view I'm planing to switch to Arch from Ubuntu because I want the speed in Arch, but I will still recommend Ubuntu to new users . And in a point of view of a new user which tries Ubuntu and get a feeling that Ubuntu is not fast like Windows XP could be devastating and the user could go back to Windows XP for just one reason, so that's something we need tho have in our thoughts.

So the best thing from now is to do some sort of benchmark so we can see if it's worth all work to do an Ubuntu i686 build, so if the results show us that the i686 build is so much faster I would be willing to donate my CPU cycles in some sort of distributing CPU system to re compile every package.

---

### Post by RAOF on 2007-08-22
The **apt-build** package is probably what you're after.  I think it can do something like "apt-build world".

I'd be very surprised if this ends up being more than a couple of percent speed improvement, but as far as I'm aware no-one has actually done (good) benchmarks for it.  If you do go ahead, please make sure the benchmarks are good :).  I'd be interested in the results.

---

### Post by kknd on 2007-08-26
Well... 

For the "normal" Ubuntu user, it doesn't matter, because there isn't a big difference.
Some time ago, I measured the time spent to run some math tests on different compiled systems, and the 686 optimized had 16% advantage (multiple tests were made). 

I'm using Arch Linux now, and I can feel differences in 5% of the cases, the other 95% is so much IO Bound that it doesn't matter.

A faster system would be good, but isn't so important for 99% of the cases.

---

### Post by ikster on 2007-10-05
just my 2c...

been hopping distro eversince and got stuck with ubuntu sometime ago.... why didnt i just go wit ubuntu as first try, guess just dont like the name... hehe

but ubuntu proves to be the best distro for newbies......... synaptic just works and help is just around the corner through google/ubuntu forum... ive had weird problems and a simple google search lists solutions i experienced, so ur never be left alone... cuz possible problem u might encounter could and have already/probably been solved.

just jumped ship to arch linux because i was googling for "i686 linux"..... i didnt know all the while ubuntu was i386..... my normal kde ubuntu desktop would run these ->
-compiz+emerald
-karamba
-terminal
-mozilla with usually 10 open tabs
-azureus
-kiba-dock

and things are slow like a duck walk... kiba dock system meter will be around 67% and i will start getting lagging windows, slow responses, slow keyboard typing, and just sucks....

now on arch linux with all that same thing going on... system is at 50% and no lagging, keyboard still responsive, snappy still... but loading openoffice at this stage would take about 5-7 seconds.....

if at that same stage in ubuntu, openoffice loads up in 10-15seconds and while loading many things got stuck, >sorta hang.......

so i think i386 vs i686, damn big deal of difference...

im running pentium D 2.6, 1gb ddr2, nvidia geforce mx 400....

so my cast of vote goes to yes i would love if ubuntu comes out wit i686.............

---

### Post by finzic on 2008-12-30
Hello,
I personally think the idea is just great.
I frankly do not understand why having all the code compiled for i486 these days... anyway, 
I tried ubuntu 8.10 alternate (yes, I love LVM...) on my Celeron 1100GHz (Coppermine) which is a pentium3 arch, and it's really rather slow. Compared to my other Debian or (better) gentoo system, Ubuntu is really slow. 
Nonetheless, the number of configured packages and the general ease of use is rather amazing.
So I would really love the idea of an Ubuntu i686 with the possibiliy to choose one's arch (e.g. -mpentium3), because it really boosts up performance on older boxes that would anyway be still very productive to use. 
If I may help in some way, please drop a note! :)
Cheers,
Luca.

---

### Post by thetankatlasash on 2009-01-02
While researching,testing/playing with linux... I read in a linux mag, I think it was "linux format", that had benchmarks for code that was compiled with gcc and code that was compiled with intel. I don't have a copy of this benchmark, but I think it was about ten percent faster(don't quote me, I just remember it was faster with intel).

I liked the idea of yoper, but it didn't have many developers and was buggy,there wasn't very many software to choose from.

What I liked to note, is that over the years of playing with linux, is that it's not the i386 that makes a slow distro, its the desktop ie:gnome. I remember installing mandriva on my friends new athlon barton 2500, that it was smoking fast, kde that is, and the installer was fast to. To be honest though, I don't feel like the updates to gnome or kde really make the desktop more productive. 
I really think that speed, and using standard toolkit to make use of your hardware, should be the main focus. 
 I think that freedesktop and the distro family should focus on a standard. With ubuntu so popular, lot's of software programmers, and proprietary software, all make packages that are compatible with ubuntu. And I think to myself, "maybe I should use something like emerde with ubuntu, or port click and run from linspire, or port suse toolkit (yast). And maybe the fedora boot optimizations. " Sounds like fun distro, but is it worth the effort. I mean with everyone talking about ubuntu while other distros just seem to stagnate, with their modern ideas. Like why can't ubuntu and redhat join forces? why not? because one uses rpm? Everyone talks about the linux revolution, but as they say, united we stand, divided we fall.

---

