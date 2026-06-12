---
title: "Why does firefox in linux suck so much?"
date: 2009-04-13
forum: Recurring Discussions
---

### Post by rugbert on 2009-04-13
Not only is it noticeably slower than in XP, but it freezes and hangs all the time. ALL the time. And Im not even loading anything intensive, just forums, reddit, and simple web pages. But it keeps hanging, when I try to change tabs, type, scroll down, just about anything. And then it freezes a lot too.

Its really starting to bother me. Are there any plans to make it not suck so hard any time soon? Or better yet, what are some good, fast, alternatives to firefox?

[/rant]

---

### Post by Simian Man on 2009-04-13
It might be imperceptibly slower than on Windows, but I'm not getting hanging, crashing or anything.  What kind of machine do you have?

---

### Post by defaultusername on 2009-04-13
rugbert,

What kind of plugins do you have installed? Flash/Java have a history of poor stability on Linux and used as browser plugins can make Firefox seem unstable. On low-end systems, too many plugins/extensions or pages open can suck up enough memory to cause a crash. Despite these considerations, Firefox will run on almost anything remotely modern without a hiccup, so I would suspect configuration issues.

---

### Post by Copernicus1234 on 2009-04-13
Its very stable for me... sounds like your system has some kind of problem. Its not Firefox.

---

### Post by ayastona on 2009-04-13
firefox rocks on my machine, im a new ubuntu user, i converted my Dell windows machine to completely linux and firefox works like a champ for me!

---

### Post by defaultusername on 2009-04-13
> **Copernicus1234 said:**
> Its very stable for me... sounds like your system has some kind of problem. Its not Firefox.

Likewise. Firefox is a major component in many Linux distros and has excellent support/reliability. If the majority of users were having issues, it would have already been rectified. However, solving configuration errors can be a big mess and two Firefox users might have vastly different settings.

---

### Post by KayakJim on 2009-04-13
Do some searches for tweaking firefox on linux / ubuntu.

The most notable improvement is to disable ipv6 and installing FasterFox.

As for the hanging issues, it sounds like you have a plugin or theme that is causing your problems. What are you using?

---

### Post by wolfen69 on 2009-04-13
> **rugbert said:**
> Are there any plans to make it not suck so hard any time soon?

no, there are no plans to make it not suck, because it works fine for most people. i have never had a problem with it on any installation i've done. it's your installation that's borked, or your hardware is not very linux friendly. try a different distro. if it's slow on that too, then it's definitely your hardware giving issues. have you done memtest or any hardware diagnostics?

---

### Post by LowSky on 2009-04-13
> **KayakJim said:**
> The most notable improvement is to disable ipv6 

and if you have a fast connection like Cable or a T1/3 to increase the page cache, but then oyu also need a machine that can handle the caching.

Or try another browser, like swiftfox, opera, iceweasel, epiphany, or one of countless others.

---

### Post by RedSingularity on 2009-04-13
Well i had some irritating problems at first but a little tinkering fixed that up!

---

### Post by cariboo on 2009-04-13
I to believe you have a configuration problem. The easiest way to repair the problem is to backup your bookmarks, then delete ~/.mozilla. A new profile will be created the next time you start Firefox a new profile will be created. The Firefox directory is hidden, so to be able to find the directory, open Places-->Home Folder and press Ctrl-h, all the hidden files and directories will show up in the right hand pane of Nautilus.

Jim

---

### Post by NFblaze on 2009-04-13
Dude...i really really wish I knew why Firefox is the suck in Ubuntu...but I really havent a clue...I mean I suppose Im having the a similar issue. My system is rather modern too... 2gbs of ram and a dual core amd64 turion...although Im running 32-bit OS. 

In Windows its pretty fast...and memory leak doesnt become an issue if rarely.

In Ubuntu it seems like the memory leak happens almost instantaneous as soon as i get my deep browsing on. The system seems to crawl...also..

... the only solution I have found was to download Swiftfox. It definitely is much better on my memory usage and load. A couple of my extensions didnt transfer to Swiftfox tho... and its much smooth and has much better stability. 

For real though try it out.

---

### Post by Gizenshya on 2009-04-13
my experience is consistent with rugbert's. It is mostly with java/flash (nt sure which... maybe both).  it freezes for about 30 seconds once or twice an hour.  and then video /audio will stop working on it about once or twice a day (depending on how often I use it).

A friend of mine had the same problem but said there was another program that interfered with it that caused the issues... and he fixed it.  I've just been too busy to check it out as of late.

---

### Post by ibuclaw on 2009-04-13
Firefox is very well known to fsync constantly to disk - three or four times - everytime you refresh/load a new page. 

For the fix, read here: [http://ubuntuforums.org/showthread.php?t=1103926](http://ubuntuforums.org/showthread.php?t=1103926)

Although, having tried Firefox 3.1 up to Firefox 3.6 (the svn nightly builds). I can confirm that this is an issue no more in upstream.

Regards
Iain

---

### Post by sdennie on 2009-04-13
Are you running Ubuntu 8.04?  Did you install the updates?  It sounds like you are having a problem that used to exist but was fixed long ago and the updates will help.

---

### Post by djmh on 2009-04-13
i have a netbook (dell mini 9)
so its not the most high end computer (16 gig sdd and 1 gig of ram )
but it runs firefox pretty well , i just take it very easy on the plugins
and im waiting for chrome , i think that will be a great browser for my ubuntu system :)

---

### Post by Mortus Pryde on 2009-04-13
I'm new to Ubuntu, have Java and Flash installed and run it on an older laptop as you can see below. Aside from a few minor hitches in the transition, no issues using FireFox all along and yet to have any. I do miss some of the plugins/extentions I have in windows such as FireShots, but I am VERY happy to have Foxmarks.

---

### Post by 3Miro on 2009-04-13
Well doesn't mozilla FireFox derive from the old mozilla and wasn't mozilla the default browser for Gnome? I always believed that Linux is the Foxy's natural habitat and in fact for me it runs in Ubuntu much better thanit runs under XP.

If you guys that are having trouble can provide us with some details, then we can all try to resolve the issue. Run the system monitor ans keep and eye on the CPU usage of FireFox and any possible rouge processes, describe if the problem occurs when visiting specific web-pages, and of course list plug-ins and such that might be causing trouble.

---

### Post by memories on 2009-04-13
I've been wondering the same thing. It's my #1 item on "5 things I hate about linux" in the experiences forum. 

It runs damn fast in Linux, but it just runs damn fast-er in XP, even if by a very small bit. Deleting the .mozilla directory helps a lot in my case but it's not an option. Playing around with the memory settings help as well, but not significantly. I run Swiftweasel but don't notice much of a boost over vanilla ff3.

---

### Post by rugbert on 2009-04-13
Im running Ubuntu 8.10 on a HP pavillion dv2000. 3 gigs ram, AMD Turion 64 X2.

I have a few plugins, stumble, delicious (that ill probably disable) and firebug.

---

### Post by connorh123 on 2009-04-13
I found a topic around here about some guy being able to run Chrome, it seemed like it worked out well. But, I'm not risking the work for it.

---

### Post by skymera on 2009-04-13
1) Firefox may be slow because of IPv6 issues. Google it.
2) Firefox may not be using pipelining. Google it.
3) Increase max connections in Firefox. Google it.

My few simple suggestions

---

### Post by SuperSonic4 on 2009-04-13
Firefox is very stable on my system - much better than the windows version. Although I am using the 3.1 beta

---

### Post by memories on 2009-04-13
In my case the slowness has nothing to do with DLing pages. It's more client side. It takes awhile to launch, switching tabs isn't instant, sometimes it "pauses" a little when loading pages, etc. It sounds unusable but all my slowness complaints are barely noticable. If I had never tried FF on Windows I would say it's blazing fast - and it is, but it's just faster for me on XP.

