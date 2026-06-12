---
title: "Arch vs Debian vs Gentoo vs Slack"
date: 2009-09-09
forum: Recurring Discussions
---

### Post by fela on 2009-09-09
OK so I have a home server right now running Ubuntu, and obviously I want to put a more stable, faster, and most of all geekier distro on it.

Specs are:
CPU: Athlon 64 LE-1600 2.2GHz (OS has to support Cool'n'Quiet, I guess that's in the kernel so no worries there)
RAM: 2GB DDR2
GPU: integrated Geforce 6150, however the server runs headless
1x500GB SATAII HDD
Canon Pixma iP5300 printer (usb)

So with all that in mind, let the flamewars begin:

What's the best distro out of Debian Stable, Arch, Gentoo and Slackware? The OS has to meet these criteria aswell:
1) has to support 64 bit
2) has to be _extremely_ stable but having a reasonably current linux kernel

My current candidate is Slackware because I've never used it before and I've heard it's very stable, next candidate is Debian stable after that (as it's very stable and well-supported and has a brilliant package manager).

Plus, the distro needs to support KDE 3.5 as I'd like to use that so my dad can do GUI administration (yes I keep telling him he should learn bash).

---

### Post by wojox on 2009-09-09
I chose Debian. Slackware would be second (never used it though). Gentoo to much source code. Arch to rolling/bleeding for server production. I run Arch on my laptop for fun.

I run Jaunty on my server 32 bit. No GUI. Runs pretty decent.

---

### Post by fela on 2009-09-09
> **wojox said:**
> I chose Debian. Slackware would be second (never used it though). Gentoo to much source code. Arch to rolling/bleeding for server production. I run Arch on my laptop for fun.

I run Jaunty on my server 32 bit. No GUI. Runs pretty decent.

I chose debian aswell (my own poll :lol:). I was also thinking about all the compiling time in Gentoo but I've heard you can get it very stable (or very unstable).

I think I'm gonna go with Slackware as I've never used it before. I'm using Debian on my desktop though and I know it's very good and stable (my one's more stable than Ubuntu was even though it's the testing release).

---

### Post by terazen on 2009-09-09
What part about ubuntu is unstable?  A specific program?  I'm just curious because I haven't had problems on any of mine in 4 years except once that I enabled a faulty moodle mod.  I only have 6 linux servers so maybe I've missed someting.

---

### Post by Whiffle on 2009-09-09
Debian or Slack, depending what you're familiar with.  I have debian on my server, its not given me any problems (even after taking out the hard drive, and sticking it in entirely differnet hardware, and running it).  I'm running slack on my desktop right now, works fine... 

I guess its personal preference really.  I think Arch and Gentoo tend to be too bleeding edge for that kind of duty though.

---

### Post by Sporkman on 2009-09-09
> **fela said:**
> OK so I have a home server right now running Ubuntu, and obviously I want to put a more stable, faster, and most of all geekier distro on it.


If you want stable & fast, go with Ubuntu Server. If you want geekier (i.e., more work & headaches), then go with one of the other options. :)

---

### Post by Bachstelze on 2009-09-09
> **Sporkman said:**
> If you want stable & fast, go with Ubuntu Server. If you want geekier (i.e., more work & headaches), then go with one of the other options. :)

Tru dat.

---

### Post by Cardale on 2009-09-09
> **HymnToLife said:**
> Tru dat.

double tru dat

---

### Post by fela on 2009-09-09
> **terazen said:**
> What part about ubuntu is unstable?  A specific program?  I'm just curious because I haven't had problems on any of mine in 4 years except once that I enabled a faulty moodle mod.  I only have 6 linux servers so maybe I've missed someting.

That wasn't one of the reasons for replacing ubuntu, but yeah it has been unstable in my case. Ubuntu 9.04 had sound problems where it was due to high latencies - running the low latency kernel wouldn't work as the nvidia drivers didn't like it, and when I tried compiling my own kernel with the same config as generic except realtime and a higher timer (1000HZ), it just dropped me to a busybox.

The reason i want to replace Ubuntu is because it's too bloated and has way more stuff that I need - I want to slim it down to just the stuff that I absolutely need.

I think I'm gonna install debian as I read about slackware's package manager and that kind of turned me off the idea (and aptitude is brilliant).

I'll have to try gentoo some day on my desktop.

---

### Post by wirelessmonkey on 2009-09-09
Slack!

---

### Post by nandemonai on 2009-09-09
> **fela said:**
> That wasn't one of the reasons for replacing ubuntu, but yeah it has been unstable in my case. Ubuntu 9.04 had sound problems where it was due to high latencies - running the low latency kernel wouldn't work as the nvidia drivers didn't like it, and when I tried compiling my own kernel with the same config as generic except realtime and a higher timer (1000HZ), it just dropped me to a busybox.

The reason i want to replace Ubuntu is because it's too bloated and has way more stuff that I need - I want to slim it down to just the stuff that I absolutely need.

I think I'm gonna install debian as I read about slackware's package manager and that kind of turned me off the idea (and aptitude is brilliant).

I'll have to try gentoo some day on my desktop.

Why not go for a Server install rather than a desktop install?

I'd hardly call a server install bloated :P

---

### Post by cariboo on 2009-09-09
This is not a support question. Moved to recurring, where it belongs.

---

### Post by kk0sse54 on 2009-09-09
Gentoo, it's my favorite linux distro by far.Unfortauntely I no longer run it as I'm pretty much a full time *BSD user and I just don't have the time or motivation to maintain two source based distros. I'm running Arch right now, which has been mostly fantastic although the occasional instability gets a bit annoying. Slackware is another favorite, great stability coupled with fantastic control and simplicity. With the release of Slackware 13.0 I've been seriosuly considering moving from Arch to Slack. Debian ,despite my disklike for APT, is another solid distro that my sister runs on an older machine. I appreciate it's reliability but personally I'm just not too interested in it.

---

### Post by fela on 2009-09-10
> **nandemonai said:**
> Why not go for a Server install rather than a desktop install?

I'd hardly call a server install bloated :P

It lacks the 'geek factor' :P

Plus the latest 'stable' version doesn't support KDE3. Bummer.

---

### Post by fela on 2009-09-10
> **cariboo907 said:**
> This is not a support question. Moved to recurring, where it belongs.

It was originally :)

---

### Post by jondkent on 2009-09-10
I tend to bounce between distro, but my main favs are:

[LIST]
[*]Ubuntu
[*]Arch
[*]Debian
[/LIST]

Used Gentoo for years, loved it, but just got sick and tied of builds.  Arch I like alot, but it does like to break, esp on the X front quite a bit, which is very annoying.  Debian great, but the politics just gets annoying, so I tend to always end up back with Ubuntu.  Slack..hmm..used it a few years ago and..well...felt like I gone back to the early 90's.  Nice and all but nope not for me.

Geek factor..hmmm..they all have it.  Every distro can be mod'ed to be what you want, but just because you spent the weekend getting something installed impresses me little.  However, if you spent the weekend performance tuning, with real benchmarks to show the performance improvement, that'll impress me.

