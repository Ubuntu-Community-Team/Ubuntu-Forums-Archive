---
title: "Next Linux kernel - 2.6.40 or 3.0.0?"
date: 2011-05-25
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-05-25
There is a discussion going on regarding versioning the next kernel release cycle.
We have now 2.6.39.
Next will be 2.6.40 or depending on new versioning 3.0.0.

Linus Torvalds has started this discussion on the kernel developer mailing list.

---

### Post by teh603 on 2011-05-25
> **Harry33 said:**
> There is a discussion going on regarding versioning the next kernel release cycle.
We have now 2.6.39.
Next will be 2.6.40 or depending on new versioning 3.0.0.

Linus Torvalds has started this discussion on the kernel developer mailing list.For those of us not on the kernel developer list, what are the major differences between 3.00 and 2.640?

---

### Post by silex89 on 2011-05-25
Is there a major change in the kernel if the new version is 3.0.0:confused:

---

### Post by Starks on 2011-05-26
No major changes. Just a new versioning scheme.

---

### Post by Harry33 on 2011-05-26
> **teh603 said:**
> For those of us not on the kernel developer list, what are the major differences between 3.00 and 2.640?

Actually there is no differencies at all between those. They are the same.
This is a kind of discussion Linus Torvalds started would it be time to name the newest kernel 3.0.0 or just continue the 2 series naming.

Generally upgrading the versioning from 2 series to 3 series would require at least one major change. Now it is planned that this kernel would be thoroughly cleaned up from a lot of old cruft, but is that enough, let's see.

---

### Post by dext on 2011-05-26
as i understand it, there wont be another 0 in 3.0.0 . it will just be 3.0 , the other 0 will be for Maintainers of the kernel

---

### Post by gnomeuser on 2011-05-26
I don't so much care about the version number, though I will admit that .40 is getting a bit high. Perhaps 201X.[1-4] would do well. We do releases roughly every 3 months anyways, so just settling on that as a numbering scheme seems okay.

Regardless, it will be awesome, it looks to finally fix the kswapd using 100% CPU issue, at least SuSE's Mel Gorman has been hard at work on the problem. Also overlay fs looks to finally solve the union mount feature request which has been around since.. early 2.5

---

### Post by IanW on 2011-05-26
So 2.6.40 = 3.0

The discussion is just to decide what to _call_ the next kernel.

---

### Post by MacUntu on 2011-05-26
No. It's also being discussed if that would be a good time to get rid of cruft (support for components you would only find in ancient systems).

---

### Post by VinDSL on 2011-05-26
I'm not a betting man, but my money is on Linux 3.0  ;)

---

### Post by sammiev on 2011-05-27
Would at least like to see it cleaned up before it makes it to a 3.0 or even to the next 2.6.4? version. GL :)

---

### Post by teh603 on 2011-05-27
> **MacUntu said:**
> No. It's also being discussed if that would be a good time to get rid of cruft (support for components you would only find in ancient systems).Careful with ditching legacy components. As late as '03 you could still get motherboards with ISA slots. And never mind what happened to the NuBus slot driver... as far as I can tell, someone decided it was cruft and axed it when Apple and a few others were still making computers with them.

---

### Post by MacUntu on 2011-05-27
> **teh603 said:**
> Careful with ditching legacy components.
The 2.6 line could be continued like the 2.4 kernel I guess.

---

### Post by teh603 on 2011-05-27
> **MacUntu said:**
> The 2.6 line could be continued like the 2.4 kernel I guess.I'm not saying we have to, if we can make useful improvements elsewhere. I just don't want someone put into a situation where a brand new computer has unsupported legacy hardware that someone in an ivory tower has decided no longer needs to be supported.

We have enough ivory tower decisions here as it is.

---

### Post by dino99 on 2011-05-27
there is no need to worry, the oldest kernels are available :)

---

### Post by NCLI on 2011-05-27
> **dino99 said:**
> there is no need to worry, the oldest kernels are available :)

I think people are more concerned about users who don't know what a kernel is ;)

---

### Post by dino99 on 2011-05-27
> **NCLI said:**
> I think people are more concerned about users who don't know what a kernel is ;)

hm, its the bleeding edge forum here, so it might be known by every one :)

---

