---
title: "Ubuntu vs Gentoo"
date: 2009-11-16
forum: Recurring Discussions
---

### Post by dE_logics on 2009-11-16
Since I've switched to Gentoo (From Ubuntu 8.10); I'm posting here to remove the myth that speed hardly matters among Linux distributions; I'm telling you, there's MAJOR performance difference between Ubuntu and Gentoo, it's more than what I expected...firefox startup times got boosts, the general startup of the system good boosted (ok...it's not right to compare this...it's all about customization here), major improvement in warm startup times of openoffice...ktorrent is very fast (I mean the UI, of course not the bandwidth :P); the recovery from a heavy job is fabulous, it does not slow down when running continuously for long hours.......and I'll go on and on.....

Best of all, my system is swift even when the CPU is set to ondemand, otherwise in Ubuntu I had to set it to max core frequency all the time!

And yes, the system is, compared to Ubuntu, VERY responsive when the memory is full...I mean, I just switched to Gentoo...I was compiling 3 software at a time (total of 6 compilations actually), the system went slow, so I opened the system monitor and to my surprise only 11 MB was free!!...Ubuntu just STOPS working at such a state, while Gentoo was fabulous.


All this was done on Xfce4


So, man...the distribution matters MAJOR...not small but MAJOR differences; if you say there's hardly a speed difference, it's cause - 

1) You did not configure your use flags well...or just went through it.

2) You configured the kernel blindly (actually I'll optimize the configuration further to make the system faster).

3) You did not set the CFLAGS to be optimized for your processor.

I'm not saying Ubuntu is bad, but this is just to remove this myth...otherwise Gentoo and Ubuntu cant be compared...Gentoo is too fast and comparatively hard, Ubuntu is too easy; but I don't know about the speed relative to the average speed of all Linux distributions.

---

### Post by Zoot7 on 2009-11-16
I played with Gentoo 4 years ago for about 3 months, mainly to throw myself in the deep end to learn the inner workings of Linux.
I found it was quite snappy in comparison to openSUSE (which was my other main distro at the time), but the huge amounts of source put me off it. Hence why I abandoned it in favour of Debian at the time.

But yeah I've gotta agree, once your done with the compilation and have it set up to your needs, it can be a lot snappier than the other distros.
I must give it another shot at some point.

---

### Post by HappyFeet on 2009-11-16
[IMG]http://www.nyblom.org/pub/gentoo.png[/IMG]

---

### Post by solwic on 2009-11-16
> **HappyFeet said:**
> [IMG]http://www.nyblom.org/pub/gentoo.png[/IMG]

:lolflag:

---

### Post by wirelessmonkey on 2009-11-16
As a gentoo admin(10 servers, 100 desktops), I believe gentoo is not worth the aggravation except in situations where extreme performance tuning is NECESSARY, just isn't worth it over any enterprise distribution.

---

### Post by Zoot7 on 2009-11-16
> **HappyFeet said:**
> ....   
:lolflag:

> **wirelessmonkey said:**
> As a gentoo admin(10 servers, 100 desktops), I believe gentoo is not worth the aggravation except in situations where extreme performance tuning is NECESSARY, just isn't worth it over any enterprise distribution.
I think Gentoo is a classic example of a hobbyist's distro, I wouldn't use it for anything else really.

---

### Post by HappyFeet on 2009-11-16
> **Zoot7 said:**
> :lolflag:


I think Gentoo is a classic example of a hobbyist's distro, I wouldn't use it for anything else really.

Yeah, if you have a lot of time, patience, and blood pressure medication, it's a great distro. Just don't expect Dell to start preinstalling it anytime soon.

---

### Post by dE_logics on 2009-11-16
[QUOTE=Zoot7]but the huge amounts of source put me off it.[/QUOTE]

Yeah, it takes lots of space, you're right.


You tried cleaning up the distfiles directory?...but it does take lots of space in general...maybe cause it needs to install the developer packages.

But you can try passing the Os flag to reduce sizes.

---

### Post by dE_logics on 2009-11-16
> **HappyFeet said:**
> [IMG]http://www.nyblom.org/pub/gentoo.png[/IMG]

[IMG]http://img195.imageshack.us/img195/8666/ogaaanrrdglkx5hfdcn3slk.jpg[/IMG]

Well, yeah Gentoo is very bad when it comes to compilations, I cant imagine Gentoo working on those PCs of 1999; now with the quad and dual core, it's a lot faster BUT you really need to have patience still.

For e.g it took me a week to setup my Gentoo box, I did not compile openoffice (as a result it's slow) cause it requires 4 to 6 GB of free space...and around...I think 10+ hours of compilation on an Athlon X2 running at 1.8 ghz. What I did was set portage to compile the software in the night, and during the day it was done in the background.

BUT the features of the package managment system makes up very much for the long time...I mean, you can compile the software of 1 system (for e.g a netbook) on a more powerful system to reduce compilation times.

We also have 'ccache' etc...

[QUOTE=Zoot7]I think Gentoo is a classic example of a hobbyist's distro, I wouldn't use it for anything else really. [/QUOTE]

No no no...the speed optimization and customization is wroth it...I mean just compile in the background...that's it...problem solved.

If you're using Gentoo you're learning "Something" about Linux.

---

### Post by dE_logics on 2009-11-16
And yes, the Debian pacaking system needs to learn a lot from Portage...

---

### Post by jrusso2 on 2009-11-16
What was the method used to discover this speed differences>?  What benchmarks were used?

---

### Post by fluxlizard on 2009-11-16
If you want something easy like ubuntu but much faster try pclinuxos gnome edition. Similar look and feel, similar packages in similar quantity (by which I mean lots- no idea actual numbers, but lots in both) in the repos, much faster and lighter on it's feet- I can run it comfortably on a p3 700 mhz laptop with 256 mb ram. But I use ubuntu on my main pc because it's the easiest of distros to get answers and obscure packages for..

---

### Post by Zoot7 on 2009-11-17
> **dE_logics said:**
> Yeah, it takes lots of space, you're right.


You tried cleaning up the distfiles directory?...but it does take lots of space in general...maybe cause it needs to install the developer packages.
Yeah I used to have to clean it up every so often. Been a while since I used it though...

---

### Post by Zoot7 on 2009-11-17
> **dE_logics said:**
> If you're using Gentoo you're learning "Something" about Linux.
Precisely, that was my reason to try it out. 
I haven't used a better distro to find out about the inner workings of Linux since.

---

### Post by dE_logics on 2009-11-17
> **jrusso2 said:**
> What was the method used to discover this speed differences>?  What benchmarks were used?

In general speed difference, startup times, shutdown times, ok don't consider these 2 anyway, so take a look at other things -- Thunar is faster.

Warm startups of openoffice dropped form 5 to 6 seconds to ~2 seconds (notice, I'm still using binary packages for openoffice.

Gimp loads in ~3 seconds...in Ubuntu it was a hefty ~20.

System is swift even if CPU is set to on demand.

Firefox is VERY fast

Right now the system is using 270 mb of physical memory depite 2 tabs in firefox being opend + parcellite running + gnome-ppp + system monitor. On startup it's around 120 mb.

Virtually there's a boost in everything!

And yes, the smooth scroll of firefox works fantastic now.




One thing I really hate about Ubuntu as compare to gentoo is this "version" system of Ubuntu...8.04, 8.10, 9.04, 9.10 etc....

What's the utility...why not just do it Gentoo style?...only the packages get upgraded.

I'm maintaining Ubuntu on a thumb drive (I get lots of request to install Linux, but I only install Ubuntu) and I find it difficult to maintain cause of this version system.

---

### Post by dE_logics on 2009-11-17
> **fluxlizard said:**
> If you want something easy like ubuntu but much faster try pclinuxos gnome edition. Similar look and feel, similar packages in similar quantity (by which I mean lots- no idea actual numbers, but lots in both) in the repos, much faster and lighter on it's feet- I can run it comfortably on a p3 700 mhz laptop with 256 mb ram. But I use ubuntu on my main pc because it's the easiest of distros to get answers and obscure packages for..

Personally I wanted an empty distribution...who's every component is built to my needs and optimized for performance...Gentoo was the only one, each binary (except openoffice) is built for my system and needs -- athlon64 and my use flags.

[QUOTE=Zoot7]Yeah I used to have to clean it up every so often. Been a while since I used it though...[/QUOTE]

Yeah also, you should have cleaned portage's temp folder.../var/tmp/portage and /var/tmp/log.

/var/tmp/portage can reach sizes of 1 GB easily, if you ever plan to compile openoffice...it'll grow to atleast 4bg and at most 6gb.

If a package fails to compile or you quit the compilation, that place is not cleaned automatically...you have to manually remove stuff from it.

---

### Post by jrusso2 on 2009-11-17
> **dE_logics said:**
> In general speed difference, startup times, shutdown times, ok don't consider these 2 anyway, so take a look at other things -- Thunar is faster.

Warm startups of openoffice dropped form 5 to 6 seconds to ~2 seconds (notice, I'm still using binary packages for openoffice.

Gimp loads in ~3 seconds...in Ubuntu it was a hefty ~20.

System is swift even if CPU is set to on demand.

Firefox is VERY fast

Right now the system is using 270 mb of physical memory depite 2 tabs in firefox being opend + parcellite running + gnome-ppp + system monitor. On startup it's around 120 mb.

Virtually there's a boost in everything!

 

And yes, the smooth scroll of firefox works fantastic now.




One thing I really hate about Ubuntu as compare to gentoo is this "version" system of Ubuntu...8.04, 8.10, 9.04, 9.10 etc....

What's the utility...why not just do it Gentoo style?...only the packages get upgraded.

I'm maintaining Ubuntu on a thumb drive (I get lots of request to install Linux, but I only install Ubuntu) and I find it difficult to maintain cause of this version system.

The reason I asked was the benchmarks I have read on compiling have only shown about 2% difference in speed.

---

### Post by DeusExM1 on 2009-11-17
I agree with you that Gentoo performs better (it has to, because u optimize the OS for your system).

I have tried it myself and found it to be true. Having said that, i must also say that it was the biggest waste of time I have ever spent on any OS. 

It takes a pretty good amount of effort to set everything up. (mine took several days!). Gentoo is not for everyone thats for sure. Even though now i know how to work with Gentoo i would still choose Ubuntu over it any day. I dont think its necessary to optimize every little thing, considering that we live in a world of dual and quad core processors now.

But thats my personal standpoint. Im sure some people would choose gentoo... But Ubuntu has my vote.

---

### Post by HappyFeet on 2009-11-17
> **DeusExM1 said:**
> I dont think its necessary to optimize every little thing, considering that we live in a world of dual and quad core processors now.


Exactly how I feel. I have a killer rig and don't need any speed tweaks. An OC'd quad-core cpu, and 6gb of fast ram, insure that *everything* is fast. But if you're into spending 3 hours to install VLC, go for it. Because we all know that the half second you save while opening it, is a life changing experience. ;)

---

### Post by dE_logics on 2009-11-17
> **jrusso2 said:**
> The reason I asked was the benchmarks I have read on compiling have only shown about 2% difference in speed.

In that case, one claimed 20% boosts in render times of blender on Gentoo (and I do use blenders...wait I'll try).

aaa huumm...I do not see that much of a difference, but I really don't remember how much time it took...I think it took 24 second in windows, 21 seconds in Ubuntu and right now 18 seconds on Gentoo.

The difference is not in the raw processing power, but the applications which are compiled..if the benchmark tries to keep the custom built kernel out of the way, there will really be no difference.

Benchmark wont account the swift ness of the system...I set my kernel to be a low-latency desktop (lowest of all available options) as a result my system responds even when under heavy load.

So all we can see is performance of the system which is through the compiled applications for the current e.g I've a long download list in mldonkey...it used to take lots of time for mldonkey to load them, but now it reduced from minutes to seconds...the difference?...this is the compiled version of mldonkey with the following advantages - 

1) Optimized only for athlon64 processors
2) The following use flags were activated during compilation - "gtk ocamlopt -doc -fasttrack -gd -gnutella -guionly -magic"

So most probably the precomputed application was built with these options in mind, here they are not required, so they are removed...as a result less number of libraries loaded, and so the binary is faster and consumes less memory...this is the advantage apart from the customization.

Notice if you just prepare the binaries from the source by just "./configure"...you wont see much of the difference, you need to activate the optimizations, the requirements as listed in ./configure --help; e.g. in banshee, you can ./configure --disable-ipod so as to not let banshee compile with ipod support...I have such use flags set in Gentoo...so it does this for all packages...I've even disable virtualization, the Ubuntu kernel is build with it's support...this is just an example.

---

### Post by dE_logics on 2009-11-17
> **DeusExM1]i must also say that it was the biggest waste of time I have ever spent on any OS. [/QUOTE]

Oh yes, but just initially.

For e.g. kat is not in the portage tree, and I'm trying to compile it through the given ebuilds on bugzilla of Gentoo said:**
> "I dont think its necessary to optimize every little thing, considering that we live in a world of dual and quad core processors now."

Yes, maybe, but the responsiveness is still very much improved...I mean I do scientific calculations, and converting audio...in all that there's a significant boost cause all this takes time.

A big e.g is Wine.

If you're not doing hefty tasks like compressing with lpaq/paq, less audio conversion, only simple tasks like word processing, simple calc calculations...then a binary distribution is right for you...but still you would really prefer Gentoo on a netbook...you can compile the binaries for it on another system.

---

### Post by Zoot7 on 2009-11-18
> **DeusExM1 said:**
> Having said that, i must also say that it was the biggest waste of time I have ever spent on any OS.
Haha, gotta agree there. :)