Your no geekier 'cos you run a certain distro.

---

### Post by fela on 2009-09-10
> **jondkent said:**
> Your no geekier 'cos you run a certain distro.

I was kind of joking :)

But I do much prefer my current Debian to Ubuntu - Ubuntu seemed to just have too much junk and bloat, mainly made so it's easier to use by computer newbies.

My current debian system is tuned to maximum performance with a slimmed down, architecture optimized, 1000HZ kernel with voluntary preemption for almost maximum balance between latency, raw throughput, speed and device compatibility. I know I have great latency as I can listen to music and watch videos with no lag, even with my latest optimized kernel in the process of compiiling. The latest kernel is in production due to my very bad mistake of not including nvidia framebuffer support in my last kernel (which was also compiled today btw, that's two new kernels in one day :P).

---

### Post by kk0sse54 on 2009-09-10
You compile custom kernels in ubuntu too ;)

---

### Post by fela on 2009-09-10
> **C!oud said:**
> You compile custom kernels in ubuntu too ;)

Of course. You can theoretically do anything in Ubuntu that you can in Debian. Thing is, ubuntu seems to include loads of junk and not ask you what you want to install and more importantly what you don't want to install. For example I don't use Gnome but when I installed Ubuntu gnome was the only desktop choice (apart from kubuntu but I didnt' know about that then), and there wasn't an option to install it without a desktop environment either (apart from ubuntu server but I also didnt' know about that).

When I installed debian it gave me the choice of installing just the base system or different categories such as servers, desktop environments, etc etc etc.

I chose to just install the base system and built up on that once it was already installed.

---

### Post by Perfect Storm on 2009-09-11
You can hardly say that the server installation is bloated. Install it, don't install any DE/WM and run it remotely.

Then you have both stability, non-bloat and a "geek-factor" on your server.


Though you do that as well with (nearly) any other distros, it's up to you. But you did asked in an Ubuntu Forum ;)

---

### Post by fela on 2009-09-11
> **Artificial Intelligence said:**
> You can hardly say that the server installation is bloated. Install it, don't install any DE/WM and run it remotely.

Then you have both stability, non-bloat and a "geek-factor" on your server.


Though you do that as well with (nearly) any other distros, it's up to you. But you did asked in an Ubuntu Forum ;)

I'm definitely gonna install a window manager, possibly a full blown KDE3 DE as it's a (relatively) modern system and can easily run that. I have the GUI because there are people other than me who need to be able to administrate it but don't know the CLI. Right now the DE is gnome, which seems very bloated. I've used KDE3 on a 1.8GHz pentium 4 with 256MB and a pre-geforce nvidia Vanta graphics card (32MB VRAM), with no lag. So KDE3 is very fast. Failing KDE, I'd install something like OpenBox or Fluxbox, or LXDE or whatever.

I'm now thinking of trying a distro with a totally different package manager as I've only ever used debian based package managers. I'm thinking along the lines of emerge, pacman, etc. :P

Never RPM though.

---

### Post by zolookas on 2009-09-12
Go with Debian stable. It is supported for a long time and packages are (surprise) stable!

But, actually, I've had Arch server a few years ago and it worked very well.

---

### Post by renkinjutsu on 2009-09-12
i thought nvidiafb kills your console.. i've included it in my kernel before, and as a result, i had to recompile my kernel.

anyway, Ubuntu has a minimum install CD that has an Arch-like install, so you can install just what you need without the bloat

---

### Post by Bachstelze on 2009-09-12
> **renkinjutsu said:**
> i thought nvidiafb kills your console.. i've included it in my kernel before, and as a result, i had to recompile my kernel.

Only if you also have the nvidia X driver. They don't play nice together.

---

### Post by 1clue on 2009-09-20
The only one of these I have not tried is Arch.

Having read all 3 pages of posts, I'm not sure if I understand the original poster's definition of "geeky."  It certainly does not match my definition, because there is no way I would have a WM on a server.

On desktops, I am currently using Ubuntu at this time.  If you do your job on the box, and you do not do Linux technical support for a living, then Ubuntu is about as good as I've found.  It's not nearly as bloated as RHEL or Suse when you get the business versions.

BTW, I have equal affection for both KDE and Gnome, in terms of usability.  Both can get very large though.

IMO, if you have a home server and you like to tinker with Linux, then install Gentoo.  You will learn more about how Linux really works in a month than you did in the last 5 years on every other platform.  If you want to do Linux technical support for a living, install 4 different boxes and install different implementations of each service.  Keep them all running for a year, and chances are you can answer a whole lot of questions.

You can get serious bloat on absolutely any Linux platform, I've had boxes gummed up worse than your least favorite flavor of Windows.  With Gentoo, you can either be extremely trim, extremely tight and extremely functional, or you can lose it and install everything.  My first couple installs with that were horrendous, but last box I installed I kept it very small, fast and effective right up until the lightning took it.

Right now I'm installing Ubuntu onto a brand new i7 920 box.  I will also install Gentoo, but I don't have time for that now.  Hoping I can spend a few less minutes a day waiting for that than my P4.  :)

---

### Post by kevCast on 2009-09-20
Go with Slackware. The reason it's not mentioned is because most people don't bother with it. They either are scared away by others stories, or don't understand it. It does have a package manager. slackpkg, rpm2tgz, and you can grab sbopkg to install slackbuilds from slackbuilds.org. Slackbuilds are bash scripts that automate the build.

It's clean, simple, and stable. Debian stable still had bugs on my laptop, testing had annoying bugs, and sid broke it. Arch has annoying bugs, and general instability issues. Gentoo is good, however, I find the devs attidutes annoying. Not as annoying as Debian users, but annoying still. I've also found Gentoo devs have become a tad too conservative with the stable release. It's name is true to what you get, though. Gentoo has gone a little down hill since the user/dev exodus. When I installed it and did a

```
emerge --sync && emerge -uDavN
```

and it complained about how the package "man-pages" conflicted with my portage profile. WTF? Most people looking for the next "cool" Linux left it for Arch. Go back to 2002-2005, and you couldn't get away from people going on and on about how Gentoo is soo good, USE flags this, CFLAGS that, etc.

Slackware gives you a system. You install what you want. I love this for a workstation, as I can get a fully functional system, with developer tools and a desktop, in a few minutes. People go on about "bloat." Bloat, as I've inferred it, is something along the lines of software and services. Slackware, you pick which services you want to start on boot during install, and stopping a service is as easy as

```
chmod -x /etc/rc.d/rc.ServiceName
```

You can slim it down, during and post install. However, it's my opinion that hard disk space is cheap, and I don't really mind if my install is 3GB instead of 2GB on my 250GB hard drive. This bothers some people, but not me. All the scripts and config files are VERY well documented, and on first boot the root user has a email from Pat Volkerding describing the system, and where to get help if help is needed.

> **zolookas said:**
> Go with Debian stable. It is supported for a long time and packages are (surprise) stable!

But, actually, I've had Arch server a few years ago and it worked very well.
I get a kick when people point to Debian and say it's supported for a long time, considering Slackware is still supporting version 8.1.

[http://slackware.osuosl.org/slackware-8.1/ChangeLog.txt](http://slackware.osuosl.org/slackware-8.1/ChangeLog.txt)

And old doesn't necessarily mean stable, either.

Use Slack, you'll never go back.

---

### Post by fela on 2009-09-21
Well I've installed Debian Stable (Lenny) on it, mainly because I had a USB stick with the netinstaller on and it was just convenient. I'm not planning on installing a WM, and I've also discovered the wonderful webmin interface for controlling virtually everything on the server - I don't actually log into its command line that often anymore. It's running web interfaces for practically everything actually, it has a completely-web-based torrent client based on PHP called torrentflux, which works quite well. I don't see any point in time where I'll need a WM, and Debian seems to be doing everything quite nicely and hassle free.

Thanks for all the posts, guys.

---

### Post by fela on 2009-09-21
> **Bachstelze said:**
> Only if you also have the nvidia X driver. They don't play nice together.

Tell me about it - I'm still trying to get a single head (let alone dual head) widescreen framebuffer working with the nvidia drivers, it's a total nightmare! I'm guessing it would all be fixed if nvidia played well with the Linux devs (and vice versa).

---

### Post by Bachstelze on 2009-09-21
> **fela said:**
> Tell me about it - I'm still trying to get a single head (let alone dual head) widescreen framebuffer working with the nvidia drivers, it's a total nightmare! I'm guessing it would all be fixed if nvidia played well with the Linux devs (and vice versa).

It's just the nvidiafb driver which isn't compatible with the nvidia X driver, but it doesn't really matter. Just use uvesafb (or whichever framebuffer driver you want) instead of nvidiafb and you will be fine.

---

### Post by fela on 2009-09-22
> **Bachstelze said:**
> It's just the nvidiafb driver which isn't compatible with the nvidia X driver, but it doesn't really matter. Just use uvesafb (or whichever framebuffer driver you want) instead of nvidiafb and you will be fine.

I've compiled kernels galore, using uvesafb, nvidiafb, vesafb, you name it. Nothing seems to work. Konsole is a great graphical emulator though. I don't really use the console anymore as the GUI is stable enough to do work in now.

---

### Post by Exodist on 2009-09-22
I vote Debian, its known for being very stable. Plus I get around debian based distros much better.

Arch I have never used.
Gentoo isnt piratical since you have to compile everything, thus slow deployment. 
I have had Slack on servers, but thats because it was the server admins choice. I would have put debian on them.. hehe

---

### Post by tcoffeep on 2009-09-22
I voted for Gentoo, because Funtoo wasn't up there.

---

### Post by SomeGuyDude on 2009-09-22
Flip a coin.

If you don't like what you tried, try another one.

Although, for my money, Slack's rather... sparse package handling leaves a lot to be desired. Leaving dependency-handling up to the user is not part of my definition of "enjoyable".

---

### Post by Bigtime_Scrub on 2009-09-22
I voted Debian because I am more familiar with it and because we are on an unbuntu forums I would assume everyone here has familiarity with Debian. Slack would be second to me, it is rock solid and not a knock on it at all. It's just I would feel more comfortable with it. Debian Stable is just like the name implies. STABLE.

---

### Post by Simian Man on 2009-09-22
Arch and Gentoo are not really the best choice for servers.  You can use them of course, but some people even use Windows for this purpose - if you can imagine :).

I'd choose CentOS or Debian - whichever one you are more familiar with.

---

### Post by Sporkman on 2009-09-22
> **Simian Man said:**
> Arch and Gentoo are not really the best choice for servers.  You can use them of course, but some people even use Windows for this purpose - if you can imagine :).