---

### Post by rage9 on 2009-04-14
The system I have now, a 2.4 quad core intel, with 4 gigs of ram is great.  A few months ago I was running a 2 ghz Intel laptop with 512 mb of slow *** SDRAM.  I'll tell you what, Firefox worked much better under Ubuntu then Windows.  I'm sure that has something to do with the "Windows Slow Down" factor.

---

### Post by tommyhot on 2009-04-14
I also have performance issues with Firefox 3.0.x. It is so slow comparing to firefox in Vista. Maybe it's because I run compiz fusion but I didn't notice this with Opera etc.

Now I'm playing with Firefox-3.6 (alpha) and all the performance issues are gone! Firefox is soo responsive now, it feels even faster than Chrome on Vista. Of course there are some bugs like address bar showing wrong address and weird scrollbar colors, but who cares if it's so damn fast?

---

### Post by tamas305 on 2009-04-14
I have a full install of Ubuntu on a USB drive and am running it off of that...I have noticeable lags and timing errors but that's expected considering I am running it off of a USB DRIVE! Run xp off of a USB drive (I don't even know if it is possible) and run firefox and compare. I have no idea what type of system or firefox you have but it should be the same experience, if not better, than in Windows

-tamas

******************************************************
java + eclipse = happiness

---

### Post by pantone186 on 2009-04-14
Yep I get the same things happening to me, even on fresh installs - total freeze and computer lock-up. Sometimes I can force quit (but then after that nothing seems to work properly and I have to power-off the computer) or power-off the computer. very occasionally it will sort itself out

---

### Post by carusoswi on 2009-04-14
> **rugbert said:**
> Not only is it noticeably slower than in XP, but it freezes and hangs all the time. ALL the time. And Im not even loading anything intensive, just forums, reddit, and simple web pages. But it keeps hanging, when I try to change tabs, type, scroll down, just about anything. And then it freezes a lot too.

Its really starting to bother me. Are there any plans to make it not suck so hard any time soon? Or better yet, what are some good, fast, alternatives to firefox?

[/rant]

I cannot say that it is slower in Ubuntu than in XP on my setup, but it most definitely crashes - and this is a known problem that, to my knowledge, has never been fixed.  My machine isn't the latest and greatest, but it isn't exactly lame, either - Pentium 4, 3.0 ghz, 2gb RAM.  It shouldn't need more than that just to keep running.  In my case, freezes are like instant, solid ice.  No chance to capture a log file or any such thing.  The only button I have control over when FF freezes is the hard reboot button.

If you do a search, you can assure yourself that others have been plagued with this problem, and I doubt it has much at all to do with your hardware, since no one as far as I can tell, has been able to sort it out.

Caruso

---

### Post by Mokoma on 2009-04-14
it only sucks on single core machines, it works significantly better on dual/tri/quad etc...

---

### Post by Tamlynmac on 2009-04-14
> Mokoma
it only sucks on single core machines, it works significantly better on dual/tri/quad etc... 

I'm running a P4 right now and haven't experienced any of these issues. Firefox works just fine and is faster than my neighbors Vista dual core machine running FF. As others have attempted to point out, it may simply be a FF configuration issue.

---

### Post by zero244 on 2009-04-14
I dont have any complaints with Firefox 3.x on Linux, other than for some reason most of the streams on Youtube have stopped working.
I have to watch youtube streams on Opera.

---

### Post by AKviking on 2009-04-15
I've been using it on my PC at work with NO problems.  I've had more trouble with Firefox on my XP machine at home.

I used to have lots of trouble with IE, but haven't used that in years and hopefully I'll be saying the same about Windows soon.

---

### Post by tamas305 on 2009-04-15
> **pantone186 said:**
> Yep I get the same things happening to me, even on fresh installs - total freeze and computer lock-up. Sometimes I can force quit (but then after that nothing seems to work properly and I have to power-off the computer) or power-off the computer. very occasionally it will sort itself out

Mind you I am running the entire OS off of a USB drive so it is expected that there will be some lag. Firefox should run just fine if Ubuntu is installed to a 7200 rpm hard drive

-tamas

************************************************
java + eclipse = happiness

---

### Post by belim on 2009-04-15
I am currently running FF 3.0.8 on Ubuntu 8.10 with all updates and it is rocked solid, faster and more reliable than XP. I am running on a Dell Latitude E6500 with a 7200Rpm HDD and a Intel C2D T9400 with 4GB of RAM.

I was previously running Gentoo on the same hardware, and FF was rock solid then to. I never had less than 30tabs open and as its a laptop I would close FF and save all tabs then reopen 30tabs at once and it never fell over. It was slow loading ~30 pages at once obviously but once that was done it was back up to speed and running fine. 

Also for the record I have never tweaked FF ;)

---

### Post by stchman on 2009-04-15
> **rugbert said:**
> Not only is it noticeably slower than in XP, but it freezes and hangs all the time. ALL the time. And Im not even loading anything intensive, just forums, reddit, and simple web pages. But it keeps hanging, when I try to change tabs, type, scroll down, just about anything. And then it freezes a lot too.

Its really starting to bother me. Are there any plans to make it not suck so hard any time soon? Or better yet, what are some good, fast, alternatives to firefox?

[/rant]

Firefox runs very well on all (5) of my machines.  I do not know what problems you are having.

Firefox on XP might be a tick faster (XP is a much older OS), but the speed is there.

---

### Post by Crafty Kisses on 2009-04-15
> **rugbert said:**
> Not only is it noticeably slower than in XP, but it freezes and hangs all the time. ALL the time. And Im not even loading anything intensive, just forums, reddit, and simple web pages. But it keeps hanging, when I try to change tabs, type, scroll down, just about anything. And then it freezes a lot too.

Its really starting to bother me. Are there any plans to make it not suck so hard any time soon? Or better yet, what are some good, fast, alternatives to firefox?

[/rant]

Personally, I've never had any problems with Firefox under Linux, now call me lucky but I seriously haven't. In fact I think it works better under Linux. If Firefox isn't working for you, I simply say try using a different browser, there's a ton for Linux.

---

### Post by Dileeshvar on 2009-04-18
yup its stable in my system as well
So i dont find firefox sucks with linux :)

---

### Post by Zsev on 2009-04-20
Are you guys in denial or what ? And I can only assume that those who are OK with Ubuntu+Firefox has not had the priviledge of using it in XP before. 

When browsing pages with plain text it seems ok, but anything with flash content and it feels like you're running FF on a 500mhz pc. Also, font smoothing is just plain bad. Lcdlegacy fix helps a bit, but is NO where near XP's font quality. 

This happens on all 5 of my hardware setups so meh...Ubuntu's browsing experience is alright, but its far from great. I like Ubuntu but I think we all need to be honest with our user experiences.

---

### Post by el.sic on 2009-04-20
I noticed this when I first made the switch from windows to Ubuntu recently but I disabled IPV6 and that fixed it. Now is just as good if not better than xp.

---

### Post by dandis on 2009-04-21
Firefox sucks on Windows too. The freezes were driving me crazy, so I switched to nightly Chromium builds.

---

### Post by mitchellweston23 on 2009-04-21
i am having the same problem.
i am using a wired internet connection and am running ubuntu hardy heron 8.04 i have a hp compaq nc6220.
Whats Wrong?
also my computer freezes quite often even if i am not running any applications?

---

### Post by TenPlus1 on 2009-04-21
Firefox has always worked fine for me in linux, even flash and java...  Mind you, I do use Opera as my main browser...

---