### Post by teh603 on 2011-05-27
> **dino99 said:**
> hm, its the bleeding edge forum here, so it might be known by every one :)Y'see, I know what the kernel is, but I have no real idea how to add drivers and build my own, and this isn't the time or place to try and teach me. And I don't think I've got that much ability beyond someone transitioning from Windoze, either, except maybe some familiarity with command prompts from the Apple II and MS-DOS.

For example, if I have a D-Link 650+ wireless card whose kernel-level driver was removed (true story, and I do have one of those- my Winbook won't boot with it in the PC card slot) from the main line kernel, an "average user" like me would have no idea how to recompile the kernel with a working driver, or get newer material into an older kernel so I can run more recent software.

This isn't some old PC XT, by the way; this stuff only dates back to '03.

---

### Post by MacUntu on 2011-05-27
> **teh603 said:**
> This isn't some old PC XT, by the way; this stuff only dates back to '03.

That's (almost) 8 years! While the components may be fine and serve your needs, the PC _is_ old.

That's why I don't see a problem with lead-free solder: computer parts die faster, and you can get rid of legacy cruft from the kernel w/o worrying about users with old - working - hardware. :P

---

### Post by murderslastcrow on 2011-05-28
So the solution is to basically suggest a 2.6.xx kernel for anyone with a computer before Vista came out? A lot of people switched to Linux because they didn't want to upgrade to Vista- I think it's fair to say that a good deal of Linux users have this older hardware right now, and a lot of them, like my parents, have no clue what a kernel is. It would be, to say the least, a bit disastrous for me personally if I had to suddenly find a solution for over 20 people I know who I've helped get into Linux.

Of course, it's only about 100 dollars to get a decent computer with modern parts off of eBay that would probably make things more enjoyable, anyway, but most of them don't have problems on their computers with 512 MB of RAM and a dinky video card, even considering Unity.

So sure, it's fine to go ahead if it's really a necessity, so long as it's acknowledged that it will affect a lot of users. As much as I encourage people to get modern parts, even if it's something like a net-top, for some people (ie. not in Europe and the U.S.) it won't be a possibility.

I do think it's safe to abandon anything that won't even be able to run Xfce, though. People who use WMs probably know enough to use an older kernel. I just doubt this is as much of a non-issue as people are making it out to be. I'm well aware none of it is official, of course, and that if the benefits outweigh the cost it would be worth it to abandon some of that hardware.

---

### Post by MacUntu on 2011-05-28
Chill.. I suggest everyone to browse the kernel config (download the kernel source, run 'make xconfig') to know what 'support for legacy stuff' means. It's not about getting rid of support for PATA or floppy disks. :D

---

### Post by amano on 2011-05-28
> **silex89 said:**
> Is there a major change in the kernel if the new version is 3.0.0:confused:

I think that they got completely rid of the Big Kernel Lock (BKL). They tried to achieve that for the whole 2.6. series. Linux 3 would be a new age. The age without the BKL.

---

### Post by MacUntu on 2011-05-28
> **amano said:**
> I think that they got completely rid of the Big Kernel Lock (BKL). They tried to achieve that for the whole 2.6. series. Linux 3 would be a new age. The age without the BKL.

A BKL-less kernel was possible with 2.6.38 and it's gone in 2.6.39.

---

### Post by CreativeReach on 2011-05-29
I would love to see them clean up what they call "cruft", If somones got an ancient  machine they got to use some semi-old software....Big deal? nah just name 3.0 an dump that stuff!:popcorn:

---

### Post by donalgodon on 2011-05-29
The MOST important thing in the new kernel?

Reduce the power consumption!

My power usage increased around 20-25 percent from the last 10.10 kernel to Natty.

A 25 percent battery drain increase is a HUGE problem for me.

This is a known issue, so I hope that it's job number one.

Next, I want to see better support for Sandy Bridge graphics, etc.

---

### Post by xebian on 2011-05-29
It's a 3.0

```
Linux kubu5 3.0.0-rc1-ik0 #1 SMP Sun May 29 21:26:24 CDT 2011 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by alphacrucis2 on 2011-05-29
> **xebian said:**
> It's a 3.0

```
Linux kubu5 3.0.0-rc1-ik0 #1 SMP Sun May 29 21:26:24 CDT 2011 x86_64 x86_64 x86_64 GNU/Linux
```

Have Ubuntu said which version is planned to be released with Oneiric?

---

### Post by JMB74 on 2011-05-30
[https://wiki.ubuntu.com/KernelTeam/Specs/KernelOneiricVersionAndFlavours](https://wiki.ubuntu.com/KernelTeam/Specs/KernelOneiricVersionAndFlavours)

3.0 I presume?

---

### Post by Starks on 2011-05-30
> **murderslastcrow said:**
> So the solution is to basically suggest a 2.6.xx kernel for anyone with a computer before Vista came out?

No. Most, if not all, cruft being removed for 3.0 would affect only PCs from the 386/486 and very early Pentium era.

---

### Post by MacUntu on 2011-05-30
Well, as we now know [0][1], there won't be anything removed from 3.0.

[0]: [http://thread.gmane.org/gmane.linux.kernel.mm/63589/focus%3D57764](http://thread.gmane.org/gmane.linux.kernel.mm/63589/focus%3D57764)
[1]: [http://thread.gmane.org/gmane.linux.kernel.mm/63589/focus%3D9873](http://thread.gmane.org/gmane.linux.kernel.mm/63589/focus%3D9873)

---

### Post by teh603 on 2011-05-30
> **Starks said:**
> No. Most, if not all, cruft being removed for 3.0 would affect only PCs from the 386/486 and very early Pentium era.Geez, that stuff's still in there? Guess more people than I thought are still using ISA slots and all that...

---

### Post by Milos_SD on 2011-05-30
Running great here.
```
uname -a
Linux c2d-desktop 3.0.0-rc1-core2duo #1 SMP PREEMPT Mon May 30 11:42:42 CEST 2011 x86_64 x86_64 x86_64 GNU/Linux
```

I only had to change something in nvidia binary driver to make it work on this kernel. :)

---

### Post by zika on 2011-05-30
> **Milos_SD said:**
> Running great here.
```
uname -a
Linux c2d-desktop 3.0.0-rc1-core2duo #1 SMP PREEMPT Mon May 30 11:42:42 CEST 2011 x86_64 x86_64 x86_64 GNU/Linux
```I only had to change something in nvidia binary driver to make it work on this kernel. :)
Faster than [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0-rc1-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0-rc1-oneiric/) ...

---

### Post by dhave-dhave on 2011-05-30
[www.kernel.org](www.kernel.org) shows 3.0.

---

### Post by gnomeuser on 2011-05-30
> **teh603 said:**
> Geez, that stuff's still in there? Guess more people than I thought are still using ISA slots and all that...

The "cruft" removal was only a proposal. Nothing major has happened at all. The biggest change for me is that they finally squashed the kswapd using 100% CPU bug.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/789982](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/789982)

---

### Post by nanog on 2011-05-30
> **donalgodon said:**
> The MOST important thing in the new kernel?
A 25 percent battery drain increase is a HUGE problem for me.
This is a known issue, so I hope that it's job number one.


There is an ubuntu bug report but no one has reported this to upstream. Upstream is typically not responsive to user-land bugs without a bisect and git commit. Some of them are also not the biggest fans of ubuntu (or gnome).

---

### Post by VinDSL on 2011-05-31
> **VinDSL said:**
> I'm not a betting man, but my money is on Linux 3.0  ;)
w00t!

Where's the pay out window?!?!?  :D

---

### Post by fil0~ on 2011-05-31
> **Milos_SD said:**
> I only had to change something in nvidia binary driver to make it work on this kernel. :)
Here is the point, what have you changed?

---

### Post by Milos_SD on 2011-05-31
> **fil0~ said:**
> Here is the point, what have you changed?

I extracted driver with ```
sh NVIDIA-Linux-x86_64-270.41.19.run -x
```

And then in that directory you have "kernel" directory. In there you have file "conftest.sh", open it, and find this line > BASE_CFLAGS="-D__KERNEL__ \ and change it to: > BASE_CFLAGS="-O2 -D__KERNEL__ \

Then, in the same directory find file "nv-linux.h" and in there do this:

- Find: > #elif LINUX_VERSION_CODE < KERNEL_VERSION(2, 7, 0)

- change it to: > #elif LINUX_VERSION_CODE < KERNEL_VERSION(3, 1, 0)

- or just comment that line like this: >  //#elif LINUX_VERSION_CODE < KERNEL_VERSION(3, 1, 0) (buy adding " // " in front of it). This is what I did, and the above line is what people at nvnews forums suggested.

---

### Post by zika on 2011-05-31
```
:~$ uname -a
Linux cave 3.0.0-0300rc1-generic #201105310830 SMP Tue May 31 08:34:42 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```... :)

---

### Post by paul_in_london on 2011-05-31
No sign of a 32 bit build at the moment though :(

---

### Post by teh603 on 2011-05-31
> **paul_in_london said:**
> No sign of a 32 bit build at the moment though :(Maybe they've decided that the i386 platform is cruft?

I jest, of course.

---

### Post by paul_in_london on 2011-06-01
My quad-core machine is as dead as a dodo (tried replacing the PSU at the time, but that didn't fix it) and I still haven't done anything else about it - partly because one of my friends donated an older machine to me and I've been making do with that.

Even when the dead PC was working I never had much luck with 64 bit. 4x2GB ram sticks and I suspect some of it is bad, but 32 bit was stable enough. This happened late last year, which shows how good I am at getting around to things!

---

### Post by teh603 on 2011-06-01
> **paul_in_london said:**
> My quad-core machine is as dead as a dodo (tried replacing the PSU at the time, but that didn't fix it) and I still haven't done anything else about it - partly because one of my friends donated an older machine to me and I've been making do with that.

Even when the dead PC was working I never had much luck with 64 bit. 4x2GB ram sticks and I suspect some of it is bad, but 32 bit was stable enough. This happened late last year, which shows how good I am at getting around to things!Never tried memtest?

---

### Post by paul_in_london on 2011-06-01
> **teh603 said:**
> Never tried memtest?

Thanks for the thought. Yeah I did when I first got the machine actually because I initially tried using the 64 bit builds and had all sorts of problems (e.g. a cold boot was typically ok, but the way I remember it after the PC had been on for a while a reboot would usually give a kernel panic).

Memtest did indicate some bad ram so I should probably have investigated further, but I found that the 32 bit builds worked ok and ended up sticking with those.

---

### Post by JMB74 on 2011-06-02
> **paul_in_london said:**
> No sign of a 32 bit build at the moment though :(

Looks like they can't get the RC1 or daily git mainline snapshot to build for i386 for now.

I get also the same error when I try to build myself. :(

---

### Post by xeizo on 2011-06-02
I had no problem compiling it from git for 64-bit, but to use Nvidias kernel-module one must use the tip from earlier in the thread. Go to /usr/src/nvidia... and:

> In there you have file "conftest.sh", open it, and find this line
Quote:
BASE_CFLAGS="-D__KERNEL__ \
and change it to:
Quote:
BASE_CFLAGS="-O2 -D__KERNEL__ \
Then, in the same directory find file "nv-linux.h" and in there do this:

- Find:
Quote:
#elif LINUX_VERSION_CODE < KERNEL_VERSION(2, 7, 0)
- change it to:
Quote:
#elif LINUX_VERSION_CODE < KERNEL_VERSION(3, 1, 0)

before installing the kernel, works perfect! 

The earlier post had one additional step, but I omitted it because it makes the module fail. The exact procedure as above is troublefree.

I tried installing the kernel from daily too, same thing with Nvidia, one must do as above.

---

### Post by JMB74 on 2011-06-02
It looks like 64bit does build ok, but that's no good for me.

Also nothing to do with nvidia in my case, as I don't use that.

It's the build error something like:

> ERROR: "pm_idle" [arch/x86/kernel/apm.ko] undefined! 
ERROR: "default_idle" [arch/x86/kernel/apm.ko] undefined! 
make[3]: *** [__modpost] Error 1 
make[2]: *** [modules] Error 2 
make[1]: *** [sub-make] Error 2for i386 builds that fails for me. The above is from the recent [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/") builds, but my errors were pretty much the same.

Probably just need to tweak the config, but haven't got time to try ATM.

---

### Post by dhave-dhave on 2011-06-02
> **xeizo said:**
> I had no problem compiling it from git for 64-bit, but to use Nvidias kernel-module one must use the tip from earlier in the thread. Go to /usr/src/nvidia... and:



before installing the kernel, works perfect! 

The earlier post had one additional step, but I omitted it because it makes the module fail. The exact procedure as above is troublefree.

I tried installing the kernel from daily too, same thing with Nvidia, one must do as above.

Thanks very much for this tip. Getting the nvidia module to compile properly was the last hurdle for me. The change to kernel 3.0 might be mainly cosmetic, but since the Linux kernel has been at version 2.x for 15 years -- really! -- this is an historic occasion. Sort of. ;)

---

### Post by paul_in_london on 2011-06-08
> **JMB74 said:**
> It looks like 64bit does build ok, but that's no good for me.

Also nothing to do with nvidia in my case, as I don't use that.

It's the build error something like:

for i386 builds that fails for me. The above is from the recent [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/") builds, but my errors were pretty much the same.

Probably just need to tweak the config, but haven't got time to try ATM.

Was hoping to see a 32 bit build for 3.0-rc2, but nope. Also just checked today's daily build ([http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/)).

Still no joy. :(

---

### Post by JMB74 on 2011-06-08
> **paul_in_london said:**
> Was hoping to see a 32 bit build for 3.0-rc2, but nope. Also just checked today's daily build ([http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/daily/current/")).

Still no joy. :(

I got fed up waiting, so built my own 32bit.

Disable APM support in the config, and this works fine for me.

[https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild)

Running fine on RC2+ at the moment. :)

---

### Post by paul_in_london on 2011-06-08
:lol:> **JMB74 said:**
> I got fed up waiting, so built my own 32bit.

Disable APM support in the config, and this works fine for me.

[https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild)

Running fine on RC2+ at the moment. :)

@JMB74: Thanks for the link. Never actually bothered trying to build my own before. It's bad enough upgrading packages and ports on FreeBSD. :lol: There are some things to like about FreeBSD, which I recently installed for the first time on one of my machines. Very tedious (rather than difficult) to set up as a desktop and get everything working, but that's another topic.

Anyway, maybe now is the time to try. Well not right this second, but...

---

### Post by JMB74 on 2011-06-08
> **paul_in_london said:**
> Anyway, maybe now is the time to try. Well not right this second, but...

Well, you are in luck, as it looks like they've now fixed the 32bit build problems.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0-rc2-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0-rc2-oneiric/)

---

### Post by mc4man on 2011-06-08
> **donalgodon said:**
> The MOST important thing in the new kernel?

Reduce the power consumption!

My power usage increased around 20-25 percent from the last 10.10 kernel to Natty.

A 25 percent battery drain increase is a HUGE problem for me.

This is a known issue, so I hope that it's job number one.

Next, I want to see better support for Sandy Bridge graphics, etc.
There is a patch that MAY help - comments 57 -60
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131)
some test packages (natty
[http://people.canonical.com/~apw/lp760131-natty/](http://people.canonical.com/~apw/lp760131-natty/)

---

### Post by paul_in_london on 2011-06-08
> **JMB74 said:**
> Well, you are in luck, as it looks like they've now fixed the 32bit build problems.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0-rc2-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0-rc2-oneiric/)

@JMB74: Thanks. Actually kicked off a 32 bit kernel build on a VM before I left work, went for a couple of beers and then discovered when I got home that the 386 debs for 3.0-rc2 had finally popped up!

It'll be interesting to find out tomorrow if my compilation worked.

---

### Post by JMB74 on 2011-06-09
Looks like we are now getting official 3.0 builds going directly into the Oneiric repos

[https://launchpad.net/ubuntu/oneiric/+source/linux/3.0-0.1](https://launchpad.net/ubuntu/oneiric/+source/linux/3.0-0.1)

---

### Post by Harry33 on 2011-06-09
Hmm, that is true.
New kernel 3.0-0.1, and it is a rc1.

---

### Post by portis on 2011-06-09
It's rc2. 

 [ Major Kernel Changes ]

  * rebase from v2.6.39 to v3.0-rc1
  * rebase from v3.0-rc1 to v3.0-rc2

> **Harry33 said:**
> Hmm, that is true.
New kernel 3.0-0.1, and it is a rc1.

---

### Post by JMB74 on 2011-06-09
RC2 I think.

> [ Major Kernel Changes ]    
* rebase from v2.6.39 to v3.0-rc1   
* rebase from v3.0-rc1 to [COLOR=Red]v3.0-rc2[/COLOR]

EDIT: Oops! Cross posted.

---

### Post by Harry33 on 2011-06-09
> **portis said:**
> It's rc2. 

 [ Major Kernel Changes ]

  * rebase from v2.6.39 to v3.0-rc1
  * rebase from v3.0-rc1 to v3.0-rc2

True, so it seems.

---

### Post by Harry33 on 2011-06-09
Well I could not get dkms working.
Nvidia-current module building failed.

I'll open a new thread on this issue.

---