I'd choose CentOS or Debian - whichever one you are more familiar with.

Ubuntu Server is also a good choice for stability & performance.

---

### Post by &#32 Greg on 2009-09-22
> **Simian Man said:**
> Arch and Gentoo are not really the best choice for servers.  You can use them of course, but some people even use Windows for this purpose - if you can imagine :).

I'd choose CentOS or Debian - whichever one you are more familiar with.

Gentoo can be fine for a server... it's a stable distribution.

---

### Post by hoppipolla on 2009-09-22
I voted Arch, but to be honest I haven't used much of it or straight Debian.

Slackware I have used extensively and enjoyed it (it's wonderfully flexible when it comes to packages), but I don't think it's the best choice.

If it were me choosing a more techie or "hardcore" distro, I would  go for probably Arch, maybe Debian :)

---

### Post by Eisenwinter on 2009-09-23
I voted Arch, but I'm biased, because I use Arch.

---

### Post by tcoffeep on 2009-09-23
> **hoppipolla said:**
> I voted Arch, but to be honest I haven't used much of it or straight Debian.

Slackware I have used extensively and enjoyed it (it's wonderfully flexible when it comes to packages), but I don't think it's the best choice.

If it were me choosing a more techie or "hardcore" distro, I would  go for probably Arch, maybe Debian :)

Arch isn't all that hardcore :P

---

### Post by fela on 2009-09-23
I've now learned that the only perfect distro is the one you make yourself, and that goes with any operating system.

But Debian's doing very well on my server :)

---

### Post by tjwoosta on 2009-09-24
> **fela said:**
> OK so I have a home server right now running Ubuntu, and obviously I want to put a more stable, faster, and most of all geekier distro on it.

Specs are:
CPU: Athlon 64 LE-1600 2.2GHz (OS has to support Cool'n'Quiet, I guess that's in the kernel so no worries there)
RAM: 2GB DDR2
GPU: integrated Geforce 6150, however the server runs headless
1x500GB SATAII HDD
Canon Pixma iP5300 printer (usb)

So with all that in mind, let the flamewars begin:

What's the best distro out of Debian Stable, Arch, Gentoo and Slackware? The OS has to meet these criteria aswell:
1) has to support 64 bit
2) has to be _extremely_ stable but having a reasonably current linux kernel

My current candidate is Slackware because I've never used it before and I've heard it's very stable, next candidate is Debian stable after that (as it's very stable and well-supported and has a brilliant package manager).

Plus, the distro needs to support KDE 3.5 as I'd like to use that so my dad can do GUI administration (yes I keep telling him he should learn bash).

Im an avid arch user but for what your doing I think debian or slackware would be best suited.

---

### Post by MisfitI38 on 2009-09-24
The best OS for a server is the OS you are most familiar with..unless you have significant time to invest in familiarizing yourself with OpenBSD. :)

---

### Post by fela on 2009-09-24
> **MisfitI38 said:**
> The best OS for a server is the OS you are most familiar with..unless you have significant time to invest in familiarizing yourself with OpenBSD. :)

It takes me what, 5 minutes to learn the basics of a new OS. Maybe it's just me but I don't really ever find computers hard to use (except when they have amarok 2 installed of course ;)).

But anyway I have debian and it's great.

---

### Post by Sporkman on 2009-09-24
> **fela said:**
> It takes me what, 5 minutes to learn the basics of a new OS.

Not when it comes to the BSDs - they are not very user-friendly.