Although, I did learn a lot about the inner workings of Linux by using Gentoo, for that I don't think there's any better distro out there.

---

### Post by GodLikeCreature on 2009-11-18
I cannot relate to the OP, to be honest.  I do professional audio recording with Ubuntu, have done my share of video manipulation and  encoding, and many tasks that any Windows user would consider heavy on the system.  I have done some of those while listening to music, browsing the web, watching movies, etc. 

I am yet to see my system monitor reach the 1GB RAM mark!

Sometimes, when encoding video, I may see one of the 4 cores go to 100% eventually, but the CPU charge is more than reasonable.

I personally think Ubuntu provides a very balanced compromise between ease of use and performance, it has IMHO the strongest community support (something I have learned to value very much), and has lots of applications available.

And btw, I like trying different distros, and have a PC solely dedicated to that.  Lately I have installed Mandriva 2010, OpenSuSE 11.2 and Fedora 12.  If I compare any of those to Karmic, I can hardly tell any difference in performance, at least nothing that 99.9% of the users would care about, so I think that the statement about performance being negligible across distros is not inaccurate.

---

### Post by dE_logics on 2009-11-18
Well then, try Gentoo, but do read the docs well and tweak the system not just blindly configure it.

Ok...it will take you time to learn Gentoo.

---

### Post by HappyFeet on 2009-11-19
> **dE_logics said:**
> but still you would really prefer Gentoo on a netbook

Gentoo isn't the only thing that will run well on a netbook. I wrote a tutuorial for doing a cli install of ubuntu on the eeepc, and I can assure you it was *very* fast. I don't think doing all that extra work to get gentoo working on a netbook, is worth it. But that's just me. If I ever need to have a light install, I'll do a cli of debian or ubuntu. But if gentoo is your thing, go for it. It's all linux, right?

---

### Post by waspbr on 2009-11-19
I gotta say I am curious now, I use my desktop for some scientific calculations with OpenFOAM and I think I might just give gentoo a shot and see if there is a significant performance increase. In fact I am downloading it as we speak. 

Does anyone know any noob guides for gentoo?

---

### Post by longtom on 2009-11-19
> **waspbr said:**
> Does anyone know any noob guides for gentoo?

[http://dkap.info/plug/20050202-gentoo/](http://dkap.info/plug/20050202-gentoo/)

[http://www.gentoo.org/doc/en/handbook/#doc_chap2](http://www.gentoo.org/doc/en/handbook/#doc_chap2)

You, my friend, have a long journey in front of you.  May it be a rewarding experience for you....

---

### Post by Bachstelze on 2009-11-19
Pure placebo effect. Anyone who knows anything about compilers will tell you that compile-time optimisations matter very little for most applications.

---

### Post by mivo on 2009-11-19
> **Bachstelze said:**
> Pure placebo effect. Anyone who knows anything about compilers will tell you that compile-time optimisations matter very little for most applications.

That may be so, but doesn't change the fact that Ubuntu has become bloated and is relatively slow if compared to manually set-up distros like Gentoo or Arch. Ubuntu "feels" slow when you launch apps, and Firefox in Ubuntu is noticeably slower than in other distros (except Fedora 12, which seems to perform on the same level as Ubuntu).

I'm not saying Gentoo is necessarily worth the extra time and effort it requires, but it's not just a placebo effect that it is faster than Ubuntu.

---

### Post by dE_logics on 2009-11-19
> **HappyFeet said:**
> Gentoo isn't the only thing that will run well on a netbook. I wrote a tutuorial for doing a cli install of ubuntu on the eeepc, and I can assure you it was *very* fast. I don't think doing all that extra work to get gentoo working on a netbook, is worth it. But that's just me. If I ever need to have a light install, I'll do a cli of debian or ubuntu. But if gentoo is your thing, go for it. It's all linux, right?

Yep, I prefer the hard way...Gentoo.

[QUOTE=waspbr]Does anyone know any noob guides for gentoo?[/QUOTE]


aaa...no.

The best is the Gentoo handbook - 

[http://www.gentoo.org/doc/en/handbook/index.xml](http://www.gentoo.org/doc/en/handbook/index.xml)

If you do not understand that, you're not ready for Gentoo.

> I use my desktop for some scientific calculations with OpenFOAM

Thanks dude.


I just saw it in the Gentoo repositories and I think you're gonna have a very bad time compiling it.

[QUOTE=Bachstelze]
Anyone who knows anything about compilers will tell you that compile-time optimisations matter very little for most applications.[/QUOTE]

I have around 20 use flags in effect if emerge Openoffice, in cause of OpenFOAM, it's 2, but including the dependencies, it makes up a total of ~25 use flags declarations.

---

### Post by grayrainbow on 2009-11-19
> **Bachstelze said:**
> Pure placebo effect. Anyone who knows anything about compilers will tell you that compile-time optimisations matter very little for most applications.
I do hope people around installers don't think such a ********(is someone every use program compile in debug mode?). It will be gorges if installer do inplace compilation(which microsoft already present with latest .NET for user space application), and a lot of graphics card driver use some part of it. Hope it will be done for kernel and for every package in distribution in the future.

---

### Post by dE_logics on 2009-11-21
You all might be interested in this - 


[http://gcc.gnu.org/onlinedocs/gcc/i386-and-x86_002d64-Options.html](http://gcc.gnu.org/onlinedocs/gcc/i386-and-x86_002d64-Options.html)

---

### Post by dE_logics on 2009-11-21
So I've just changed my use flags to -march=athlon64-sse3

---

### Post by renkinjutsu on 2009-11-21
> **GodLikeCreature said:**
> I cannot relate to the OP, to be honest.  I do professional audio recording with Ubuntu, have done my share of video manipulation and  encoding, and many tasks that any Windows user would consider heavy on the system.  I have done some of those while listening to music, browsing the web, watching movies, etc. 

I am yet to see my system monitor reach the 1GB RAM mark!

Sometimes, when encoding video, I may see **one of the 4 cores** go to 100% eventually, but the CPU charge is more than reasonable.

I personally think Ubuntu provides a very balanced compromise between ease of use and performance, it has IMHO the strongest community support (something I have learned to value very much), and has lots of applications available.

And btw, I like trying different distros, and have a PC solely dedicated to that.  Lately I have installed Mandriva 2010, OpenSuSE 11.2 and Fedora 12.  If I compare any of those to Karmic, I can hardly tell any difference in performance, at least nothing that 99.9% of the users would care about, so I think that the statement about performance being negligible across distros is not inaccurate.

You don't use multiple threads?! SHAME!!

---

### Post by JBAlaska on 2009-11-21
Well, I'm to L337 to use Ubuntu and I'm gonna post about it in the Ubuntu forum!!

j/k Lol's

---

### Post by renkinjutsu on 2009-11-21
> **dE_logics said:**
> Yep, I prefer the hard way...Gentoo.


Sounds like you'd like [this]("http://www.linuxfromscratch.org/lfs/") more than gentoo

Give it a shot, and tell us how it compares to Gentoo/Ubuntu, then i might try experimenting with it

---

### Post by dE_logics on 2009-11-21
> **renkinjutsu said:**
> You don't use multiple threads?! SHAME!!

:lolflag:

---

### Post by Frak on 2009-11-21
> **Bachstelze said:**
> Pure placebo effect. Anyone who knows anything about compilers will tell you that compile-time optimisations matter very little for most applications.
Aye.

If you feel speed, it's from dependency optimisations, not compile time optimisations.

---

### Post by dE_logics on 2009-11-21
> **renkinjutsu said:**
> Sounds like you'd like [this]("http://www.linuxfromscratch.org/lfs/") more than gentoo

Give it a shot, and tell us how it compares to Gentoo/Ubuntu, then i might try experimenting with it

[http://www.linuxfromscratch.org/lfs/view/stable/chapter03/packages.html](http://www.linuxfromscratch.org/lfs/view/stable/chapter03/packages.html)

Holy god!...this is even more basic than Gentoo!

I think Gentoo used to be the same a few years back...stage 1 tarballs, stage 2, then stage 3...now we start from stage 3.



I have to say it's pretty interesting...I have to try this.

---

### Post by dE_logics on 2009-11-21
> **Frak said:**
> Aye.

If you feel speed, it's from dependency optimisations, not compile time optimisations.

Yes, mostly from dependency optimizations.


But if you have an unusual processor, then he compile time optimizations will actually matter.

Furthermore...can anyone tell me how are the binaries of Ubuntu made?

I mean, what are the optimizations?...O1, O2, O3...

---

### Post by Frak on 2009-11-22
> **dE_logics said:**
> Yes, mostly from dependency optimizations.


But if you have an unusual processor, then he compile time optimizations will actually matter.

Furthermore...can anyone tell me how are the binaries of Ubuntu made?

I mean, what are the optimizations?...O1, O2, O3...
I believe it's -Os, or all O2 flags that do not cause larger resulting binary size.

---

### Post by Regenweald on 2009-11-22
> **mivo said:**
> That may be so, but doesn't change the fact that Ubuntu has become bloated and is relatively slow if compared to manually set-up distros like Gentoo or Arch. Ubuntu "feels" slow when you launch apps, and Firefox in Ubuntu is noticeably slower than in other distros (except Fedora 12, which seems to perform on the same level as Ubuntu).

I'm not saying Gentoo is necessarily worth the extra time and effort it requires, but it's not just a placebo effect that it is faster than Ubuntu.

Have to disagree on the whole 'noticeably slower' thing. Basing my opinions on Phoronix benchmarking reviews of Ubuntu against players like Arch, Fedora and BSD, If I'm going to spend hours or days setting up and OS as opposed to the Ubuntu 15-20 minute install, I don't want to see Ubuntu beating you in any benchmarks and when you win, I don't want head and shoulders, I want you orders of magnitude ahead of Ubuntu. 

This is simply not the case. For all its 'bloat' performance wise Ubuntu is a little ahead in some, a little behind in some. I think that Gentoo, Arch, BSD and Fedora are amazing projects, to name a few, and I could easily install all of them, but
[LIST=1]
[*]they have no mission critical tech that I absolutely need
[*]I already installed Ubuntu :)
[*]the effort of reinstallation is way too much to save an estimated few minutes over a 1 year period
[/LIST]

Depends on the user i guess ;)

---

### Post by Frak on 2009-11-22
> **mivo said:**
> That may be so, but doesn't change the fact that Ubuntu has become bloated and is relatively slow if compared to manually set-up distros like Gentoo or Arch. Ubuntu "feels" slow when you launch apps, and Firefox in Ubuntu is noticeably slower than in other distros (except Fedora 12, which seems to perform on the same level as Ubuntu).

I'm not saying Gentoo is necessarily worth the extra time and effort it requires, but it's not just a placebo effect that it is faster than Ubuntu.
Apps in Ubuntu are compiled against every concievable dependency available. Just taking firefox for example, out of the 30 or so dependencies (taking a rough estimate) only about 2 or 3 of those are *really *required to have it run.

A user from a forum-I-won't-name-here made a video that named just that if you want to see it. [Link]("http://www.youtube.com/watch?v=tqQMqQxf-Ik&feature=player_embedded") (NSFW)

---

### Post by wilee-nilee on 2009-11-22
> **Frak said:**
> 
A user from a forum-I-won't-name-here made a video that named just that if you want to see it. [Link]("http://www.youtube.com/watch?v=tqQMqQxf-Ik&feature=player_embedded") (NSFW)

All four are good times.;)

---

### Post by brij on 2009-11-22
i think ubuntu and gentoo has their own pros and cons. I use both distros but when it comes to choose distro for server i would go with gentoo coz its powerful tool portage i know it takes a hell amount of time when you install a package but its time well spent. While ubuntu is the best distro when you want it for desktop. Everything works out of the box drivers and all that stuff. 

Its just my opinion as i said i use both and i am happy with both of them

---

### Post by dE_logics on 2009-11-22
> **Frak said:**
> I believe it's -Os, or all O2 flags that do not cause larger resulting binary size.

Yes, that is what we exactly do not know in Ubuntu...these binaries are built on the devloper's idea.

There is around 5 - 7% performance difference if lpaq9m is compiled with O2 are instead of to Os.

Notice, even if the performance difference is 2%...it sums up to a very large value is adopted system wide, including the libraries (if you know calculus you will understand what I mean).

---

### Post by dE_logics on 2009-11-22
> **Regenweald said:**
> Have to disagree on the whole 'noticeably slower' thing. Basing my opinions on Phoronix benchmarking reviews of Ubuntu against players like Arch, Fedora and BSD, If I'm going to spend hours or days setting up and OS as opposed to the Ubuntu 15-20 minute install, I don't want to see Ubuntu beating you in any benchmarks and when you win, I don't want head and shoulders, I want you orders of magnitude ahead of Ubuntu. 

This is simply not the case. For all its 'bloat' performance wise Ubuntu is a little ahead in some, a little behind in some. I think that Gentoo, Arch, BSD and Fedora are amazing projects, to name a few, and I could easily install all of them, but
[LIST=1]
[*]they have no mission critical tech that I absolutely need
[*]I already installed Ubuntu :)
[*]the effort of reinstallation is way too much to save an estimated few minutes over a 1 year period
[/LIST]

Depends on the user i guess ;)

Same way, personally I find lots of difference and using Gentoo is very worth it.