### Post by Dougie187 on 2009-04-21
> **Zsev said:**
> Are you guys in denial or what ? And I can only assume that those who are OK with Ubuntu+Firefox has not had the priviledge of using it in XP before. 

When browsing pages with plain text it seems ok, but anything with flash content and it feels like you're running FF on a 500mhz pc. Also, font smoothing is just plain bad. Lcdlegacy fix helps a bit, but is NO where near XP's font quality. 

This happens on all 5 of my hardware setups so meh...Ubuntu's browsing experience is alright, but its far from great. I like Ubuntu but I think we all need to be honest with our user experiences.

Are you kidding? The font's in xp are gross looking. All XP does to smooth fonts is distort the image a bit, so it gets fuzzier instead of crisper. The fonts in ubuntu are nice and crisp and sharp looking. They are significantly easier to read. I spent of a day messing with the fonts in both to get a comparison, and the end result was fonts in XP are junk compared to the fonts in ubuntu.

Try using bitstream vera sans roman for your fonts with subpixel smooting on if you have an LCD, otherwise you probably want best Shapes. It looks so much better than the fonts in XP do.

I've used firefox in both ubuntu and in xp and I haven't noticed a large difference in either as far as speed, however it seems to crash a lot more in xp for me. There are many threads that detail how to optimize firefox, you might read some of them.

---

### Post by cb951303 on 2009-04-21
i used firefox since the initial release on linux with a variety of machines, it always sucked compared to windows version.

---

### Post by Bios Element on 2009-04-21
> **Codename said:**
> Personally, I've never had any problems with Firefox under Linux, now call me lucky but I seriously haven't. In fact I think it works better under Linux. If Firefox isn't working for you, I simply say try using a different browser, there's a ton for Linux.

I think it's something to bring up, but I'm getting tired of people going on and on and on about it. I'm willing to bet that there are already bug reports open on it.

---

### Post by tommyhot on 2009-04-23
Latest 3.0.9 release is much faster for me. Maybe you should give it a try :)

---

### Post by SpyroViper on 2009-04-23
In my experience, Linux FF has been faster, more stable, more useable and have nicer looking fonts.  FF in XP and Vista was slow, unstable and paused a lot while doing simple tasks.  It's the same in OS X, much better than the Windows version.  I also do some litmus testing for FF and my platforms of choice are Linux/OS X.

---

### Post by mdawgmike on 2009-04-23
I've also had some minor issues with Firefox in Ubuntu, which I don't have with the same version in XP.  The main issue being the random hanging problem.  I do have the Adobe Flash plugin.  Is this the problem?  I think most times I get the hangs it is when it's loading a page with flash.  What happens is that the application window goes grey for awhile (program stops responding I think), then it goes back to normal after a few seconds to a minute.  During this time my computer is just fine (i.e. I can move the mouse and work in other applications), so it's definitely something with Firefox.  Any suggestions?  

I am currently running 8.10 x86_64, but will probably be upgrading to 9.04 when I get home tonight to see if that solves the problem.  All in all I must say Ubuntu is much much better than XP for my uses.  Things load faster, its more simple and almost completely intuitive, and almost everything works properly by default.  All I really use XP for is gaming (which I am an avid PC gamer).  It's a shame that very few Windows apps get ported over, or are otherwise developed for Linux in the first place :(.  It really is a far superior OS.

---

### Post by JK3mp on 2009-04-23
There's any possible array of reasons for freezing and instability. DOesn't mean its from FF. FF used to have the issue but it has been resolved in recent updates. Could be improper configurations, increase Cpu from window manager, also as far as firefox your connection speed and type of media your loading. (though many i noticed said they had problems with just minor basic web pages).

---

### Post by starcannon on 2009-04-23
> **rugbert said:**
> Not only is it noticeably slower than in XP, but it freezes and hangs all the time. ALL the time. And Im not even loading anything intensive, just forums, reddit, and simple web pages. But it keeps hanging, when I try to change tabs, type, scroll down, just about anything. And then it freezes a lot too.

Its really starting to bother me. Are there any plans to make it not suck so hard any time soon? Or better yet, what are some good, fast, alternatives to firefox?

[/rant]

Hmm, I don't have any of those issues. I don't run windows, so I'll just take your word for it that its faster; all I can say about that is, mines fast enough for me.

If you want a wicked fast browser, check out [Dillo]("http://www.dillo.org/")

---

### Post by Aflack on 2009-04-23
im pretty sure its no just for some users. on 9.04, firefox sucks badly compared to when i run it on vista. and my machine is quite modern,

AMD Quad Core 2.2GHz
GeForce 9400GT 512 Video Mem
5GB RAM

FireFox is too slow for me, so I don't use Ubuntu that much anymore.

---

### Post by amoeba801 on 2009-04-24
I'll add my experiences.

Firefox is shockingly bad on my system (8.10, i386, 1 GB RAM) - when accessing a web site heavily load with with flash (like wwww.neatorama.com), the whole system grinds to a halt (90% cpu etc)

My graphics card is an old Geforce 6610 XL.

My problem seems to be a problem with firefox and/or flash and/or nvidia.

I've tried several approaches to fix the problems: I now use NVIDA's driver 180.44, plus some of the tweaks they were recommending (nvidia-settings -a InitialPixmapPlacement=2 -a GlyphCache=1). However, with no improvement.

The problem seems to fall in the cracks between organisations and there is probably little interest in a helping a small niche market (& maybe the probel I have is only with older graphics cards).

I don't expect the problem to be fixed. 

For a while I just disabled flash in FF until recently as I discovered the add-on FlashBock. It works well,does what I need & FF performance is good. 

I've now moved on with my life.

I started to see whether the problem exists with Flash in Chrome but the dev version I installed didn't seem to support Flash and I lost interest.

---

### Post by dazzlindonna on 2009-04-24
FF is definitely borked for some of us, and its NOT just linux that's the problem.  Do a search on Twitter for [firefox crash] and you'll see tons of complaints.  For me, I can narrow it down to being a javascript and/or flash problem.  With js turned off, I never crash. With js on, I crash regularly throughout the day.  I've tried running it with a new profile, no plugins, etc.  Sometimes, I think I've got it fixed, only to see the problem return later.  Just because it's wonderful for some, it's not wonderful for all.  I had hoped 3.09 would resolve the issues but it didn't.

At this point, I'm looking for a new browser.  Any suggestions?  I'm a heavy user, and I would hate to give up plugins, but anything is better than crashing constantly.

---

### Post by Tommmyboy on 2009-04-24
These are general comments on this topic which may or may not be applicable to the original poster but relevant to subsequent posts.

I don't know if someone already suggested this... if you have installed and then subsequently uninstalled several extensions, a lot of them don't clean up very well after themselves leaving behind a slew of preferences... Mozilla's own Weave add-on is even guilty of this bad behavior. If you haven't already tried this, I'd recommend going into the config file (type about:config in the URL and just answer yes when it prompts you, you may already know this), type extension in the search box, and find and reset preferences for any deleted addons (ctrl-click, or right click in Windows or Linux and choose reset). When you've reset them all, restart Firefox and the preferences will be gone from the config file; I noticed a huge performance improvement after doing this little bit of housecleaning.

Anyway, I use Firefox 3.0.9 in Jaunty on an iMac G5 PPC and it just rocks the house in comparison to XP or Mac OS 10.5.6 (OS X both on my aforementioned iMac and MacBook 3,1 2Ghz Intel Core 2 Duo). In Jaunty on my MacBook, it too blazes past it's OS X counterpart. It's so freakin fast and stability has not been an issue at all. 