---

### Post by ~sHyLoCk~ on 2009-09-24
> **fela said:**
> It takes me what, 5 minutes to learn the basics of a new OS.
Really tall claims! I understand if you're talking about ubuntu. :)

> **Sporkman said:**
> Not when it comes to the BSDs - they are not very user-friendly.

Or gentoo stage installs. I would love to see him learn openBSD in 5minutes though. :P

---

### Post by NewlyHuman on 2009-09-24
I only see two options in the poll, really.

I use Arch on some of my desktops and it's great, but for a server, no thanks. Same goes for Gentoo.

Both being cutting-edge and rolling release means you're getting dozens of updates a week, kernel upgrades inclusive. My Debian server averages a reboot or two a year - It would be much more frequent if I were updating for each kernel on a rolling-release distro.

---

### Post by 1clue on 2009-09-24
> **NewlyHuman said:**
> I only see two options in the poll, really.

I use Arch on some of my desktops and it's great, but for a server, no thanks. Same goes for Gentoo.

Both being cutting-edge and rolling release means you're getting dozens of updates a week, kernel upgrades inclusive. My Debian server averages a reboot or two a year - It would be much more frequent if I were updating for each kernel on a rolling-release distro.

And you're telling me that Debian doesn't do rolling releases?!?  Why is it that at least every other day, I get an updates window in Ubuntu?  Why did I get updates every other day in Debian?

You can choose your update strategy in any distro.  You can tune your update manager to only pay attention to critical security issues, and you can see what is about to be upgraded before you upgrade.  Or you can choose to not upgrade at all.

---

### Post by rookcifer on 2009-09-24
> **fela said:**
> Plus, the distro needs to support KDE 3.5 as I'd like to use that so my dad can do GUI administration (yes I keep telling him he should learn bash).

If this is your requirement, then Gentoo is definitely the way to go (I would recommend it regardless of DE).

There are a few reasons I think Gentoo is best:

A) KDE 3.5 is still in the stable repos, thus you have no need to worry about keywords or unmasking KDE 4.

B) Gentoo is great for older hardware since the system is built and compiled from scratch with optimized CFLAGS.  There is **no** distro that will perform better.

C) The Gentoo stable tree is, well, very stable.

D) You have hardened-Gentoo which is great for servers.  You are not going to find this level of security in many other distros.  You have a choice between SELinux and Grsecurity for the MAC and the hardened kernel also comes with the PaX patch.  There aren't many distros that include PaX.

---

### Post by hessiess on 2009-09-24
Arch, Gentoo is also good if you have lots of time to let it compile.

---

### Post by Deiz on 2009-09-24
> **1clue said:**
> And you're telling me that Debian doesn't do rolling releases?!?  Why is it that at least every other day, I get an updates window in Ubuntu?  Why did I get updates every other day in Debian?

You can choose your update strategy in any distro.  You can tune your update manager to only pay attention to critical security issues, and you can see what is about to be upgraded before you upgrade.  Or you can choose to not upgrade at all.

Uh, might want to look up the definition of [rolling release](http://en.wikipedia.org/wiki/Rolling_release).

Debian stable and Ubuntu are not rolling releases. They release at set intervals and only minor updates tend to be applied within the same release.

As for the latter point, why? It's best to use a distro suited to a task than attempt to make one into something it's not. With Arch, minimizing the number of updates involves an elaborate list of ignored packages. It's far less elegant than simply using a distribution that updates less often.

---

### Post by tcoffeep on 2009-09-24
> **hessiess said:**
> Arch, Gentoo is also good if you have lots of time to let it compile.

Gentoo doesn't take too long to compile, depending on what you want to compile. I made an installer script, and I can have a running GUI in about 2 hours. Then I add in the non-essential things (browsers, evince (without gnome support), im, etc), and that takes a lot longer. (6 hours, i think, was the average "install/compile kernel/update system with new make.conf/add in gui/install non-essentials" run)

---

### Post by 1clue on 2009-09-24
Having administered several Gentoo servers, if you stick to "stable" you are no worse off than anything else, rolling release or not.

Don't do a kernel upgrade unless you have a reason to do so.  Ignore anything that doesn't have "security fix" in the description.

FWIW, Debian and Ubuntu stick so much junk on there that there's a lot to upgrade.  Gentoo, you install exactly what you need and no more, and that's the "default" way to do it.  You can't have a security hole in something that isn't there.  Ubuntu Server at least keeps X off of there, but still seems like a larger install than Gentoo by the time you get it set up for what you need.

Furthermore, if you set your system up properly you will have your software compiled with any unnecessary options turned off, again reducing security exposure simply by removing things you don't need.

If you just blindly follow the lead of the distro, pretty much any and every operating system can get you in trouble.

Two tricks I find handy are:
[LIST=1]
[*]Watch the forums, and don't upgrade the package if there are a lot of problems being posted.
[*]Have a staging box, where you install the upgrades right away, and then test those for a week or so before you move them to the servers.
[/LIST]

---

### Post by hessiess on 2009-09-24
> **tcoffeep said:**
> Gentoo doesn't take too long to compile, depending on what you want to compile. I made an installer script, and I can have a running GUI in about 2 hours. Then I add in the non-essential things (browsers, evince (without gnome support), im, etc), and that takes a lot longer. (6 hours, i think, was the average "install/compile kernel/update system with new make.conf/add in gui/install non-essentials" run)

I installed it in A VM and it took about 2 days just to get a usable CLI environment going...

---

### Post by 1clue on 2009-09-24
Maybe you weren't around in the early days of Linux?  I took that long to get Slackware going back then, and I thought it was about average.

Gentoo is significantly different than everything else.  I still haven't found a distro that I kept my first install attempt, and that includes a Mac running Mac OS.

For familiar hardware, I can get a Gentoo install up in about 3 hours to the point where it's a usable CLI system.  Considering that you are compiling every piece of software on there, that's pretty good.

A really good strategy for a distro like Gentoo is to get your absolute basics in there, and then try to start using it.  When you run into something you need, install it and then keep going.  You wind up with a system which only has what you really want to use, rather than stuff you think you might want to play with some day.

---

### Post by fela on 2009-09-24
> **Sporkman said:**
> Not when it comes to the BSDs - they are not very user-friendly.

They can't be more user unfriendly than blindly ln-ing /dev/usb_device_here to /dev/scd0, /dev/cdrom and /dev/dvd just to be belt and braces, just so you can install your system. And then stabbing in the dark with another problem by chrooting into your new installation and updating the initramfs because you MIGHT have installed to an LVM but can't remember, but know you don't have LVM support in your initramfs. All with NO internet access (that's cheating :P).

All of which happened to me.

---

### Post by fela on 2009-09-24
> **1clue said:**
> A really good strategy for a distro like Gentoo is to get your absolute basics in there, and then try to start using it.  When you run into something you need, install it and then keep going.  You wind up with a system which only has what you really want to use, rather than stuff you think you might want to play with some day.

I do that anyway, so I know what's on my system and, more importantly, what's not.