I too do not have that much amount of time, but I did it in installments...I used the flexibly of Gentoo to install it through my installed Ubuntu...yes it took me about 10 months (I did it in installments) to clear about everything but finally I think it was worth it.

Furthermore Gentoo cannot be benchmarked...it's configuration is all about the user...you can make is dead slow...you can make it super fast or super small...it's all on you.

So we don't know what Phoronix did.

Oh yes - 

[http://www.linux-mag.com/id/7574/1/](http://www.linux-mag.com/id/7574/1/)


I guess my theory was right.

That was just through the optimization...no use flags mentions...use flags will add major to the swiftness.

---

### Post by nikhilbhardwaj on 2009-11-22
lfs is really hardcore
i gave it a shot
but eventually got bored
just too much compiling to do

ubuntu is bloated
gentoo is faster
but arch is as fast as gentoo and no compiling too

---

### Post by Arup on 2009-11-22
Its just a perception that Ubuntu is bloated, there is not a single benchmark or substantiated evidence out there that shows Ubuntu or Fedora or SuSE lagging behind so called hardcore distros apart from bragging rights and placebo effect.

In a recent Fedora 12RC versus Ubuntu Karmic, Ubuntu managed to edge out Fedora in the majority of tests, the margins were small but mind you, we are talking about the so called bloated OS ;) 

I for one would rather take the supreme convenience of Ubuntu with bloat over others.

---

### Post by ~sHyLoCk~ on 2009-11-22
Compiling everything gets boring after a while. [Here]("http://pdg86.wordpress.com/2009/11/18/rant-arch-or-gentoo/")'s my thoughts on gentoo. 
I'm happy with a slightly [completely negligible] slower system, rather than spending hours compiling stuffs to work. And not just once, repeating the same process on each upgrades. My SUSE is pretty fast enough for me. ;)

---

### Post by mivo on 2009-11-22
> **Arup said:**
> Its just a perception that Ubuntu is bloated, there is not a single benchmark or substantiated evidence out there that shows Ubuntu or Fedora or SuSE lagging behind so called hardcore distros apart from bragging rights and placebo effect.

Are we talking about the benchmarks that were done with distros having different kernels, different versions of drivers and components, etc? ;) Oh, and that test of a final release with the first wave of updates compared to a RC of Fedora. Most competent Linux users on the Phoronix forums considered these so-called benchmarks useless and just for show.

I don't really need other people's experiences on their computers with their stock installations (and it is only out of the box installations that are used) to tell whether Arch, to name one, runs noticeably faster on my setups with my configuration and my software. Boot times are shorter (unrelated, but worth mentioning: the 9.10 Live CD takes over 4 minutes - I have never seen a slower Live CD), applications start much faster, everything is snappier. Not to mention the lower RAM usage even in very similar DE/software environments. After an Ubuntu install, I do the same I do after a bundled XP install: I spent time removing all the unwanted stuff. In the same time I can set up an Arch system that will not need a reinstall twice a year.

Now, if you are one of those users who run the Live CD every six months and click on the "install" button without really tweaking anything or adjusting it to your hardware, your needs and your environment, those benchmarks may have a value to you. To others, the performance differences are obvious. As Frak said, just look at the dependencies of some Ubuntu apps. If you think that has no impact on performance, well, okay.

---

### Post by Arup on 2009-11-22
> **mivo said:**
> Are we talking about the benchmarks that were done with distros having different kernels, different versions of drivers and components, etc? ;) Oh, and that test of a final release with the first wave of updates compared to a RC of Fedora. Most competent Linux users on the Phoronix forums considered these so-called benchmarks useless and just for show.

I don't really need other people's experiences on their computers with their stock installations (and it is only out of the box installations that are used) to tell whether Arch, to name one, runs noticeably faster on my setups with my configuration and my software. Boot times are shorter (unrelated, but worth mentioning: the 9.10 Live CD takes over 4 minutes - I have never seen a slower Live CD), applications start much faster, everything is snappier. Not to mention the lower RAM usage even in very similar DE/software environments. After an Ubuntu install, I do the same I do after a bundled XP install: I spent time removing all the unwanted stuff. In the same time I can set up an Arch system that will not need a reinstall twice a year.

Now, if you are one of those users who run the Live CD every six months and click on the "install" button without really tweaking anything or adjusting it to your hardware, your needs and your environment, those benchmarks may have a value to you. To others, the performance differences are obvious. As Frak said, just look at the dependencies of some Ubuntu apps. If you think that has no impact on performance, well, okay.

The benchmarks done were on same kernels or at least close to each other. As another poster pointed out, the so called faster distros didn't set the benchmarks on fire, nor did they manage to surpass Ubuntu to a greater degree, few milliseconds here or there hardly makes any difference but to fans of so called fast distros, its like manna from heaven. The point is that every six months, the Ubuntu staff at the cost of rebuttal from some users tweak their distros quite well so there is really no need to tweak them further at the cost of stability. Speaking of dependencies, its those same dependencies that makes a first time user feel at home with Ubuntu, try peddling a hardcore compile all disto to a person migrating from Windows, suffice to say he or she would gladly go back to Windows in a flash. Speaking of install, it takes maximum of 15 minutes to install Ubuntu every six months or I can stick to a LTS version in case I don't wish to do so. 15 minutes for a spanking brand new distro is a little price to pay considering what we gain.

Now for some, the placebo effect or the effect of few milliseconds may mean a lot and for some, no matter how fast Ubuntu is, it will never be faster than their so called favorite hard core distro. Speaking of speed, sidux is quite snappy, in fact as snappy as the so called fast distros. Even the KDE version runs fast, its highly optimized and the xfce version is a scorcher, however, friendly it is not. Everything is cli and I wouldn't dare recommend that to a new or casual Linux user just because he or she can gain a few miliseconds here or there.

---

### Post by Regenweald on 2009-11-22
> **Arup said:**
> The benchmarks done were on same kernels or at least close to each other. As another poster pointed out, the so called faster distros didn't set the benchmarks on fire, nor did they manage to surpass Ubuntu to a greater degree, few milliseconds here or there hardly makes any difference but to fans of so called fast distros, its like manna from heaven. The point is that every six months, the Ubuntu staff at the cost of rebuttal from some users tweak their distros quite well so there is really no need to tweak them further at the cost of stability. Speaking of dependencies, its those same dependencies that makes a first time user feel at home with Ubuntu, try peddling a hardcore compile all disto to a person migrating from Windows, suffice to say he or she would gladly go back to Windows in a flash. Speaking of install, it takes maximum of 15 minutes to install Ubuntu every six months or I can stick to a LTS version in case I don't wish to do so. 15 minutes for a spanking brand new distro is a little price to pay considering what we gain.

Now for some, the placebo effect or the effect of few milliseconds may mean a lot and for some, no matter how fast Ubuntu is, it will never be faster than their so called favorite hard core distro. Speaking of speed, sidux is quite snappy, in fact as snappy as the so called fast distros. Even the KDE version runs fast, its highly optimized and the xfce version is a scorcher, however, friendly it is not. Everything is cli and I wouldn't dare recommend that to a new or casual Linux user just because he or she can gain a few miliseconds here or there.

Exactly, no one is saying that the other distros are not milli/seconds faster or telling you not to like or use them. You like the DIY distros for your reasons. We like Ubuntu for ours, and don't mind a few seconds in a few benchmarks. Can't we simply enjoy computing ? ;)

---

### Post by kevCast on 2009-11-22
Gentoo is OK.

---

### Post by dE_logics on 2009-11-23
> **Arup said:**
> Its just a perception that Ubuntu is bloated, there is not a single benchmark or substantiated evidence out there that shows Ubuntu or Fedora or SuSE lagging behind so called hardcore distros apart from bragging rights and placebo effect.

In a recent Fedora 12RC versus Ubuntu Karmic, Ubuntu managed to edge out Fedora in the majority of tests, the margins were small but mind you, we are talking about the so called bloated OS ;) 

I for one would rather take the supreme convenience of Ubuntu with bloat over others.

What bout the 1200 packages by default?...On Ubutnu I had like 1500 package installed and with the same software set I have ~750 in Gentoo.

And what bout this - 

