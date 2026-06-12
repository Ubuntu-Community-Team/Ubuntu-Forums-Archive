---
title: "64 bit, is it worth it?"
date: 2008-12-24
forum: Recurring Discussions
---

### Post by dottedquad on 2008-12-24
Hello all!  I've been using Ubuntu for 1yr now and haven't looked back since.  Now, I'm in the market to upgrade my computer.  New cpu, motherboard and the works.  I've noticed how much the price dropped on AMD quad core CPUs and I am looking closely into buying one.

How is Ubuntu in the 64bit world and is it hard to get drivers and what not to work on a 64bit system or, should I just stick to with 32bit for now?

-thanks,
     Rich

---

### Post by Kosimo on 2008-12-24
> **dottedquad said:**
> Hello all!  I've been using Ubuntu for 1yr now and haven't looked back since.  Now, I'm in the market to upgrade my computer.  New cpu, motherboard and the works.  I've noticed how much the price dropped on AMD quad core CPUs and I am looking closely into buying one.

How is Ubuntu in the 64bit world and is it hard to get drivers and what not to work on a 64bit system or, should I just stick to with 32bit for now?

-thanks,
     Rich

Acutally 64bit has a "reasonable good" support. All the major apps, Firefox, Flash Player 10, nvidia or ati drivers,  etc are already available for 64bit. But, at the moment I don't see any real benefit to moving to 64bit.

---

### Post by cariboo on 2008-12-24
Now that there are 64bit plugins for flash and java, there is no reason to stay away from a 64bit didtribution.

Jim

---

### Post by jamesrl on 2008-12-24
Depends what you are doing.  On my Intel core 2, I got signficantly faster (e.g., ~50%) performance executing certain python scripts (computational analysis for work involving arrays of 64 bit floats) running in 64 bit mode than 32 bit mode.

But for say any other application I rarely notice a difference, and maybe flash works a tad poorer (e.g., i notice significant video quality decline with multiple flash videos going simultaneously) than in 32 bit.

---

### Post by dottedquad on 2008-12-24
On the machine I use day to day is practically an all around machine.  I pretty much do everything and program in PHP the most.  I'm looking for a machine that will last me 5+ yrs without the worries of upgrading.  I do, however, understand that may not be possible to do hardware failing.

-Rich

---

### Post by overdrank on 2008-12-24
Hi and I would say if your system can support it then use 64bit. :)

---

### Post by jerome1232 on 2008-12-24
> **cariboo907 said:**
> Now that there are 64bit plugins for flash and java, there is no reason to stay away from a 64bit didtribution.

Jim

Well as much as I normally say go 64 bit the only exception is if the computer is low on ram in the first place. I just switched back to 32 bit on my 1 GB of ram system and am using ~20% less ram. On 1 GB of ram this is enough reason to keep me here until I can get more ram for this system.

---

### Post by Ben Page on 2008-12-24
This is a simple Q.
If youre using 3 or 4 GB of RAM go 64bit, If youre using 2GB or less RAM, go 32bit.
Only real advantage of 64 bit OS is a posibility to alocate 3+ GBs of RAM, as the apps go, were not there yet, in few years, maybe, but not just yet.
It is stoopid to build 64bit system for now (exeptional cases and profesionals excluded).

---

### Post by interurban on 2008-12-24
I've used both 64 and 32 bit in the last few months and didn't really notice a difference performance-wise.  Like they said above, the biggest benefit is if you're doing intense calculations.  It's really up to you.  I'd say go 64 bit, it might take a little cajoling to get things "just right" but it's easier to do it now than have to switch a couple of years down the road.

---

### Post by bodhi.zazen on 2008-12-24
> **Ben Page said:**
> This is a simple Q.
If youre using 3 or 4 GB of RAM go 64bit, If youre using 2GB or less RAM, go 32bit.
Only real advantage of 64 bit OS is a posibility to alocate 3+ GBs of RAM, as the apps go, were not there yet, in few years, maybe, but not just yet.
It is stoopid to build 64bit system for now (exeptional cases and profesionals excluded).