One of my computer pet hates is having a bloated mess of an operating system. On my server everything's insanely clean and tidy, I'm a bit of a computer clean-freak. There's no window manager of course, everything is administered through web interfaces and SSH.

---

### Post by tcoffeep on 2009-09-24
> **hessiess said:**
> I installed it in A VM and it took about 2 days just to get a usable CLI environment going...

A VM is usually pretty heavy on it's own, let alone adding in virtual compilation, isn't it? :P

---

### Post by doorknob60 on 2009-09-24
Debian. It is one of the best distros for Servers IMO, and it should be very familiar if you have Ubuntu experience (which I think is safe to assume). 2nd place would be Arch, but I'd still go with Debian since it's typically more stable, and on Arch if you go forever without updating, updating can break things (my mom did that...).

---

### Post by Cope57 on 2009-09-24
**fela**, I have been using Debian with a 64 bit kernel since 2003.  What distribution were you using in 2003?  Just switch back to it, I am sure it has a 64 bit kernel available.

---

### Post by tjwoosta on 2009-09-24
Im surprised there are so few votes for slackware. Slackware is a great server distro, it should be right up there with debian.

---

### Post by tcoffeep on 2009-09-24
Slackware is one of the few distros I've never tried :(

---

### Post by 1clue on 2009-09-24
> **tcoffeep said:**
> A VM is usually pretty heavy on it's own, let alone adding in virtual compilation, isn't it? :P

Have you used a modern VMware on modern hardware?  It's not that much slower than if the compiler were running along side your native OS, with whatever else you have running.  The only thing actually trapped are the privileged instructions and then there's a very thin layer over the drivers.

---

### Post by RedSquirrel on 2009-09-24
> **tcoffeep said:**
> Slackware is one of the few distros I've never tried :(
It's definitely worth a look. (I always end up coming back to Gentoo, though. :))

---

### Post by ~sHyLoCk~ on 2009-09-24
Slackware!Slackware!Slackware!:popcorn:

Anyway as a server distro even centos is good. :D

Btw, gentoo doesn't take 2days to get a CLI :o I think people just blatantly spread such false rumours about gentoo without even trying themselves! It took me 3 hours to get gnome-meta and 15-30mins for LXDE.

---

### Post by kevCast on 2009-09-24
I've been considering Gentoo, I'm just a little cautious from previous experiences. How is it these days?

---

### Post by ~sHyLoCk~ on 2009-09-24
> **kevCast said:**
> I've been considering Gentoo, I'm just a little cautious from previous experiences. How is it these days?

What were your previous experiences? :P Gentoo has been the same since 1999 :D

---

### Post by running_rabbit07 on 2009-09-24
> **fela said:**
> 

Does the apt-get in Debian work the same as it does in Ubuntu? I am installing it on a VBox so I can get some practice for a future install.

---

### Post by kevCast on 2009-09-24
> **~sHyLoCk~ said:**
> What were your previous experiences? :P Gentoo has been the same since 1999 :D
Well, generally, good, but scary.

The request to emerge -C man-pages because of a profile conflict on stable scared be a little bit.

---

### Post by ~sHyLoCk~ on 2009-09-24
> **kevCast said:**
> Well, generally, good, but scary.

The request to emerge -C man-pages because of a profile conflict on stable scared be a little bit.

Well all I can say is refer to gentoo handbook thoroughly during install also I would suggest keeping [this]("http://www.gentoo-install.com/") site open during install for quick references.

---

### Post by tjwoosta on 2009-09-25
> **running_rabbit07 said:**
> Does the apt-get in Debian work the same as it does in Ubuntu? I am installing it on a VBox so I can get some practice for a future install.

Yep, exactly the same.  Apt is actually originally from debian.

---

### Post by cityrama on 2009-09-25
Surely Debian is bloated? it comes on 5 DVD's at nearly 20GB. and that's light compared

to the CD version.

However I always read Debian is much better then Ubuntu at things like flash.

---

### Post by MisfitI38 on 2009-09-25
> **fela said:**
> It takes me what, 5 minutes to learn the basics of a new OS..

Heh. I lol'd.

---

### Post by Sporkman on 2009-09-25
I don't care for distros for which you have to read a manual to install it. Everything you need to know during installation should be displayed on the screen IMO.

---

### Post by tcoffeep on 2009-09-25
> **Sporkman said:**
> I don't care for distros for which you have to read a manual to install it. Everything you need to know during installation should be displayed on the screen IMO.

That's your opinion. Yet people praise the installer guides for Gentoo and Arch. So, apparently, everything *you* need to know should be displayed. Some people like explanations of what they're doing. (cos, you see, some of the installers that require a small guide - they are a more of a DIY job than an auto-installer ;) )

---

### Post by tjwoosta on 2009-09-25
> **cityrama said:**
> Surely Debian is bloated? it comes on 5 DVD's at nearly 20GB. and that's light compared

to the CD version.

However I always read Debian is much better then Ubuntu at things like flash.

Thats because those dvd's have the entire repositories on them. This is incase people don't have the resources to download packages from the internet as they need them. You usually wouldn't actually install everything on the dvd's, you just search through the packages and install what you want. 

Most people just use the netinst cd which is only about 180 mb or theres an even smaller one thats only 40 mb.

---

### Post by running_rabbit07 on 2009-09-25
> **tjwoosta said:**
> Thats because those dvd's have the entire repositories on them. This is incase people don't have the resources to download packages from the internet as they need them. You usually wouldn't actually install everything on the dvd's, you just search through the packages and install what you want. 

Most people just use the netinst cd which is only about 180 mb or theres an even smaller one thats only 40 mb.

I tried the netinstall twice so far today and both failed. I installed with the 5 DVD set and for some reason it decided to download some of the files and they made the install fail. Right now I have the VBox installing one last time with the network card turned off. Apparently there is a conflicting net file.

You are right. Debian only installs all of those disks if you highlight to install all of the server stuff along with the desktop and laptop environments. Even then, it does not install all of the files from the disks.

---

### Post by 1clue on 2009-09-25
I don't understand what's so hard to install with Debian.  It's got to be the simplest old-school distribution out there.  Ubuntu is a thin veneer over Debian, which is a point for Ubuntu.  I think the Ubuntu team focuses mostly on making things easier to set up, especially with GUI tools.

That's not to say it's ALL the Ubuntu team does, but it's the most obvious thing.  For people who want all the information on the screen during the install, Ubuntu is definitely the way to go, or maybe RedHat or Suse with their highly commercialized versions.

Gentoo is not for everyone.  it's for people who either know what they want or want to figure out what they want, in detail, before they do something.  Gentoo lets you have complete control of the box, per-package, and control how each of those packages is installed.  If that sounds pedantic to you, then just stay off their site.  If it sounds intriguing, then Gentoo is your baby, and going there will get you in touch with a lot of like-minded geeks.  (including me)

---

### Post by running_rabbit07 on 2009-09-25
> **1clue said:**
> I don't understand what's so hard to install with Debian.  It's got to be the simplest old-school distribution out there. 