[http://www.linux-mag.com/id/7574/1/](http://www.linux-mag.com/id/7574/1/)

What about Gimp starting at 3 seconds instead of 30?...what bout the smooth scroll in Firefox?...explicitly stating, if you're an advanced user and do not plan to switch to Gentoo or arch; it's a shame!

> **~sHyLoCk~ said:**
> Compiling everything gets boring after a while. [Here]("http://pdg86.wordpress.com/2009/11/18/rant-arch-or-gentoo/")'s my thoughts on gentoo. 
I'm happy with a slightly [completely negligible] slower system, rather than spending hours compiling stuffs to work. And not just once, repeating the same process on each upgrades. My SUSE is pretty fast enough for me. ;)

I do not understand why do people forget the utility of virtual desktops.

Tip, at night before you goto sleep make a bash script - 

emerge --update --deep --world
emerge --depclean
revdep-update

That's about it.

[QUOTE=Arup]nor did they manage to surpass Ubuntu to a greater degree, few milliseconds here or there hardly makes any difference[/QUOTE]

Firefox warm startup times - 

2 -> 1 second diff = 1000 ms

Gimp - 
30 -> 3 = 27000 ms

start up - 

~90 -> 30 = 60000ms

Openoffice warm startup (notice, it's precompile and installed on Gentoo) - 
2 -> 1 = 1000ms


TONS more...

> Speaking of dependencies, its those same dependencies that makes a first time user feel at home with Ubuntu, try peddling a hardcore compile all disto to a person migrating from Windows, suffice to say he or she would gladly go back to Windows in a flash. Speaking of install, it takes maximum of 15 minutes to install Ubuntu every six months or I can stick to a LTS version in case I don't wish to do so. 15 minutes for a spanking brand new distro is a little price to pay considering what we gain.

You're right about this but what about the missing customization?

And what do you mean by reinstall?...you can always upgrade.

I used Ubtuntu for 7 - 8 months (that all the experience on Linux, switched to Gentoo around a month from now) yes, the distro was slow but the speeds were around the same throughout (although it slows down major when continuously operating.)


An yes, also see to the chaos theory, a small optimization in each library and binary will result in a massive optimization in the speeds of the whole distro.

> Everything is cli and I wouldn't dare recommend that to a new or casual Linux user just because he or she can gain a few miliseconds here or there.

Notice, we're not talking about new users.

[QUOTE=Regenweald]
Can't we simply enjoy computing ?[/QUOTE]

It is more enjoyable now when I do not have to set the core speed to max or 1.6 or 800 manually all the time and yet the lap is MUCH faster than Ubtunu and I'm sorta ok with the speed.

The compilation is done in the background...I hardly notice!

---

### Post by jacobs444 on 2009-11-23
> **dE_logics said:**
> In general speed difference, startup times, shutdown times, ok don't consider these 2 anyway, so take a look at other things -- Thunar is faster.

Warm startups of openoffice dropped form 5 to 6 seconds to ~2 seconds (notice, I'm still using binary packages for openoffice.

Gimp loads in ~3 seconds...in Ubuntu it was a hefty ~20.

System is swift even if CPU is set to on demand.

Firefox is VERY fast

Right now the system is using 270 mb of physical memory depite 2 tabs in firefox being opend + parcellite running + gnome-ppp + system monitor. On startup it's around 120 mb.

Virtually there's a boost in everything!

And yes, the smooth scroll of firefox works fantastic now.




One thing I really hate about Ubuntu as compare to gentoo is this "version" system of Ubuntu...8.04, 8.10, 9.04, 9.10 etc....

What's the utility...why not just do it Gentoo style?...only the packages get upgraded.

I'm maintaining Ubuntu on a thumb drive (I get lots of request to install Linux, but I only install Ubuntu) and I find it difficult to maintain cause of this version system.

open office on karmic, and a 4 year old pc- 7 seconds/ firefox=3/gimp 5/ firefox works great, scrolls smooth, 300mb used with gimp firefox and open office, open.

i for one used gentoo, and even when optimized only noticed a 1-1.5 sec shave off anything. Honestly slackware with xfce was faster for me than gentoo, and way easier to install- yet harder to find extra packages for.

---

### Post by dE_logics on 2009-11-23
> **jacobs444 said:**
> open office on karmic, and a 4 year old pc- 7 seconds/ firefox=3/gimp 5/ firefox works great, scrolls smooth, 300mb used with gimp firefox and open office, open.

i for one used gentoo, and even when optimized only noticed a 1-1.5 sec shave off anything. Honestly slackware with xfce was faster for me than gentoo, and way easier to install- yet harder to find extra packages for.

Openoffice in karmic is a modified version...install the original and see.

May I see your make.conf and pls post your .config of your kernel.

And yes, I forgot, I'm using broken graphs drivers...opensource ATI.

---

### Post by ~sHyLoCk~ on 2009-11-23
> **dE_logics said:**
> 
I do not understand why do people forget the utility of virtual desktops.

Tip, at night before you goto sleep make a bash script - 

emerge --update --deep --world
emerge --depclean
revdep-update

That's about it.


Because that makes maintenance easier? Just blindly running the script? It's like taking care of a 1month old baby. You need to give it constant attention.

That doesn't take care of the time factor either. My PC is always up. Even during the night it's running and doing some work. I don't want to compile all day, all night for some micro seconds speed boost. That's ridiculous. And there's no reason to either. I will obviously use something which gets my job done easily  without much harassment. [This thread]("http://ubuntuforums.org/showthread.php?t=1330907") has a few responses which I feel is the same reason why I don't use it as my main OS.

Don't get me wrong, gentoo was fun at the beginning, when i was learning new stuffs, but then I just use it now for my server. For a regular desktop use, it's overkill.

---

### Post by dE_logics on 2009-11-23
> **~sHyLoCk~ said:**
> Because that makes maintenance easier? Just blindly running the script? It's like taking care of a 1month old baby. You need to give it constant attention.

That doesn't take care of the time factor either. My PC is always up. Even during the night it's running and doing some work. I don't want to compile all day, all night for some micro seconds speed boost. That's ridiculous. And there's no reason to either. I will obviously use something which gets my job done easily  without much harassment. [This thread]("http://ubuntuforums.org/showthread.php?t=1330907") has a few responses which I feel is the same reason why I don't use it as my main OS.

Don't get me wrong, gentoo was fun at the beginning, when i was learning new stuffs, but then I just use it now for my server. For a regular desktop use, it's overkill.

> emerge --update --deep --keep-going --world
emerge --depclean
revdep-update

And even after an error it will continue...then you can see the errors in the morning.


Ok, Gentoo is hard, but it IS very swift...speed differences are a LOT faster.


Oh I forget...I configured to kernel to make a low latency desktop...so I think it worked; here - 

Processor type and features -> Preemption Model (Voluntary Kernel Preemption (Desktop))  ---> Preemptible Kernel (Low-Latency Desktop)

Ok I've decided to install Gentoo and Ubuntu on a thumb dirve and see the performance difference.

I expect a minimum of 30% performance boosts in Gentoo.

Now this will take time....

---

### Post by Arup on 2009-11-23
GIMP starts in 6 seconds flat here, OO with Java on starts at 8 seconds, these are all cold start up times. So the loss of few seconds to Gentoo is not justifying the switch over. Now if the difference were to be in minutes, then I would think about all the trouble. Right now Ubuntu, Fedora et al are doing a fine job. Lets say on the same hdd, with Perfect disk optimized files, Ubuntu Karmic still is quicker to OO and GIMP than Win7 on Photoshop and OO.

---

### Post by dE_logics on 2009-11-23
> **Arup said:**
> GIMP starts in 6 seconds flat here, OO with Java on starts at 8 seconds, these are all cold start up times. So the loss of few seconds to Gentoo is not justifying the switch over. Now if the difference were to be in minutes, then I would think about all the trouble. Right now Ubuntu, Fedora et al are doing a fine job. Lets say on the same hdd, with Perfect disk optimized files, Ubuntu Karmic still is quicker to OO and GIMP than Win7 on Photoshop and OO.

Ok, so why not compare windows and Gentoo where windows is installed on a Jaguar and Gentoo on a P-I with 32 mb ram?



Windows is a lot faster hu??


Why not post your make.conf and tell me what changes did you made to the kernel before installing Gentoo?

---

### Post by Arup on 2009-11-23
Why bring in Windows here, its pointless, we are talking about so called optimized distros versus regualar ones here aren't we?

---

### Post by dE_logics on 2009-11-23
> **Arup said:**
> Why bring in Windows here, its pointless, we are talking about so called optimized distros versus regualar ones here aren't we?

You missed that point.

You system configurations are different from mine, yours is a better one so obviously it will work faster for you!

Jaguar is a supercomputer.

Why not install the debs given in openoffice.org...try that and see...installing that will make you have all Openoffice components, I'm not sure what will be the performance difference but there was a lot for me.

The actually reason why my system is that swift is cause I configured each and every part of my kernel according to my needs, I made it a low latency desktop (effectively lowering the speeds)...added support for all file systems (that made it slow), removed support for unwanted hardware like ipod, iphone etc... (I removed everything that I do not understand when it comes to the hardware) which reduces the memory usage and increases the boot times, made the kernel for AMD64, many more...it's uncountable it took days to configure the kernel.

Then I optimized my use flags for stuff like - 
Remove support for KDE and GNOME
Use GTK if possible
Do not compile with qt4 and qt3

And yet I say there is a LARGE scope of improvement...for e.g I've included composites which I actually do not need (now I realize...no use with broken graphs drivers).

I have brasero installed and it has a hard dependency on Nautilus...so Gentoo compiles Nautilus in a rather unique way...it doesn't have any buttons...just the file menu and is actually unusable.

If I was using Ubtunu or a source based distribution I would have got a fully fledged Nautilus will all possible dependencies which practically would have installed the whole gnome desktop environment.

How did all this happen?...through use flags, if I would have not set them, my Gentoo would have been just like Ubtunu...slow clumsy and a resource hog.

---

### Post by dE_logics on 2009-11-23
Can you imagine Ktorrent running with 7 MB memory?...in Ubutnu it was 100+!!...it's warm startup times are negligible...same is for firefox.

And this was NEVER...not even to close to this in Ubuntu.

---

### Post by Arup on 2009-11-23
I am aware of Jaguar but brining in Windows doesn't really make it an apt comparison.

As for Open Office, I had installed the .debs on 8.04 a while back as the Scribbler's PPA had an issue with their Hardy built, I didn't find the .deb ones any faster than the ones installed by default. If you take Java out, OO opens up quite quick and you can also use the quick launcher which makes OO launch quite quick.

If I am on an ancient Pentium with 16mb the words slow, bloated and clumsy would come into play, as such, Ubuntu does a swell job with a smaler memory footprint than Win7 on same PC. It gives the convenience of daily use and guess what, I have stopped compiling my own kernel as well, the speed differences are just negligible. I only install nvidia drivers and compile mplayer and x264,ffmpeg to get the latest stuff, not for speed.

---

### Post by dE_logics on 2009-11-23
> and you can also use the quick launcher which makes OO launch quite quick.

Quick launcher for Openoffice???...where?

> If I am on an ancient Pentium with 16mb the words slow

:lolflag::lolflag::lolflag::lolflag::lolflag::lolflag:

Dude, I can't believe this...I'm talking about AMD athlon x2 with a GB of DDR2 ram.

It took (on ubutnu) and still takes me about 20 seconds to start openoffice...no difference this front.

I'll check with java off wait.

You said how much ram?...again?

> Ubuntu does a swell job with a smaler memory footprint than Win7 on same PC.

Ubtunu on my lap consumed 250 MB memory on startup, and now it's 120. And I actually had tweaked Ubuntu to reduce on the resource consumption.

I cant be happier!!



So why don't tell me what efforts did you do to optimize you Gentoo?...I did efforts, I told you, now tell me what you did.

---

### Post by kevCast on 2009-11-23
Someone's on a placebo high.

---

### Post by dE_logics on 2009-11-23
> **kevCast said:**
> Someone's on a placebo high.

I just installed Ubuntu 9.10, and these are the results - 

Firefox consumes the same amount of memory -- ~47MB with Gentoo handbook opened.

Gnome system monitor consumes 8 mb memory on Ubuntu and 5.9 mb memory on Gentoo.

Smooth scroll in Firefox is horrible in Ubtunu...cannot be used where as in Gentoo I can easily use it...it's just a *bit* slow.

Best of all Gentoo uses 120 - 140 mb memory on startup and Ubuntu was using 304.

Now I'm using 2.6.30 on Gentoo and 2.6.31 on Ubtuntu.


I wont be comparing the startups now cause I've installed Ubuntu on a thumbdrive.



NOW tell me who's having placebo...it's basically windowze and Ubtunu newbies who do not know a thing and actually start trying Gentoo...as a result - 

1) Gentoo is of no good

2) Gentoo is a resource hog

3) Gentoo is horrible

And actually Ubuntu as compared to Gentoo is crap!!...how can you compare such a fabulous distribution to such a rubbish nooby resource hog made for windows people?

And I still say my Gentoo can me modified by a great deal to deliver more!...for e.g. now I've removed xcomposites through use flags...that should increase performance...though by a small amount.

---

### Post by Arup on 2009-11-23
And Gentoo can be installed with ease by anyone I suppose, in this day of 4GB memory standard, why even bother. The start up memory that Ubuntu consumes is due to the convenience scripts they have enabled, all that can be turned off at the cost of inconvenience via the start up applet. Let me ask you, what is 8mb versus 5.9mb, you call that a victory for Gentoo after all that hard work. Thats appaling in every sense. So after all the hard work and compilation, all for a 100-200mb gain at the cost of a distro which is definitely not plug and play. You wish everyone trying out Linux should be on Gentoo. If thats the case, its gonna be real lonely in Linux world. Thanks to distros like SuSE, Fedora, Ubuntu, we have Linux as a ever growing popular alternative to Windows in the desktop world.

In the end, I have another question to ask from you? Is it that lonely at the Gentoo forum that you have to come here and call Ubuntu bloated. It seems you come to a forum specifically for Ubuntu users and put them down every chance you get. Whats the point of your presence here may I ask?

---

### Post by falconindy on 2009-11-23
Wow, 4 pages and no one has posted [this](http://funroll-loops.info/) yet.

---

### Post by Arup on 2009-11-23
> **falconindy said:**
> Wow, 4 pages and no one has posted [this](http://funroll-loops.info/) yet.



OMG this is too good, thanks a lot....... :D:D:D

---

### Post by kevCast on 2009-11-23
> **dE_logics said:**
> I just installed Ubuntu 9.10, and these are the results - 

Firefox consumes the same amount of memory -- ~47MB with Gentoo handbook opened.

Gnome system monitor consumes 8 mb memory on Ubuntu and 5.9 mb memory on Gentoo.

Smooth scroll in Firefox is horrible in Ubtunu...cannot be used where as in Gentoo I can easily use it...it's just a *bit* slow.

Best of all Gentoo uses 120 - 140 mb memory on startup and Ubuntu was using 304.

Now I'm using 2.6.30 on Gentoo and 2.6.31 on Ubtuntu.


I wont be comparing the startups now cause I've installed Ubuntu on a thumbdrive.



NOW tell me who's having placebo...it's basically windowze and Ubtunu newbies who do not know a thing and actually start trying Gentoo...as a result - 

1) Gentoo is of no good

2) Gentoo is a resource hog

3) Gentoo is horrible

And actually Ubuntu as compared to Gentoo is crap!!...how can you compare such a fabulous distribution to such a rubbish nooby resource hog made for windows people?

And I still say my Gentoo can me modified by a great deal to deliver more!...for e.g. now I've removed xcomposites through use flags...that should increase performance...though by a small amount.
Optimization myths were dispelled in Gentoo a long time ago, or at least I thought so.

The main interest of Gentoo is USE flags. They really cut the fluff. The optimizations in your make.conf are nice, sure, but they hardly matter for the majority of applications. Resource intensive ones, expect a boost. Things like video editors, 3D modeling software, etc. But pidgin? Brasero? gnome-system-monitor?

Your comparing a completely customized Gentoo install vs a plain Ubuntu one. It's not only make.conf customization, but kernel optimization as well. That's where you going to see a boost. However, you'd see the biggest boost if you'd just drop DEs all together and stick to a window manager and cut down on startup services. You can compile a kernel and run Openbox on Ubuntu as well. You can kill services on Ubuntu.

Your assumption of everyone being an Ubuntu or Windows "newb" is wrong as well. There are many users on these forums that have used a great many operating systems, all catering to different types of users and achieving the same ends with multiple means. I've used Gentoo. It was OK. I didn't like the time it took to compile and didn't see a benefit in it. You do.

C'est la vie.

---

### Post by kelvin spratt on 2009-11-23
Come on guys gentoo is is good but not that good Distros like Sidux is faster, Arch is faster and much lighter on resources than Gentoo/Ubuntu.

---

### Post by kevCast on 2009-11-23
> **kelvin spratt said:**
> Come on guys gentoo is is good but not that good Distros like Sidux is faster, Arch is faster and much lighter on resources than Gentoo/Ubuntu.

...?

---

