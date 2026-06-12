---
title: "Ubuntu vs. Sabayon vs. Flavor of the Week."
date: 2009-06-11
forum: Recurring Discussions
---

### Post by Shibblet on 2009-06-11
I am wondering if there is a significant performance increase over Ubuntu by running Gentoo or Sabayon?

I have a friend who constantly tells me that Sabayon is SO much faster than Ubuntu.

Besides the "source" vs. "binaries" aspect, what benefits would you gain from either vs. the hindrances.

I also threw in the "flavor of the week" notion to see if someone would rather use a different distro for comparison.

---

### Post by rookcifer on 2009-06-11
> **Shibblet said:**
> I am wondering if there is a significant performance increase over Ubuntu by running Gentoo or Sabayon?

I have a friend who constantly tells me that Sabayon is SO much faster than Ubuntu.

Besides the "source" vs. "binaries" aspect, what benefits would you gain from either vs. the hindrances.

I also threw in the "flavor of the week" notion to see if someone would rather use a different distro for comparison.

Sabayon is really not based on Gentoo anymore.  They have invented their own binary package manager and it's the default.  Sure, you can use Portage if you want, but I doubt most people do, because if they did they would just use Gentoo to begin with.

If you install Gentoo from a stage3 and do an "emerge --oneshot binutils gcc virtual/libc" followed up by an "emerge -e world" then you will see some performance increase over a binary distro like Ubuntu.  

Secondly, with Gentoo you can specify which optional dependencies you want to install for each package.  With binary distros you are stuck with the deps the guy who compiled the package wanted to include.  Gentoo gives you the freedom to only include the dependencies you want or need.

So the speed benefits are two fold:

1) Compiling the system with optimized gcc flags (-march, -O2 or -O3, etc)

2) The ability to omit unneeded dependencies, thus making the system lighter.


I have always found Gentoo a bit faster than binary distros.  However, there is a trade-off; Gentoo and all its compiling takes a lot of time and the install is not for a newb.

---

### Post by Shibblet on 2009-06-11
So, when running a distro like Sabayon or Gentoo, is compiling the kernel a necessity?  In which case, don't you have to re-compile all of your programs in order to get them to run with the new kernel?

I might not understand this correctly, but if I do, it sounds like an awful lot of work.

---

### Post by rookcifer on 2009-06-12
> **Shibblet said:**
> So, when running a distro like Sabayon or Gentoo, is compiling the kernel a necessity?  In which case, don't you have to re-compile all of your programs in order to get them to run with the new kernel?