You make it sound like I am the one doing something wrong. They programmed it to look for newer software during the select and install process and it apparently couldn't get the right files. 

It may be simple but they have something messed up in their netbooting repository because I have tried to boot via the mini CD and the DVD set and the only way it installed properly was with the NIC unavailable to it. 

I knew what i was getting into and I made a few small changes with each attempt to install and finally got it installed and running.

As far as installing in a partition instead of VBox, it won't happen on this system with Lenny. Lenny does not like my NVIDIA. I tried for several days to get that to work and it just wasn't working. I got impatient with trying to work with a 600 by 800 resolution so I found another distro and went with it.

I still prefer Ubuntu over installing Debian because it looks better, installs way faster, and has a better support forum. You can't beat the knowledge some people here are willing to share.

---

### Post by cityrama on 2009-09-25
> **tjwoosta said:**
> Thats because those dvd's have the entire repositories on them. This is incase people don't have the resources to download packages from the internet as they need them. You usually wouldn't actually install everything on the dvd's, you just search through the packages and install what you want. 

Most people just use the netinst cd which is only about 180 mb or theres an even smaller one thats only 40 mb.


That's what Mandriva did back when it was known as Mandrake, couple of DvD's that let you install just what one wants and no more.

I thank you because I never noticed the net install CD. use the DVD media for something else now. :)

---

### Post by 1clue on 2009-09-25
Rabbit,

I'm not trying to start a flame here.  I just never imagined you could get trouble installing Debian like you have.  For the last 5 years or so, every install I made was similar to yours (minimal+net update) if the distro has such an option.

With Gentoo, that's really the only option that makes sense.  You'll wind up downloading all that stuff anyway, so you'd just as well put the minimal on it, update it and then go from there.

FWIW, I don't have much use for plain old Debian.  I like Ubuntu because it's no-fuss and all the desktop stuff people seem to want is there already, and I like Gentoo because you get exactly what you want.  It's like Yin and Yang, diametrically opposed distros, but each elegant in its own way.

Gentoo is only a difficult install because it's time consuming.  No matter how fast your computer is, configuring a kernel takes time.  Reading documentation takes time.  Gentoo has been referred to as a distro for making a distro.  I don't know if I would go that far, but it's not very far off.  Anyway, if you can follow instructions you can install Gentoo, in most cases.  It's just that there are so darned many instructions.

---

### Post by running_rabbit07 on 2009-09-25
> **1clue said:**
> Rabbit,

I'm not trying to start a flame here.  I just never imagined you could get trouble installing Debian like you have.  For the last 5 years or so, every install I made was similar to yours (minimal+net update) if the distro has such an option.

With Gentoo, that's really the only option that makes sense.  You'll wind up downloading all that stuff anyway, so you'd just as well put the minimal on it, update it and then go from there.

FWIW, I don't have much use for plain old Debian.  I like Ubuntu because it's no-fuss and all the desktop stuff people seem to want is there already, and I like Gentoo because you get exactly what you want.  It's like Yin and Yang, diametrically opposed distros, but each elegant in its own way.

Gentoo is only a difficult install because it's time consuming.  No matter how fast your computer is, configuring a kernel takes time.  Reading documentation takes time.  Gentoo has been referred to as a distro for making a distro.  I don't know if I would go that far, but it's not very far off.  Anyway, if you can follow instructions you can install Gentoo, in most cases.  It's just that there are so darned many instructions.

No problem. I apologize for shooting back so harshly. I was surprised at the problems I was having, too.

---

### Post by Siljrath on 2009-10-10
tough question.   great question.  epic question.  pertinent que~

before i waffle on further, [disclaimer] i'll come clean and admit **i'm not qualified to answer this question**.  so feel free to skip by the rest of my waffle and musings on this topic which i feel too ill-informed to do justice to.

i've rarely used any of them in their raw original forms for very long.
slack a few times.
debian once or twice, and several a half *** job of installing besides.
gentoo, couple o attempts at making systems i like, great education, really admirable in many respects not so well lauded in slack or debian.
arch... ahem... i'm not sure i ever remember making anything useable of this or not.. like others, i played around in virtualbox a bit with it, but like with debian, my lack of intimate knowledge with my hardware did pose problems.

i am also already quite biassed towards slack and gentoo.

slack is the grandaddy throroughbred of linux distributions.  how can you go wrong?   it's so pure n brilliant.  does well to stick to the original ethos i think.  i've often said "i think installing slackware at least once should be a mandatory part of the curriculum in school."

gentoo, it does things neat little things, things that you know have been created from the of by folks who really had a great understanding of their OS, and things you know have been masterfully carved or grafted or improved unto this new throroughbred.  i still never really made the best use of all the masses of seeeeerious performance tips available in there, and not just jeremy-clarkson POWER tweaks, but james-may finess and preference tweaks... you can really line up your air vents if you so wish with a gentoo.  loads of fun to get your sleaves rolled up if you like.  and likely sure to be a great boon to your box even if you dont learn it well enough to know to get it to hug well to the optimal for your hardware. and use style..

debian.  yeah... amazing. up there with gentoo, and probably beyond, for how readily available it is on any weird stuff.... i can get an iso for my arm based phone architechture , for example.  but uhh, like i said, i never really used it much.   used it more back in 2004 actually, back when i did know my old box so well i had fewer issues installing and getting everything ... or at least nearly everything, working.   that was more comon problem back then, the " nearly  everything " syndrome, comon to all distros back then.

arch.  now although i've not driven her as much as any of the other three in the ring...  (sorry, my heads spinning from the mix os sports-commentator metaphorizing, i'll stop that.) .. i have however, given arch a decent chunk of attention.  like debian,most attempts to install and have everything work, have generally been scattered with failures.  though this is more from convenience conditioned lazienes, rather than any failing on the distros part i must point out.  total pebcak error.  but arch is indeed a special and worthy contender here.  it's a rugged, to the point cateram-gumpert kitcar, real corp-beating man in shed stuff.  quality craftsmanship from serious high calibre coders.  it's tidy, it's tight, it's potent, its not hobbled in any wya by any of its tightening, so you're getting the full wammy despite it often being pimped around town as a light distro... its not dsl / slitaz / tinycore / deli light. it's just had alot of the fat cut off and kept on a better diet than most so to keep the meat more lean.  tho of course, the others might also attempt to claim this, this is not any of their greatest n strongest points, all of them otherwise having other points what cause them to be great.

is there to be a winner here?   sure... we're all winners if we pick any of these four distros surely.  they're all pretty solid n serious pieces of kit.  no flim flam here.   .... why are some of you looking at gentoo?  stop that!   gentoo is seriously awesome!  did i hear someone murmer the lightbulb joke? thats not *hehehe* funny.  stop that.  ok, ok, this comic relief aside, gentoo is probably still gonna be my pick.  it will give you an awesome machine, teach you billions, like deep down the rabbit hole billions.
arch will teach you loads too, arch seems to do well, like many of the other light distros i said it wasnt like, do, to let all the really cool tips rise to the forefront more rapidly, like they have more boyancy reaching the surface for all to see with greater immediacy.
gentoo i think might be contradictingly both the most harshcore and the most well assisted.  the truth and balance of that statement varying from user to user.  depends (and this statement blankets out further than just this circumstance) on one's aptitudes and aproach, one's learning style(s), motivation, preferences, and so on, as to which best fits you.  n there again, bing, i hit the magic concept in open source freedom software... have it how you like it.  and that especially is the point with these four distros.