### Post by kevCast on 2009-11-23
[http://www.linux-mag.com/id/7574/1/]("http://www.linux-mag.com/id/7574/1/")

Recent benchmark between Gentoo with various optimizations and Ubuntu 9.04.

---

### Post by ~sHyLoCk~ on 2009-11-23
One of these days I'm gonna try out funtoo.

---

### Post by Frak on 2009-11-23
> **~sHyLoCk~ said:**
> One of these days I'm gonna try out funtoo.
You should, it's awfully fun.

---

### Post by dE_logics on 2009-11-23
> **Arup said:**
> And Gentoo can be installed with ease by anyone I suppose, in this day of 4GB memory standard, why even bother. The start up memory that Ubuntu consumes is due to the convenience scripts they have enabled, all that can be turned off at the cost of inconvenience via the start up applet. Let me ask you, what is 8mb versus 5.9mb, you call that a victory for Gentoo after all that hard work. Thats appaling in every sense. So after all the hard work and compilation, all for a 100-200mb gain at the cost of a distro which is definitely not plug and play. You wish everyone trying out Linux should be on Gentoo. If thats the case, its gonna be real lonely in Linux world. Thanks to distros like SuSE, Fedora, Ubuntu, we have Linux as a ever growing popular alternative to Windows in the desktop world.

In the end, I have another question to ask from you? Is it that lonely at the Gentoo forum that you have to come here and call Ubuntu bloated. It seems you come to a forum specifically for Ubuntu users and put them down every chance you get. Whats the point of your presence here may I ask?

I'm talking about advanced users only how many times do I have to tell you that?

What I'm trying to say here is that Gentoo does have an advantage when at compared to Ubuntu...and I'm showing it here.


In a world of 4gb ram, 1tb hard disks, and quad core processors...why use an operating system which uses only 304 mb memory on startup and uses so damn less processor.

Why not use Windows 7 which will consume 1/4th of your memory easily and with anti viruses the OS always consuming one full core of your system...so why use Linux?...no security issues, you have lots of resources...install 2 antiviruses and 2 firewalls and your system is secure!!...why use Linux in a windows majority world?


I use linux cause of customization and optimization and that's why I've been using Gentoo to get most out of my hardware; and compiling the programs results in best possible optimization and customization...there is NO doubt in it.

Gimp loads EVERYTHING that I do not need on startup...whereas in Gentoo it's only loading fu-script>>>>result>>>>>fractional startup times and 22.5 mb memory usage as compared to 28 mb of Ubuntu

In my 1gb system having 2 processors, in which I use virtual desktops quiet a lot (songs + photoediting, CAD, firefox, openoffice, lots of thunar instances, lots of compression and administrative tasks) the difference is apparent...Ubutnu is rubbish when it comes to performance.

I'm doing more benchmarks with heavy applications.

---

### Post by Arup on 2009-11-23
Yes you are, by rubbishing Ubuntu every chance you get but the benchmarks and time difference show that Gentoo at the most is just a placebo effect and even if it does have its miniscule advantages, its laughable and a waste of time and effort. Now I know why that site compared Gentoo users to Ricer users, its quite apt.

GIMP loads way faster on my Karmic than PS on Win 7 on the same PC so where is the issue here, you just saved few seconds with your Gentoo installs and thats bragging. LOL!

I don't use Win7 for other reasons, I have the hardware that will run Win7 with ease but thats not why I use Ubuntu and Linux in general for many other reasons and harware definitely is not one of them although yes, Ubuntu feels far snappier than Win7 on my PC. Even with hundred firewalls, hundred AVs Win7 won't be as secure as Ubuntu or Linux. Even the benchmarks posted in this thread indicate very little if any advantage of Gentoo over Ubuntu and yet you keep calling it bloated. Maybe you want Ubuntu to be an unfriendly, unusable distro like Gentoo.

Are you really for spreading Linux or for dooming it forever? With Gentoo you surely will, no one in his or her same mind would ever consider Linux.

And for last time, if Ubuntu is that bloated for you, what the hell are you doing here in Ubuntu forum  apart from spreading FUD. Why not hang out in Ricer/Gentoo forums and sing accolades of how you saved 3 seconds over Ubuntu. ;)

---

### Post by dE_logics on 2009-11-23
> **kevCast said:**
> Optimization myths were dispelled in Gentoo a long time ago, or at least I thought so.> 

When amd64 was launched Gentoo was around 30% faster than any other -- if a new processor is launched, for any binary to get accustomed to it - 

1)First gcc needs to implement the new processor type.

2) Then you gotta wait for the developers to generate the new optimized binaries; that will take atleast a year, and you're very much dependent on the developers BTW.


I wanna remain on the safer and faster side -- just recompile the system after changing your processor type and ensuing you upgrade to the changed GCC -- you will start using your processor to it's top abilities the second day.

Now a days, if you have an athlon (not athlon II) or core 2 duo...the optimizations wont matter, but if you have a xeon, phenom or an absolutely new and very distinct processor..........it's very worth it.

[quote]The main interest of Gentoo is USE flags. They really cut the fluff. The optimizations in your make.conf are nice, sure, but they hardly matter for the majority of applications. Resource intensive ones, expect a boost. Things like video editors, 3D modeling software, etc. But pidgin? Brasero? gnome-system-monitor?

Yes, you're right...I'm looking at this right now...Ktorrent using 7 mb...can you believe that?...I still cant believe it! And I do all the above software you mentioned excluding pidgin...and all at the same time too.

[quote]Your comparing a completely customized Gentoo install vs a plain Ubuntu one. It's not only make.conf customization, but kernel optimization as well. That's where you going to see a boost. 

Yeah, that's what I'm trying to tell these people...they don't understand...they can't customize and say Gentoo is rubbish!...this is insanity!...these people should better stay mum or say away from Gentoo rather than actually degrading the impression of the distribution to public!

> However, you'd see the biggest boost if you'd just drop DEs all together and stick to a window manager and cut down on startup services. You can compile a kernel and run Openbox on Ubuntu as well. You can kill services on Ubuntu.

But the advantages of the USE flags will still remain.

---

### Post by dE_logics on 2009-11-23
> **kevCast said:**
> [http://www.linux-mag.com/id/7574/1/]("http://www.linux-mag.com/id/7574/1/")

Recent benchmark between Gentoo with various optimizations and Ubuntu 9.04.

Yes I did point that out in this tread it self.

Ubuntu is - 

5% slower in monkey audio encoding -- ok does not matter.

57% slower when converting from avi to lavc.

using more CPU in all video playbacks.

Not comparing compilation times -- not required, but it's 11% slower in Apache compilation times, 28% faster mplayer compilation times, 9% faster when compiling mysql.

Draws a whooping 21 frames/second less in Enemy territory, 11 FPS in sudokut, 32 and 43 FPS with O2 and O3 in supertuxkart, 20 FPS in UT2004, 46 FPS in another map of UT, 41 FPS in another map, 23 FPS in another, 47 FPS in the last map.

11.6% in a graphs benchmark

15% slower in RAW to PPM image conversion.

500s slower in Pov-ray when compared with Os and 92 seconds with O2.

26%, 14...............man it's endless...no doubt I feel Gentoo as fast!!...it's not a placebo it has been prove through benchmarks here...and I'm gonna do the same!!...and I've proved my point till now.

---

### Post by dE_logics on 2009-11-23
-------------------------------------------------

***_[COLOR="Red"]Ok that's it...[/COLOR]_***


I'm gonna start a new thread after by own benchmarks have been proven...thread will be Gentoo performance myths.

---

### Post by Frak on 2009-11-23
> **dE_logics said:**
> -------------------------------------------------

***_[COLOR="Red"]Ok that's it...[/COLOR]_***


I'm gonna start a new thread after by own benchmarks have been proven...thread will be Gentoo performance myths.
There's no myth Gentoo has better performance, but it's not because of compilation optimizations. It's because of the dependencies (re: use-flags).

---

### Post by hoppipolla on 2009-11-23
> **Bachstelze said:**
> Pure placebo effect. Anyone who knows anything about compilers will tell you that compile-time optimisations matter very little for most applications.

To be totally fair, I have more commonly heard that it DOES make a speed difference...

Additionally, things like custom-built kernels do make a difference.

I don't know, I haven't done this stuff in ages and have never compiled my GUI for example, but just common belief seems to be that it has an effect...

---

### Post by dE_logics on 2009-11-23
I'm mum...

---

### Post by Arup on 2009-11-23
> **hoppipolla said:**
> To be totally fair, I have more commonly heard that it DOES make a speed difference...

Additionally, things like custom-built kernels do make a difference.

I don't know, I haven't done this stuff in ages and have never compiled my GUI for example, but just common belief seems to be that it has an effect...

I did compile my own Kernel for the heck of it, was common years back when I was on SuSE, guess what, very little if any real world difference in my case.

---

### Post by Frak on 2009-11-24
> **Arup said:**
> I did compile my own Kernel for the heck of it, was common years back when I was on SuSE, guess what, very little if any real world difference in my case.
I had a faster boot time, but that was it.

---

### Post by Arup on 2009-11-24
> **Frak said:**
> I had a faster boot time, but that was it.

Yes but the current Karmic is quite quick to boot as well.

---

### Post by jrusso2 on 2009-11-24
> **hoppipolla said:**
> To be totally fair, I have more commonly heard that it DOES make a speed difference...

Additionally, things like custom-built kernels do make a difference.

I don't know, I haven't done this stuff in ages and have never compiled my GUI for example, but just common belief seems to be that it has an effect...

Yes well it used to be common belief the world is flat and there be dragons here.

If you can't measure it you can't prove it and therefore its not happening.

---

### Post by ~sHyLoCk~ on 2009-11-24
> **Arup said:**
> Yes but the current Karmic is quite quick to boot as well.

You're the first person to say karmic boots fast. If anything, I've found Arch, gentoo, sidux to boot faster than any other distros. Even Jaunty booted faster than karmic. Much faster. openSUSE 11.2 boots quite fast as well. They have this "fast-boot" function, I'm not sure what that is, but it works great.

---

### Post by Arup on 2009-11-24
> **~sHyLoCk~ said:**
> You're the first person to say karmic boots fast. If anything, I've found Arch, gentoo, sidux to boot faster than any other distros. Even Jaunty booted faster than karmic. Much faster. openSUSE 11.2 boots quite fast as well. They have this "fast-boot" function, I'm not sure what that is, but it works great.

Kamric boots faster than Jaunty here and Open SuSE as well. Also gets to functional desktop faster than Jaunty. Sidux is quicker, I will agree but not the KDE version, the XFCE one only.

---

### Post by kevCast on 2009-11-24
> **~sHyLoCk~ said:**
> You're the first person to say karmic boots fast. If anything, I've found Arch, gentoo, sidux to boot faster than any other distros. Even Jaunty booted faster than karmic. Much faster. openSUSE 11.2 boots quite fast as well. They have this "fast-boot" function, I'm not sure what that is, but it works great.
I've got my Slackware 13 install down to 5 second boot.

---

### Post by ~sHyLoCk~ on 2009-11-24
> **kevCast said:**
> I've got my Slackware 13 install down to 5 second boot.

omfg.. I want your /usr/src/linux/.config :p
After tweaking out the smp kernel , removing support for things I didn't need and then adding compact to lilo, I got it to boot in around 20sec. which is quite fast for slack.

---

### Post by kevCast on 2009-11-24
> **~sHyLoCk~ said:**
> omfg.. I want your /usr/src/linux/.config :p
After tweaking out the smp kernel , removing support for things I didn't need and then adding compact to lilo, I got it to boot in around 20sec. which is quite fast for slack.
[http://humanreadable.nfshost.com/sdeg/boot_time.htm]("http://humanreadable.nfshost.com/sdeg/boot_time.htm")

Following that, plus using
```
make defconfig
make menuconfig
```

It's all trial and error. Keep your stock kernel handy, as well as your sanity. ;)

*Edit: Forgot to say you only need to do "make defconfig" once. Considering your choice of distros I'll bet you knew that, but if a random linux googler stumbles across this, I don't want to confuse him/her, or worse, agitate.*

---

### Post by ~sHyLoCk~ on 2009-11-24
Thanks man, will give it a test when I have some time.:D

---

### Post by dE_logics on 2009-11-24
> **Arup said:**
> I did compile my own Kernel for the heck of it, was common years back when I was on SuSE, guess what, very little if any real world difference in my case.

And exactly what did you do?

make menuconfig
<exit>
make && make modules_install?

That's it?


Ok continuing with the benchmarks.

Ktorrent uses 7 mb instead of 14 mb...and is very sluggish Ubuntu.

Inkscape uses 66 mb instead of 80 mb.

Blender is unusable on Ubuntu...the frames per second drops are terrible, by unusable I also mean that the screen swaps with the background if I interact, on minimizing/closing blender I cannot see the desktop...all I see is blender...you have to do some sorta interaction on the whole screen to fix this.


Ubuntu is VERY sluggish in ondemand mode as a result the developers have set it to performance by default.


Despite the phoronix benchmarks and what I'm speaking about here, you ubuntu (Windows Linux) fanboys (those who do not agree with me) say it doesn't make a difference...WOW!!


The reality is compiling from source is the best possible way to optimize your system...you Ubuntu fanboys do not agree cause - 

1) Since you're naively Next>next>finish windows users you are inept of configuring anything in Gentoo or the Linux kernel.

2) You cannot live with the fact that long compilation times (which actually does not make a difference to me since I use my virtual desktops) actually result in dramatic performance boosts through fantastic dependency resolution and right configuration time options.

3) Cause you're Ubuntu fanboys.

4) Since we're not talking new users here, you using Ubuntu manifests that
  4.1) You do not want to make your own custom build system.
  4.2) Do not wanna learn anything.
  4.3) In a full week wont even get a single day free to install such distributions.
  4.3) Do not use your virtual desktops.

---

### Post by jrusso2 on 2009-11-24
I am not saying it doesn't make a difference but the difference is so slight as to not be worth the extra trouble to get a couple of percent.  And not all areas even see that.

Anyone who has read my posts can hardly call me a Ubuntu fanboy or a fanboy of any OS.  I am realistic in the strengths and weaknesses of what I use.

---

### Post by dE_logics on 2009-11-24
> **jrusso2 said:**
> I am not saying it doesn't make a difference but the difference is so slight as to not be worth the extra trouble to get a couple of percent.  And not all areas even see that.

Anyone who has read my posts can hardly call me a Ubuntu fanboy or a fanboy of any OS.  I am realistic in the strengths and weaknesses of what I use.

Phoronix benchmarks showed more than 50% boosts when using non-use-flags-set Gentoo and yet you say the difference is in nanoseconds.


You see I don't compile my software...Gentoo and portage does...it currently running in the background, and I'm not noticing it...it'll be finished in 4-5 hours and I'll just continue working............so that's the effort that you do.



Man...I can't leave Gentoo...The speed and feature (portage) of this distro as compared to Ubuntu is fabulous...Ubuntu is trash in font of Gentoo. I'm getting countless advantages using this and if someone says there are no advantage.........it just freaks me out.