You don't have to compile the toolchain and all the low level stuff if you don't want to (that's what stage 3 tarballs are for).  All you have to compile is the kernel, the desktop environment, and the apps you put on it.  However, I always compile everything (including gcc, glibc, etc.) so I can get optimal performance from the compiler itself.

 The kernel is the easy part and doesn't take long to compile on modern hardware, especially if you strip out unneeded options from it (it takes me ~15 minutes or so on my dual-core).  The desktop environment takes quite a while (maybe 2-3 hours on a dual core).  The toolchain takes even longer.

> I might not understand this correctly, but if I do, it sounds like an awful lot of work.

It's a lot of work the first few times you do it.  I think of Gentoo like a "hell week" in military training.  Few have the endurance or will to make it through, but once you do, it's all for the better and can give you the "perfect" system.

---

### Post by spupy on 2009-06-12
In Gentoo, actually in all distros, the kernel itself doesn't take too long to compile. What takes your time is going through all the available options and carefully selecting the ones you need.
Also, the kernel has a set API which doesn't change when you recompile, so your programs will work with the new kernel.
In my opinion, what gives Gentoo more performance is not the from-source installation, but the fact that you start with an bare-bones system and add only the stuff you need. Unneeded cruft is not there to begin with.

---

### Post by tcoffeep on 2009-06-12
I've been enjoying gentoo far more than I have been enjoying any other distro I've tried. I'm quite surprised at how fun it is, and I really like portage/emerge.

---

### Post by kk0sse54 on 2009-06-12
> **Shibblet said:**
> So, when running a distro like Sabayon or Gentoo, is compiling the kernel a necessity?  In which case, don't you have to re-compile all of your programs in order to get them to run with the new kernel?

I might not understand this correctly, but if I do, it sounds like an awful lot of work.

You do not have to compile your own kernel in Gentoo, there is a generic one available during the installation process but I say if you're are going to bother with a Gentoo installation might as well go through with it completely and compile your kernel. And no you do not have to re compile all your programs whenever you compile a new kernel

---

### Post by Shibblet on 2009-06-12
So then, after "Hell Week" do you really gain a lot of performance compared to Ubuntu?

---

### Post by mdmarmer on 2009-06-12
No, there is not a great increase in performance.  I think most folks are best off with a stable distro like Mepis that is based on ease of use.  Ubuntu or Kanotix would be a second or third choice for me. If you want cutting edge try sidux or maybe Sabayon, but imho, Sabayon is usually less stable than other distros.  If you want performance you will spend a lot of time tweaking -- and it's probably easier to tweak Ubuntu or Mepis or sidux or Sabayon than it is to tweak Gentoo -- but that's why there are so many distros.

[http://sidux.com/PNphpBB2-viewtopic-t-2508.html](http://sidux.com/PNphpBB2-viewtopic-t-2508.html)

Mike

---

### Post by bodhi.zazen on 2009-06-12
> **Shibblet said:**
> I am wondering if there is a significant performance increase over Ubuntu by running Gentoo or Sabayon?

I have a friend who constantly tells me that Sabayon is SO much faster than Ubuntu.

Besides the "source" vs. "binaries" aspect, what benefits would you gain from either vs. the hindrances.

I also threw in the "flavor of the week" notion to see if someone would rather use a different distro for comparison.

"speed" is dependent on many variables including both hardware and configuration and what services you are running.

I find that there is a small performance boot in things such as file systems (ext4 vs ext3 vx XFS) and compiliing your own software.

These performance boots are modest, at best, and with anything resembling modern hardware you are unlikely to notice an effect.

You will still get the most speed boot out of hardware (faster processor, faster access time on hard drive, more ram) .

Next  comes optimizing what packages you use (gedit is faster then OOO for example) and what services are run (do you really need network manager and support for bluetooth ? ).

Last comes compiling from source and file system.

Ubuntu is designed to give new users as best an experience as possible, which means a larger kernel with additional options and additional services (such as Network Manager and Bluetooth) sometimes at the expense of speed.

You need to take these things into account.

For example, there was a recent article on Distrowatch comparing a minimal install of Xubuntu to Debian + XFCE. But what you should compare , IMO is a minimal Ubuntu install + a minimal XFCE install to minimal Debian + minimal XFCE.

You can build a minimal Ubutnu system which is nice and light and fast easier (IMHO) then gentoo. Sabayon does all the compiling for you, but updating a Sabayon install is not so easy (unless of course you do not mind downloading another 4 Gb iso and re-installing).

Last you should take any "Benchmarks" with a large grain of salt. When was the last time you created 10,000 files, renamed them, then deleted them ?

At the end of the day, keep learning and trying new things, this is what linux is all about. Freedom to customize and freedom to do as you wish.

---

### Post by Shibblet on 2009-06-12
> **bodhi.zazen said:**
> "speed" is dependent on many variables including both hardware and configuration and what services you are running.

Gotcha, that makes sense.

> **bodhi.zazen said:**
> I find that there is a small performance boot in things such as file systems (ext4 vs ext3 vx XFS) and compiliing your own software.

These performance boots are modest, at best, and with anything resembling modern hardware you are unlikely to notice an effect.

Thanks.  I wanted a "non-extreme" opinion.  People make such "extreme" statements about performance increase.

> **bodhi.zazen said:**
> Ubuntu is designed to give new users as best an experience as possible, which means a larger kernel with additional options and additional services (such as Network Manager and Bluetooth) sometimes at the expense of speed.

They say that you will learn Linux the best by accomplishing a Gentoo installation, but the Gentoo handbook is about 2 steps away from assembler.  I truly don't know if I have it in me.  ;)

> **bodhi.zazen said:**
> Last you should take any "Benchmarks" with a large grain of salt. When was the last time you created 10,000 files, renamed them, then deleted them ?

That's hilarious.  :lolflag:
About the last time I timed my boot-up!  :P

> **bodhi.zazen said:**
> At the end of the day, keep learning and trying new things, this is what linux is all about. Freedom to customize and freedom to do as you wish.

Ubuntu has been a great learning experience, in terms of being my "first" true experience into open source operating systems.  It's almost like a gateway to a different world.

The best thing about Ubuntu is that the learning curve is there if you need it.  With Gentoo, learning is part of installation.

---

### Post by Mehall on 2009-06-12
Installing Arch is a good way to learn about your system, but without it having to take overnight, and without it getting too awkward. Also, the Arch documentation is the best I have ever seen for anything, FOSS or not.

Also, Slackware is well known for getting people to learn Linux.

Few people, if I'm honest, need to know Linux like installing gentoo teaches.

Have you ever seen Linus or SABDFL use Gentoo?

---

### Post by tcoffeep on 2009-06-12
I don't use Gentoo to learn Linux. I use Gentoo because emerge is my favourite package manager, though Pacman is a damned close second, and aside from building from source, it's deliciously solid.

---

### Post by Shibblet on 2009-06-12
> **Mehall said:**
> Have you ever seen Linus or SABDFL use Gentoo?

You just blew my mind.

---

### Post by kk0sse54 on 2009-06-12
> **Shibblet said:**
> 
They say that you will learn Linux the best by accomplishing a Gentoo installation, but the Gentoo handbook is about 2 steps away from assembler.  I truly don't know if I have it in me.  ;)


The biggest problem with Gentoo is that many of the skills that you will learn are very Gentoo specific and don't necessarily reflect the standard vanilla way of doing things in linux (something more easily learned in Slackware). That being said though personally I've learned the most both from Gentoo and Slackware and both are great systems. As for the actual install I don't think it's anywhere near as bad as what most people characterize it as, as long as you are comfortable in the command line. Documentation is fantastic so as long as you follow the handbook you will be fine. Plus it's not like you would be doing a stage1 install ;). Bottom line though use what you will be comfortable with. You can learn just as much with Ubuntu as you could with one of the more "advanced distros", it just involves you actively seeking it rather than being thrust into a situation where you are forced to learn.

> 
Have you ever seen Linus or SABDFL use Gentoo? 

Have you ever seen Linus or SABDFL use Arch? Don't ever pick a distro or DE just because so and so uses it ;)

---

### Post by Mehall on 2009-06-12
> **C!oud said:**
> The biggest problem with Gentoo is that many of the skills that you will learn are very Gentoo specific and don't necessarily reflect the standard vanilla way of doing things in linux (something more easily learned in Slackware). That being said though personally I've learned the most both from Gentoo and Slackware and both are great systems. As for the actual install I don't think it's anywhere near as bad as what most people characterize it as, as long as you are comfortable in the command line. Documentation is fantastic so as long as you follow the handbook you will be fine. Plus it's not like you would be doing a stage1 install ;). Bottom line though use what you will be comfortable with. You can learn just as much with Ubuntu as you could with one of the more "advanced distros", it just involves you actively seeking it rather than being thrust into a situation where you are forced to learn.



Have you ever seen Linus or SABDFL use Arch? Don't ever pick a distro or DE just because so and so uses it ;)



True. But my point was, even those with in-depth knowledge of Linux at it's deepest level (e.g. the ones who MADE the damn thing) use OOTB distros.

I used Arch on one computer, because I was having a regression issue with the ndiswrapper in Debian/Ubuntu, and because the computer is old, and I don't need a desktop on it.

Slackware or something else would have sufficed, but I had the Arch ISO DLed already.

---

### Post by bodhi.zazen on 2009-06-12
After distro hopping for long enough you will find that, under the hood, they are all about the same.

If you can vi (vim if you prefer) and read man pages you can run any distro you wish.

---

### Post by WatchingThePain on 2009-06-12
I'd rather use Ubuntu than Sabayon (Pretentious name).

The Italians invented a 7 gear tank in WWII. First gear plus 6 speeds in reverse.

---

### Post by rookcifer on 2009-06-13
> **Mehall said:**
> Have you ever seen Linus or SABDFL use Gentoo?

Linus has actually said he doesn't like the "advanced" distros.  A quote:

> And when it comes to distributions, ease of installation has actually been one of my main issues - I'm a technical person, but I have a very specific area of interest, and I don't want to fight the rest. So the only distributions I have actively avoided are the ones that are known to be "overly technical" - like the ones that encourage you to compile your own programs etc.

Yeah, I can do it, but it kind of defeats the whole point of a distribution for me. So I like the ones that have a name of being easy to use. I've never used plain Debian, for example, but I like Ubuntu. And before Debian people attack me - yeah, I know, I know, it's supposedly much simpler and easier to install these days. But it certainly didn't use to be, so I never had any reason to go for it.

---

### Post by bodhi.zazen on 2009-06-13
I think the idea that one distro is more "advanced" then another is not a good one.

Any distro can be as "advanced" as you like and you can patch and compile the Ubuntu code if you wish.

Distros are a collection of packages (repositories) and package management tools + documentation + community.

Ubuntu strives to be easy to install. Once you learn any distro they are all fairly easy to use, it is just there is a larger initial learning curve with Arch or Gentoo.

My comments on gentoo are as above, emerge is a very nice tool, but much of gentoo sysadmin is very gentoo specific. Arch and slackware are better in this area. pacman is a very nice tool as well.

apt-get is a nice tool and can build from source as well as pacman.

I think it depends on what you want to do with your time. Do you want to compile and tweak your performance ? compile from source - go for gentoo.

Or do you want to configure a web server ? Desktop publishing ?

What Linus is saying is that he does not care to spend all his time compiling the core system.

You can learn a ton from Ubuntu, and you can start with a minimal install and build up, and you can download, patch, and compile from source if you wish. Ubuntu does not have much in the way of limitations.

---

### Post by albinootje on 2009-06-13
> **Shibblet said:**
> I am wondering if there is a significant performance increase over Ubuntu by running Gentoo or Sabayon?


I have not tried Sabayon yet, but I've used Arch Linux in the past for several months, and my Gnome desktop startup in Arch was a lot faster than in Ubuntu.

I think it has to do with Ubuntu loading all kind of extra in the "gnome session", and the desktop theme+icons, and .. Arch is build for 686.

---

### Post by WatchingThePain on 2009-06-13
Arch is very compact and fast.
The only other distro that interests me right now is Gentoo.
One guy on here said if you spend 3 days setting Gentoo up you will not be dissapointed.
Stuff has to be compiled mostly on Gentoo I gather, which seems like a good thing.

---

### Post by albinootje on 2009-06-13
> **WatchingThePain said:**
> I'd rather use Ubuntu than Sabayon (Pretentious name).


Besides Sabayon which has/had roots in Gentoo, there's also Funtoo, a pre-compiled Gentoo: [http://www.funtoo.org](http://www.funtoo.org)

---

### Post by bodhi.zazen on 2009-06-13
> **albinootje said:**
> I have not tried Sabayon yet, but I've used Arch Linux in the past for several months, and my Gnome desktop startup in Arch was a lot faster than in Ubuntu.

I think it has to do with Ubuntu loading all kind of extra in the "gnome session", and the desktop theme+icons, and .. Arch is build for 686.

Arch is available for x86_64 (started with i686, 64 bit Arch has been available for some time now, I am guessing a year or more, give or take a few months and depending if you count pre-release).

If you run live Sabayon is fine, if you install go Gentoo.

---

### Post by rookcifer on 2009-06-13
> **bodhi.zazen said:**
> I think the idea that one distro is more "advanced" then another is not a good one.

Any distro can be as "advanced" as you like and you can patch and compile the Ubuntu code if you wish.[quote]

Agreed.  As you said, all Linux distros use essentially the same toolchain, kernel, and desktop environments.  The main differences are package managers and some of the configuration options (where modules and init scripts are stored, for instance).

[quote]You can learn a ton from Ubuntu, and you can start with a minimal install and build up, and you can download, patch, and compile from source if you wish. Ubuntu does not have much in the way of limitations.

True.  But distros like Gentoo are *made* for this type of thing, thus building Gentoo from scratch is probably actually easier than Ubuntu or Fedora, etc., because Gentoo automates the whole thing through Portage.  Moreover, the support for this type of thing tends to be better with Gentoo because they *expect* a lot of people asking low-level questions.

---