i think it probable that there are far fewer % who use their gentoo, slack, arch or debian in their vanila state as there would be for say, slitaz, slackware, suse, redhat, traditional "live" distros, etc to take a guess at a few possible more vanilla-likely distros.   or who knows, maybe i'm wrong, maybe the debian, gentoo, arch and slackware folks are dull and unimaginative..  bwahahaha.  yeah right.  its clear to see thats not the case, i remember most freshly, with arch, and i'm sure with all, from browisng the forums' show and tell type sections, and indeed, all the rest.  its open source, u make it like u like it, modularise n change bits all you want to try things out n make it better.  so whats under the more superficial stuff?   what sets them appart?   its when i drill down to that question, that i still go with gentoo.  ...so long as you have installed slackware once in your life. :D  if you dont know your system all that well, you're more likely to get snagged on a hurdle with debian and arch, and least likely, in my experience with slackware.

now most of my gentoo experience is in the form of sabayon admittedly.  alot of time with versions in the 3.4s, which was leaning more still gentoo-ish like, like a well preconfigured gentoo system, rather than the 3.5 and 4.x which have become increasingly more their own thing, a real sabayon distro, rather than a mere "well configured gentoo" (which i think not so "mere", but actually the superior), thanks largely to the creation and ongoing improvement and developement of it's own package management stuff.  but even as it shifted to what i considered a more removed method, where i liked 3.4 becuase it seemed to serve as the perfect intermediate stage distro from which you could trickle down from the noob friendly autoworld of everything works already n you didnt need to know how, into the world of fiddling n tweaking n learning more dimensions to your system.


there are many distros which kind of offer hesame thing in slackware, though none i've tried seem quite to offer the slickness of entry nor the presence of a funneling-towards-geekdom-system-savvy choice, as was present in sabayon.  


like how my respect and admiration for gentoo started long before i ever tried it, the same thing i note is in it's infancy with arch.  arch, like slackware, i reserve a place for it in my mind as my one-day-to-be main-distro.  slackware especially on that front, possibly withhelp on account of how long it's had to set root in my mind.

infact, i'm really starting to take a dislike for having noticed this thread, this question, this battle of the 4.  and i mean, this really is THE 4 now isnt it.  who else is a contender in the ring with these 4?  if it's out there, its still to come far enough out of obscurity for me to know about it.

these are the serious daddys of distros.  a term almost beneath slackware, the graaaaannnnndaddy distro.  and debian's pretty much as much an old timer as ol' slack.  the term daddy almost to big it's hanging off the sholder's of lil arch who looks like a fresh faced new boy, but if you look close, he's got the stubble on his chin pretty thick, just shaved real tidy.  looks like he'll be retaining his youthful looks long into the time even when he starts to get called a grandaddy and slack is considered the great grandaddy.   gentoo is like the weird uncle.... who always wears a toxic green nylon nitted jumper, and tells you about his weird ideas and experiments... it's a lil like gentoo is a bit of a linux of linux.  but i love it for it's technological accolades, of which there are several worth looking up (and i dont mention them directly knowing full well you'll find even more i dont know about),  and not just because it seems to naturally have set itself apart a little, all the while without having left the pack.

i admit it... debian, i do shy from a touch because of the kinda devil-imp like iconography... i know, its probably a bit of a silly reason, but there it is, i said it.  i mean... i dont even want gremlins in my machine, so why would i want devils?!   i dont want bill gates (or other capitalist/fascist/corporatist) in my computer, so why would i opt out of the devil i know for this other devil... oh, thats right, because this one is open source....  so suposedly, you can get to know it, AND what it's doing to you, where before, you couldnt because of trade secrets.  oh well... its better than proprietary then, but i'll still sharpen my skills with friendlier distros first before i take on peering into the devil's [debian's] domain.   ... y'know, incase it's like a R-U-L33T test, those who cant check the code are left with nasties...  and only those who r leet enough fo read all their source code will know to immunise themselves.   hehe, probably a paranoid fantasy, but actually a nice metaphor of a sort for the truth.   if ya dont know what you're doing, you can quite easily jepordise your system.  :D   so i suppose thats why i still have my stabilizers on after years with linux, prefering still to have nicely preconfigured systems that are easier on the installation.  more automated, less hassle, less knowledge required.   i know, shocking preference, and quite contrary to my ideals.

so i do my gentoo the easy way with sabayon, n just kinda funtoo-ise it a little bit and use portage instead of entropy.

i do my debian the easy way with crunchbang.  (ok, thats ubuntu really, innit, not debian.)

i do my slackware the easy way with slax... tho thats not really very slackware-ish, but still lovable and worth checking out for its own reasons aside..... so uhh, ahem, let me redo this slackware summation bit....

i do my slackware the easy way with slackware.  cos once you slack, you wont go back.  :D  ;)  :rolleyes:

i'll do my arch the easy way with chakra... possibly, last alpha i tried failed.. but we'll see.   depending on how tidy n tight they keep their kde, i might stick it out with it... though these days, i lean more towards the lean minimal to the point light desktop environments hobbled together from the best components.  ecclectically you might say.


you see, this is probably the point i need to make most....