I mean it manifest how did you optimize your Gentoo.........that's what I see here.




I have to say there are major performance optimizations done in Kramic (as compared to 8.10)...I have to say I'm impressed...they have improved virtually everything, but removed wvdial which is very bad.

---

### Post by kelvin spratt on 2009-11-24
> **dE_logics said:**
> And exactly what did you do?

make menuconfig
<exit>
make && make modules_install?

That's it?


Ok continuing with the benchmarks.

Ktorrent uses 7 mb instead of 14 mb...and is very sluggish Ubuntu.

Inkscape uses 66 mb instead of 80 mb.

Blender is unusable on Ubuntu...the frames per second drops are terrible, by unusable I also mean that the screen swaps with the background if I interact, on minimizing/closing blender I cannot see the desktop...all I see is blender...you have to do some sorta interaction on the whole screen to fix this.


Ubuntu is VERY sluggish in ondemand mode as a result the developers have set it to performance by default.


Despite the phoronix benchmarks and what I'm speaking about here, you ubuntu (Windows Linux) fanboys (those who do not agree with me) say it doesn't make a difference...WOW!!


The reality is compiling from source is the best possible way to optimize your system...you Ubuntu fanboys do not agree cause - 

1) Since you're naively Next>next>finish windows users you are inept of configuring anything in Gentoo or the Linux kernel.

2) You cannot live with the fact that long compilation times (which actually does not make a difference to me since I use my virtual desktops) actually result in dramatic performance boosts through fantastic dependency resolution and right configuration time options.

3) Cause you're Ubuntu fanboys.

4) Since we're not talking new users here, you using Ubuntu manifests that
  4.1) You do not want to make your own custom build system.
  4.2) Do not wanna learn anything.
  4.3) In a full week wont even get a single day free to install such distributions.
  4.3) Do not use your virtual desktops.


For your info Insksape uses 46.4mb in my Arch, setup makes Gentoo, a bit heavy does it not and Ubuntu even more so.
But does it really matter when Gentoo needs days to compile. 
Arch takes 2hr and ubuntu. even less it takes months to recover the setup time In Gentoo by lost production.

---

### Post by Arup on 2009-11-24
> **dE_logics said:**
> And exactly what did you do?

make menuconfig
<exit>
make && make modules_install?

That's it?


Ok continuing with the benchmarks.

Ktorrent uses 7 mb instead of 14 mb...and is very sluggish Ubuntu.

Inkscape uses 66 mb instead of 80 mb.

Blender is unusable on Ubuntu...the frames per second drops are terrible, by unusable I also mean that the screen swaps with the background if I interact, on minimizing/closing blender I cannot see the desktop...all I see is blender...you have to do some sorta interaction on the whole screen to fix this.


Ubuntu is VERY sluggish in ondemand mode as a result the developers have set it to performance by default.


Despite the phoronix benchmarks and what I'm speaking about here, you ubuntu (Windows Linux) fanboys (those who do not agree with me) say it doesn't make a difference...WOW!!


The reality is compiling from source is the best possible way to optimize your system...you Ubuntu fanboys do not agree cause - 

1) Since you're naively Next>next>finish windows users you are inept of configuring anything in Gentoo or the Linux kernel.

2) You cannot live with the fact that long compilation times (which actually does not make a difference to me since I use my virtual desktops) actually result in dramatic performance boosts through fantastic dependency resolution and right configuration time options.

3) Cause you're Ubuntu fanboys.

4) Since we're not talking new users here, you using Ubuntu manifests that
  4.1) You do not want to make your own custom build system.
  4.2) Do not wanna learn anything.
  4.3) In a full week wont even get a single day free to install such distributions.
  4.3) Do not use your virtual desktops.


Nope, I optimized the heck out of it, took me quite a few tries to get it right but I did, removed everything non essential, optimized for CPU, changed timer, optimized file system and many more to list and yet, did I see any huge difference, no. Are you ***+uming that you are the only one with knowledge to compile a kernel. Typical Gentoo attitude I see.

You Gentoo/Ricer/Placebo fanboyz would never realize the fact that its just futile. Why should we have to compile our own when Ubuntu does that for us, we concentrate on other stuff that is using the OS, not building it. What do we need that for really? 10 seconds gain here and 60mb gain there. Deny the Phoronix benchmarks all you can but till its proven that a 3 day compiled Gentoo rips apart Ubuntu, Fedora or SuSE, it will remain a fact that its a minuscule gain and that too mostly placebo and nothing else. As they said, 90bhp subcompact with spoilers of a Porsche 934 Kremer Turbo. LOL!


Ubuntu frequency scale is on ondemand here and never felt the need for anything else. Blender works fine, GIMP handles my 25MP RAW images from Alpha 900 with ease. Transmission works for days without any slowdowns, I rip CDs with RipperX and use WinFF to transform movies, absolutely no issues there. All you are doing is spreading FUD against Ubuntu and that too at the Ubuntu forum. You directly compare Ubuntu users with Windows users which is ridiculous but fully expected from someone living on placebos alone. I guess the Gentoo forum must be a lonely place that you have to come down and assert yourself here. Maybe deep down you have the same doubt as to your Gentoo's capabilities and therefore you come down and try and act superior here, point is no one is interested or buying your few seconds of gain it allegedly promises.

---

### Post by Arup on 2009-11-24
> **dE_logics said:**
> Phoronix benchmarks showed more than 50% boosts when using non-use-flags-set Gentoo and yet you say the difference is in nanoseconds.


You see I don't compile my software...Gentoo and portage does...it currently running in the background, and I'm not noticing it...it'll be finished in 4-5 hours and I'll just continue working............so that's the effort that you do.



Man...I can't leave Gentoo...The speed and feature (portage) of this distro as compared to Ubuntu is fabulous...Ubuntu is trash in font of Gentoo. I'm getting countless advantages using this and if someone says there are no advantage.........it just freaks me out.

I mean it manifest how did you optimize your Gentoo.........that's what I see here.




I have to say there are major performance optimizations done in Kramic (as compared to 8.10)...I have to say I'm impressed...they have improved virtually everything, but removed wvdial which is very bad.


Where did you see the 50% boost, more FUD :D

At most it was 10-15% max and that to me is pitiful.

---

### Post by cariboo on 2009-11-24
This thread is turning into a mine's bigger than yours thread. Closed for 24 hours.

Edit: thread reopened

---

### Post by dE_logics on 2010-02-09
Today I did a bit of benchmarks of startup times, and yes, Gentoo was fast.

Gentoo is slow, it's not faster etc... is all a myth. I don't care what people say...point is I've measured and found it to be at least 30% faster (and at a max of 60%). Even time you benchmark Gentoo...it always comes ahead...it's not a matter of doubt that Gentoo is the fastest of the lot...CONSIDERABLY.

People saying Gentoo is slow and all...I just cant believe them. Either they have misconfiguration the system, have not optimized it by that much or are just biased...that's final with me.

---

### Post by Frak on 2010-02-09
> **dE_logics said:**
> Today I did a bit of benchmarks of startup times, and yes, Gentoo was fast.

Gentoo is slow, it's not faster etc... is all a myth. I don't care what people say...point is I've measured and found it to be at least 30% faster (and at a max of 60%). Even time you benchmark Gentoo...it always comes ahead...it's not a matter of doubt that Gentoo is the fastest of the lot...CONSIDERABLY.

People saying Gentoo is slow and all...I just cant believe them. Either they have misconfiguration the system, have not optimized it by that much or are just biased...that's final with me.
Again, people are saying Gentoo is not faster because it is realistically *not faster*. The installation you do with gentoo has less dependencies, and that is why it seems faster. So, technically, yes, Gentoo is faster because it installs less crap along with it. Factually, no, the binaries produced are not much faster than a generic i686 binary. It feels faster, but it is only usually faster by 1% or 2%. Nothing noticeable.

---

### Post by dE_logics on 2010-02-09
> **Frak said:**
> Again, people are saying Gentoo is not faster because it is realistically *not faster*. The installation you do with gentoo has less dependencies, and that is why it seems faster. So, technically, yes, Gentoo is faster because it installs less crap along with it. Factually, no, the binaries produced are not much faster than a generic i686 binary. It feels faster, but it is only usually faster by 1% or 2%. Nothing noticeable.

Yeah, exactly. Virtually only 1 thing matters -- the USE flags and lower dependencies.

The CFLAGS and all only matter when you're on a unique processor...or something very higher end.

However 2 benchmarks by 2 very large organizations say the optimization does matter. Major.

Anyway who know how Ubuntu binaries are made?...may be it does not have any optimizations! and to be generic, some features might be snipped out (for e.g it might just be sse3)...so that might again give a disadvantage

So to be on the safe side...I'm sticking to Gentoo. I don't know how it does it...but it somehow does.

---

### Post by Frak on 2010-02-09
> **dE_logics said:**
> Anyway who know how Ubuntu binaries are made?...may be it does not have any optimizations! and to be generic, some features might be snipped out (for e.g it might just be sse3)...so that might again give a disadvantage

As I recall, Ubuntu binaries are optimized for i686, which is just about every modern processor (i786, i886, and i986). The SSE optimizations rarely make a difference. The program has to be created in such a way to support that. There's more speed in multi-threads than there are in SSE instruction sets. Both of which have to be specially designed. A stock program in Ubuntu and Gentoo with the same dependencies should run roughly at the same speed. The Gentoo version will probably be faster, but by a very, *very* small margin.

---

### Post by MisfitI38 on 2010-02-09
> **dE_logics said:**
> 
For e.g it took me a week to setup my Gentoo box...
Hope you did it on your personal time.
>  
And yes, the Debian pacaking(sic) system needs to learn a lot from Portage...
Heh. I lol'ed.

---

### Post by mamamia88 on 2010-02-09
i tried sabayon before and it was pretty cool but i hated sulfur and eventually went back to ubuntu.  how does gentoo compare to sabayon?

---

### Post by dE_logics on 2010-02-09
> **Frak said:**
> As I recall, Ubuntu binaries are optimized for i686, which is just about every modern processor (i786, i886, and i986). The SSE optimizations rarely make a difference. The program has to be created in such a way to support that. There's more speed in multi-threads than there are in SSE instruction sets. Both of which have to be specially designed. A stock program in Ubuntu and Gentoo with the same dependencies should run roughly at the same speed. The Gentoo version will probably be faster, but by a very, *very* small margin.

You mean if the 2 sources are compiled with identical options.

> **MisfitI38 said:**
> Hope you did it on your personal time.

Heh. I lol'ed.

Does the Debian packaging system know ANYTHING about prelinking?...Portage knows.

What about unstable package support?...what about the masking of these packages? What about the --keep-going option?...this option is missing and it causes a pain in the *** in Debian.

But if you just apt-get install...you wont find a difference.

---

### Post by Satoru-san on 2010-02-10
I use gentoo.

It runs fast and it has no problems once you get it working.

Installing programs takes forever, but I would never go back to ubuntu.

---

### Post by docus on 2010-02-10
I use Arch these days which is fast enough for me, but I'm curious about Gentoo - how does it compare to Arch stability-wise?  After spending a week setting up a Gentoo system it'd be very frustrating if stray updates borked the system...

---

### Post by MisfitI38 on 2010-02-10
> **dE_logics said:**
> You mean if the 2 sources are compiled with identical options.



Does the Debian packaging system know ANYTHING about prelinking?...Portage knows.

What about unstable package support?...what about the masking of these packages? What about the --keep-going option?...this option is missing and it causes a pain in the *** in Debian.

But if you just apt-get install...you wont find a difference.
Hope you live a looooooong time, because the time you save by prelinking may just negate your compile times and 7 days to set up your system by the time you turn 120 years old.
There simply is no argument to be made if you are trying to brag about Gentoo speed, as you have mentioned several times in this thread already. Simple arithmetic proves that the milliseconds you save on application startup will never offset the time required for compiling or system maintenance.
Gentoo is a great system, but it does not need senseless fanboi rhetoric or trolling to prove its quality.

---

### Post by Satoru-san on 2010-02-11
> **docus said:**
> I use Arch these days which is fast enough for me, but I'm curious about Gentoo - how does it compare to Arch stability-wise?  After spending a week setting up a Gentoo system it'd be very frustrating if stray updates borked the system...
Do you even have to ask? Arch is EXTREMLY unstable, however you could make gentoo as unstable if you run USE="*" and "~x86" and use overlays for everything, and use overnight ebuilds. Then you are on the bleeding and not working edge.

Me? I prefer a stable system that runs fast and does what I want it to do. I run stable everything, I compile my own kernel, I like doing it, I update my kernel everytime there is a new stable one.

Gentoo isnt so much hard to install (unless you dont have internet) as it is hard to get Xorg working ;) Especially if you have an ATI r600 or r700 card.

Should run this one :)
```
for f in `qlist -IC`; do emerge -uDvNt $f | grep ebuild; done
```Cheers.

---

### Post by ~sHyLoCk~ on 2010-02-11
> **Satoru-san said:**
> Arch is EXTREMLY unstable
yup specially when u cant figure out what b0rked ur system as u didn't care 'nuff to read the news and mailing lists! Just by a pacman -Syu your computer may burst into flames and you may catch fire. :o STAY AWAY FROM ARCH!!

> **Satoru-san said:**
>  I compile my own kernel, I like doing it, I update my kernel everytime there is a new stable one.

You can do that with any distro.:popcorn:

---