32 bit OS can access up to 64 Gb RAM. It is called [PAE](http://en.wikipedia.org/wiki/Physical_Address_Extension)

When you say otherwise you :

1. Help propagate mis information.

2. sound uneducated.

So please do not do this.

---

### Post by chewit on 2008-12-24
64bit is best for muilt-core processors and more than 3GB RAM. 64bit is omptimized for muilt-core processing as well.

---

### Post by fSubZero on 2008-12-24
> **bodhi.zazen said:**
> 32 bit OS can access up to 64 Gb RAM. It is called [PAE](http://en.wikipedia.org/wiki/Physical_Address_Extension)

When you say otherwise you :

1. Help propagate mis information.

2. sound uneducated.

So please do not do this.

However, using PAE does have a negative impact on system performance, and not all apps will take advantage of it.

(Sorry, for the MS link, but it's a good treatment of the issue when dealing with intel chipsets)
[http://www.microsoft.com/whdc/system/platform/server/PAE/pae_os.mspx](http://www.microsoft.com/whdc/system/platform/server/PAE/pae_os.mspx)

---

### Post by smuggly on 2008-12-24
Give Ultimate Edition_64 A Try2.0 Just Came Out.Im Running 1.8 LTS (Hardy)_64 But 2.0 Is Intrepid .I Love It .Im Running AMD 9750X4 Phenom.It Runs Great.Very Quick.....smuggly

[http://forumubuntusoftware.info/index.php?sid=9f68ca1499147e4120c8c6b11bf72ff8](http://forumubuntusoftware.info/index.php?sid=9f68ca1499147e4120c8c6b11bf72ff8)

---

### Post by gn2 on 2008-12-24
64 bit will do some tasks significantly faster than 32 bit: [http://tinyurl.com/6gbtw9](http://tinyurl.com/6gbtw9)

If the hardware supports 64 I say go 64.

---

### Post by Titan8990 on 2008-12-24
> 32 bit OS can access up to 64 Gb RAM. It is called PAE


While this is true, not all boards support PAE.


> 64bit is best for muilt-core processors and more than 3GB RAM. 64bit is omptimized for muilt-core processing as well.


I'm pretty sure all the Ubuntu kernels have it set for multi-core optimization.

---

### Post by bodhi.zazen on 2008-12-24
> **fSubZero said:**
> However, using PAE does have a negative impact on system performance, and not all apps will take advantage of it.

(Sorry, for the MS link, but it's a good treatment of the issue when dealing with intel chipsets)
[http://www.microsoft.com/whdc/system/platform/server/PAE/pae_os.mspx](http://www.microsoft.com/whdc/system/platform/server/PAE/pae_os.mspx)

That may be true for windows, to be honest I am not sure. And that page is comparing PAE to a 64 bit OS. Obviously this may be a choice when purchasing hardware, but I know of no way to run a 64 bit kernel on a 32 bit core.

I have not noticed a performance hit on Linux, although I do not have benchmarks to prove it.

And not every app uses dual cores or high memory on a 64 bit OS either.

My point still stands, 32 bit OS can handle up up 64 Gb of RAM.

---

### Post by gn2 on 2008-12-24
> **bodhi.zazen said:**
> My point still stands, 32 bit OS can handle up up 64 Gb of RAM.

So long as the OS isn't most 32 bit versions of Windows: [http://en.wikipedia.org/wiki/Physical_Address_Extension#Windows](http://en.wikipedia.org/wiki/Physical_Address_Extension#Windows)

---

### Post by bodhi.zazen on 2008-12-24
tis true, Microsoft charges for a PAE enabled kernel 9which is probably why most people do not know about it), yet another reason I do not run Windows :twisted;

---

### Post by insane_alien on 2008-12-24
PAE is a hack at best. 64-bit would use the address space far more efficiently as it wouldn't have to rely on blocked storage.

as for the OP, of course 64-bit is worth it, it gives you exactly the same hassle as the 32-bit installation(none) and you get more for your buck(in this case, including getting your buck back)

---

### Post by bodhi.zazen on 2008-12-24
> **insane_alien said:**
> PAE is a hack at best. 64-bit would use the address space far more efficiently as it wouldn't have to rely on blocked storage.

Again I ask, how exactly do you install a 64 bit on on a 32 bit CPU ?

---

### Post by fSubZero on 2008-12-24
> **bodhi.zazen said:**
> That may be true for windows, to be honest I am not sure. And that page is comparing PAE to a 64 bit OS. Obviously this may be a choice when purchasing hardware, but I know of no way to run a 64 bit kernel on a 32 bit core.

I have not noticed a performance hit on Linux, although I do not have benchmarks to prove it.

And not every app uses dual cores or high memory on a 64 bit OS either.

My point still stands, 32 bit OS can handle up up 64 Gb of RAM.


I wasn't trying to disagree with you, just to point out that PAE isn't a perfect solution if you are concerned about perfomance. The OS is still using 32bit addressing and there are what are essentially "hacks" as (someone else pointed out) to utilize memory outside of the 32bit address range. Without even reading any technical papers, you can probably logically conclude that in order to do this, you will encounter some form of translation to the higher ranges and thus performance will be affected by increased processor usage and slower memory reads.  

Whether that's relevant (or noticeable) is purely up to the use you want to put your system. I would guess (as you said) that most end-users would never notice the difference.

---

### Post by fSubZero on 2008-12-24
> **bodhi.zazen said:**
> Again I ask, how exactly do you install a 64 bit on on a 32 bit CPU ?

You wouldn't. It won't work unless the chip supports the 64bit instruction set.

---

### Post by Gulyan on 2008-12-24
> **bodhi.zazen said:**
> Again I ask, how exactly do you install a 64 bit on on a 32 bit CPU ?
32 bit processors can not execute 64 bit code :)

---

### Post by acalafra on 2008-12-24
I've been running 64 bit since fiesty and never really had any problems with it. Sure it took a little more work to get flash working but there was plenty of guidance available. These days its a cake walk. Flash and Java now readily available. And anything that doesnt work usually just needs a --force-architecture...i'd go for it

---

### Post by egalvan on 2008-12-24
> **bodhi.zazen said:**
> 32 bit OS can access up to 64 Gb RAM. It is called [PAE](http://en.wikipedia.org/wiki/Physical_Address_Extension)

When you say otherwise you :

1. Help propagate mis information.

2. sound uneducated.

So please do not do this.

This leaves me with a question...

I just installed 8GB RAM on a dual-core AMD X2.

An Ubuntu 8.04.1 32bit LiveCD showed less than 4GB under top.

Installed 8.04.1 32bit Server, and top now shows all 8GB.

I read that the kernel has different flags set for desktop  and Server. Is this the explanation?

Thanks.

ErnestG

---

### Post by jamesisin on 2008-12-24
> **bodhi.zazen said:**
> Again I ask, how exactly do you install a 64 bit on on a 32 bit CPU ?

Not to nitpick but the OP is talking about buying/building new hardware.

Shall I ask you how to install more than 2gb of RAM in my Dell Dimension 8200?

My new machine, which I just purchased, is a 64bit quad proc.  I am running a 64bit os on that machine.  In part, I am doing this to increase the market share for 64bit writers.  (But it is really fast.)  I wouldn't mind seeing 32bit go the way of the dodo--eventually.

---

### Post by Keen101 on 2008-12-24
Yep, i think 64 bit is the way to go.

---

### Post by RaveJunkie on 2008-12-24
I had the "advantage" of starting to use linux on the x64bit architecture.  I found the biggest headache was waiting to use flash,  but i finally have the plugins and everything works.  As for crashes and no hardware support?  i see none really, i have a brand new gaming rig and it works flawlessly till i mess with it  LOL.   


The other HUGE headache latly was trying to get adobe AIR to work,   by doing that you have to install the 32libs and even after i did that it still dont work, and after reading 12 links i gave up.    For that matter adobe sucks, they have like nearly no 64bit support on most things or have to be begged to do so it seems.  F them i say.....


I have SLI running with 8 gigs of ram,  so its fun to emulate winblows VIA vm then watch a movie and pretty much anthing i can think up other then a benchmark test and not even peg the cpu or ram...... love it.

---

### Post by dottedquad on 2008-12-24
Interesting!  It's practically a tie on which way to go.  Honestly, I'm not using my computer to compile huge mathematical calculations.  I'm also not a gamer.  The only reason I thought about 64bit is I can use more ram(4+ gigs).  Also, I'm looking towards the future.  If I buy a quad core AMD processor can that cpu down grade to 32bit?

-Thanks,
     Rich

---

### Post by RaveJunkie on 2008-12-24
Also was going to say im running a quad boot with vista 32bit and 64bit ultimate..... 64bit ultimate is a NON stop headache and soooo not worth it and sits idle using like 10-20 % of my ram..... but thats a big deal when you have 8 gigs!!!

---

### Post by nynoah on 2008-12-24
I am on 64bit and have been for well over a year now.  I have had no problems with 64 bit.  If you multitask or run many programs in the background (such as Torrents or multiple vids or vids while doing other things) it really does make a difference.

---

### Post by jamesisin on 2008-12-24
If you buy 64bit hardware you ought to be able to run a 32bit system on it (it depends, as it always does, on driver availability).  64bit architecture is backwards compatible.

If you are thinking of the future, then you should certainly look to 64bit hardware.  You can always set up a dual boot environment to compare for yourself a 64bit and a 32bit system.

My original dream was to set up a 64bit Ubuntu machine with ungodly amounts of ram and then run a 32bit vm for those applications which won't run in 64bit (I'm not clear that Ubuntu 64bit includes a 32bit emulation layer for running old applications--Windows Vista does).  I am holding off on that particular dream for now, mostly because I have several 32bit machines I can use for the other stuff.

But in the end if I were buying new machines (and in the last two years I have bought two) I would buy 64bit without question.

Remember, if you buy 32bit hardware you cannot make the test I described above.

---

### Post by bodhi.zazen on 2008-12-24
I think I would like to clarify my message , if that makes sense.

I think you should run a kernel appropriate to your CPU and RAM.

I you have a 32 bit processor -> 32 bit OS, PAE if you have > 3.2 Gb RAM

If you have a 64 bit processor -> IMO you should at least start with a 64 bit kernel.

I run 64 bit Ubuntu on my 64 bit processors and, IMO, support is equal to 32 bit support.

If you have a specific reason to run a 32 bit OS, like say the need for wine (64 bit is in development for example) then you can run 32 bit on a 64 bit processor without any problems.

---

### Post by bodhi.zazen on 2008-12-24
> **jamesisin said:**
> Not to nitpick but the OP is talking about buying/building new hardware.

Well, since you asked ....

I was not responding to the OP, I was clarifying mis information that was posted later in the thread.

---

### Post by jamesisin on 2008-12-24
No harm, no foul.

Mostly I think we agree anyway.

Can this PAE theoretically be applied to a 64bit architecture?

---

### Post by jerome1232 on 2008-12-24
> **jamesisin said:**
> No harm, no foul.

Mostly I think we agree anyway.

Can this PAE theoretically be applied to a 64bit architecture?

64 bit can theoretically access 16 exabytes of ram. I don't think we'll be exceeding that any time soon.

---

### Post by bodhi.zazen on 2008-12-25
> **jamesisin said:**
> No harm, no foul.

Mostly I think we agree anyway.

Can this PAE theoretically be applied to a 64bit architecture?

In theory, yes. fSubZero was pointing out some limitations of this.

If your cpu is pae enabled (the 64 bit CPU I have seen are) you can then run a pae enabled 32 bit kernel to access additional ram.

```
grep --color=always pae /proc/cupinfo
```

will show you if your cpu is pae enabled.

Again, although I do not have the bench marks to prove it, with a 64 bit cpu, I think your performance would be better with a 64 bit kernel rather then a 32 bit pae enabled kernel.

Although again to be honest the "average" desktop user will not likely see a huge difference between all these options.

Personally, the only time I use pae is on the rare occasion I am running a 32 bit pae enabled cpu with > 3.2 Gb RAM.

To see if you have a 64 bit cpu use 

```
grep --color=always ' lm ' /proc/cpuinfo
```

---

### Post by bodhi.zazen on 2008-12-25
> **egalvan said:**
> This leaves me with a question...

I just installed 8GB RAM on a dual-core AMD X2.

An Ubuntu 8.04.1 32bit LiveCD showed less than 4GB under top.

Installed 8.04.1 32bit Server, and top now shows all 8GB.

I read that the kernel has different flags set for desktop  and Server. Is this the explanation?

Thanks.

ErnestG

Yes, the server kernel is pae enabled.

---

### Post by gn2 on 2008-12-25
> **bodhi.zazen said:**
> 
Again, although I do not have the bench marks to prove it, with a 64 bit cpu, I think your performance would be better with a 64 bit kernel rather then a 32 bit pae enabled kernel.

For certain tasks e.g. encoding audio and video, there are definite advantages with 64-bit. 
As shown here:  [http://tinyurl.com/6gbtw9](http://tinyurl.com/6gbtw9)

---

### Post by jamesisin on 2008-12-25
Thanks, jerome1232.  You got what I was driving at.  I'll be working on that for my next machine.  Them's a lotta bytes.

---

### Post by egalvan on 2008-12-26
> 8.04.1 32bit Desktop
8.04.1 32bit Server

I read that the kernel has different flags set for desktop and Server. Is this the explanation?
Thanks. ErnestG


> **bodhi.zazen said:**
> Yes, the server kernel is pae enabled.


Is there any reason given why the desktop version does not have PAE enabled?

Does the desktop kernel see and use multiple cores  i.e. SMP?

Do you see any dis/advantages to using the server kernel with Gnome or KDE DM's?

ErnestG

---

### Post by indiana_crook on 2008-12-26
Lets face it, the world and technology is evolving.  Everything that "is now", will soon be "once was."  32 bit will be obsolete before you know it.  Use 64 bit if you have the option, you won't regret it.  Mine is awesome!

---

### Post by jerome1232 on 2008-12-26
> **egalvan said:**
> 
Does the desktop kernel see and use multiple cores  i.e. SMP?


I can answer one of those yes it does, the server kernel does too.

```
Linux deathbane 2.6.24-22-server #1 **SMP** Mon Nov 24 19:14:19 UTC 2008 i686 GNU/Linux

Linux direbane 2.6.27-9-generic #1 **SMP** Thu Nov 20 21:57:00 UTC 2008 x86_64 GNU/Linux
```

---

### Post by bodhi.zazen on 2008-12-26
> **egalvan said:**
> Is there any reason given why the desktop version does not have PAE enabled?

IMO no good reason. there have been requests to provide a PAE enabled desktop kernel.

> Does the desktop kernel see and use multiple cores  i.e. SMP?The general kernel does yes. You can test with :

```
cat /proc/cpuinfo
```It will list your CPU.

> Do you see any dis/advantages to using the server kernel with Gnome or KDE DM's?

ErnestGThe server kernel is optimized for server functions (primarily file transfer). The average user will probably not notice much of a performance difference, but to be honest, compiling the desktop kernel to enable PAE is not *too* difficult.

---

### Post by jamesisin on 2008-12-26
I ran cat on cpuinfo and it says I have 1 core.  My System Monitor shows both cores.  Explain?

---

### Post by bodhi.zazen on 2008-12-26
Please post the output of cat /proc/cpuinfo

or you can :

```
grep --color=always 'cpu cores' /proc/cupinfo
```

And 

uname -a

keep in mind, the first processor is 0 , the second is 1

---

### Post by jamesisin on 2008-12-26
Ah, I see.  I misread the output.  It lists my two cores as two procs (each with one core).  Not exactly correct but close enough I guess.

---

### Post by Cracauer on 2008-12-26
Debian and hence Ubuntu have almost completely ignored supporting 32 bit binaries in 64 bit installations.

There are some things that want to run in 32 bits, namely web browser chains involving Flash and video players (xine etc.) that use the Win32 binary codecs. 

Other things apply, for example Wine, 32 bit Windows emulation in 64 bits, breaks for me when I go from libc-2.3 to 2.7.

Unless you are either sure you need none of this junk, or you are comfortable using chroots, or you can relocate things very well (just LD_LIBRARY_PATH will not do for any of the above thanks to general GNOME braindamage) you should stay with 32 bits.

A PAE kernel will allow you to use RAM above 4 GB.

The only thing you are really missing is things that need more than 3 GB of virtual memory, but that's very rare. The speed difference is too small to play a role.

---

### Post by wmichaelb on 2008-12-26
That's interesting. I'm running both 32- and 64-bit versions on two different sets of partitions in the same systems, and on Firefox 3.0, the difference feels like 2:1 faster on 64-bit. The same is true for the 64-bit version of SUSE 11.0 compared to the 32-bit version of 8.04. My system uses a base Intel 2180 2 GHz core 2 duo with 2 GB of RAM. I think I've got $250 total in the system, and it really runs.

---

### Post by bodhi.zazen on 2008-12-27
> **Cracauer said:**
> Debian and hence Ubuntu have almost completely ignored supporting 32 bit binaries in 64 bit installations.

There are some things that want to run in 32 bits, namely web browser chains involving Flash and video players (xine etc.) that use the Win32 binary codecs.

I have all those things running with no problem at all in both 8.04 and 8.10. I did not need to do much of anything manually (the only thing was a little trick for playing DVD, but the procedure is the same for 32 and 64 bit).

> Other things apply, for example Wine, 32 bit Windows emulation in 64 bits, breaks for me when I go from libc-2.3 to 2.7.

Wine is more problematic, or so I hear. I very rarely run Windows, and usually to test something like samba or cross platform software. Why not just run virtualization ?

> Unless you are either sure you need none of this junk, or you are comfortable using chroots, or you can relocate things very well (just LD_LIBRARY_PATH will not do for any of the above thanks to general GNOME braindamage) you should stay with 32 bits.

64 bit is much easier, IMO, with the exception of wine, then you make it sound. I have not had to do anything with chroot or LD_LIBRARY_PATH to get flash, music, or DVD/Movies on 64 bit OS.

Please do not take this post as oppostional, but my experience with 64 bit has not been as you describe (although it was some time ago).

> A PAE kernel will allow you to use RAM above 4 GB.

You are preaching to the choir now, music to my ears.

> The only thing you are really missing is things that need more than 3 GB of virtual memory, but that's very rare. The speed difference is too small to play a role.

I agree. Most desktop users will not use more then 2 Gb max.

---

### Post by Cracauer on 2008-12-27
> **bodhi.zazen said:**
> I have all those things running with no problem at all in both 8.04 and 8.10. I did not need to do much of anything manually (the only thing was a little trick for playing DVD, but the procedure is the same for 32 and 64 bit).


You run a 32 bit firefox or 32 bit xine on 64 bit Ubuntu without having had to do much? How?

---

### Post by bill516 on 2008-12-27
OK, I went to the Wikipedia page re PAE and thanks for he suggestion.  Now help me with a variant on Dottedquad's initial question.

Suppose we are going to purchase a new machine from a Linux vendor who will install a distribution available in 32 or 64 bit versions.

Suppose we put, let us say, 8 gigs of ram in the machine (who knows why, but we do).

Now, is Bodhi.zazen saying that both the 32 bit and 64 bit OS versions will see and utilize the full 8 Gigs of Ram?

Even if that is true should we not assume that a 64 bit system would use it more efficiently?

I ask because I too have been trying to figure out just what the advantage is to a 64 bit Linux system.  My 32 bit system works very well indeed, but I would move to 64 bit if a good case could be made for it.

---

### Post by gn2 on 2008-12-27
> **bill516 said:**
> 

Suppose we are going to purchase a new machine from a Linux vendor who will install a distribution available in 32 or 64 bit versions.

Suppose we put, let us say, 8 gigs of ram in the machine (who knows why, but we do).

Now, is Bodhi.zazen saying that both the 32 bit and 64 bit OS versions will see and utilize the full 8 Gigs of Ram?

Even if that is true should we not assume that a 64 bit system would use it more efficiently?

I ask because I too have been trying to figure out just what the advantage is to a 64 bit Linux system.  My 32 bit system works very well indeed, but I would move to 64 bit if a good case could be made for it.

32 bit Ubuntu needs to be tweaked to use that much RAM, a default installation won't see it all.

The advantage of 64-bit comes with certain tasks for example video or audio encoding which will complete much quicker in 64-bit.

---

### Post by bodhi.zazen on 2008-12-27
> **Cracauer said:**
> You run a 32 bit firefox or 32 bit xine on 64 bit Ubuntu without having had to do much? How?

No, I do not run either of those. I run the default firefox from the repos (I assume it is 64 bit, but I do not know).

I do not run xine.

I run vlc.

I agree, if you insist on running 32 bit applications you will struggle with 64 bit Ubuntu.

So yes, you need to evaluate your needs when choosing an OS, same as windows vs Ubuntu vs Fedora vs Centos vs Gentoo vs Slackware vs ....

My point is, if you do not *need* wine, or you use virtulization for your windows needs, 64 bit Ubuntu will do most tasks (note tasks, not applications). I can browse the web, play music, watch movie DVD, everything I want, all with the default apps, or at least the ones I chose to use, all with minimal effort. In fact it is as easy s the 32 bit version,

I felt your posting style exaggerates the "difficulty" of running 64 bit Ubuntu by insisting on or using certain applications that have no 64 bit port without explaining the 64 bit alternates that basically work without any difficulty.

---

### Post by jerome1232 on 2008-12-27
I'm curious as to why you guys are saying wine is hard to run under 64 bit...

I installed wine from the repository, then I fire up my favourite Windows game and it works... It's still a 32 bit Windows environment and everything but there aren't any hitches that I can see.

I understand if I were to compile wine I have to jump through a few hoops but just to install and use no.

For those rare times you run into a 32 bit program with 32 bit library dependencies getlibs comes to the rescue. It's always worked for me.

I actually switched back to 32 bit recently and after 3 days using it I'm updating my backups and moving back to 64 bit transcoding is going way to slow over here in 32 bit land.

---

### Post by bodhi.zazen on 2008-12-27
Thanks for the update jerome1232.

As I said I do not use wine at all, so the last time I looked wine, like flash, would not run on 64 bit Ubuntu without a bit of work.

Glad to hear it has changed for the better.

---

### Post by Cracauer on 2008-12-27
OK, let's backtrack before it gets confusing.

Wine actually does run on 64 bits, that means 32bit Win32 runs on 64 bits, it is just more fragile. In particular for me it broke completely under libc-2.7/ld-2.7.so.

Running an actual 32 bit Firefox chain or 32 bit Xine chain is a pain in the allerwertesten, and a first grade one. You can of course run Firefox and Xine in 64 bits, but you have to wrap the 32 bit Flash (unless you run Flash10 which is available in 64 bits) and you will not be able to use the Win32 codecs in a 64 bit Xine.

I never claimed it's undoable, in fact I have a variety of chroots and self-build relocated trees to help this, but it is advanced Unix usage.  If you want a turn-key system with no fancy plugin wrappers and able to play all the exotic video codecs you have to start at 32 bits.

The speed advantage of 64 bits will usually only show up in things like SQL servers that make use of a lot of 64 bit numbers. There are more registers but it doesn't cause a massive speedup in amd64. It is not possible that you can feel a speed advantage on the desktop from this.  If 64 bit Ubuntu feels faster than 32 bit it must be in the build options. It could be built with less junk compiled on or with different compiler flags. It's also possible that the kernel doesn't use all your RAM.

On the contrary, the same program compiled for 64 bits can be slower because it takes up more memory.  Each pointer is now 64 bits instead of 32 (wasting 4 bytes for each pointer) and a lot of integers that were randomly declared "long" for no reason (not needing the extended range) are now also wasting 4 bytes each.

In some code this can be a huge increase. Complicated, dynamic code that makes heavy use of linked lists, or double linked lists, can easily operate on data twice the size, trashing your CPU caches, TLBs and possibly RAM.

---

### Post by Cracauer on 2008-12-27
> **bodhi.zazen said:**
> 
I do not run xine.

I run vlc.

Same problem, if you want to run the collection of binary Win32 codecs you need a 32 bit player.

---

### Post by pinged on 2008-12-27
Well if you want one to last 5+ years than go with the intel/amd quad core 64 bit processor, at the moment i'm looking into investing in one. 
If you want one to last your whole life than that would be the top spec mac pro with 2 quad core intel 64 bit processors and every other top spec you can get on it all for about $35000

---

### Post by Coder543 on 2008-12-27
32-bit computers _***cannot***_ I repeat **_*cannot*_** use more than 4 gigs of ram. This is mathematically provable! The computer uses 32 bits for each memory address. So what is the maximum value 32 bits can hold? 4.2949673E9. What does that mean?
4.2949673E9 bytes
4194304 kilobytes
4096 megabytes
4 gigabytes

This is not a marketing scam, this is a mathematical fact.

---

### Post by jerome1232 on 2008-12-27
> **Coder543 said:**
> 32-bit computers _***cannot***_ I repeat **_*cannot*_** use more than 4 gigs of ram. This is mathematically provable! The computer uses 32 bits for each memory address. So what is the maximum value 32 bits can hold? 4.2949673E9. What does that mean?
4.2949673E9 bytes
4194304 kilobytes
4096 megabytes
4 gigabytes

This is not a marketing scam, this is a mathematical fact.
Yes they can, we just pretend it's 36 bits
[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

---

### Post by bodhi.zazen on 2008-12-27
> **Coder543 said:**
> 32-bit computers _***cannot***_ I repeat **_*cannot*_** use more than 4 gigs of ram. This is mathematically provable! The computer uses 32 bits for each memory address. So what is the maximum value 32 bits can hold? 4.2949673E9. What does that mean?
4.2949673E9 bytes
4194304 kilobytes
4096 megabytes
4 gigabytes

This is not a marketing scam, this is a mathematical fact.

I always LOL when I read /. hear these kinds of posts.

I love the blank stares you get when you try to educate people.

The PAE kernel adds 4 bits, so you need to re-do the math.

32 bit kernels can use up to 64 Gb RAM if they are PAE enabled (hardware side) and use a PAE kernel (software side).

Again, read this link:

[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

It has additional links if you wish to read the technical details.

Otherwise, when you make such claims / posts you just make yourself look bad / uneducated.

---

### Post by bodhi.zazen on 2008-12-27
> **Cracauer said:**
> I never claimed it's undoable, in fact I have a variety of chroots and self-build relocated trees to help this, but it is advanced Unix usage.  If you want a turn-key system with no fancy plugin wrappers and able to play all the exotic video codecs you have to start at 32 bits.

If you wish to make customizations, that is fine. In fact that is what makes Linux fun (IMO).

I got the impression from your posting style that you are implying that all this is somehow necessary to run 64 bit Ubuntu.

So ...

I am just clarifying, for anyone new to 64 bit Ubuntu, that none of this is necessary. You can for the most part do anything with a 64 bit Install of Ubuntu that you can do with a 32 bit install of Ubuntu.

64 bit Ubuntu works "out of the box" and flash and the various codics and DVD playback are no more difficult then a 32 bit install.

If you wish to customize, more power to you. But these customizations are no longer necessary (they were when 64 bit was first released).

---

### Post by jamesisin on 2008-12-27
Is there a nice tutorial for setting up PAE (on 8.10)?

I may as well try it out on this machine (currently showing 3.6gb ram), unless there is a doomsday caution I should know about.  This is my main machine after all.

---

### Post by theozzlives on 2008-12-27
I went to 64 bit for awhile on my coreduo laptop, I ran into a few apps and drivers I couldn't install. Of course one computer was running Jaunty Alpha 1 for awhile. Now my whole network is 32 bit 8.10. I can run an apt-cacher that way.

---

### Post by bodhi.zazen on 2008-12-27
> **jamesisin said:**
> Is there a nice tutorial for setting up PAE (on 8.10)?

I may as well try it out on this machine (currently showing 3.6gb ram), unless there is a doomsday caution I should know about.  This is my main machine after all.

yes.

You can install the server kernel (it is PAE enabled) or you can compile your own :

[http://ubuntuforums.org/showthread.php?t=855511](http://ubuntuforums.org/showthread.php?t=855511)

In the long run, if you stay with 32 bit, I advise compiling your own, but that is me ...

---

### Post by jamesisin on 2008-12-27
What advantage do I gain by compiling my own?

---

### Post by bodhi.zazen on 2008-12-27
The server kernel is optimized for servers, ie file sharing and not for typical desktop utilities. 

Truth be told, you are unlikely to notice much of a difference.

Compiling your own kernel = 1 geek point, 5 points if it boots :twisted:

---

### Post by egalvan on 2008-12-27
> **gn2 said:**
> 32 bit Ubuntu needs to be tweaked to use that much RAM, a default installation won't see it all.

.

I'm running a 32bit Ubuntu, and it sees all 8GB very well, thank you.
No "tweaks" needed.

Ok, it's the SERVER 32bit Ubuntu, as I've yet to put a DE on it.
Command line only, for now.

And thanks to Bohdi.zazen for his support in this.:)

ErnestG

---

### Post by egalvan on 2008-12-27
bodhi.zazan chuckles when he reads post "proving" that 32-bit OS's cannot use/see more than 4G of RAM.

And I agree completely with him.

But I also chuckle when I see ANY post trying to prove that "32bit is better/worse than 64bit, and/or needed / not needed".

I saw similar arguments (RAM sizes adjusted) when the industry moved from 16bit to 32bit.

I saw similar arguments (RAM sizes adjusted) when the industry moved from 8bit to 16bit.

I saw similar arguments (RAM sizes adjusted) when the industry moved from 4bit to 8bit.:lolflag:

Let's face it folks, the wave keeps moving on, and if we don't move, it will roll right over us.

And does anyone else remember that famous software man saying
"No one will ever need more than 512**KiloBytes** of memory"?:P

---

### Post by Cracauer on 2008-12-28
> **Coder543 said:**
> 32-bit computers _***cannot***_ I repeat **_*cannot*_** use more than 4 gigs of ram. This is mathematically provable! The computer uses 32 bits for each memory address. So what is the maximum value 32 bits can hold? 4.2949673E9. What does that mean?
4.2949673E9 bytes
4194304 kilobytes
4096 megabytes
4 gigabytes

This is not a marketing scam, this is a mathematical fact.

Apart from PAE ignorance you also seem to confuse physical and virtual memory. Did you read much of the discussion to far?

I personally run a box like this:
```

Linux pls.[censorred] 2.6.24.3-perfctr-cracauer
#5 SMP PREEMPT Wed Apr 23 08:08:15 EDT 2008 i686 GNU/Linux
             total       used       free     shared    buffers     cached
Mem:      11850980    8192196    3658784          0     317032    4717584

```

---

### Post by Cracauer on 2008-12-28
> **bodhi.zazen said:**
> 
If you wish to customize, more power to you. But these customizations are no longer necessary (they were when 64 bit was first released).

So somebody hacked up a wrapper to use Win32 codecs in a 64 bit video player?

That would be great but I don't think it's the case.

---

### Post by benjite on 2008-12-28
1.  Will the BIOS access 64GB of ram?  We are talking about putting a hardware system together and some systems are BIOS limited to 3GB of ram, so your comment may be out of place.  However since this is about hardware as well as software make sure to build a system that can support x64 code and access atleast 8GB or ram from the bios and you will be happy a long long time and such a system with a phenom can be done for about $400 is you shop around.  MOBO/CPU/4GB ram less than $200 if you got the rest of the hardware.

2. The way you replied is hardly in keeping with your signature, not that I mind because I think that people who do not know how to handle humiliation probably can't handle criticism either, but your correction about linux x86 being able to handle 64GB is hardly important given consumer MOBO's go up to 24MB at the high end and 8MB on the low end for MOBO's capable of handling an x64 CPU.  I don't know of and x86 only MOBO's that recognize more than 3GB at the consumer level.  Do you?

BTW.  Desmod Tutu is wrong about Ubuntu.  Ubuntu is about how my human perfection comes from how I care about your human perfection and this is served by humiliation.  Ubuntu technically doesn't refer to torture or oppresion as it is a possitive animus where my perfection depends on how I care about your perfection or more specifically about our perfection, seing as that is about all that is correct about ubuntu in Mr. Tutu's statement.  Knowing we are a part of a greater whole, but that means we have to put our care for that greater whole before our own vanities or the vanities of a diety such as Jesus the famous/evil one.

---

### Post by Cracauer on 2008-12-28
> **benjite said:**
> 1.  Will the BIOS access 64GB of ram?   
I haven't seen a BIOS screwing up PAE.

Many BIOSes screw up the remapping so that even with PAE or 64 bits you get only 7.5 out of 8 GB RAM due to the device space.

> **benjite said:**
>   We are talking about putting a hardware system together and some systems are BIOS limited to 3GB of ram,  

No, see above. Even if they screw up the remapping, you can still go above 4 GB.

 > **benjite said:**
> I don't know of and x86 only MOBO's that recognize more than 3GB at the consumer level.  Do you?


Who cares? If you really need to know, socket 478 system with pre-em64T Netburst CPUs are 4 GB unregistered DDR RAM capable system that do not do 64 bits. There were a ton out there, that was the standard platform during 2003-2004.

But this thread is about putting a 32 bit OS on a 64 bit system so that you don't have to play tricks in case you need *some* 32 bit packages.

---

### Post by bodhi.zazen on 2008-12-28
:lolflag:

If I were buying / building new hardware I would go 64 bit all the way.

There was a time, however, when 32 bit pae processors were substantially cheaper, and if you have the hardware, no reason not to use it.

Don't forget that this is old technology. Windows had the technology available with Windows 2000, and Linux with the 2.6 kernel.

So while you are talking about building new I am talking about supporting the older hardware.

Would I buy a 32 bit processor in this day and age, NO

Have I run some older 32 bit hardware with > 4 Gb RAM YES. This hardware still performs reasonably well for basic desktop use (web surfing, word processing, e-mail).

---

### Post by bodhi.zazen on 2008-12-28
> **Cracauer said:**
> So somebody hacked up a wrapper to use Win32 codecs in a 64 bit video player?

That would be great but I don't think it's the case.

I guess I just do not understand your point in this issue.

My 64 bit installs all work without having to do anything special. I install Ubuntu just the same as 32 bit, the installer asks the same questions. Post install I apt-get install the same applications (in general, although there are some minor differences), and I can listen to music, watch DVD movies, and use flash in Firefox without doing anything other then installing the appropriate applications / codics, same as 32 bit.

I did not have to do chroot this or chroot that or recompile any application from source.

In terms of RAM, my laptop has 4 Gb RAM and unless I am running virtualization I have not ever been limited by a lack of RAM.

I also have not noticed any performance degradation.

Perhaps I am just not understanding your point, but it seems as if your are making 64 bit Ubuntu to somehow be difficult. It seems to me you are either making some kind of personal customization that I have never needed or trying to make a square peg fit through a round hole. Obviously you are trying to tell me something, but I don't get it.

Suffice it to say, I do not understand you point and I find running 64 bit Ubuntu (or Fedora for that matter) is just as easy as 32 bit Ubuntu.

---

### Post by Cracauer on 2008-12-28
Do you know what the Win32 codecs as used in xine or mplayer are for?

I think the misunderstanding is right there. I don't "customize", I just want the video players to have their full capabilities.

---

### Post by bodhi.zazen on 2008-12-28
Thank you, 

Yes, what are the issues you are having with them, what limitations are you speaking of ?

So far they seem to be working just fine on my system.

---

### Post by Cracauer on 2008-12-28
I'm not sure whether you make fun us or not, but for the benefit of other readers: of course the binary codecs that we use in video players, called win32codecs, allow you to play video formats for which no OpenSource codec is available.

If you don't miss them, fine, but please don't assume that everybody else is be happy with a limited player.

My Linux and FreeBSD machine play random stuff off the Internet more often than my wife's Windows XP. That's what a really working computer is about.

I also doubt that a pluginwrapper to use 32 bit plugins in a 64 bit firefox is as robust and as able to run all kinds of junk plugins as a 32 bit firefox.

---

### Post by gn2 on 2008-12-28
> **Cracauer said:**
> I also doubt that a pluginwrapper to use 32 bit plugins in a 64 bit firefox is as robust and as able to run all kinds of junk plugins as a 32 bit firefox.

Unless you know for sure then why cast doubts?

I have both 32-bit and 64-bit versions of Ubuntu 8.04 and 8.10.
There is no noticeable difference between them that I can see. 
Codecs were a problem in 64-bit Ubuntu once upon a time, but definitely not any more.

---

### Post by atoponce on 2008-12-28
> **bodhi.zazen said:**
> Again I ask, how exactly do you install a 64 bit on on a 32 bit CPU ?

You don't. PAE doesn't give 64-bit functionality to the kernel. It only allows the kernel to address more RAM, and thus expand the user/kernel splits that must take place. If you don't see the 'lm' flag in /proc/cpuinfo, your kernel doesn't support 64-bit. Period.

---

### Post by bodhi.zazen on 2008-12-28
> **Cracauer said:**
> I'm not sure whether you make fun us or not, but for the benefit of other readers: of course the binary codecs that we use in video players, called win32codecs, allow you to play video formats for which no OpenSource codec is available.

If you don't miss them, fine, but please don't assume that everybody else is be happy with a limited player.

My Linux and FreeBSD machine play random stuff off the Internet more often than my wife's Windows XP. That's what a really working computer is about.

I also doubt that a pluginwrapper to use 32 bit plugins in a 64 bit firefox is as robust and as able to run all kinds of junk plugins as a 32 bit firefox.


Thank you for that as well. You are right, some people may not know what you mean by the win32codecs.

As indicated by gn2, they are working as well for me on 64 bit Ubuntu as they do on 32 bit. This is a shared laptop and my wife uses flash / javascript / and a number of the win32codics. I have problems playing some of them on Linux in fact.

I watch DVD movies with my children.

As I indicated, all of this is working on 64 bit Ubuntu and the installation is the same to the "end user". I install the same applications and codics on both 32 and 64 bit. Yes I understand that behind the scenes I am using ppluginwrapper (nspluginwrapper).

As I stated, I do not use xine, I use VLC. The only "problem" I had was with watchind DVD movies and sound, I needed to change to the OSS drivers.

I have not had any issues with 64 bit and it is all working, just as easy or hard as 32 bit. I did nothing other then use apt-get and run a script (for DVD, same script as on 32 bit). I have not made any type of chroot or any fancy customizations or modifications.

I can play a wider range of music / videos on Linux then Windows (some of the codics my wife uses are a pain to get running even on Windows).

Can you give us more specific details as to your  issues / problems ?

As indicated by gn2, these things used to be problematic with 64 bit, but no longer.

---

### Post by Cracauer on 2008-12-28
> **gn2 said:**
> Unless you know for sure then why cast doubts?


WTH?

Here it is right out of the horse's mouth:
[http://gwenole.beauchesne.info//en/projects/nspluginwrapper](http://gwenole.beauchesne.info//en/projects/nspluginwrapper)

> 
Compatibility

The following plugins work *reasonnably well*:
    *
      Acrobat Reader (5.0.9, 7.0.1, 8.1.2)
    *
      DejaVu Libre (3.5.14)
    *
      Flash Player (7.0, 9.0, 9.0 update 3, 10.0)
    *
      Linux JPEG 2000 (0.0.2)
    *
      Mplayerplug-in (2.80, 3.25)
    *
      Real Player (10.0.5)
    *
      ICA Citrix Client
    *
      Squeak VM (3.7)
    *
      Tcl/Tk (3.1.0)
    *
      3DMLW (1.0.3)

*emphasis* added by me.

> **gn2 said:**
> 
I have both 32-bit and 64-bit versions of Ubuntu 8.04 and 8.10.
There is no noticeable difference between them that I can see. 
Codecs were a problem in 64-bit Ubuntu once upon a time, but definitely not any more.

You got a better source for 64 bit codecs?

[http://www.mplayerhq.hu/MPlayer/releases/codecs/](http://www.mplayerhq.hu/MPlayer/releases/codecs/)


Edit bodhi.zazen: If you wish to see the details, please click [Cracauer]("http://ubuntuforums.org/member.php?u=392315")'s link.

---

### Post by bodhi.zazen on 2008-12-28
[Cracauer]("http://ubuntuforums.org/member.php?u=392315") : That is not a problem you are having, that is pasting information from other web sites.

I use many applications that are not on that list without  problems.

Your posting style is misleading at best. You are implying that things that are working are somehow broken without providing details.

---

### Post by Cracauer on 2008-12-28
So you think the right way to deal with this is to edit my post where I showed how fewer codecs are available for amd64, although the link you left does not allow you to see that information without downloading and unpacking a few of the many files in there?

I could go and look for videos that don't play with a 64 bit player due to this problem. But since you've gone to abusing your moderator's privileges to mess with my posts I think it's time to put this discussion out of it's misery now.

You see, we will both be able to prove our points: I'll be able to come up with a 32 bit Firefox plugin that is broken in nspluginwrapper if I waste enough time on it, and I'll be able to find a video that plays in a 32 bit player with win32codecs that doesn't play with the limited set of 64 bit codecs. You will be able to claim that both are so obscure and rare that it doesn't matter. I'll say it matter for those who encounter them. You'll say there are too few. So why bother?

I think you are just dead set to justify Debian's and Ubuntu's decision to not provide a far-reaching 32 bit compatibility environment, one of the few things that Fedora gets right.

---

### Post by gn2 on 2008-12-28
> **Cracauer said:**
> I think you are just dead set to justify Debian's and Ubuntu's decision to not provide a far-reaching 32 bit compatibility environment, one of the few things that Fedora gets right.


Seems to me that you have just "outed" yourself as a Fedora fanboy.

The stuff you have posted really has no place in the Ubuntu Forum "Absolute Beginner Talk" section, as it is entirely unhelpful.

A Linux beginner is highly unlikely to notice any difference in ease of use between 32 and 64 bit Ubuntu.

If you really want to contribute to the development of 64-bit Ubuntu then there are better methods of dong so than the posts you have made in this thread.

Maybe you could post your thoughts on the matter in the [64-bit Forum]("http://ubuntuforums.org/forumdisplay.php?f=343")?

---

### Post by howefield on 2008-12-28
> **gn2 said:**
> Seems to me that you have just "outed" yourself as a Fedora fanboy.

The stuff you have posted really has no place in the Ubuntu Forum "Absolute Beginner Talk" section, as it is entirely unhelpful.

A Linux beginner is highly unlikely to notice any difference in ease of use between 32 and 64 bit Ubuntu.

If you really want to contribute to the development of 64-bit Ubuntu then there are better methods of dong so than the posts you have made in this thread.

Maybe you could post your thoughts on the matter in the [64-bit Forum]("http://ubuntuforums.org/forumdisplay.php?f=343")?

+1 

100% on the money.  :lolflag::lolflag:

---

### Post by bodhi.zazen on 2008-12-28
> **Cracauer said:**
> So you think the right way to deal with this is to edit my post where I showed how fewer codecs are available for amd64, although the link you left does not allow you to see that information without downloading and unpacking a few of the many files in there?

No, you posted a long list of *.dll which did not add any content. I left yoru link which I think is more then sufficient.

> I could go and look for videos that don't play with a 64 bit player due to this problem. But since you've gone to abusing your moderator's privileges to mess with my posts I think it's time to put this discussion out of it's misery now.

You see, we will both be able to prove our points: I'll be able to come up with a 32 bit Firefox plugin that is broken in nspluginwrapper if I waste enough time on it, and I'll be able to find a video that plays in a 32 bit player with win32codecs that doesn't play with the limited set of 64 bit codecs. You will be able to claim that both are so obscure and rare that it doesn't matter. I'll say it matter for those who encounter them. You'll say there are too few. So why bother?


Why are you searching for things that are broken ? I am asking you what is not working for you.

> I think you are just dead set to justify Debian's and Ubuntu's decision to not provide a far-reaching 32 bit compatibility environment, one of the few things that Fedora gets right.

Fedora is a fine distro and there is no need to start distro bashing. You have not stated a single thing that is broken for you in Ubuntu or Debian and distro bashing is uncalled for. If you go searching on any distro you will find let us say bugs. The proper proceedure is to use the bug tracking / reporting system (rather then distro bashing).

Likewise, lets not start using words such as "fanboy" either.

The point is, if there is something that is not working for you we will support you. If you wish to go searching for bugs, and file bug reports, more power to you.

I agree, since you are not running ubuntu 64 bit, you have not stated a single specific problem you are having with 64 bit Ubuntu, and you are not listening to those of us are telling you these things are working it is not much of a conversation.

---

### Post by Cracauer on 2008-12-28
You people are not thinking straight :)

I said "the one thing Fedora gets right". I distaste Fedora with a good amount of passion and recommend against installing it every opportunity I get.

I am actually a FreeBSD fanboy, if you have to know.

[edited out a bunch of stuff]

---

### Post by Cracauer on 2008-12-28
> **bodhi.zazen said:**
> No, you posted a long list of *.dll which did not add any content. I left yoru link which I think is more then sufficient.



Did you even visit that link before you edited my post? 

To get to the lists of DLLs in the amd64 and the i386 codec packages you have to download them all and unpack them.

That can hardly count as sufficient.


 > **bodhi.zazen said:**
> 


Why are you searching for things that are broken ? I am asking you what is not working for you.


I use the 32 bit versions, so things *are* working for me.

You just don't have the codecs for all these microsoft specific video formats (and a bunch of others) available in AMD64.

> **bodhi.zazen said:**
> 


Fedora is a fine distro and there is no need to start distro bashing. You have not stated a single thing that is broken for you in Ubuntu or Debian and distro bashing is uncalled for. If you go searching on any distro you will find let us say bugs. The proper proceedure is to use the bug tracking / reporting system (rather then distro bashing).

Likewise, lets not start using words such as "fanboy" either.

The point is, if there is something that is not working for you we will support you. If you wish to go searching for bugs, and file bug reports, more power to you.


All I said is that they provide a 32 bit compatibility environment that directly supports Firefox and Xine/mplayer.  Debian and Ubuntu do not.  The 32 bit compatibility environment provided by Debian and Ubuntu is just a bunch of very basic libraries with no GUI support. 

To run a 32 bit Firefox binary in Fedora you download it and run it.

To do that in Debian or Ubuntu you need either a chroot (which is pretty advanced if you want to transparently drop into it with correct userids). Or you have to install a chroot and instead of chrooting into it carefully redirect a whole bunch of GTK/GNOME stuff to proper locations, only to be forced to use LD_PRELOAD hacks for specific things where the GNOMies forgot to obey to envrionment variables.

And yes, that's the *only* thing that Fedora does better. What do you think why I'm using Debian and Ubuntu for Linux?


 > **bodhi.zazen said:**
> 
I agree, since you are not running ubuntu 64 bit, you have not stated a single specific problem you are having with 64 bit Ubuntu, and you are not listening to those of us are telling you these things are working it is not much of a conversation.

Of course I run 64 bit installs.

I just run 32 bit binaries in a variety of solutions from chroots to compile-time reloated trees.  And I have said so several times in this thread.  For a moderator you don't seem to pay much attention.

P.S., if you edit another post of mine to remove evidence that isn't readily available I'll raise an official complaint. You are abusing moderator's powers here.

---

### Post by bodhi.zazen on 2008-12-28
Cracauer: I have been nothing but polite to you and there is no need for your behavior.

If you feel you need to list all those *.dll please use an attached file.

You have not stated a specific issue you need assistance with as such your long list of *.dll added very little to the conversation and I do not think people wish to scroll through such a long list.

---

### Post by Cracauer on 2008-12-28
> **bodhi.zazen said:**
> Cracauer: I have been nothing but polite to you and there is no need for your behavior.

If you feel you need to list all those *.dll please use an attached file.

You have not stated a specific issue you need assistance with as such your long list of *.dll added very little to the conversation and I do not think people wish to scroll through such a long list.

What I have posted is the list of video codecs supported in the win32dll packages (that require a 32 bit video player, which you may or may not be able to run in a 64 bit Ubuntu) and the list of video codecs support in AMD64, which isn't even 1/10th.

That is, *directly* a list of things not working if you run plain 64 bits, and you deleted it from somebody else's post.

You see, the reason why the list was so annoyingly long was that there are so many 32 bit codecs supported ;)

Anyway...

I know that your next step will be locking up this thread after making some kind of final statement that I can't reply to, so why don't we just get it over with?

Fact is that there are some obscure things that require 32 bit programs. Which in turn exposes one of the rare weaknesses in Ubuntu, the lack of a comprehensive 32 bit compatibility environment to smoothly run these. These are facts.

Whether these obscure things are required for new users or not is up to debate. But I can tell you that if a user comes across some form of *.wmv video he can tell whether it's working or not very easily.  The difference between a running video and an blank screen with an error message is pretty obvious even for the worst n00bs.

Fact is also that the authors of nsdiswrapper are very careful in their claims about what kind of 32 bit plugin runs in a 64 bit browser and make no statements for general use. Much more careful than you.

---

### Post by gn2 on 2008-12-28
> **Cracauer said:**
> I distaste Fedora with a good amount of passion and recommend against installing it every opportunity I get.

I am actually a FreeBSD fanboy, if you have to know.

In which case I apologise unreservedly for my erroneous comment.

---

### Post by overdrank on 2008-12-28
Moved to  Recurring Discussions

---

### Post by jamesisin on 2008-12-28
This has gotten all so very entertaining.

Two questions:

bodhi.zazen - If I choose option 2.1 from the page you linked (add the server kernel), I will be able to select from either kernel at boot?  That sounds like I would then be able to make a pretty basic sort of (almost) side-by-side comparison, yes?

Cracauer - Have you come across a file that would not play in 64bit Ubuntu?  If so, can you link to that video (or whatever) here?

---

### Post by bodhi.zazen on 2008-12-28
> **jamesisin said:**
> This has gotten all so very entertaining.

:lolflag:

> Two questions:

bodhi.zazen - If I choose option 2.1 from the page you linked (add the server kernel), I will be able to select from either kernel at boot?  That sounds like I would then be able to make a pretty basic sort of (almost) side-by-side comparison, yes?

Yes, as you boot, at the grub screen, you will get a text menu where you can select the kernel to boot. If you have a "hidden menu" you will need to press escape I believe to see the menu (read the screen, sorry if I am off on that).

---

### Post by jamesisin on 2008-12-28
Thanks.  I'll try that route.

---

### Post by Kilz on 2008-12-28
> **Cracauer said:**
> 

All I said is that they provide a 32 bit compatibility environment that directly supports Firefox and Xine/mplayer.  Debian and Ubuntu do not.  The 32 bit compatibility environment provided by Debian and Ubuntu is just a bunch of very basic libraries with no GUI support. 

To run a 32 bit Firefox binary in Fedora you download it and run it.

To do that in Debian or Ubuntu you need either a chroot (which is pretty advanced if you want to transparently drop into it with correct userids). Or you have to install a chroot and instead of chrooting into it carefully redirect a whole bunch of GTK/GNOME stuff to proper locations, only to be forced to use LD_PRELOAD hacks for specific things where the GNOMies forgot to obey to envrionment variables.

And yes, that's the *only* thing that Fedora does better. What do you think why I'm using Debian and Ubuntu for Linux?


As a long time 64bit user, and one who has tried to address these things for other users I feel I must point out a few problems with your statements and what is in fact reality.


1. You do not in any way shape or form need a chroot to run 32bit applications in 64bit Ubuntuas long as the supporting libraries are present in the /lib32 or /usr/lib32 directory.

Perhaps your knowledge pre dates Dapper Drake (6.06). Breezy Badger (5.10) did indeed have this issue, but time and technology marches on.

2. While it is true that there is no gui. Getlibs solves the one and only problem of getting and installing libraries 32bit libraries. 

This is linux, a gui is nice, but it isnt necessary.

Lastly let me point out the futility of running a 32bit Firefox. 64bit plugins are here. :D

---

### Post by Half-Left on 2008-12-28
Using PAE on a 32bit system does give rather a big overhead, this is why they do the memory split in the kernel now. If you have 4Gb+ ram then 64bit is the way and ofcourse it's worth it.

---

### Post by Cracauer on 2008-12-28
> **jamesisin said:**
> 
Cracauer - Have you come across a file that would not play in 64bit Ubuntu?  If so, can you link to that video (or whatever) here?

Well, I don't want to waste too much time on this as certain people will - for whatever video I find - say that it's not interesting, you don't need it, Linux n00bs won't understand it etc.

Second, it's not that easy since there is a mess of container data formats, video and audio codecs and it is fairly non-obvious which codec is actually needed for what file.

Anyway, this might do:
[http://www.microsoft.com/windows/windowsmedia/musicandvideo/hdvideo/contentshowcase.aspx](http://www.microsoft.com/windows/windowsmedia/musicandvideo/hdvideo/contentshowcase.aspx)
[http://download.microsoft.com/download/2/0/9/20907788-993F-4EF6-8D75-F0DD93207FB8/AdrenalineRush_720.exe](http://download.microsoft.com/download/2/0/9/20907788-993F-4EF6-8D75-F0DD93207FB8/AdrenalineRush_720.exe)

You can unpack it with unzip.

The resulting .wmv file requires, on my system, win32 DLLs to play. I have a 64 bit Debian with a /usr/local32 tree with 32 bit stuff, including a xine/mplayer chain. /usr/lib/codecs/wmv9dmod.dll is chosen as the codec, which pulls in some stuff from OLEAUT32.

That *probably* means you can't play it on AMD64, but as I said earlier it might for a variety of reasons work for particular videos.

Let me know how that goes, as long as it doesn't result in too much wasted time we can debug.

Please start the video player in verbose mode (xine --verbose) so that it tells you which codec was used.

---

### Post by Cracauer on 2008-12-28
> **Kilz said:**
> As a long time 64bit user, and one who has tried to address these things for other users I feel I must point out a few problems with your statements and what is in fact reality.


I am using Linux/amd64 and FreeBSD/amd64 from the moment they were available.  In fact I'm tying from one.  In a 32 bit Firefox.

> **Kilz said:**
> 

1. You do not in any way shape or form need a chroot to run 32bit applications in 64bit Ubuntuas long as the supporting libraries are present in the /lib32 or /usr/lib32 directory.

Perhaps your knowledge pre dates Dapper Drake (6.06). Breezy Badger (5.10) did indeed have this issue, but time and technology marches on.

2. While it is true that there is no gui. Getlibs solves the one and only problem of getting and installing libraries 32bit libraries. 


Errr, I specifically referenced firefox.

So you say that in newer Ubuntus you have all the 32 bit libs around to run a 32 bit Firefox binary, including gtk, pango and all that junk and that somebody found a solution to make pango look up *.so files in the right path without having to use LD_PRELOAD with libpangohack.so.0.0?

I don't think this statement is accurate.

BTW, the advantages of running an insecure piece like Firefox with it's plugins in a chroot, apart from compatibility, should be pretty obvious.

 > **Kilz said:**
> 
This is linux, a gui is nice, but it isnt necessary.


We were specifically discussing Firefox and plugins and xine/mplayer and codecs, both of which require X11.

> **Kilz said:**
> 
Lastly let me point out the futility of running a 32bit Firefox. 64bit plugins are here. :D

Sure, all plugins, and all working nsdiswrapper, when the author of nsdiswrapper is much more sceptical than the zeolots here.

Also, show me where to download Firefox-3.1b2 as amd64 binary.

Here are the available binaries:
[http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.1b2/](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.1b2/)

---

### Post by tuxxy on 2008-12-28
> **Cracauer said:**
> 
I also doubt that a pluginwrapper to use 32 bit plugins in a 64 bit firefox is as robust and as able to run all kinds of junk plugins as a 32 bit firefox.

Your point is flawed and if you had used 64-bit OS at all or researched them a little better maybe you would know about the 64-bit flash plugin

---

### Post by Cracauer on 2008-12-28
> **tuxxy said:**
> Your point is flawed and if you had used 64-bit OS at all or researched them a little better maybe you would know about the 64-bit flash plugin

Sure.

Link to flash9 64 bit binary?

Hint: it's a big deal that Flash finally came out as a 64 bit binary - Flash10. Don't you read flashdot errr slashdot :)

You people start to disgust me. You don't even do the minimal research of trying to look up something as easy as this and you have no problem just posting away without even keeping up-to-date with what's available.

---

### Post by jamesisin on 2008-12-28
Well, the file does play (in Totem)...

But when I launch the file I get a codec error.  I accept its offer to search for a suitable codec and this fails.

Not sure what the missing codec might add (as I said the file does play).

Is this consistant with your 32bit behaviour?  Is there supposed to be sound because I was getting no audio?

---

### Post by Cracauer on 2008-12-28
> **jamesisin said:**
> Well, the file does play (in Totem)...

But when I launch the file I get a codec error.  I accept its offer to search for a suitable codec and this fails.

Not sure what the missing codec might add (as I said the file does play).

Is this consistant with your 32bit behaviour?  Is there supposed to be sound because I was getting no audio?

Well, I get both audio and video without any error messages. Xine and mplayer. 64 bit OS, 32 bit players.

You say a 64 bit totem is actually playing video? Can you run verbose and tell me what decoder is handling the video?

---

### Post by jamesisin on 2008-12-28
No.  I am running this in 32bit.  That's why I asked if this was consistant with your 32bit behaviour.

---

### Post by gn2 on 2008-12-28
> **Cracauer said:**
> Also, show me where to download Firefox-3.1b2 as amd64 binary.

Will the current most recent stable version of FF3 do?
(b2 = second Beta release, therefore not ideal for everyone)

[http://packages.ubuntu.com/intrepid/amd64/firefox-3.0/download](http://packages.ubuntu.com/intrepid/amd64/firefox-3.0/download)

But if you install 64-bit Ubuntu 8.10, you won't need to use the link.

---

### Post by Cracauer on 2008-12-28
> **jamesisin said:**
> No.  I am running this in 32bit.  That's why I asked if this was consistant with your 32bit behaviour.

Oh, sorry.

I get both video and sound but on the first video on the page the sound is stuttery. I might want to try a different sound codec if I remember how to tell xine which one I want.

Now I would really like one of the 64 bit defenders try it. (it might work, who knows whether somebody made a plugin for a 64 bit Win64 dll and/or ffmpeg people hacked it up, but I can feed more crancky video formats until they run out of patience)

---

### Post by MikeTheC on 2008-12-29
> **bodhi.zazen said:**
> 32 bit OS can access up to 64 Gb RAM. It is called [PAE](http://en.wikipedia.org/wiki/Physical_Address_Extension)

When you say otherwise you :

1. Help propagate mis information.

2. sound uneducated.

So please do not do this.

When you also stop to consider that, right now, 3-4GB of RAM is the *stock* configuration on the majority of new systems, 64 bit is rapidly becoming a mandatory requirement.

---

### Post by deanjm1963 on 2008-12-29
Yes, I think 64bit is worth it.

I recently upgraded my own machine to a 64bit system, AthlonX2 6000 - 4gb ram, nVidia 9600GT 1GB ram.

I also purchased 2 other boxes that contained AthlonX2 5600 - 4gb ram and inbuilt nVidia graphics for my father and a friend.

All the machines now run either Hardy 64bit or Intrepid 64bit.

To be honest, they run without a flaw, graphic drivers work as they should and in general they seem a little "snappier".

I can play any DVD/movie file/sound file that I could do in the 32bit versions. I did purchase the 64bit codecs from Fluendo (not from the Canonical Store, the Fluendo versions are newer versions and you get more file formats, e.g. deb, rpm, tar.gz in both 64/32 bit). A small price to pay considering the money I used to fork out for Windows software.

The latest alpha of Flash 64bit from Adobe runs just as good as the 32bit final release, I've had no crashes, Firefox behaves great with it. I can't complain, even though there is no 64bit Java Plug-In (not available in the repos just yet, but it is out there), the OpenJava works just as well.

I'd recommend using the 64bit version over the 32bit version if you can do so.

My 2 cents worth!

---

### Post by Greyed on 2008-12-29
> **MikeTheC said:**
> When you also stop to consider that, right now, 3-4GB of RAM is the *stock* configuration on the majority of new systems, 64 bit is rapidly becoming a mandatory requirement.

Your definition of rapidly certainly does not jive with mine.  PAE can address up to 64Gb.  New systems are coming stock with 1-2Gb (3-4Gb for high end, granted, but hardly the majority).  So even taking your 4Gb upper end we're still only using 6.25% of the available address space and it has taken years to go from 1Gb for high end machines to 4Gb your rapidly is at least on the order of 10 years before the mandatory portion of your statement kicks in.  10 years ain't "rapid" in terms of computers.  Using my latest gaming rig as a bench mark that is **2** motherboard/CPU changes from now.  :P

---

### Post by Kilz on 2008-12-29
> **Cracauer said:**
> I am using Linux/amd64 and FreeBSD/amd64 from the moment they were available.  In fact I'm tying from one.  In a 32 bit Firefox.

Errr, I specifically referenced firefox.
No problem, I have extensive knowledge of installing 32bit firefox on 64bit ubuntu. [Some could even say I wrote the book on the subject.]("http://ubuntuforums.org/showthread.php?p=1174435") I also have a lot of experience with 64bit. I am one of its leading supporters. 99% of my posts were made in or about the 64bit section and version.
> **Cracauer said:**
> 
So you say that in newer Ubuntus you have all the 32 bit libs around to run a 32 bit Firefox binary, including gtk, pango and all that junk and that somebody found a solution to make pango look up *.so files in the right path without having to use LD_PRELOAD with libpangohack.so.0.0?

I don't think this statement is accurate.

Yes all you need are the supporting libraries. But no, you dont have to preload anything. That will lead to a series of useless errors showing if the user starts firefox in a terminal (See below)
```
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
```. Its much better to point out the path to firefox anyway.
```
export LD_LIBRARY_PATH=/usr/lib32/libpangohack.so.0
``` I believe this is because the version you are using was not compiled on Ubuntu, but Red Hat.

> **Cracauer said:**
> 
BTW, the advantages of running an insecure piece like Firefox with it's plugins in a chroot, apart from compatibility, should be pretty obvious.
How about this idea.**[COLOR="Red"] Dont run 32bit Firefox. You dont need to.[/COLOR]**
 
> **Cracauer said:**
> 
We were specifically discussing Firefox and plugins and xine/mplayer and codecs, both of which require X11. the 64bit mplayer and plugins are in the 64bit repositories. There is also a xine. Most people I know use vlc.

> **Cracauer said:**
> Sure, all plugins, and all working nsdiswrapper, when the author of nsdiswrapper is much more sceptical than the zeolots here.
Nsdiswrapper?.... Are you having a problem with your wireless card?
I dont even use nspluginwrapper and I have no issues. I am running Adobe flash, Sun Java, Vlc plugin, and firefox. All are 64bit.

> **Cracauer said:**
> 
Also, show me where to download Firefox-3.1b2 as amd64 binary.

Here are the available binaries:
[http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.1b2/](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.1b2/)
The truth is, not many development versions are made for 64bit. This isnt Ubuntu's problem. Feel free to post a bug report on bugzilla pointing out the lack of a 64bit development version to Mozilla. [I have a feeling they will send you here.]("https://developer.mozilla.org/en/Build_and_Install")

---

### Post by zika on 2008-12-29
>  Originally Posted by [B]Cracauer
[/B]Also, show me where to download Firefox-3.1b2 as amd64 binary.You do not want 3.1b2, You want nightly: [http://http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-3.2a1pre.en-US.linux-x86_64.tar.bz2]("http://http//ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-3.2a1pre.en-US.linux-x86_64.tar.bz2") because it is even more stable and polished.

---

### Post by Cracauer on 2008-12-29
All right. So can you play the video I linked to in a 64 bit player (bought codecs or not)? I'm curious, honestly.

Sorry for mixing up nsdiswrapper and nspluginwrapper. I don't use any of that stuff.

---

### Post by Delever on 2008-12-29
> **Cracauer said:**
> All right. So can you play the video I linked to in a 64 bit player (bought codecs or not)? I'm curious, honestly.

Video loads on both MPlayer and GStreamer, but no audio. It's 64bit system here. It seems it can play as much as 32bit system. But we are getting off-topic.

64 bit, is it worth it? - It depends on user. I usually don't need to extract exe files as archives to play video on my system (wtf?), and I would never encode my videos in proprietary format to cause end user any problems with playback. I understand that many users will do that, only to find that in reality they need to care about encoding.

I understand the need to adapt, and in some cases adapting to support anything is necessary. However I like to think about my 64bit choice as gentle push to get those 32bit legacy roots out of 64 bit system. There is no doubt that 64bit system is worth it, just because it is the system which will be/is used in the future/now.

---

### Post by MikeTheC on 2008-12-29
> **Greyed said:**
> Your definition of rapidly certainly does not jive with mine.  PAE can address up to 64Gb.  New systems are coming stock with 1-2Gb (3-4Gb for high end, granted, but hardly the majority).  So even taking your 4Gb upper end we're still only using 6.25% of the available address space and it has taken years to go from 1Gb for high end machines to 4Gb your rapidly is at least on the order of 10 years before the mandatory portion of your statement kicks in.  10 years ain't "rapid" in terms of computers.  Using my latest gaming rig as a bench mark that is **2** motherboard/CPU changes from now.  :P

A quick trip to even your local BestBuy will prove my point. Most of those systems are above the 2GB mark, coming in at typically either 3 or 4GB stock. Apple is an exception, since -- to the best of my knowledge --  they don't sell any stock configurations with more than 2GB of RAM. And clearly, the NetBooks are all below 2GB. Still, that's the exception, not the rule.

Heck, CompUSA is selling most of their brand- and off-brand named tower systems with 3-4GB of RAM. Go build a system and all the motherboards out there support at least 4GB of RAM, with many supporting more than that.

With all due respect, you're completely leaving out competition as a factor. The moment one company starts selling "stock" configs with 3-4GB of RAM, everyone else jumps on the bandwagon. Now true, we probably won't see 8GB stock next year, but we are moving up in the world in terms of RAM that's standard. Moreover, it's not a matter of the rate of speed, so much as it's the fact we've crossed the threshold.

---

### Post by uberdonkey5 on 2008-12-29
sorry, I don't have much technical knowledge, but I do know that for some tough mathematical problems computing power is increasing faster than the current computers could calculate it i.e. if you have a tough mathematical problem, if you wait a year to buy a top of the range computer you will solve it faster than buying a top of the range computer now and running it for a year.

I think really, its a turning point for 64bit, and I too will get one. However, strategically its probably best to remember this... whatever you buy now will be out of date and much cheaper in 5 years time.

Its good (and altruistic) to increase the market shareof 64bit, but the best strategy is:
- to not buy a new computer unless you really need to (can't you do what you want to do now with your current computer???), and if you do, buy the best computer you can afford to buy now (within reason).

I bought duo core when 1st came out, with 2GB RAM (most I could get) and now gonna upgrade to 4GB (maxed out for my dell laptop).However, one day, when it falls to pieces, I'll get a 64bit.

---

### Post by jerome1232 on 2008-12-29
I don't know about that, I built my current setup, oh 5 or 6 years ago, it still works fine for everyday use. It wasn't expensive at all, cost me $800 to build it. Yes Athlon 64's were AMD's first x86_64 cpu's.

Athlon64 3700+ (2.4 Ghz), 1 GB DDR Ram@166 hz, 250 GB Sata II HDD, 5600LE Nvidia.

---

### Post by jamesisin on 2008-12-29
> **Cracauer said:**
> Now I would really like one of the 64 bit defenders try it.

I'm sorry. I don't mean to be difficult, but if it doesn't work in 32bit it doesn't seem a very strong candidate against 64bit.

I have become an advocate of Linux for Anybody:

[Linux for Anybody]("http://www.soundunreason.com/InkWell/?page_id=313")

Playing these particular files looks to be beyond what I would likely have my mother do.

---

### Post by Kilz on 2008-12-29
> **Cracauer said:**
> All right. So can you play the video I linked to in a 64 bit player (bought codecs or not)? I'm curious, honestly.

Sorry for mixing up nsdiswrapper and nspluginwrapper. I don't use any of that stuff.

I see video in a pretty much repository pure Interpid setup as far as codecs and media players are concerned . But lets take a look at one more thing. The site you link to is Microsoft. Microsoft is going to make 100% sure something isnt going to work in Linux. Next someone will point out a Lexmark problem (they are notorious for poor linux support)

---

### Post by coolen on 2008-12-29
I just switched from 32 to 64-bit on my desktop and laptop.

I really don't notice much difference. Drivers all worked exactly as before, flash and java were no problem. I've encountered only two problems: I can't undervolt my laptop (this is the first time I tried, so it may just be the CPU. The project is still young) and Gloobus wouldn't work (could not find the required libraries).

Other than that, pretty much everything works fine. I see no real reason not to, and you'll be adding to the need for really good 64-bit applications.

You'll (probably) suffer nothing for it, and could well benefit.

---

### Post by Cracauer on 2008-12-29
> **Kilz said:**
> I see video in a pretty much repository pure Interpid setup as far as codecs and media players are concerned . But lets take a look at one more thing. The site you link to is Microsoft. Microsoft is going to make 100% sure something isnt going to work in Linux. Next someone will point out a Lexmark problem (they are notorious for poor linux support)

Didn't I predict that no matter what video I link to somebody would come up and say it's an irrelevant video? :) You are missing the point, dude.

It's a video codec, wmv9, and it is used outside Microsoft. Many more obscure video and audio formats require obscure codecs.

The whole point here is that a 32 bit player (which can run on a 64 bit OS) has a whole bunch more codecs than you have with a 64 bit player. I make no claims as to whether any videos out there that use one of these codecs are important to you. Myself, I'll run whatever video player gives me the most codecs, and that is a 32 bit xine/mplayer, running in my 64 bit OS, but doing that requires some fiddling that a n00b wouldn't be able to do.

I don't plan to waste any more time on this, though. Pages ago I have posted the list of available binary codecs for 32 and 64 bits and a moderator nuked the list from my post. You can reproduce it if you like.

I never claimed a Linux n00b wouldn't be able to live with limited codecs, or with nspluginwrapper for that matter.

All I say is that I'm proud that *my* Linux and FreeBSD machines play more, many more, videos (with audio, thank you) than my wife's Windoze XP install. That's damn cool, and it's part of why I use Linux and FreeBSD in the first place - they get the job done.  

I should have known better than getting into a fight not only with Ubuntu zealots who label me a Fedora fanboi for mentioning that Fedora has a real Linux/i386 compat environment (as does FreeBSD) but also seem to be violent 64 bit advocates who think that everything that isn't available in amd64 cannot be of any use to anybody (talk about selective perception). I am zeolot enough not to run Windoze, and I run 64 bit Unixes, but starting a crusade against every last bit of 32 bit code running in your 64 bit OS is insane even by my standards.

Overall, I don't think that most people who bashed me in this discussion even know how the win32codecs for xine/mplayer even work. Actual facts would get in their way of thinking.

I'll now go back to be a Lisp zealot and bash Python fanbois over in the programming section. You can go and mislead new Ubuntu users all you like.

---

### Post by jamesisin on 2008-12-29
Well, I hope you are not lumping me into those you have disparaged here.  I really am interested in your side.

For myself, I would advise anyone asking me about purchasing new hardware to opt for 64 bit hardware.  Would I advise them to install the 64 bit Ubuntu?  That remains to be seen.  Probably yes though because if there does turn out to be something that is unavailable in 64 bit they can always run a 32 bit virtual machine for that purpose.

Now, the file you asked me to test may or may not be obscure.  I do think obscurity does have an impact, but for the moment I just want to talk about that file and how it relates to what I'm looking at.  I was not able to play the audio on those MS files.  (Nor was a 64 bit user.)  I have the basic stuff installed here (the bundle of non-free stuff including flash), though I have not paid for any additional codecs.

This is about as deep as a new user, and these are the folks I am advocating to under my Linux for Anybody, is likely to get.  If they won't play in 32 bit it won't matter to any of those users if they won't play in 64 bit--nothing to miss.

If you have another file you'd like me to test on my 32 bit system (and which some 64 bit cat will also then test), I am happy to do so.

Ok, that being said, I still feel as though I should take a moment to make a philosophical statement about obscurity.

Suppose:

There is, right now, some file--a very obscure file--which will only play on one specific computer.  There is also, right now, some file which will play on any computing device which can be powered on.  These are the two ends of the obscurity spectrum.

No one would claim that any system should be made to run all files of the first class.  Clearly that would be impractical.  So we draw a line somewhere between these two extremes.  Where that line is drawn can be mapped out according to the law of diminishing returns.

My point?  Merely being obscure does not guarantee it ought to be ingnored, sure, but just as surely it does not guarantee it ought to be developed.

---

### Post by Cracauer on 2008-12-29
> **jamesisin said:**
> Well, I hope you are not lumping me into those you have disparaged here.  I really am interested in your side.


No, no.

> **jamesisin said:**
> 
For myself, I would advise anyone asking me about purchasing new hardware to opt for 64 bit hardware.  

Of course. The only 32 bit hardware left, if any, is those with crippled caches.

> **jamesisin said:**
>   Would I advise them to install the 64 bit Ubuntu?  That remains to be seen.  Probably yes though because if there does turn out to be something that is unavailable in 64 bit they can always run a 32 bit virtual machine for that purpose.


A Linux n00b running a virtual machine?

I find it difficult enough to run a chroot for X11 programs. Just managing the $DISPLAY variable and passing all the arguments all the way through the userid change to root, the chroot and then the userid change back to the original user is something that I consider advanced.

I'm skipping your section on particular files. If people are really interested somebody else can go hunt stupid codec files.  I think we all know that
1) there are some files
2) some people will say they are irrelevant, some will say they matter

> 
My point?  Merely being obscure does not guarantee it ought to be ingnored, sure, but just as surely it does not guarantee it ought to be developed.

The whole discussion developed from the question whether a 64 bit OS has *any* disadvantages.  Yes there are some, and in Ubuntu and Debian they are bigger than in Fedora and FreeBSD.

I never made statements that complete n00bs would care.

---

### Post by Delever on 2008-12-29
> **Cracauer said:**
> Didn't I predict that somebody would come up and say it's an irrelevant video? :) I make no claims as to whether any videos out there are important to you. Myself, I'll run whatever video player gives me the most codecs, but doing that requires some fiddling that a n00b wouldn't be able to do. I don't plan to waste any more time on this. I never claimed a Linux n00b wouldn't be able to live with limited codecs, or with nspluginwrapper for that matter. I should have known better than getting into a fight not only with Ubuntu zealots who label me a Fedora fanboi but also seem to be violent 64 bit advocates who think that everything that isn't available in amd64 cannot be of any use to anybody. I run 64 bit Unixes, but starting a crusade against every last bit of 32 bit code running in your 64 bit OS is insane even by my standards. I don't think that most people who bashed me in this discussion even know how the win32codecs for xine/mplayer even work. Actual facts would get in their way of thinking. You can go and mislead new Ubuntu users all you like.

Right. Sorry for starting the fight.

---

### Post by jamesisin on 2008-12-29
Yeah, I think VirtualBox makes it easy enough that even someone new to Linux could manage it.  Probably not my mom, but let's keep this in perspective.  (The one current problem with VB involves downloading it from Sun instead of using the one in the repos--or adding Sun to your repos list.)

I guess my final assessment will be something like: if there are any disadvantages to 64 bit they are relatively minor and most users are unlikely to experience any difference.

---

### Post by gn2 on 2008-12-30
> **Cracauer said:**
> I should have known better than getting into a fight not only with Ubuntu zealots who label me a Fedora fanboi for mentioning that Fedora has a real Linux/i386 compat environment (as does FreeBSD) but also seem to be violent 64 bit advocates who think that everything that isn't available in amd64 cannot be of any use to anybody (talk about selective perception). I am zeolot enough not to run Windoze, and I run 64 bit Unixes, but starting a crusade against every last bit of 32 bit code running in your 64 bit OS is insane even by my standards.

You are starting to be absurd.
No-one is starting any crusade.
You have either forgotten or overlooked that you have received an apology for the fanboy comment which I made.

Read the original question and consider who is asking it.
Then look at your own experience of running **Ubuntu** 64-bit and 32-bit.

I have been doing so for over one year and have yet to find anything in my regular travels through PC and interwebland that will not play in 64-bit that will play in 32.

The answer to the OP's question is "definitely yes".

---

### Post by Cracauer on 2008-12-30
> **jamesisin said:**
> 
I guess my final assessment will be something like: if there are any disadvantages to 64 bit they are relatively minor and most users are unlikely to experience any difference.

I never claimed anything else. Also note that although I want some 32 bit apps I run them in the 64 bit OS.

The extended discussion only started over the question whether 64 bit can *everything* 32 bit can, for an inexperienced user. That claim isn't true, and the 64/32 bit mix I run is not trivial enough.

On the other hand, there is no advantage of 64 bits that a new user would notice either :)

---

### Post by gn2 on 2008-12-30
> **Cracauer said:**
> On the other hand, there is no advantage of 64 bits that a new user would notice either :)

E.G. they might not notice that video encoding is much quicker....?

---

### Post by Cracauer on 2008-12-30
> **gn2 said:**
> E.G. they might not notice that video encoding is much quicker....?

You got a link to more concrete benchmarks of this?

Sure, media encoding will be faster, but how much? In most cases speed differences between 32 and 64 bit builds are less caused by more registers or higher sse versions, but by the fact that the i386 build is compiled with less aggressive compiler options, usually to keep things compiled in a way that it even runs on a Pentium-1. I have also seen cases where the i386 build is completely generic, while the amd64 build has specific CPU types set.

I think it would be interesting to give this a spin if there are specific enough benchmarks out there.

---

### Post by gn2 on 2008-12-30
> **Cracauer said:**
> You got a link to more concrete benchmarks of this?

Sure, media encoding will be faster, but how much? 

See Page 4 of the tinyurl link in post 14 of this thread.

In my own experience, encoding tasks are anything from 30 to 50% faster in 64 bit, which is a huge performance increase for no outlay.

---

### Post by Cracauer on 2008-12-31
> **gn2 said:**
> See Page 4 of the tinyurl link in post 14 of this thread.

In my own experience, encoding tasks are anything from 30 to 50% faster in 64 bit, which is a huge performance increase for no outlay.

Thanks.

The ogg audio encoding looks like something that would be quick enough to reproduce.

---

### Post by Frak on 2008-12-31
> **Cracauer said:**
> All right. So can you play the video I linked to in a 64 bit player (bought codecs or not)? I'm curious, honestly.

Sorry for mixing up nsdiswrapper and nspluginwrapper. I don't use any of that stuff.
Sounds like somebody didn't install their w64codecs from the medibuntu repositories :rolleyes:

---

### Post by Half-Left on 2008-12-31
I'm been running pure 64bit for a while now, because I compile my own kernel I've turned off 32bit binary support, just dont need it

---

### Post by rasmus91 on 2009-02-17
Hi

I don't remember if i posted anything in this thread before... (think i did)

Yeah, I'd say 64 bit is better... 

I've just switched to 32 bit, so i found out that 64 bit is way faster on this computer.

(i wouldn't recommend anyone buying AMD how ever, but thats a little of topic.) 

But if your system exceed the limits of 32 bit, Yeah switch to 64 bit, then it'll be way faster

---