I'd have to cast my evil eye on Flash, just like many others here have mentioned. Although it would be a backtrack, I wish Adobe would do something about Flash - it's too ahead of it's time for the architecture on most people's computers - it sucks up so much memory and it's the only thing aside from rendering graphics or Quicktime movies that causes my fans on my MacBook to blow full speed and so loud it makes me wonder what kind of damage over the long haul all that heat might be doing to my machine. There's a reason why Camino (Mozilla's Mac native browser) includes Flashbock as a built in preference (I have Flashblock installed in all my Firefox installs, except Jaunty on my G5 as there is no Flash).

Add-ons in Firefox are the best thing and the worst thing that has happened to web browsers. Thanks to the wonders of open source, anyone can write one - that means there are a lot of extensions written by people with subpar coding skills that will eat memory, cause crashes and hangs, or even break Firefox. Yeah a certain extension may be the most useful tool you ever had in your travels across the internet, but if it's fool of bloat because it's poorly written... well, there's a trade off you've got to make. I have three... oldbar (makes the Awesome Bar behave like the URL bar in Firefox 2) and restore scroll position... both are just simple, sleek addons that I use for really basic functionality. It's just inevitable if you have like 5 or more add ons, especially ones that perform outlandish, death defying feats, that you're going to run into trouble at some point.  

I'd check out [http://kb.mozillazine.org/Problematic_extensions](http://kb.mozillazine.org/Problematic_extensions) just to ensure you're causing yourself any headaches that could be easily remedied.

---

### Post by blazingnikons on 2009-04-26
I could uninstall all of my add-ons and Firefox on 8.10 would still f*ck up every other flash video or audio file and runaway on 1/9 sites with a flash advertisement or some javascript.  I've tried all the "fixes" on the forums and other sites, to no avail.  What's that?  Remove javascript and flash?  HEY UBUNTU "PROS"--THIS ISN'T 1996. Have fun surfing the net without flash and java, about as much fun as playing basketball with a rock.

I have an Acer laptop with 3 gigs of ram and an Intel t3400 @ 2.16 GHz -- not a gaming machine, but it should run Ubuntu no matter how bloated you can make it.  Ubuntu is supposed to "just work"...my experience has been that "it just works" actually means spending hours trying to get it to do what XP did without trouble.  I've had more black screens of death than I ever had blue screens of death, and I update every day. I report/confirm bugs when I can.  I spend hours looking for solutions online and tediously enter the snake oil into terminal hoping that this time my OS will finally stop sucking.  Nope.  In fact, once things start to go acceptably well, and update comes along and creates a whole new set of problems.  I just want to surf the net, do word processing and that sort of thing.  That's all.  And yet, myself and no one else can even seem to get Firefox to run on the "greatest linux distro ever."  That's my rant.  

Inb4/ "it works perfectly for me, XP sux, you just don't know how to configure (i.e. waste days rewriting your "it just works" OS), etc.

---

### Post by yoasif on 2009-04-26
> **blazingnikons said:**
> I could uninstall all of my add-ons and Firefox on 8.10 would still f*ck up every other flash video or audio file and runaway on 1/9 sites with a flash advertisement or some javascript.  I've tried all the "fixes" on the forums and other sites, to no avail.  What's that?  Remove javascript and flash?  HEY UBUNTU "PROS"--THIS ISN'T 1996. Have fun surfing the net without flash and java, about as much fun as playing basketball with a rock.

I have an Acer laptop with 3 gigs of ram and an Intel t3400 @ 2.16 GHz -- not a gaming machine, but it should run Ubuntu no matter how bloated you can make it.  Ubuntu is supposed to "just work"...my experience has been that "it just works" actually means spending hours trying to get it to do what XP did without trouble.  I've had more black screens of death than I ever had blue screens of death, and I update every day. I report/confirm bugs when I can.  I spend hours looking for solutions online and tediously enter the snake oil into terminal hoping that this time my OS will finally stop sucking.  Nope.  In fact, once things start to go acceptably well, and update comes along and creates a whole new set of problems.  I just want to surf the net, do word processing and that sort of thing.  That's all.  And yet, myself and no one else can even seem to get Firefox to run on the "greatest linux distro ever."  That's my rant.  

Inb4/ "it works perfectly for me, XP sux, you just don't know how to configure (i.e. waste days rewriting your "it just works" OS), etc.have you tried disabling desktop effects (compiz)?

also, i've had good luck with the firefox-3.5 package ([installable via ppa]("https://launchpad.net/~fta/+archive/ppa"))... much faster.

---

### Post by blazingnikons on 2009-04-26
> **yoasif said:**
> have you tried disabling desktop effects (compiz)?

also, i've had good luck with the firefox-3.5 package ([installable via ppa]("https://launchpad.net/~fta/+archive/ppa"))... much faster.


*sigh*


...yes. I've also tried the icedtea plugin instead of the official Sun one. And I've tried different flash plugins and found they work worse that the Adobe one I run now (10.22.87 or whatever it is). I have few addons and I've checked to see if they cause the behaviors -- no.  I've gone so far as to build and run snatch, the ext3 defragmenter just in case.  Also, I've tried SeaMonkey and Opera.  Beneath those two browsers are countless other browsers that each work with fewer and fewer websites.

The saddest thing is that Firefox works better (though not perfectly) in WINE than natively Ubuntu. So, I surf natively, then when I want to watch a video or listen to a flash audio track I open the WINE Firefox. I've been told that the 64-bit distro is at the heart of the problems, and from what I've seen on blogs and forums, intrepid amd64 does seem to have more things go wrong with it.  I installed it because I thought it would run faster, be more stable, and allow me the freedom to run software of both 32 and 64 bit varieties. To go off on a tangent, I've tried since December to get the damn touchpad to keep from bouncing my cursor all over when typing -- syndaemon isn't recognized, and the evil xorg-conf package contains no tools which recognize my touchpad to the point where I can set it to deactivate after I start typing, either in gnome or via editing various files myself -- that's a whole different issue...  The point is, that I'm trying hard to love Ubuntu specifically and Linux in general, but if there's no browser which can handle the contemporary and common sites of the web, how can the vast majority of people not accept the swollen Vistas and draconian, overpriced Apple OS/software as their only real option? Why does my browser occasionally lead to a restart? Why can the same browser on macs and windows easily handle youtube videos while failing miserably on Ubuntu? Why hock a 64-bit architecture if it works like crap for everyday purposes? Why is it essential I have to edit a handful of files and download patches and plugins just to get LastFM to scobble songs to my library (which has yet to happen)? Why does my cursor keep bouncing all over the page when I type, tossing bits of words here and there or not at all whenever I hit two keys at the same time or brush the edge of my desensitized touchpad--whether I'm using a standard keyboard configuration or the Acer laptop keyboard configuration? Why can I select or deselect options in gnome only to find that changing this-or-that doesn't actually change anything and I have to go and edit a file manually--what's the point of the gnome, cursor-based option in the first place?!? Why do I have to run sudo nautilus every time I have to go and try to find something that needs editing because the new security updates created a new and exciting set of bugs for me to fix? Why do chm files never seem to work in quite the same way when I open them with the same program? Why do I have to reload my gmail inbox just to see it in Ubuntuean Firefox when no other browser on no other operating system makes me do so? How can programs installed via synaptic package manager sometimes show up under applications and sometimes not -- why am I required to search for them with a xcfe-based app finder which half the time doesn't find them anyway? Why does ClamAV not allow me to update it without manually installing the 0.95 version, which in turn isn't recognized anyway just like freshclam isn't in either version?

Okay, it's late and I really am not expecting any answers.  I just needed to let some of it out. I suppose I miss those early days of XP -- I never had the blue screen of death or speed problems (before service pack 3) or any malware problems at all because I knew how to maintain and protect my OS. Plugnplay was a reality.  All problems with things like browsers and hardware had solutions.

I miss loving my computer and enjoying the internet. *tear*

k, I'm done.

---

### Post by olskar on 2009-04-26
It works fine on Linux but no one can't seriosly mean it is as fast as in Windows? Have you tried it on a newly installed Windows xp machine?

Here is some tests by the way
[http://www.tuxradar.com/content/benchmarked-firefox-javascript-linux-and-windows-and-its-not-pretty](http://www.tuxradar.com/content/benchmarked-firefox-javascript-linux-and-windows-and-its-not-pretty)

---

### Post by rugbert on 2009-04-26
After a week long internet hiatus Ill have to look over this thread.

I have removed a couple plug ins and its already better. Since before I upgraded to Jaunty last night anyway. But I dont see why the hardware specs (as mentioned a few times) would have such an issue with firefox, my laptop is pretty decent. I mean, firefox in a windows XP virtual machine runs more smoothly.

---

### Post by Bios Element on 2009-04-26
> **olskar said:**
> It works fine on Linux but no one can't seriosly mean it is as fast as in Windows? Have you tried it on a newly installed Windows xp machine?

Here is some tests by the way
[http://www.tuxradar.com/content/benchmarked-firefox-javascript-linux-and-windows-and-its-not-pretty](http://www.tuxradar.com/content/benchmarked-firefox-javascript-linux-and-windows-and-its-not-pretty)

It must depend on your rig. Firefox actually feels faster on ubuntu then it ever did for me on Vista. Maybe XP is faster but I've never had a problem with firefox.

---

### Post by Merk42 on 2009-04-26
Firefox feels slower for me in Ubuntu 8.10 or 9.04 versus Windows 7 and I think back when I had Windows XP.

I'm dual booting, so it's the same hardware, and with the exception of the Ubuntu Firefox Modifications, the same Add-Ons.

---

### Post by hailholyghost on 2009-04-26
I've noticed that YouTube videos can be jumpy on my machine, and its only 2 years old with 2G of RAM and a dual core 1.6Gig processor.

Glad to see I'm not the only one with issues!

If I understand correctly, YouTube videos use flash, and flash does not work well in Linux?

---

### Post by olskar on 2009-04-27
> **Bios Element said:**
> It must depend on your rig. Firefox actually feels faster on ubuntu then it ever did for me on Vista. Maybe XP is faster but I've never had a problem with firefox.

As rugbert said, I don't think it is because my hardware specs, firefox in a windows XP virtual machine (with lower specs than this computer) runs more smoothly.

---

### Post by rugbert on 2009-04-29
> **olskar said:**
> As rugbert said, I don't think it is because my hardware specs, firefox in a windows XP virtual machine (with lower specs than this computer) runs more smoothly.

Yea, I dont see how hardware would have any performance over JUST firefox... heres hoping for a solid chrome release tho!

---

### Post by Bios Element on 2009-04-30
> **rugbert said:**
> Yea, I dont see how hardware would have any performance over JUST firefox... heres hoping for a solid chrome release tho!

Don't hold your breath... >.> Google's not impressing so far.

---

### Post by maheshjr2000 on 2009-04-30
Have you tried firefox in Xubuntu instead? That might be faster(directed to OP).

---

### Post by blazingnikons on 2009-04-30
Everyone should watch this:

Linux Sucks! Video from LinuxFest NW
[http://lunduke.com/?p=429]("http://lunduke.com/?p=429")

This is only a fraction, dear developers and users.

---

### Post by pietjanjaap on 2009-04-30
Here is a dutch site on what to install after a fresh install of ubuntu.
Yes dutch so you have to translate with "google translate), copy the site inside it, then it will be translated.
Then ubuntu will run on it's best.
There are ofcourse also english site's with the same things on what to install.

I had that youtube would crash very often in the start of the movie.
I am using ubuntu 8.04.
Tried a lot of things, nothing worked.
Then i changed the sound to default in ubuntu, then suddenly it was ok again. So maybe a update or the sound system of ubuntu.

In firefox you can say that it should clean out things with shutdown, so this you can do.

The you can do bleachbit, (like ccleaner), looks safe to me, speeds up ubuntu.

---

### Post by DJonsson2008 on 2009-04-30
On hardy 8.4, I'm running SwiftFox with Faster Fox plugin runs smooth and fast, youtube videos play fine, no crashes with daily intensive use.

I also have Opera here as a point of reference, Opera is
a little faster, but this SwiftFox/Faster Fox combination
is about as fast as browser gets.

If I was troubleshooting slowness I'd try; using the generic
Vesa display driver, Opera and SwiftFox as tests.

---

### Post by zugu on 2009-04-30
> **Bios Element said:**
> Don't hold your breath... >.> Google's not impressing so far.

Are you for real? Did you check some recent benchmarks? Did you use Chrome or Chromium consistently as to see for yourself the humongous difference in startup times, render times and JavaScript execution times between Chrome/Chromium and Firefox?

Google's browser might be lacking a plug-in framework (coming soon) or other features you might need, but it's definitely promising, considering it blows out of the water anything (except maybe the latest builds of Safari 4).

---

### Post by dicairo on 2009-04-30
heyyy man i think you have to get a look about your plug-ins because for me its working great and really don't know why you have these problem you have to post more information i think

---

### Post by Craig73 on 2009-04-30
Under 8.10 there were sites that were more painful than others (if I opened 8-10 tabs with NewScientist my browser would practically hang).  Mind you I am running on a 1.6GHz Pentium M 1.5GB but that should be sufficient.

I remember disabling all addons and it not making much of a difference.

But I'm on Jaunty now, and running 2.6.30-RC2, and newer Firefox and things are OK, so...

I'm more saying it isn't just you - I have been there.

[BTW - I was under the impression there was a performance regression in the last few kernel that impacted sqllite/firefox that was resolved in 30?]

---

### Post by NFblaze on 2009-04-30
I must say the latest Firefox that came with 9.04 actually is alot better than the previous versions I used.. 

Normal HTML pages now load up with comparable speed as when im in Windows....

only thing that still semi-sucks is the Flash problem...it still loads pages containing FLash rather slow.

---

### Post by tuga on 2009-05-01
For me the combination ubuntu 9.04 x64, firefox and flash sucks. Firefox turns grey and hangs when browsing web sites with flash (like disney.com). Already reinstalled firefox and flash.
Anyone is running with knows if there are issues with ubuntu 9.04 x64, firefox and flash? Any alternative? Or do I have to install 9.04 x32?

Thanks.

---

### Post by wjwh on 2009-05-01
I am running a dual boot of XP and Ubuntu 8.04 on an old desktop (single core Pentium 2.80 GHz with only 512 MB RAM).  I run the latest Firefox on both systems.  It runs faster and more stably on Ubuntu than on XP. Each time that my son visits and uses my machine, he comments on how much faster it runs in linux than on his much more modern laptop which only runs Windows.  I have never done any tweaking, so I cannot see what it is that makes my Firefox on Ubuntu fast and stable while others here have problems. Maybe the lesson is that old is sometimes better than new! :)

---

### Post by ebanlague on 2009-05-01
[Check this quick article out]("http://www.ubuntugeek.com/speed-up-firefox-web-browser.html")

Pretty standard stuff, but helped me out quite noticeably with speed.
As for hangs and crashes, I really haven't had any so far -.-

---

### Post by longtom on 2009-05-03
For what it is worth....

I am using opera...got somehow attached to it some time ago and love the "all in one" approach, also I don't use the mail option.

No delays, no flash problems - and yes, I had my fair share of firefox problems in 8.10 as well.

Maybe try it - no frills and fuss for mine.

---

### Post by javyn999 on 2009-05-12
Jaunty's Firefox is a bit better for me now.  I have to use Opera for watching flash though.

---

### Post by Bios Element on 2009-05-13
> **zugu said:**
> Are you for real? Did you check some recent benchmarks? Did you use Chrome or Chromium consistently as to see for yourself the humongous difference in startup times, render times and JavaScript execution times between Chrome/Chromium and Firefox?

Google's browser might be lacking a plug-in framework (coming soon) or other features you might need, but it's definitely promising, considering it blows out of the water anything (except maybe the latest builds of Safari 4).

Yes I'm for real. I'm running Minefield and it blows away Chrome every which way. You can't compare a beta such as Chromium to a stable such as Firefox.

And a plug-in framework that no doubt will limit any form of advert removal. >.>

---

### Post by rahduke on 2009-05-14
I totally agree firefox sucks so bad on ubuntu, anytime u run flash it kills system memory. I'm on a core2duo 2.66ghz w/ 3gigs of ram so its not the system. Its either firefox or the flash plugin....

---

### Post by Gausian on 2009-05-15
Although i agree that ff isnt as good in ubuntu, it has been getting better.  and the release of 9.04 with ff has been the best so  far.

---

### Post by dtoronto on 2009-05-15
Firefox has always run more stable in Linux for me than in Windows.  You might want to check your add-ons and extensions.  Other than that it does run a little slower the java plugs don't run as smooth as windows.

---

### Post by Sewje on 2009-05-16
On my machine Sunspider java test in Ubunutu beat XP.

I noticed Ubuntu manages to make better use of different speed systems better than Windows.
For example Windows speed on my Laptop is pretty much same as on my Desktop, but with Ubuntu there is a lot of difference in the speed.

---

### Post by pookiebear on 2009-05-20
Running the nightly build right now. It is faster. 3.6 alpha

[http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/)

---

### Post by tobiasolesen on 2009-05-21
hi

I have an Eee pc 1000h and firefox is really running slow on it to... I have Add block plus installed... and flash player as well. If this is slow on linux can I use some other software?

I have the netbook remix installed...

tobias

---

### Post by mag1 on 2009-05-21
While loading performance can be a bit poor sometimes, my real issue is simply lag, scrolling is slow on some sites, i've tested it by turning images off and java script and refreshing, still the same, i've used adblock to remove certain things and it's still slow, its strange and can't be down to flash, though the performance of that is better under xp, its something else, it really needs sorting, especially as netbooks are quite popular now and ubuntu have remix.

---

### Post by rpm610 on 2009-05-22
Running FF 3.0.10 and Ubuntu 8.10 on an IBM Thinkpad T43 with 512MB/2.0Ghz

FF seems to run fine until it runs out of memory.  That's when the swapping to virtual memory starts, and if I don't do something quickly I'll lose control of my machine.

Issues come and go with different releases, so I figure the problem will eventually be solved.  In the mean time, I've done a couple things to cope with the issues:

1.  I have a "kill switch" on my taskbar. It basically just does a "killall firefox".  When I notice the problems starting, I just hit that and restart FF.  

2.  Occasionally I won't catch it in time, or I'll go away from the machine and, upon returning, It will be more or less frozen.  I wrote a script that I run continuously in the cron that checks the system load.  If the load goes above 5, I do a killall firefox.  The assumption is that the load is above 5 because of firefox - I don't do a lot of heavy processing.  This prevents the situations I was having where the HDD was swapping like mad for several hours because the FF/Memory issue.

Since I have FF tracking what my last visited URL was, killing it and restarting is only a minor annoyance.  The tricks listed above have reduced my need of having to do a hard restart on the machine to 0.

---

### Post by javyn999 on 2009-05-22
Firefox on Jaunty runs fine for me now, after a hell of a lot of tweaking.

---

### Post by Spiritous on 2009-05-22
Mine ran fine in Jaunty, no tweaking? And my PC is ok-ish

---

### Post by Cato2 on 2009-06-10
I find Firefox is so crashy in Linux that I'm now starting to use it on Windows (in a VM on top of Ubuntu) just so I don't have regular crashes.  I can guarantee that after a week or so with about 100 tabs open, I will get a crash - warning signs are that IFRAM elements in HTML (i.e. rectangular chunks of pages) turn into pop-up windows, and that if you close these Firefox will crash.  Some sites are unusable in this state so you have to restart anyway.

What's frustrating is that this is due to a known Firefox bug that has been unfixed for several years - see [http://ubuntuforums.org/showthread.php?t=1049958](http://ubuntuforums.org/showthread.php?t=1049958) for more details and link to the Mozilla bug posting.  It's Linux specific.  The sad thing is that nobody's fixed it in all this time.

Before someone says it's plugins, addons or Flash - I have tried a complely new profile, safe mode, etc, and none of those help.

Since not everyone uses 100 tabs at a time, I guess this bug is not a high priority, but it probably affects people with 10 tabs with a much lower probability.  

I've used Linux for 10 years now, and have used it as my main home desktop for much of that time, but I'm seriously considering getting a Mac laptop due to issues like this, and the sheer hassle of getting devices / sound to work.  I have had very time consuming problems with setup of sound, Flash, webcam and TV capture devices, and since I'm setting up a business I now can't afford the time to sort these out.

---

### Post by BlazeFire247 on 2009-06-10
I'm having the same problem. Firefox freezes whenever I upload a photo at Photobucket, or a file on my MediaFire. I don't know why that happens, and it's annoying.

---

### Post by bolweval on 2009-06-10
> **Copernicus1234 said:**
> Its very stable for me... sounds like your system has some kind of problem. Its not Firefox.

ditto...

---

### Post by growled on 2009-06-10
I have to agree with the above. I've been using Linux for 3 or 4 years now, used many different distros, and several versions of Firefox. I've never had any problems with it. I believe the error might be system related.

---

### Post by DouglasCaixeta on 2009-06-10
Firefox definitely sucks on Linux. Really, is too slow. Crash sometimes but very rare.
I use preload and still need to wait 5 seconds to open a single page! And I use just 4 addons.

Finally we can use Google Chrome, which is freaking fast! Unfortunately is still alpha.

---

### Post by WorfSOM on 2009-06-11
Been using Linux for a few years now and never had any problems with Firefox in any distro, even when multiple addons have been installed.

---

### Post by longtom on 2009-06-11
I had those problems with 8.10 and 9.04 with firefox, Opera, Epiphany....  In 8.04 all runs just fine.

---

### Post by DouglasCaixeta on 2009-06-11
I think the problem here is not Ubuntu, is Firefox.
They put a lot of effort to make it for Windows, because on windows we have a lot of good options.
What can we use on Linux?

Maybe you think Firefox is ok, but try to use Google Chrome for a day, and you will see how slow is Firefox.

---

### Post by Tamlynmac on 2009-06-11
> DouglasCaixeta
I think the problem here is not Ubuntu, is Firefox.
They put a lot of effort to make it for Windows, because on windows we have a lot of good options.
What can we use on Linux?You might try either Opera or Epiphany.

---

### Post by DouglasCaixeta on 2009-06-11
I already try. Opera has problems with some websites, and Epiphany don't have any plugins to use with.

---

### Post by Tamlynmac on 2009-06-11
> DouglasCaixeta
I already try. Opera has problems with some websites, and Epiphany don't have any plugins to use with. 	

Perhaps the solution lies in compromise. If you need the speed then you may have to sacrifice the plugins, etc. I doubt there's a solution that will meet the expectations of all.

I have no idea what your system specs are or if your issues may be improved by upgrading.

One thing I'm confident of - if the problem is directly related to either Ubuntu or Mozilla complaining here probably won't solve the problem. Nor will it be resolved without involvement from the devs. I've read many a post in this forum stating that the devs. don't spend much (if any) time on this forum. Might I suggest that notifying the devs (using the approiate procedure) directly, could improve the potential for resolution.

---

### Post by Cato2 on 2009-06-12
> **Tamlynmac said:**
> One thing I'm confident of - if the problem is directly related to either Ubuntu or Mozilla complaining here probably won't solve the problem. Nor will it be resolved without involvement from the devs. I've read many a post in this forum stating that the devs. don't spend much (if any) time on this forum. Might I suggest that notifying the devs (using the approiate procedure) directly, could improve the potential for resolution.

You are right on all counts - however, the Firefox crash bug I get every day was reported at  [https://bugzilla.mozilla.org/show_bug.cgi?id=263160](https://bugzilla.mozilla.org/show_bug.cgi?id=263160)  **five years ago in Firefox 0.9** and still is not fixed.  Clearly the open source model isn't working too well for this bug at least...

It would be great if Mozilla Foundation could use some of its huge revenues to pay developers to work on this and other long-standing bugs that are clearly not as exciting to work on as some other bugs/features.  Otherwise Firefox on Linux is unlikely to improve much IMO.

It's unfortunately that Firefox on Linux is not as good as on Windows - I end up using Windows Firefox on top of a virtual machine on Ubuntu, just to reduce the no. of crashes on Linux Firefox.

---

### Post by CK05 on 2009-06-13
[http://www.zixpk.com/2009/06/firefox-tweaks-that-will-increase-your.html](http://www.zixpk.com/2009/06/firefox-tweaks-that-will-increase-your.html)

We've all seen tweaks before from the about:config, but these ones really work. After tweaking I think it's just as good as windows again.

---

### Post by DouglasCaixeta on 2009-06-13
Why does it come already with the fastest configuration? Why do we have to change things manually? Why we have to worry about speed, while their job is about that?

---

### Post by longtom on 2009-06-14
> **DouglasCaixeta said:**
> Why does it come already with the fastest configuration? Why do we have to change things manually? Why we have to worry about speed, while their job is about that?

Ask them?  It is a fair question.  Please let us know what answer you get - would be nteresting to know.

---

### Post by dE_logics on 2009-06-14
Maybe the binaries are not supporting your hardware that well.

Why not try compiling from source?...its the fastest firefox you'll get; optimised for your system.

---

### Post by khelben1979 on 2009-06-14
[Bugs in Firefox extensions - launchpad]("https://bugs.launchpad.net/firefox-extensions").

(hope it hasn't been mentioned already, I didn't read all the replies..)

---

### Post by krul on 2009-06-14
I share the same experience, although with the latest beta's it seems becoming better.

But since the release of Opera 10 beta I really be astonished about the speed and fully Ubuntu support. All sites are working again, in earlier version of Opera there were too many issues on Ubuntu. I'd say give Opera 10 a try, you'll be amased!

---

### Post by supernix on 2009-06-15
I have never had a problem on any of my machines even the P4 running at 600MHZ yes that is a M not a G. They all run fine unless you add the wrong plugin as mentioned. But FireFox 3 rocks.

---

### Post by Cato2 on 2009-06-26
> **Cato2 said:**
> ... the Firefox crash bug I get every day was reported at  [https://bugzilla.mozilla.org/show_bug.cgi?id=263160](https://bugzilla.mozilla.org/show_bug.cgi?id=263160)  **five years ago in Firefox 0.9** and still is not fixed.  Clearly the open source model isn't working too well for this bug at least...


Firefox on Linux is getting worse, for me... I was having this bug all the time with 80 tabs (several crashes a day), but now Firefox won't even start up.  It's probably corruption of the session state (saved tabs) but then I'd expect the -safe-mode switch to work.  The session state corruption is probably down to one of the many crashes.

I really do like Firefox and have been using it on Linux as my primary browser for several years.  However, right now I'm using Firefox on a Windows VM, just to get work done, until I can figure out how to (a) get Firefox restarted and (b) recover my open tab URLs from the Tabmix Plus session files (again).

I realise this isn't the whole picture: I have a relative who does light browsing in Firefox and Linux and never has a problem - 2 to 3 tabs vs. my 80 plus.  Also, Firefox did just crash in Windows, but that was the first time in 3 months or so, and probably due to insufficient virtual memory in the VM (Windows had been complaining about this).

But it really is not good that a five year old bug that causes several crashes a day hasn't been fixed yet...

---

### Post by bhishan on 2009-06-26
just curious, what do u do with 80 tabs?

---

### Post by waspbr on 2009-06-26
never mind

---

### Post by Cato2 on 2009-06-28
Follow up on my 'Firefox won't start' problem - actually this was perhaps not Firefox's fault, but due to a problem with ESD (a sound service/daemon, alternative to the flaky PulseAudio).  A few days ago I had to restart esd, and a side effect of this was that when Firefox crashed, I could not restart it - I put an "strace" around the line in run-mozilla.sh that starts Firefox, and it showed it was hanging just after reading ~/.esd_auth.

Rebooting the PC fixed this.  Of course it's probably another Firefox bug that it can't deal with whatever problem ESD had - after all, most web pages don't need sound so Firefox should still start.

As for 80 tabs - I do a lot of web research and development for my business, using extensions such as Tab Mix Plus, Tree Style Tabs (and Tab Hunter) - these let you efficiently manage 100s of tabs and when Firefox is reliable you can leave them open for weeks, including full history and state.  

If you middle-click a link in Google search results, Tree Style tabs (which puts tabs on the left hand side so you can read a lot more of the title text on a big screen) opens them up in a collapsible tree under the tab with search results.

Firefox is an amazing browser and with plugins like Firebug/YSlow and HTTPFox it's outstanding for web development.  Just wish it could be more stable on Linux...  Hence I'm moving the heavyweight sites onto Firefox/Windows.   Opera is very stable but I find its equivalent of the Firefox 'awesome bar' very unusable as it searches the full text of pages.

The annoying thing is that I moved to Linux because it is generally so astonishingly stable - it's unfortunate that some GUI apps aren't stable, as it makes Linux a lot less viable as a desktop platform for me.

---

### Post by ngsupb on 2009-06-28
Cato2, did you try to install Swiftfox? I had some problems with Firefox, but after installing Swiftfox (the same firefox with the same addons but very optimized) I don't have problems anymore. It is faster and I think more stable.

---

### Post by harecanada on 2009-06-28
Hey rugbert,
Try this link. It's all about speeding up FireFox and it worked great for me. FF is lightning fast now.
harecanada

[http://ubuntuforums.org/showthread.php?t=1088094](http://ubuntuforums.org/showthread.php?t=1088094)

---

### Post by Simian Man on 2009-06-28
I'm using 3.5 beta 4 under F11 and it feels a **lot** faster than 3.1.  I'm sure it can be installed on Ubuntu.

---

### Post by moster on 2009-06-28
> **Simian Man said:**
> I'm using 3.5 beta 4 under F11 and it feels a **lot** faster than 3.1.  I'm sure it can be installed on Ubuntu.

Yes, but it crashes right after clicking full screen in youtube videos :)

---

### Post by Simian Man on 2009-06-29
> **moster said:**
> Yes, but it crashes right after clicking full screen in youtube videos :)

Not for me it doesn't.  Maybe when Ubuntu officially supports it you'll have a decent version :).

---

### Post by moster on 2009-06-29
> **Simian Man said:**
> Not for me it doesn't.  Maybe when Ubuntu officially supports it you'll have a decent version :).
No? Hm, I use swiftfox firefox 3.5 RC3

I knew subconscious that I was installing wrong version, but... I guess I had to have more "optimized" version :) Thanks for clearing that out.

---

### Post by Cato2 on 2009-06-30
> **ngsupb said:**
> Cato2, did you try to install Swiftfox? I had some problems with Firefox, but after installing Swiftfox (the same firefox with the same addons but very optimized) I don't have problems anymore. It is faster and I think more stable.

Not yet, and it's worth a try - however, I doubt that it fixes the specific [Firefox bug with IFRAME sites causing crash on Linux]("https://bugzilla.mozilla.org/show_bug.cgi?id=263160") (Bugzilla link) that I mentioned.

---

### Post by moster on 2009-06-30
3.5 come finally!

---

### Post by cariboo on 2009-06-30
moved to Recurring Discussions

---

### Post by d-man97 on 2009-07-02
> **moster said:**
> 3.5 come finally!

3.5 won't come until you upgrade your distro version - when it's released.

---

### Post by DouglasCaixeta on 2009-07-02
I read that the pango makes Firefox slow

[http://webupd8.blogspot.com/2009/07/ubuntu-speed-up-firefox-by-45.html](http://webupd8.blogspot.com/2009/07/ubuntu-speed-up-firefox-by-45.html)

---

### Post by SeanOScare on 2009-07-03
Firefox works absolutely fine for me.  I guess its disappointing that there are several add-ons that are not Linux compatible, but its my favourite web browser when I use Ubuntu.  I often wonder what is the point of making Opera available on Linux when it doesn't support the flash plugin?  Correct me if I got this wrong.

---

### Post by AnonCat on 2009-07-03
Flash works fine on my install of Opera.

---

### Post by Shadowking on 2009-07-03
> **defaultusername said:**
> rugbert,

What kind of plugins do you have installed? Flash/Java have a history of poor stability on Linux and used as browser plugins can make Firefox seem unstable. On low-end systems, too many plugins/extensions or pages open can suck up enough memory to cause a crash. Despite these considerations, Firefox will run on almost anything remotely modern without a hiccup, so I would suspect configuration issues.
Any way of improving flash performance on Ubuntu? Even youtube can't play well cos of this issue. Are there any alternatives for flash? I tried playing suptuxkart which is also very slow because of this.

---

### Post by emshains on 2009-07-03
> **rugbert said:**
>  Are there any plans to make it not suck so hard any time soon? 


I still can't stop laughing.

> Flash works fine on my install of Opera.
But it works even slower for me than on my install of firefox. They both crashed when I tried to watch southpark from their official website, only firefox could make a quick recovery, I killed the opera process, but the window of it was still there. (oh gosh, that last sentence sounds like a horror story for a kernel)

---

### Post by Cato2 on 2009-07-03
> **d-man97 said:**
> 3.5 won't come until you upgrade your distro version - when it's released.

It's actually very easy to install Firefox under /opt i.e. outside your normal Ubuntu-managed software.  Create a new directory /opt/firefox3.5, cd into it, download the .tar.bz2 file here, then run "tar xjvf firefox-blah.tar.bz2", then run "/opt/firefox3.5/firefox/firefox" (create a shell alias or script while you are testing it, then add it to the GNOME/KDE menus).

So far, Firefox 3.5 is stunningly fast, definitely noticeably faster with 100 tabs than Firefox 3.0.  I'll have to see if it crashes as much, but private browsing is nice and the native video support is amazing: just add a <video> tag, no need for proprietary Flash plugins etc.

If you use lots of extensions, you may have to hack them to try to make them compatible with 3.5 - this is best done by Googling for directions as it's not for newbies.  Probably 2/3 to 3/4 of my extensions worked without any changes, so you may not have to do this.

One tip for TabMix Plus (TMP) users - do a Session Export explicitly to a named session before quitting Firefox 3.0 and using Firefox 3.5.  Although a hacked TMP development build is working fine, I did lose my most recent session setup.

---

### Post by antiloop on 2009-07-03
I never had any problems with firefox performance in Ubuntu. It's as fast as in Windows 7 for me. Using Linux Mint 7 currently.

As long as I do this to fix my fullscreen flash problems (NVIDIA user) :
> 
sudo mkdir /etc/adobe
echo "OverrideGPUValidation=true" >~/mms.cfg
sudo mv ~/mms.cfg /etc/adobe/

---

### Post by cmltow on 2009-07-04
I started having the same hanging up problems in FF when I installed Jaunty, and it takes a little too long when launching some apps. But I have a five year old HP, and the only thing I have upgraded is the video card (to run Compiz). I only have 512mb of RAM (same amount of memory as the new video card) As soon as I upgrade the RAM, I'm sure these issues will go away. I just haven't had the need to upgrade until I installed Jaunty.

---

### Post by Cato2 on 2009-07-10
Firefox 3.5 is working quite nicely on Ubuntu 7.10 for me, but it still has the problem of crashing several times a day when I have about 100 tabs or more - see [this earlier posting for details]("http://ubuntuforums.org/showpost.php?p=7444095&postcount=102").  Reported **five years ago **and still not fixed.

Unfortunately this means I have to do more of my browsing on Windows (in a VM)...

---

### Post by Cato2 on 2009-07-13
Hi cmltow, 

I don't think increasing RAM will necessarily solve your crashes although it will speed things up.  Occasionally the Linux 'OOM Killer' will kick in if there is not enough memory combined with swap space. 

In my experience Linux (or Linux apps) doesn't crash much more when under memory pressure, PROVIDED you have a swap partition or file.  Type "swapon -s" to see how much swap you have, and run "top" - if it's less than 1 GB I would create a swap file, or add one on to the system - it can just be an ordinary file to avoid repartitioning.

Unfortunately Firefox 3.5 is crashing even more than 3.0 on Ubuntu, for me at any rate with 100 or so tabs.  The crashes include some that are unlike 3.0 crashes, i.e. I click on something and Firefox crashes.  (See earlier posts for a link to the bug report, and please comment here or on the bug report if you get this issue.)

With 3.0, I would only get crashes when an IFRAME was popped into a separate window due to the bug with how Firefox uses GTK.

I can only hope that Chrome on Linux puts some pressure on Firefox to improve... at least with Chrome it's only one tab that crashes, not the whole browser.

---

### Post by jago25_98 on 2009-07-13
I think what is needed is a way to tell the layperson using Firefox what is causing the problem, be it a plugin or settings. 

Checklist: Swiftfox, disable pango, purge SQL cache, check problematic extentions list (includes adblock!).
Alternatives: Chromium, Dillo, Opera, Konqueror. But I say start with swiftfox

For me slowness has been in the GUI. So I guess that's GTK

---

### Post by armagedonc on 2009-07-17
I had try opera but was worst than ff. FF didn't crash in my machine but is slow scrolling images and don't play online radios and video (youtube works like a charm) Maybe goggle chrome for linux will work better than this ff for ubuntu.

---

### Post by cmltow on 2010-01-23
I know this is an old thread., but I recently upgraded to 9.10, and that solved a lot of my issues. And soon after I upgraded to karmic I upgrade my RAM. You were right Cato2, the RAM probably wouldn't have helped the FF problems (upgrading to 9.10 sure helped), but it sure as hell sped up my day to day processes (512mb to 2gb).

---

### Post by Cato2 on 2010-01-24
At the moment Firefox is not crashing at all, still on Ubuntu 8.04 but now using Firefox 3.5.7 - a recent 3.5.x update seems to have fixed the crash bugs I was having.

---

### Post by pmorton on 2010-02-02
I agree with the original poster, to the extent that Firefox has always been among the biggest crashers of any of my apps. It's a complicated application, I know, but then Mozilla has had a good income from Google to pay for maintaining it. 

I'm using now 3.5.6, and it has yet again leaked memory away to nothing, as it has had a tendency to do for years. I don't know if it's just the Linux version.

Knowing there are other good browsers around, I'm wondering if I've persevered long enough.

---