it doesnt really matter.  any of these are likely easily fit to the needs of anyone [/i](cept i think perhaps most gentoo stands apart again, if u really needed gentoo's special powers, should u be so finikity to "need" such nerdy tweakabilities)[/i] it's really more about the apps you use on it.  if you're going to use any of these four, you're not likely to be scared off by the occasional  source installation... and indeed, may actually find yourself contributing a great deal more than had you opted for a "softer" option.
the point, before i digress and muddle it too much, its the apps.   its your configurations.   its all that stuff.   it's how much you can make it accomodate your needs, how wellit can enhance your experience, your productivity, your creativity, your workflow, your enjoyment...  and that's largely in the apps, in the community, but yes, ok, it is also in the bedrock, in the starting point, in the shared denominator... the shared denominator, the starting point, the "vanila" shared starting point for the user's experience, in gentoo and i think debian and likely arch too, and idk about slackware, is a multi-dimensional next-evolutionary teir phenomenon, a vapidity, a concept made redundant in the transcendent glory that is the ability o start your system pretty much from total base ground up... oh yeah, now i recall the ways, yes, slackware too.... all of these distros, i declare the winner!   go forth!   in victory!   they all win!    they all win?    what is that!?   all that text and the conclusion is they all win?   well yes!  because you see they dont actually fight each other.  its all open source, it's all co-op.  :D   huzzah!   mutual amplification boons for all!   huzzah!  :D

ah what do i care...  until i decide and dedicate to slack it out (or maybe gentoo...   or arch... like maybe arch when charkra gets polished n tidied), i use crunchbang.   

ah, just when i thought i was closing, i have had the idea, the solution....

install all four!

a multiboot with those four would be a work of prowess, and the true test... see which you gravitate to after a while.


i might do that... but i bet for now and a long time in the future, on my pendrive, for my laptop and elsewhere... i'll still use crunchbang linux.

---

### Post by keiichidono on 2009-10-10
Too long;Didn't Read.

---

### Post by ~sHyLoCk~ on 2009-10-10
> **CalvinB said:**
> Too long;Didn't Read.

Same.:lolflag:

---

### Post by tcoffeep on 2009-10-11
My eyes boggled before I decided it was, indeed, tl, and I dr.

---

### Post by starscalling on 2009-10-11
> **kevCast said:**
> Go with Slackware. The reason it's not mentioned is because most people don't bother with it. They either are scared away by others stories, or don't understand it. It does have a package manager. slackpkg, rpm2tgz, and you can grab sbopkg to install slackbuilds from slackbuilds.org. Slackbuilds are bash scripts that automate the build.

It's clean, simple, and stable. Debian stable still had bugs on my laptop, testing had annoying bugs, and sid broke it. Arch has annoying bugs, and general instability issues. Gentoo is good, however, I find the devs attidutes annoying. Not as annoying as Debian users, but annoying still. I've also found Gentoo devs have become a tad too conservative with the stable release. It's name is true to what you get, though. Gentoo has gone a little down hill since the user/dev exodus. When I installed it and did a

```
emerge --sync && emerge -uDavN
```

and it complained about how the package "man-pages" conflicted with my portage profile. WTF? Most people looking for the next "cool" Linux left it for Arch. Go back to 2002-2005, and you couldn't get away from people going on and on about how Gentoo is soo good, USE flags this, CFLAGS that, etc.

Slackware gives you a system. You install what you want. I love this for a workstation, as I can get a fully functional system, with developer tools and a desktop, in a few minutes. People go on about "bloat." Bloat, as I've inferred it, is something along the lines of software and services. Slackware, you pick which services you want to start on boot during install, and stopping a service is as easy as

```
chmod -x /etc/rc.d/rc.ServiceName
```

You can slim it down, during and post install. However, it's my opinion that hard disk space is cheap, and I don't really mind if my install is 3GB instead of 2GB on my 250GB hard drive. This bothers some people, but not me. All the scripts and config files are VERY well documented, and on first boot the root user has a email from Pat Volkerding describing the system, and where to get help if help is needed.


I get a kick when people point to Debian and say it's supported for a long time, considering Slackware is still supporting version 8.1.

[http://slackware.osuosl.org/slackware-8.1/ChangeLog.txt](http://slackware.osuosl.org/slackware-8.1/ChangeLog.txt)

And old doesn't necessarily mean stable, either.

Use Slack, you'll never go back.

figure i'll try this for my workstation at work ;-) +rep or w/e

---

### Post by samjh on 2009-10-11
> **Siljrath said:**
> 2387 wordsThat is a titanic post.

Could you please post a summary in 100 words or less?

---

### Post by Arup on 2009-10-11
I did, good reading, agree with you.

---

### Post by barthel on 2009-10-11
The absolute geekiest would be to roll your own distribution from scratch.

Next geekiest would be Slackware. I was a Slacker from Linux 1.2 onward. The main reason I switched was because development halted when Patrick had health issues. I turned to Ubuntu because of the large community behind the development.

Just for fun (the first isn't mine, the second is):

**Ubuntu** *(n)* - from an African word meaning "Slackware is too hard for me."

Slackware: the oldest Linux distribution. Proof? In _Back to the Future_, Mr. Strickland says: > You've got a real attitude problem, McFly. You're a slacker! You remind me of your father when he went here. He was a slacker, too.

---

### Post by ~sHyLoCk~ on 2009-10-11
LOL. :D

The only problem with slack is though the annoyance of installing something with heavy dependencies. Which are not in slackbuilds or any other slack repos. With slackware you need to be a minimalist, use things only in slackbuilds and repos. Else you have to manually sort out your dependencies recursively. Not many people with desktop requirements would want that. When i use slack, I always use the default packages Pat provides.

---

### Post by barthel on 2009-10-11
> **~sHyLoCk~ said:**
> LOL. :D

The only problem with slack is though the annoyance of installing something with heavy dependencies. Which are not in slackbuilds or any other slack repos.

Problem? What problem? :D

Back in the day (circa GNOME 1.4, but it could have been 1.2), I had posted the "correct" sequence to compile GNOME from scratch to the GNOME lists. Nothing had heavier dependencies than GNOME. I was like Virgil in the dependency Inferno. </me does Tim Allen "grunts">

On the serious side, that's actually one of the things I enjoyed with Slackware--getting rogue packages to compile cleanly and correctly. You don't *have* to be a minimalist--as long as you're willing to become intimately acquainted with your system.

Or as one of my random .sigs puts it:

Unix *is* user friendly. It's just selective about its friends.

---

### Post by ~sHyLoCk~ on 2009-10-11
> **barthel said:**
> Problem? What problem? :D


**You** may not have any problem but many do. Using slackware and gentoo are the same to me. You need to be an extreme enthusiast and stick the principles of your distro. When there are several distro which provides you with as much system control and customization [debian/arch] as slackware or getoo. Maybe not highly detailed in-depth control, but most users don't need that anyway. Just imagine manually finding out dependencies for a program you want to install and in the source package there is no dependency information mentioned. This package is not there in slackbuilds or any other slack repos. So you start compiling it, and in each step it will halt giving you errors stating which package is missing. So you go install that package first, which maybe depending on some other package. Is this worth the effort? For most slacker "yes". They believe in their principles and follow PV's decision and have their own way of doing things. I just use slack current with all the vanilla packages and a few bare essential packages needed. For everything else I use Arch, simply because pacman is God and gentoo for tinkering.

---

### Post by Siljrath on 2009-10-15
> **samjh said:**
> That is a titanic post.

Could you please post a summary in 100 words or less?

wasnt qualified to answer...  seemed to be leaning most towards gentoo, and farthest from debian.  managed to waffle alot.

---

### Post by djbon2112 on 2009-10-15
Well, I use Debian on my server, mainly because it's close to Ubuntu and that's what I learned Linux with, so I'm just comfortable administering it. If you find yourself in that boat, I'd say go with Debian first, it'll be much easier to manage.

---

### Post by the fix it man on 2009-10-25
Stereotypically  geek distros for sure, but I would say Debian is more of a bridge from Ubuntu/Mandriva/suse to the geek distros. :)

---

### Post by gnuisancev3 on 2009-10-25
If i was looking for stability? I'd go with debian.   Arch is fun for hobbyist desktops, but i wouldn't use it for much else. Same with gentoo.

---

### Post by Spoudumen on 2009-11-12
I use Arch for all my desktops / laptops and Debian for my 2 servers. The problem with Ubuntu is that it is too heavily patched, not that Debian isnt patched, but it can cause problems. Never had a problem with Debian, or Arch for that matter especially if you arent going to use a gui.

---