### Post by kevin01123 on 2010-02-12
> **~sHyLoCk~ said:**
> yup specially when u cant figure out what b0rked ur system as u didn't care 'nuff to read the news and mailing lists! Just by a pacman -Syu your computer may burst into flames and you may catch fire. :o STAY AWAY FROM ARCH!!



You can do that with any distro.:popcorn:

Giving a heads up on the mailing lists is one thing, but do you really expect a user to comb through the mailing lists to try to find their exact problem? If the developers are shipping broken code, and then gabbing about it on arch-devel, something is wrong. And if they users are gabbing about it on the mailing lists, then the code obviously wasn't tested before it was shipped.

I understand that testing every package on a distribution such as Arch is infeasible, and the poster to which you are replying should have known that. However, the idea that things like this could have been prevented had the user read the mailing lists is scapegoating.

---

### Post by ~sHyLoCk~ on 2010-02-12
> **kevin01123 said:**
> Giving a heads up on the mailing lists is one thing, but do you really expect a user to comb through the mailing lists to try to find their exact problem? If the developers are shipping broken code, and then gabbing about it on arch-devel, something is wrong. And if they users are gabbing about it on the mailing lists, then the code obviously wasn't tested before it was shipped.

I understand that testing every package on a distribution such as Arch is infeasible, and the poster to which you are replying should have known that. However, the idea that things like this could have been prevented had the user read the mailing lists is scapegoating.

Yes if you use Arch, read the forums! Read the announcements, read the news! Else don't use Arch and blame it on the devs. Arch is not for the lazy. You don't have to read the mailing lists, just be updated with the news and announcements! Don't just blindly run pacman -Syu.

---

### Post by slira on 2010-03-17
> **MisfitI38 said:**
> (...)
Gentoo is a great system, but it does not need senseless fanboi rhetoric or trolling to prove its quality.

Yes, you're right. I had ubuntu in different machines and was really happy with it. However in my laptop I'm running gentoo now. It is faster on the daily work and very stable - never crashed until now; but installing and customising for the 1st time takes time... and compiling is (very) CPU demanding. Nevertheless I'm happy with it. One of the best things is that you're never "out-of-date" because your distro has no longer support (exactly what happened with me with ubuntu... no repositories, no apt-get, dependencies headhaech, etc.).

---

### Post by bradmayne04 on 2010-03-17
I tried a live disk of gentoo the other day.  Played w/ it for about one hour.  I wasn't thrilled when it couldn't even find the ethernet controller never mind the wireless card.  Needless to say I'm not going to deal w/ something like that when there are soooooo many other distro's out there. Say what you will ubuntu may be for linux babies but I'm all for the usability!!

---

### Post by Shining Arcanine on 2010-03-18
> **Arup said:**
> And Gentoo can be installed with ease by anyone I suppose, in this day of 4GB memory standard, why even bother. The start up memory that Ubuntu consumes is due to the convenience scripts they have enabled, all that can be turned off at the cost of inconvenience via the start up applet. Let me ask you, what is 8mb versus 5.9mb, you call that a victory for Gentoo after all that hard work. Thats appaling in every sense. So after all the hard work and compilation, all for a 100-200mb gain at the cost of a distro which is definitely not plug and play. You wish everyone trying out Linux should be on Gentoo. If thats the case, its gonna be real lonely in Linux world. Thanks to distros like SuSE, Fedora, Ubuntu, we have Linux as a ever growing popular alternative to Windows in the desktop world.

In the end, I have another question to ask from you? Is it that lonely at the Gentoo forum that you have to come here and call Ubuntu bloated. It seems you come to a forum specifically for Ubuntu users and put them down every chance you get. Whats the point of your presence here may I ask?

Doing comparisons between distributions can reveal strengths and weaknesses of each, from which everyone benefits because the weaknesses will be identified for improvement and the strengths can be studied to see why they are strong.

By the way, having more hardware resources now then in the past means that the time it takes to compile software is reduced, making it less of a hassle to wait for things to compile. That leads to the question, why bother using a distribution whose package maintainers compile the software for you? It certainly is not optimized for your system and having every obscure feature included in them will make software take longer to start, as dE_logics showed with some numbers for the load times of various software packages between Gentoo and Ubuntu.

