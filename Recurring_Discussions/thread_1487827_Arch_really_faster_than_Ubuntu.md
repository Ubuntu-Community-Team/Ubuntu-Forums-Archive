---
title: "Arch really faster than Ubuntu?"
date: 2010-05-19
forum: Recurring Discussions
---

### Post by Linuxforall on 2010-05-19
Not really.

[http://www.phoronix.com/scan.php?page=article&item=ubuntu_arch_faster&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_arch_faster&num=1)

While we often hear "Arch is faster than Ubuntu" and similar statements in our forums and via email comments, this really is not the case. At least when both Arch and Ubuntu are put in as much a stock configuration as possible to reflect the "out of the box" experience encountered by most users, the numbers shown on this Intel Core 2 Duo notebook show the performance to be about the same.

---

### Post by RiceMonster on 2010-05-19
The only reason Arch would faster is because a lot of people will have less services and other things running. That, mixed with placebo.

Big deal anyway.

---

### Post by Linuxforall on 2010-05-19
> **RiceMonster said:**
> The only reason Arch would faster is because a lot of people will have less services and other things running. That, mixed with placebo.

Big deal anyway.

Agreed with the Placebo part, actually they go through such pains installing Arch that its their belief that its gotta be fast, same with Gentoo which was tested as well sometimes earlier and it really didn't set Ubuntu on fire.

---

### Post by philinux on 2010-05-19
Moved to recurring discussions.

---

### Post by ophthop on 2010-05-19
It is indeed slightly faster, according to what's written in the article and the benchmarks. Still Difference is not wide enough to justify a change.

---

### Post by andamaru on 2010-05-19
Arch is optimized for i686 architectures so it will be faster than  Ubuntu(assuming Ubuntu isn't using i686) on newer CPU. Because of the nature of Arch Linux the average user of the distribution is only going to have the services and applications they want running in the background, this will also speed up the distribution.

In conclusion, If you were to go and install Arch Linux it would be faster than Ubuntu is. How much faster or if it will be noticeable is another question.

---

### Post by Penguin Guy on 2010-05-19
> **Linuxforall said:**
> Agreed with the Placebo part, actually they go through such pains installing Arch that its their belief that its gotta be fast,
[QUOTE="'So Long and Thanks for All the Fish'"]It is very easy to be blinded to the essential uselessness of it by the sense of achievement you get from getting it to work at all.[/QUOTE]
Although I think the belief that Arch Linux is faster is partly preconception, I think it also has to do with the kind of 'hardcore' system configuration that Arch Linux is all about. Try testing an Arch user's system after the said Arch user has done all their configuration and tweaking stuff - I expect it'll be noticeably faster.

---

### Post by Linuxforall on 2010-05-19
Except for situations where composting manager was involved, its not even slightly faster in any of the tests, nothing conclusive at all. Both distros were used stock, no tweaks were done.

All services can be easily tweaked on Ubuntu as well and then a personal kernel compiled, so just like you can tweak Arch, you can tweak Ubuntu or for that matter any linux distro. The real darkhorse of speed distro is sidux and it would be an interesting test indeed when Ubuntu is pitched against it.

---

### Post by Dharmachakra on 2010-05-19
Hmm... 99% of Phoronix is bullshit, but this may be part of the 1% that isn't.

---

### Post by Simian Man on 2010-05-19
Linux is Linux is Linux.  The upstream sources are largely the same between different distros.  So why would one be significantly faster than another?  Magic?

> **andamaru said:**
> Arch is optimized for i686 architectures so it will be faster than  Ubuntu(assuming Ubuntu isn't using i686) on newer CPU.
That only holds if you use 32-bit Linux.  Anyone who cares that much about performance is likely using 64-bit Linux anyway.

> **Dharmachakra said:**
> Hmm... 99% of Phoronix is bullshit, but this may be part of the 1% that isn't.

Agreed.

---

### Post by andamaru on 2010-05-19
> **Simian Man said:**
> Linux is Linux is Linux.  The upstream sources are largely the same between different distros.  So why would one be significantly faster than another?  Magic?


That only holds if you use 32-bit Linux.  Anyone who cares that much about performance is likely using 64-bit Linux anyway.



Agreed.

I can't believe I didn't of think that, I really should be moving 64-bit myself.

---

### Post by snowpine on 2010-05-19
Arch can be slower than Ubuntu, if you set it up that way. :)

I always thought the main "advantages" of Arch were its minimal install process, excellent DIY documentation, and rolling release of new applications. 

Arch is only "fast" if that is your goal and you set it up that way.

---

### Post by Tibuda on 2010-05-19
I have used both and I think both can be as fast as you want (considering from a minimal ubuntu install). Arch still wins me because of the rolling release system.

---

### Post by Linuxforall on 2010-05-19
> **danielrmt said:**
> I have used both and I think both can be as fast as you want (considering from a minimal ubuntu install). Arch still wins me because of the rolling release system.

Since you like rolling release, you might be interested in sidux as well.

---

### Post by snowpine on 2010-05-19
> **Linuxforall said:**
> Since you like rolling release, you might be interested in sidux as well.

Arch and sidux are really two opposite sides of the "rolling release" coin, in my experience. 

sidux is a fringe use case of the vast Debian project, whose main focus is cranking out an extremely stable release every couple of years. While sidux is often called "rolling release" it is subject to ebbs and flows in development based on the Debian Stable release cycle ("soft freeze"). sidux is KDE-centric and is released as a Live CD with a speedy graphical installer. 

Arch has no time-based releases; the entire and sole focus of the project is to create a "pure" rolling release. It is desktop-agnostic and is typically installed from a minimal netinstall, with the end user determining exactly what form the finished system will take. The apps tend to be a little newer than in sidux, too, the "nonfree" stuff is trivially easy to install, and the community is generally more tolerant of experimentation beyond the approved methods.

So, while sidux and Arch are two of the best rolling release distros, I would say the similarity ends there. If you want to spend an afternoon molding your own ideal system, Arch is for you; if you want a speedy KDE desktop in less than 20 minutes, you can't beat sidux. I have had very positive experiences with each of them and nothing but respect for both projects. :)

---

### Post by cariboo on 2010-05-19
> **andamaru said:**
> Arch is optimized for i686 architectures so it will be faster than  Ubuntu(assuming Ubuntu isn't using i686) on newer CPU. Because of the nature of Arch Linux the average user of the distribution is only going to have the services and applications they want running in the background, this will also speed up the distribution.

In conclusion, If you were to go and install Arch Linux it would be faster than Ubuntu is. How much faster or if it will be noticeable is another question.

```
Linux redstone 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 **i686** GNU/Linux
```

This on my Compaq Mini 110, with atom n270 cpu.

From my experience on older hardware, There really isn't that much difference between an Arch install and a minimal Ubuntu install, not enough to be noticeable.

---

### Post by Tibuda on 2010-05-19
> **Linuxforall said:**
> Since you like rolling release, you might be interested in sidux as well.

I have already tried it (the XFCE edition), but I still prefer Arch. :) To each their own...

---

### Post by del_diablo on 2010-05-19
They did not measure boot time, ergo the main difference is gone :/

---

### Post by Shining Arcanine on 2010-05-19
> **Linuxforall said:**
> Agreed with the Placebo part, actually they go through such pains installing Arch that its their belief that its gotta be fast, same with Gentoo which was tested as well sometimes earlier and it really didn't set Ubuntu on fire.

If you are referring to the Linux Magazine tests, the tests were flawed. Everyone on the Gentoo forums that examined the benchmarks disagreed with the testing methodology employed, which involved a system that was in a configuration that Gentoo users never use.

The main speed benefits from Gentoo are the following, ordered from relatively most important to relatively least important:

[LIST=1]
[*]A minimal installation.
[*]USE Flags, which allow unneeded program features to be stripped from the compiled binaries.
[*]Optimized kernels, which typically contain both kernel and rcu preemption support, which are needed for smooth desktop environments.
[*]Optimized compiler flags, which further trim binary sizes and improve execution speeds.
[/LIST]

Ubuntu on the other hand has a kitchen sink approach to installations and program features, so it has tons of background services that are unnecessary, bloated binaries that contain features that are never used and generic optimizations that were intended for the original Pentium processor.

There is a huge difference between Ubuntu and Gentoo Linux in the areas that matter, predominantly system boot times, application load times, and overall system responsiveness.

> **danielrmt said:**
> I have used both and I think both can be as fast as you want (considering from a minimal ubuntu install). Arch still wins me because of the rolling release system.

Have you tried Gentoo Linux? It has a rolling release system too and is a bit better at handling library upgrades that break API compatibility because of its source based approach to installation. When an upgrade (e.g. icu 4.2 to 4.4) breaks software, you can just run revdep-rebuild and Gentoo's package manager will automatically detect and recompile all of the affected software.

---

### Post by Shining Arcanine on 2010-05-19
> **cariboo907 said:**
> ```
Linux redstone 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 **i686** GNU/Linux
```

This on my Compaq Mini 110, with atom n270 cpu.

From my experience on older hardware, There really isn't that much difference between an Arch install and a minimal Ubuntu install, not enough to be noticeable.
While I know that you are talking about Arch, I think that there are merits to distributions that strive for efficiency. Gentoo being one of them, despite its real focus being on customizability, tends to be faster than Ubuntu. If you think otherwise, tell that to the guy who posted the following thread on the Gentoo forums:

[http://forums.gentoo.org/viewtopic-t-828094-highlight-.html](http://forums.gentoo.org/viewtopic-t-828094-highlight-.html)

Ubuntu has a great deal of bloat and according to him (in [another post]("http://forums.gentoo.org/viewtopic-p-6284135-highlight-.html#6284135") he made at the Gentoo forums), switching from Ubuntu to Gentoo reduced his system's memory usage from 400MB to 200MB during a typical session and that is with the same applications in use.

Ubuntu has a ton of unnecessary software features built into it by its package managers on the off-chance that some person might need it, on top of generic code optimizations that are intended for the original Pentium. The result is that many binaries are bloated with both unnecessary code and duplicated code that allows various processors to have "optimized codepaths".

The lower memory footprint that Gentoo Linux has translates into more available memory available for use as cache by the kernel, which results in a more responsive system. There is no getting around that.


By the way, here is the output of uname -a for my laptop, with its actual name replaced with the term "Laptop" for privacy purposes:

> $ uname -a
Linux Laptop 2.6.34 #1 **SMP PREEMPT** Tue May 18 09:57:44 EST 2010 i686 Genuine Intel(R) CPU T2400 @ 1.83GHz GenuineIntel GNU/Linux

Notice it uses a non-generic SMP PREEMPT kernel, which is something that is not available on Ubuntu and also something that as far as I know, is not available on Arch as well.

---

### Post by chessnerd on 2010-05-19
The people I know who use Arch generally install Openbox as their window manager/desktop environment, so that would also help with performance.

I can't say anything about the majority of Arch users, as I've never been to the Arch Forums or read any usage info, but I'm guessing that most Arch users install Openbox, Fluxbox, LXDE, or some other light-weight WM/DE. This could improve performance over Gnome in graphical areas as well.

However, I am glad to see that the Ubuntu team has done a good job of keeping performance in Ubuntu solid and look forward to see what improvements are made in 10.10.

---

### Post by Shining Arcanine on 2010-05-19
> **chessnerd said:**
> The people I know who use Arch generally install Openbox as their window manager/desktop environment, so that would also help with performance.

I can't say anything about the majority of Arch users, as I've never been to the Arch Forums or read any usage info, but I'm guessing that most Arch users install Openbox, Fluxbox, LXDE, or some other light-weight WM/DE. This could improve performance over Gnome in graphical areas as well.

However, I am glad to see that the Ubuntu team has done a good job of keeping performance in Ubuntu solid and look forward to see what improvements are made in 10.10.

They could do more. Enabling kernel preemption, enabling rcu preemption, switching to a 1000Hz clock and using dynamic ticks in the kernels they distribute with their desktop CDs would help tremendously. The current situation where that is not done is making Linux look bad by having Ubuntu perform poorly in graphical benchmarks. I am planning to file a blue print proposing it soon because even though I do not use Ubuntu Linux, it affects me too because Phoronix is making Ubuntu appear to be representative of Linux performance, even though it is not.

---

### Post by chessnerd on 2010-05-19
> **Shining Arcanine said:**
> They could do more. Enabling kernel preemption, enabling rcu preemption, switching to a 1000Hz clock and using dynamic ticks in the kernels they distribute with their desktop CDs would help tremendously. The current situation where that is not done is making Linux look bad by having Ubuntu perform poorly in graphical benchmarks. I am planning to file a blue print proposing it soon because even though I do not use Ubuntu Linux, it affects me too because Phoronix is making Ubuntu appear to be representative of Linux performance, even though it is not.

I know little about the core elements of Linux performance, but I can say this: on the desktop, Ubuntu represents all of Linux.

Ubuntu makes up nearly 60% of all desktop installs, so Ubuntu's performance impacts the entire market. (Additionally, Ubuntu's many derivatives, like Mint and Crunchbang, make up another sizable part of the market)

So, any improvement in Ubuntu's performance would be felt on almost all Linux desktops. Do not hesitate to propose any ideas you have, even if you don't use Ubuntu. If they are accepted it will be felt everywhere.

---

### Post by Tibuda on 2010-05-19
> **Shining Arcanine said:**
> Have you tried Gentoo Linux? It has a rolling release system too and is a bit better at handling library upgrades that break API compatibility because of its source based approach to installation. When an upgrade (e.g. icu 4.2 to 4.4) breaks software, you can just run revdep-rebuild and Gentoo's package manager will automatically detect and recompile all of the affected software.

No thanks, I like pre-compiled binary packages.

---

### Post by Shining Arcanine on 2010-05-19
> **chessnerd said:**
> I know little about the core elements of Linux performance, but I can say this: on the desktop, Ubuntu represents all of Linux.

Ubuntu makes up nearly 60% of all desktop installs, so Ubuntu's performance impacts the entire market. (Additionally, Ubuntu's many derivatives, like Mint and Crunchbang, make up another sizable part of the market)

So, any improvement in Ubuntu's performance would be felt on almost all Linux desktops. Do not hesitate to propose any ideas you have, even if you don't use Ubuntu. If they are accepted it will be felt everywhere.

Ubuntu does not represent all of Linux, but ever since Dell started selling systems with Ubuntu preinstalled, many people seem to be inclined to believe that.

Anyway, I have been busy filing bug reports related to either Gentoo Linux or software that I use on Gentoo Linux. While I think I have nailed all of them down (excluding some issues with KNetworkManager that need to go to upstream), I have a headache at the moment, so I will get around to proposing that desktop centric features of the Linux kernel be enabled by default on Ubuntu desktop installations when it subsides.

---

### Post by Shining Arcanine on 2010-05-19
> **danielrmt said:**
> No thanks, I like pre-compiled binary packages.

Then you might like Sabayon Linux:

[http://www.sabayon.org/](http://www.sabayon.org/)

It is Gentoo Linux based, but uses binary packages, so it delivers the best of both worlds.

---

### Post by MisfitI38 on 2010-05-19
> **Shining Arcanine said:**
> ...Have you tried Gentoo Linux? It has a rolling release system too and is a bit better at handling library upgrades that break API compatibility because of its source based approach to installation. When an upgrade (e.g. icu 4.2 to 4.4) breaks software, you can just run revdep-rebuild and Gentoo's package manager will automatically detect and recompile all of the affected software.

You have posted such nonsense many times before. Repetitions do not make truths out of non-truths.

The only way an Arch system would break library version matching is if a user was blatantly careless enough to selectively install packages after synching his package database, while simultaneously neglecting to perform a system-wide upgrade. Even if such a blunder was committed, a simple pacman -Syu would fix it (in a matter of seconds with a broadband connection).

PEBKAC is universal, please don't use twisted 'logic' to prove fanboi points concerning your distro of choice.

BTW, Arch has a ports system if one wanted to waste some time rebuilding 'affected' packages.

---

### Post by Shining Arcanine on 2010-05-20
> **MisfitI38 said:**
> You have posted such nonsense many times before. Repetitions do not make truths out of non-truths.

The only way an Arch system would break library version matching is if a user was blatantly careless enough to selectively install packages after synching his package database, while simultaneously neglecting to perform a system-wide upgrade. Even if such a blunder was committed, a simple pacman -Syu would fix it (in a matter of seconds with a broadband connection).

PEBKAC is universal, please don't use twisted 'logic' to prove fanboi points concerning your distro of choice.

BTW, Arch has a ports system if one wanted to waste some time rebuilding 'affected' packages.

The icu 4.4 upgrade was difficult for arch. There is a bug report regarding it:

[http://bugs.archlinux.org/task/19049](http://bugs.archlinux.org/task/19049)

It was an issue on Gentoo too, but on Gentoo, there was revdep-rebuild available to fix it. While you can compile stuff on Arch, or any other Linux system with the proper tools installed, I do not believe that Arch has tool that can detect the broken packages and instruct the package manager to rebuild them.

Since building packages is a secondary function for Arch's package manager, a tool to automate detection of broken packages and rebuild them is not something that anyone would expect it to have. Trying to substitute Arch Linux's ability to rebuild packages that you manually specify for a tool that automates the process of finding packages that are broken and recompiling it for you is blatant fanboyism and it does not help anyone.

---

### Post by MisfitI38 on 2010-05-20
> **Shining Arcanine said:**
> The icu 4.4 upgrade was difficult for arch. There is a bug report regarding it:

[http://bugs.archlinux.org/task/19049](http://bugs.archlinux.org/task/19049)


Trivial. 1 affected package, fixable using ABS with a simple version bump in a PKGBUILD.

---

### Post by Shining Arcanine on 2010-05-20
> **MisfitI38 said:**
> Trivial. 1 affected package, fixable using ABS with a simple version bump in a PKGBUILD.

The only major (and obvious) package was Open Office, but there were other packages affected by it as well. On Gentoo, revdep-rebuild was able to identify all of these and recompile them.

---

### Post by Shazzam6999 on 2010-05-21
I think the difference between Arch, Gentoo, and Ubuntu truly shines on computers lacking in power. On my quad core/8g RAM/5870 I notice very little difference. On my laptop with a 1.6ghz single core/1g RAM/x1300 the difference is pretty visible when using GNOME. That said, on my laptop I use Openbox and I'm pretty sure Arch + Openbox will fly on anything.

---

### Post by Linuxforall on 2010-05-21
So will Ubuntu minimal install or Lubuntu.

---

### Post by Shazzam6999 on 2010-05-21
Well to quote you, "reflect the "out of the box" experience encountered by most users". I hardly think the Ubuntu minimal install reflects "the 'out of box' experience encountered by most users"; Lubuntu is not an officially supported Ubuntu spinoff and it is a different DE; whereas I'm referring to my experience solely with the GNOME desktop. If you take any distro and uninstall every unneccesary component then it will clearly run faster; however, some distros are created in such a way that makes them more convenient to create an efficient setup. Ubuntu is created with the kitchen sink philosophy, whereas, Arch is created with the KISS philosophy. You could install Ubuntu, wipe all the unneccesary components and then have it run faster than Arch; or, you could simply install Arch. At their cores most distros are essentially the same, in my opinion: the only difference really is personal preference. Which is why I'll sit here all night and estole the virtues of Gentoo and Arch, while you will estole the wonders of Ubuntu.

If we want to get into specifics as well, test APT vs PacMan. PacMan is visibly quicker than APT. I get a giggle everytime I think of Portage and emerge in this test though.

---

### Post by ubun2warrior on 2010-05-21
ubuntu works quiet fast on most machines but on older machines it is a bit slow. Even though if someone puts up some tips on tweaking ubuntu so that it runs faster can be of great help. you know stopping some unwanted services,etc

---

### Post by Linuxforall on 2010-05-22
What did this test prove once for all, both stock installs and Arch didn't really do that fast over Ubuntu, now if you tweak Arch, it will get faster and same goes for Ubuntu, question is not tweaking, question is stock comparisons here which would be the norm in most cases. As for apt versus pacman, apt is quite fast in cli and there is no conclusive evidence otherwise of pacman setting apt on fire with its speed.

---

### Post by Shining Arcanine on 2010-05-22
> **Linuxforall said:**
> So will Ubuntu minimal install or Lubuntu.

As far as I know, Arch Linux is a minimal installation from the start and you can run LDXE on it too and get the boost that comes from running Arch in adddition to the boost you get from running LDXE in place of GNOME. There will be some overlap, but Arch Linux will still be faster than Ubuntu Linux.

By the way, as far as the jargon is concerned, Lubuntu is not Ubuntu, so you cannot use LXDE (or any other desktop environment) to speed up Ubuntu. Apparently, Ubuntu is only Ubuntu if it is running either GNOME or no desktop environment. :/

> **Linuxforall said:**
> What did this test prove once for all, both stock installs and Arch didn't really do that fast over Ubuntu, now if you tweak Arch, it will get faster and same goes for Ubuntu, question is not tweaking, question is stock comparisons here which would be the norm in most cases. As for apt versus pacman, apt is quite fast in cli and there is no conclusive evidence otherwise of pacman setting apt on fire with its speed.

I understand that Arch Linux is meant to be tweaked, while Ubuntu Linux tries its best to avoid user attempts at tweaking. Saying you can tweak Ubuntu Linux too really is not a fair comparison, as people on these forums would likely tell you to leave the configuration files alone and only touch the GUI configuration dialogs while with Arch Linux, people on their forums will likely tell you to use a terminal and edit the actual files.

---

### Post by Linuxforall on 2010-05-22
Ubuntu Linux can be tweaked as much as one wants, there is not such prevention by design, however in terms of convenience, Ubuntu comes with most settings by default. CLI can be used with same effect as it can be used on other distros, again there is no such lock by design.

As for speed boost, at the cost of sounding redundant, the test and my own personal install of both distros have proved conclusively that there little if any to be had with an Arch install over Ubuntu.

---

### Post by snowpine on 2010-05-22
I found Arch very fast when I used it. The Arch + Gnome interface felt as "snappy" as the Ubuntu + Openbox I was switching from. Unfortunately I found it a bit "crashy" so overall it was a time waster, not a time saver for me. (And I fully blame myself, not Arch itself, for the crashes... we all know that problems with Arch are always the user's fault!) I think if Phoronix had included the time required to install, tweak, and administer the system in their equation, Ubuntu would have been the clear winner. :)

---

### Post by MisfitI38 on 2010-05-22
> **Shining Arcanine said:**
> The only major (and obvious) package was Open Office, but there were other packages affected by it as well. On Gentoo, revdep-rebuild was able to identify all of these and recompile them.
*sigh* revdep-rebuild is a tool which was implemented to address a *common issue inherent to source-based systems.*
It is *extremely* rare on a binary system to have a library version mismatch. Further, it is trivial to fix with ABS, as I indicated countless times before.
If one package is affected, rebuild it against the library, or downgrade it. 
If multiple packages are affected, rebuild or downgrade the library as necessary.

---

### Post by Shining Arcanine on 2010-05-22
> **Linuxforall said:**
> Ubuntu Linux can be tweaked as much as one wants, there is not such prevention by design, however in terms of convenience, Ubuntu comes with most settings by default. CLI can be used with same effect as it can be used on other distros, again there is no such lock by design.

As for speed boost, at the cost of sounding redundant, the test and my own personal install of both distros have proved conclusively that there little if any to be had with an Arch install over Ubuntu.

The fact that it can be does not mean that it is encouraged. Ubuntu tries it best to keep people out of the terminal. Post a thread here asking for advice on how to compile your own kernel in a manner compatible with Ubuntu's package manager citing that you like designing the .config file to best suit your hardware and usage patterns as the reason and people will likely deride you for it.

> **MisfitI38 said:**
> *sigh* revdep-rebuild is a tool which was implemented to address a *common issue inherent to source-based systems.*
It is *extremely* rare on a binary system to have a library version mismatch. Further, it is trivial to fix with ABS, as I indicated countless times before.
If one package is affected, rebuild it against the library, or downgrade it. 
If multiple packages are affected, rebuild or downgrade the library as necessary.

Actually, revdep-rebuild is a tool which was implemented to address a common issue inherent to *rolling distributions*. Whether your distribution is binary or source based is irrelevant if it is a static distribution.

Your statements regarding Arch Linux after you mistook an attribute of rolling distributions for an attribute of source based distributions also apply quite well to Gentoo Linux. In terms of the frequency of updates available for Gentoo Linux, it is extremely rare for things to break on it too, because core library updates that break binary compatibility themselves are extremely rare in comparison to all other forms of updates. The same is true on Arch Linux. These things are extremely trivial to fix with Gentoo's package manager, and they can be fixed using the exact methods you specified.

---

### Post by weezerBo on 2010-05-23
When uninstalling / installing packages I think Arch is most definitely faster than any Debian based distro. 

I don't remember the exact message since I haven't used it in a long while, but when installing a package using apt you get a message along the lines of "Reading database". This operation has sometimes taken _***minutes ***_to complete. It seems worse when it's the first time you've run it since a reboot, I guess it caches the results and they're wiped after a boot. 

And then it goes through a "Setting up" phase which can also take a while. 

The only delay when installing a package in Arch is how fast it can extract the tgz. 


Now as far as running, everday use, I've found it slightly faster -- but this is only because I don't have 1001 services running.

Lucid trounces it boot speed by far though.

---

### Post by WinterRain on 2010-05-23
> **weezerBo said:**
> 
I don't remember the exact message since I haven't used it in a long while, but when installing a package using apt you get a message along the lines of "Reading database". This operation has sometimes taken _***minutes ***_to complete.

Huh? Are you sure you're thinking of ubuntu? Package management for me is very fast.

---

### Post by nrs on 2010-05-24
> **WinterRain said:**
> Huh? Are you sure you're thinking of ubuntu? Package management for me is very fast.
weezerBo = me. I forgot to log out of my brothers account earlier. 
All Debian based distributions use the same package management system. (That's essentially what makes a distro Debian.) 

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/398870](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/398870) it appears they finally fixed this is Lucid. It existed for ~9 years.

---

### Post by WinterRain on 2010-05-24
> **nrs said:**
> 
All Debian based distributions use the same package management system. (That's essentially what makes a distro Debian.) 
I'm aware of this.

> **nrs said:**
> [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/398870](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/398870) it appears they finally fixed this is Lucid. It existed for ~9 years.
Maybe I'm lucky, but I've never experienced this bug.

Anyway, I'm very happy with package management in debian/based distros. Just because something else may save a couple of seconds doesn't matter to me. We all need to use what we feel comfortable with.

---

### Post by MisfitI38 on 2010-05-24
> **Shining Arcanine said:**
> 
Actually, revdep-rebuild is a tool which was implemented to address a common issue inherent to rolling distributions. 

revdep-rebuild creates a list of missing shared library dependencies and using *emerge*, re-emerges the broken packages and corresponding  libraries. Fixing this kind of breakage on any binary distro will be quicker, using a brain and a package manager to upgrade the system, without the need of this tool. If compiling is desired/required, ABS may be used, as I indicated. As you have noted, though the fixes (across binary and source-based) are ultimately  nearly identical, re-emerging all affected packages will nearly always be slower.
Therefore, why do you claim that simply by merit of being source-based, Gentoo's method is superior?
> 
...you mistook an attribute of rolling distributions for an attribute of source based distributions..
revdep-rebuild is a *Gentoo* tool provided as a stopgap to *rebuild packages* when version mismatch breakage occurs, on Gentoo, a source-based system. 
The advantage of binary is its inherent expedience.
revdep-rebuild still requires use of the user's brain. I would also further cite its advantage is closely tied to the time-consuming nature of compilation, and subsequent time saved by used revdep-rebuild. 
> In terms of the frequency of updates available for Gentoo Linux, it is extremely rare for things to break on it too..
Meh. Debatable.
> ..core library updates that break binary compatibility themselves are extremely rare in comparison to all other forms of updates. The same is true on Arch Linux. These things are extremely trivial to fix with Gentoo's package manager, and they can be fixed using the exact methods you specified.
Thank you for acknowledging the trivial nature of this issue.
However, you claimed on page 2 of this thread that Gentoo's approach to upgrades was superior based upon its source-based nature.
Your claim is an opinion, not a fact, and has impelled me to respond.
'Rolling is rolling'. If you want to make the argument that Gentoo's method of source-based packaging and its revdep-bebuild tool make for a superior method, that's fine. Just please, supply  facts if you wish to communicate anything provable.

Gentoo is a fine system. I just wish you would be more objective about it, rather than touting it as a superior alternative with each opportunity.

---