> **kevCast said:**
> [http://www.linux-mag.com/id/7574/1/]("http://www.linux-mag.com/id/7574/1/")

Recent benchmark between Gentoo with various optimizations and Ubuntu 9.04.

The general consensus on the Gentoo forums is that those benchmarks are flawed:

[http://forums.gentoo.org/viewtopic-t-817950.html](http://forums.gentoo.org/viewtopic-t-817950.html)

> **Arup said:**
> Yes you are, by rubbishing Ubuntu every chance you get but the benchmarks and time difference show that Gentoo at the most is just a placebo effect and even if it does have its miniscule advantages, its laughable and a waste of time and effort. Now I know why that site compared Gentoo users to Ricer users, its quite apt.

GIMP loads way faster on my Karmic than PS on Win 7 on the same PC so where is the issue here, you just saved few seconds with your Gentoo installs and thats bragging. LOL!

I don't use Win7 for other reasons, I have the hardware that will run Win7 with ease but thats not why I use Ubuntu and Linux in general for many other reasons and harware definitely is not one of them although yes, Ubuntu feels far snappier than Win7 on my PC. Even with hundred firewalls, hundred AVs Win7 won't be as secure as Ubuntu or Linux. Even the benchmarks posted in this thread indicate very little if any advantage of Gentoo over Ubuntu and yet you keep calling it bloated. Maybe you want Ubuntu to be an unfriendly, unusable distro like Gentoo.

Are you really for spreading Linux or for dooming it forever? With Gentoo you surely will, no one in his or her same mind would ever consider Linux.

And for last time, if Ubuntu is that bloated for you, what the hell are you doing here in Ubuntu forum  apart from spreading FUD. Why not hang out in Ricer/Gentoo forums and sing accolades of how you saved 3 seconds over Ubuntu. ;)

Having a distribution like Ubuntu is a good thing, because it provides new users with a gentle introduction to Linux. Once they start doing advanced things that require they use the CLI often, it is time for them to move on to a distribution that does not try to use automated installation scripts and fancy default GUIs to hide configuration files and the CLI from them, and as far as Linux distributions go, Gentoo Linux is the best for doing that.

Gentoo Linux will never replace Ubuntu Linux in the role of a starter operating system, but Ubuntu Linux will never be a proper substitute for Gentoo Linux in the role of a power user's operating system. All of the eye candy and automation that Ubuntu does by default gets in the way of actually using the computer and while you can fight it, it is better to use a distribution that does not have any of that by default.

> **Arup said:**
> I did compile my own Kernel for the heck of it, was common years back when I was on SuSE, guess what, very little if any real world difference in my case.

Compiling your own kernel should not make a difference if you compile it with the same options your distribution's kernel maintainer uses. If you compile it with different options, you will see a difference. The key areas in which you can observe a difference are boot-time and Desktop Environment Responsiveness. Boot-time improvements come from making everything not explicitly needed to boot to userland a module. Desktop Environment responsiveness comes from using kernel pre-emption, RCU pre-emption and 1000Hz in the kernel. Other options can make a difference, but those are the main ones. One option that does merit mention is the high resolution timer, which siphons significant CPU time from a system and should be off unless you need your system to be able to tell how much time has passed with greater than millisecond precision.

On my system, I have a kernel that boots to userland 0.5 seconds after GRUB according to the kernel messages. I also have a very responsive Desktop Environment that does not have random lags or skips, the sort of thing Con Kolivas has been trying to resolve in the Linux kernel via a process of trial and error; he made BFS because of this and afterward, the kernel developers patched a regression in the CPU scheduler that had been keeping the scheduler from efficiently using resources.

I lectured a computer science class as a substitute for one of my professors recently and before class, I connected my laptop to the projector. We were doing some hands on things in class, so I got to make use of my Desktop Environment because I was not just going through a bunch of slides. After class, one of the students wanted to know why my laptop's desktop environment appeared more responsive to him than desktop environments on other systems. I assist a professor with one of his classes for undergraduate credit, which is why I was in this situation. Anyway, a graduate student I know that is in a similar situation has a Ubuntu Linux system that takes 17 seconds before it boots to userland. That is probably an extreme in terms of how long it takes for userland to boot on Ubuntu (as I do not think it should be that slow, even for Ubuntu), but my point is that there is a measurable difference between the Gentoo way of compiling your own kernel and the Ubuntu way of letting someone else do it for you.

> **bradmayne04 said:**
> I tried a live disk of gentoo the other day.  Played w/ it for about one hour.  I wasn't thrilled when it couldn't even find the ethernet controller never mind the wireless card.  Needless to say I'm not going to deal w/ something like that when there are soooooo many other distro's out there. Say what you will ubuntu may be for linux babies but I'm all for the usability!!

I suggest you use the [System Rescue CD]("http://www.sysresccd.org/Main_Page") to install Gentoo. It is a speciallized Linux distribution based on Gentoo (kind of like how Ubuntu is based on Debian) and it has much better hardware detection than Gentoo's LiveDVD. Most Gentoo users use that to install Gentoo Linux on their systems. The steps you take to install Gentoo Linux with the System Rescue CD are virtually identical to those you take with the Gentoo LiveDVD, so using the System Rescue CD to install Gentoo Linux should be easy assuming you follow the Gentoo Handbook.

---

### Post by swoll1980 on 2010-03-18
Ubuntu vs Gentoo is like roast beef vs spider webs. They are nothing alike. They have completely different goals, and philosophies. How do you compare the two.

---

### Post by Shining Arcanine on 2010-03-19
> **swoll1980 said:**
> Ubuntu vs Gentoo is like roast beef vs spider webs. They are nothing alike. They have completely different goals, and philosophies. How do you compare the two.

I think it is more like liver versus roast beef. They are both meat, but one tastes better than the other and the other is healthier for you.

---

### Post by MisfitI38 on 2010-03-19
> **Shining Arcanine said:**
> I think it is more like liver versus roast beef..one tastes better than the other and the other is healthier for you.
Your bubbling enthusiasm may be more appropriately directed toward the Gentoo developers and community. 
On the Ubuntu (or any other non-Gentoo) forums, it is invariably interpreted as fanboi language and only serves to marginalize your view.

---

### Post by Meep3D on 2010-03-19
One's like roast beef, the other one is like getting a bag of iron ore and being instructed to make a fork.

---

### Post by Suicida| on 2010-03-27
> **Bachstelze said:**
> Pure placebo effect. Anyone who knows anything about compilers will tell you that compile-time optimisations matter very little for most applications.

It's is not the compiler in gentoo that the speed comes from, as far as gcc is concerned most of your optimizations come from the -O* setting.

There are 3 things in Gentoo that will give you a faster system:

1. Minimal USE flags. Only set use flags per package, unless it is something you are REALLY going to need system wide like ssl or tcpd. Most gentoo n00bs make the mistake of overkill on thier use flags and link in alot of unnessecary libs that most of them will never use.

2. Kernel configuration. Rip everything you don't need or use out of the kernel. Run lsmod on any generic kernel and you will see alot of wasted ram on unused modules. 

3. Daemons. Only set daemons to start in runlevels that you are going to use all of the time.

Lastly I am sick to death of the "We have quad cores and 6GB of RAM" argument. I hear the same arguement from junior programmers as an excuse for thier code, if Linux heads down this path there really won't be any reason to use Linux over windows.

---

### Post by kevCast on 2010-03-28
> **Suicida| said:**
> It's is not the compiler in gentoo that the speed comes from, as far as gcc is concerned most of your optimizations come from the -O* setting.

There are 3 things in Gentoo that will give you a faster system:

1. Minimal USE flags. Only set use flags per package, unless it is something you are REALLY going to need system wide like ssl or tcpd. Most gentoo n00bs make the mistake of overkill on thier use flags and link in alot of unnessecary libs that most of them will never use.

2. Kernel configuration. Rip everything you don't need or use out of the kernel. Run lsmod on any generic kernel and you will see alot of wasted ram on unused modules. 

3. Daemons. Only set daemons to start in runlevels that you are going to use all of the time.

Lastly I am sick to death of the "We have quad cores and 6GB of RAM" argument. I hear the same arguement from junior programmers as an excuse for thier code, if Linux heads down this path there really won't be any reason to use Linux over windows.
1. aptitude install --without-recommends foo

2. wget [http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.33.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.33.tar.bz2) && sudo tar -xvjf linux-2.6.33.tar.bz2 -C /usr/src/ && cd /usr/src/ && ln -s linux-2.6.33 linux && cd linux && make defconfig && make menuconfig

3. aptitude install rcconf

---

### Post by J_Stanton on 2010-03-29
if you want a fast system, just buy an ssd and call it a day. apps open instantly regardless of os. it makes using the so called fast distros a moot point. chew on that. and before you say its cost prohibitive, i just saw a 30gb drive for $69.

---

### Post by Frak on 2010-03-29
> **J_Stanton said:**
> if you want a fast system, just buy an ssd and call it a day. apps open instantly regardless of os. it makes using the so called fast distros a moot point. chew on that. and before you say its cost prohibitive, i just saw a 30gb drive for $69.
30GB isn't much space nowadays.

---

### Post by J_Stanton on 2010-03-29
> **Frak said:**
> 30GB isn't much space nowadays.

the drive isn't meant to be used for storage. it is plenty big enough for the os and apps though.

---

### Post by maxkit on 2010-06-11
Gentoo is much faster than Ubuntu. Some HD videos on "hard" scenes just stop working on Ubuntu in Totem. The same videos on the same Totem with the same gst-plugins work smooth on Gentoo and FreeBSD.

One more example - 7-zip benchmark (7za b). What I get on my Core2Duo 1800 MHz is:

Ubuntu: 1562 MIPS
Gentoo: 2192 MIPS
FreeBSD: 2186 MIPS
MacOSX: 2638 MIPS
Windows: 3098 MIPS

OK, Windows wins here. I'm pretty sure Visual Studio C/C++ compiler produces a better code. But all the rest use GCC. Why does Ubuntu work so terribly slow? Moreover. I just tried to run 7-zip compiled in Gentoo on Ubuntu. The same 1500 MIPS. Which means it's kernel/libs related problem.

Are there any plans to boost Ubuntu? It's a great distro, saves a lot of time, looks great and so, I absolutelly love it. But why is it so slow?

---

### Post by kaldor on 2010-06-11
> **maxkit said:**
> Gentoo is much faster than Ubuntu. Some HD videos on "hard" scenes just stop working on Ubuntu in Totem. The same videos on the same Totem with the same gst-plugins work smooth on Gentoo and FreeBSD.

One more example - 7-zip benchmark (7za b). What I get on my Core2Duo 1800 MHz is:

Ubuntu: 1562 MIPS
Gentoo: 2192 MIPS
FreeBSD: 2186 MIPS
MacOSX: 2638 MIPS
Windows: 3098 MIPS

OK, Windows wins here. I'm pretty sure Visual Studio C/C++ compiler produces a better code. But all the rest use GCC. Why does Ubuntu work so terribly slow? Moreover. I just tried to run 7-zip compiled in Gentoo on Ubuntu. The same 1500 MIPS. Which means it's kernel/libs related problem.

Are there any plans to boost Ubuntu? It's a great distro, saves a lot of time, looks great and so, I absolutelly love it. But why is it so slow?

After using Ubuntu for 2 years I replaced it with openSUSE and I was blown away at what I was missing out on; SUSE is a LOT faster overall compared to my Ubuntu experiences. Not sure why.

---

### Post by Frak on 2010-06-11
> **kaldor said:**
> After using Ubuntu for 2 years I replaced it with openSUSE and I was blown away at what I was missing out on; SUSE is a LOT faster overall compared to my Ubuntu experiences. Not sure why.
Ubuntu doesn't really deviate far from Debian, and Debian knocks Ubuntu's socks off in speed.

---

### Post by Linuxforall on 2010-06-11
SuSE is far slower than Ubuntu, in boot and well as overall running. I started desktop linux in 1999 with SuSE and the packaging issues and bugs drove me to PCLOS and then when Ubuntu came out with x64, I never looked back at others. Even though I will always try Fedora when they come out with new versions, its my second preferred distro.

I don't see Ubuntu being set on fire by Gentoo in this test, of course all sorts of excuses will come from Gentoo boyz, thats all but expected.

[http://www.linux-mag.com/id/7574/1/](http://www.linux-mag.com/id/7574/1/)

AV tests, encoding, video playback, nothing conclusive at all. Even in apache compile, linux kernel compile etc. Gentoo didn't surpass Ubuntu. Even fps in games was basically same, Gentoo had O2 optimizations done and even then, nothing was set on fire. This is such a useless topic really, A versus B versus C, we use our distros for our individual needs and requirements and apart from placebo and ego issues, there is no sense in claiming one is faster or superior than the other.

---

### Post by WinterRain on 2010-06-12
> **Linuxforall said:**
> This is such a useless topic really, A versus B versus C, we use our distros for our individual needs and requirements and apart from placebo and ego issues, there is no sense in claiming one is faster or superior than the other.

Well said. Use what works for you. To be honest, I don't care if gentoo *is* faster, I prefer the debian/ubuntu way of doing things.

---

### Post by Linuxforall on 2010-06-12
Although I don't agree wth the title, the guy makes valid pertinent points here.

[http://bagnohax.wordpress.com/2010/06/11/why-does-gentoo-suck-balls/](http://bagnohax.wordpress.com/2010/06/11/why-does-gentoo-suck-balls/)

First of all, we have to explain ourselves WHAT is gentoo and WHO ARE its users. So basically, gentoo is a source based linux distribution used by linux geeks/bored people. The whole point of playing with gentoo is really fun &#8211; but when it comes to using it in environments like software company, it sucks balls.

First of all, say we have a deadline. You start the project on&#8230; 1st June 2010 and have to finish it until 30rd September. Well okay. Would you rather use gentoo, waste 50% of the precious time you could use more productively on coding, or rather get ubuntu/debian/fedora or whatever; and save that damn 50% of time spend on compiling sources?

Speaking of compiling sources&#8230; Say you want to compile Pidgin, BUT! There&#8217;s a catch, it has shitloads of dependencies that have shitloads of other dependencies etcetera etcetera. Result? 3 hours wasted on compiling 1 app.

---

### Post by Frak on 2010-06-12
> **Linuxforall said:**
> Although I don't agree wth the title, the guy makes valid pertinent points here.

[http://bagnohax.wordpress.com/2010/06/11/why-does-gentoo-suck-balls/](http://bagnohax.wordpress.com/2010/06/11/why-does-gentoo-suck-balls/)

First of all, we have to explain ourselves WHAT is gentoo and WHO ARE its users. So basically, gentoo is a source based linux distribution used by linux geeks/bored people. The whole point of playing with gentoo is really fun &#8211; but when it comes to using it in environments like software company, it sucks balls.

First of all, say we have a deadline. You start the project on&#8230; 1st June 2010 and have to finish it until 30rd September. Well okay. Would you rather use gentoo, waste 50% of the precious time you could use more productively on coding, or rather get ubuntu/debian/fedora or whatever; and save that damn 50% of time spend on compiling sources?

Speaking of compiling sources&#8230; Say you want to compile Pidgin, BUT! There&#8217;s a catch, it has shitloads of dependencies that have shitloads of other dependencies etcetera etcetera. Result? 3 hours wasted on compiling 1 app.
Get a faster computer. Problem solved.

---

### Post by Legendary_Bibo on 2010-06-12
Wait so you like to go through the frustrations of compiling everything for a slight boost in speed? Ubuntu is very snappy for me, but then again I'm with a dual core, 4gb of ram, and a decent graphics card. Besides I never liked XFCE, I tried it with Xubuntu, and although it's fast, it's ugly looking. If I'm going to look at my computer screen all day I'd like to be able to change its appearance on the fly. I don't like any of the docks either. Come on guys, there's nothing wrong with upgrading your archaic machines :P

---

### Post by Linuxforall on 2010-06-12
> **Frak said:**
> Get a faster computer. Problem solved.

Tell that to cash strapped boss at your enterprise and pink slip would soon be waiting for you at your desk.

---

### Post by Legendary_Bibo on 2010-06-12
> **Meep3D said:**
> One's like roast beef, the other one is like getting a bag of iron ore and being instructed to make a fork.
Correction, one is like being invited to a campsite where you're given the food, and forks, and the campfire is started with gasoline and matches.
The other is like being given a bag of iron ore to make your own utensil, you have to find your own flint and tin to make your own fire, and you have to go out and make your own spear out of a tree branch and then hunt your own food.

You're doing the same thing essentially, but the depending on who you are each choice may be your cup of tea.

---

### Post by maxkit on 2010-06-12
> **Frak said:**
> Get a faster computer. Problem solved.

I am in open source community since 1996 and that is the kind of answers distract me the most. If buying a new computer is a problem solver, so why don't you suggest just to  buy a Windows, which is cheaper and solves the problem on the same PC?

This "touchy" approach of open source community leads to nothing.

Yes, Gentoo is mostly for geeks. I work with it for 10 years and it's a real pain to build something like Amarok, for example. Yes, I prefer FreeBSD to all the Linuxes for its logic, speed and stability. But hey, why Ubuntu guys react this way? Isn't it better just to solve a problem and live happily ever after (until the next problem arises :) )?

I'm pretty sure that there are ways to boost Ubuntu. That's why proprietary software wins so far - they improve.

---

### Post by llawwehttam on 2010-06-12
In my opinion the speed you get in using gentoo is amazing, but sadly its sort of diminished by the huge install and update times due to compiling.

I prefer arch but I may use gentoo in the future again.

---

### Post by Frak on 2010-06-12
> **maxkit said:**
> I am in open source community since 1996 and that is the kind of answers distract me the most. If buying a new computer is a problem solver, so why don't you suggest just to  buy a Windows, which is cheaper and solves the problem on the same PC?

This "touchy" approach of open source community leads to nothing.

Yes, Gentoo is mostly for geeks. I work with it for 10 years and it's a real pain to build something like Amarok, for example. Yes, I prefer FreeBSD to all the Linuxes for its logic, speed and stability. But hey, why Ubuntu guys react this way? Isn't it better just to solve a problem and live happily ever after (until the next problem arises :) )?

I'm pretty sure that there are ways to boost Ubuntu. That's why proprietary software wins so far - they improve.
This post sums up my entire feelings on whatever issue it is addressing.

---

### Post by Shining Arcanine on 2010-06-13
> **WinterRain said:**
> Well said. Use what works for you. To be honest, I don't care if gentoo *is* faster, I prefer the debian/ubuntu way of doing things.

The Gentoo Linux way of doing things involves giving the users the ability to customize and control systems to the fullest extent possible. That way, if there is any aspect of it that a user does not like, the OS will do its best to stay out of users' way so the users can change things to suit their own individual interests. What area does that leave for Debian/Ubuntu to fill?

By the way, have you tried any Linux Distributions other than Debian/Ubuntu? There is much more to Linux Distributions than what Debian and Ubuntu provide.

> **Frak said:**
> Get a faster computer. Problem solved.

Find a computer that can quickly solve the Boolean Satisfiability Problem and I will buy it and encourage everyone else to buy it as well:

[http://en.wikipedia.org/wiki/Boolean_satisfiability_problem](http://en.wikipedia.org/wiki/Boolean_satisfiability_problem)

I live in Big-O land, where constant factor differences in speed are insignificant, so until you find a computer that can quickly solve the Boolean Satisfiability problem on all possible inputs, the "buy a faster computer" statement does not mean much to me.

By the way, if you do discover such a system, then you will likely want to submit it to the Clay Mathematics Institute. I understand that they are offering $6 million to the first person to solve that problem. They are really offering six $1 million prizes, but work has been done that has reduced all of them to finding a system that can quickly solve the Boolean Satisfiability Problem on all inputs, so you would be awarded the prize money for all 6 problems should you discover such a system.

---

### Post by Shining Arcanine on 2010-06-13
> **Legendary_Bibo said:**
> Wait so you like to go through the frustrations of compiling everything for a slight boost in speed? Ubuntu is very snappy for me, but then again I'm with a dual core, 4gb of ram, and a decent graphics card. Besides I never liked XFCE, I tried it with Xubuntu, and although it's fast, it's ugly looking. If I'm going to look at my computer screen all day I'd like to be able to change its appearance on the fly. I don't like any of the docks either. Come on guys, there's nothing wrong with upgrading your archaic machines :P

Gentoo Linux compiles things for customization purposes and compiling things allows entire program features to be turned on and off at the binary level, which does have an impact on performance. The small performance benefit that custom tailoring machine code to your system architecture brings when using GCC is an additional benefit.

I think that you need to learn the difference between cause and effect, because here the enhanced customization is a cause while the small boost from GCC's machine specific flags is an effect.

---

### Post by Frak on 2010-06-13
> **Shining Arcanine said:**
> Find a computer that can quickly solve the Boolean Satisfiability Problem and I will buy it and encourage everyone else to buy it as well:

[http://en.wikipedia.org/wiki/Boolean_satisfiability_problem](http://en.wikipedia.org/wiki/Boolean_satisfiability_problem)

I live in Big-O land, where constant factor differences in speed are insignificant, so until you find a computer that can quickly solve the Boolean Satisfiability problem on all possible inputs, the "buy a faster computer" statement does not mean much to me.

By the way, if you do discover such a system, then you will likely want to submit it to the Clay Mathematics Institute. I understand that they are offering $6 million to the first person to solve that problem. They are really offering six $1 million prizes, but work has been done that has reduced all of them to finding a system that can quickly solve the Boolean Satisfiability Problem on all inputs, so you would be awarded the prize money for all 6 problems should you discover such a system.

Do you like posting things that are incredibly OT?

---

### Post by Shining Arcanine on 2010-06-13
You are the one who said to buy a faster computer. I really dislike that idea, because it tends to promote Gates' Law:

[QUOTE=Gates' Law]The speed of software halves every 18 months.[/QUOTE]

---

### Post by Frak on 2010-06-13
> **Shining Arcanine said:**
> You are the one who said to buy a faster computer. I really dislike that idea, because it tends to promote Gates' Law:
Frak's law: The effort needed to create a certain piece of software halves every 18 months.

---

### Post by WinterRain on 2010-06-14
[IMG]http://fun.irq.dk/funroll-loops.org/index_files/gentoo.jpg[/IMG]

---

### Post by Shining Arcanine on 2010-06-14
> **WinterRain said:**
> [IMG]http://fun.irq.dk/funroll-loops.org/index_files/gentoo.jpg[/IMG]
That describes the Gentoo Linux testing tree and overlays fairly well. Gentoo Linux users seem to be a disproportionately large source of upstream bug reports as a consequence of that, so they get things fixed.

The stable tree has the issues fixed before software filters down to it.

---

