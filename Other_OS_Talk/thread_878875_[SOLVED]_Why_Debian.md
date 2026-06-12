---
title: "[SOLVED] Why Debian?"
date: 2008-08-03
forum: Other OS Talk
---

### Post by jualin on 2008-08-03
I have been with Ubuntu for over a year and I wanted to know what are the advantages of running Debian over Ubuntu. 
Is it stability?
Better performance?

Someone ask me that on the forums yesterday and I couldn't find a good answer for it. Thank you in advance.

---

### Post by munkyeetr on 2008-08-03
I know that when I installed Debian and all the "candy features" (compiz, flash, java, codecs, etc) my system runs with a little less ram in use.

I have found that I can more easily tweak my runlevels as the /etc/inittab and rcX.d directories are available (as opposed to Ubuntu's use of Upstart).

...my 2 cents...

---

### Post by init1 on 2008-08-03
> **jualin said:**
> I have been with Ubuntu for over a year and I wanted to know what are the advantages of running Debian over Ubuntu. 
Is it stability?
Better performance?

Someone ask me that on the forums yesterday and I couldn't find a good answer for it. Thank you in advance.
1) It's a **LOT** faster. I can't stand to use Ubuntu anymore; it's so much slower than Debian Etch.

2) It's far more stable. Ubuntu crashes frequently and has several extremely annoying bugs for me. This isn't an issue in Debian. 

3) It doesn't require as much RAM as Ubuntu. I have 512MB RAM, and Ubuntu usually needs a about 100MB swap, even with just a few apps open. In Debian, I'm not swapping at all. 

Of course, Ubuntu runs better on some computers than on others. Some of these points might not apply to your experiences.

---

### Post by LaRoza on 2008-08-03
> **jualin said:**
> I have been with Ubuntu for over a year and I wanted to know what are the advantages of running Debian over Ubuntu. 
Is it stability?
Better performance?


It depends on the version of Debian.

The one thing about Debian that is consistant is its speed, it flies compared to Ubuntu.

> **init1 said:**
> 
2) It's far more stable. Ubuntu crashes frequently and has several extremely annoying bugs for me. This isn't an issue in Debian. 

Which version? If you use Lenny it may be a different story.

> 
3) It doesn't require as much RAM as Ubuntu. I have 512MB RAM, and Ubuntu usually needs a about 100MB swap, even with just a few apps open. In Debian, I'm not swapping at all. 

I'm never swapping in Ubuntu, no matter how many apps I have open.

---

### Post by jualin on 2008-08-03
Thank you everyone for all the responses. I will try it tomorrow and see if I like it.

---

### Post by LaRoza on 2008-08-03
> **jualin said:**
> Thank you everyone for all the responses. I will try it tomorrow and see if I like it.

It is like Ubuntu (Ubuntu is based on it) so if you know your way around in Ubuntu, Debian is easy (note: "knowing your way around" doesn't mean knowing where to click)

---

### Post by wolfen69 on 2008-08-03
> **init1 said:**
> 1) It's a **LOT** faster. I can't stand to use Ubuntu anymore; it's so much slower than Debian Etch.

2) It's far more stable. Ubuntu crashes frequently and has several extremely annoying bugs for me. This isn't an issue in Debian. 

3) It doesn't require as much RAM as Ubuntu. I have 512MB RAM, and Ubuntu usually needs a about 100MB swap, even with just a few apps open. In Debian, I'm not swapping at all. 

**Of course, Ubuntu runs better on some computers than on others. Some of these points might not apply to your experiences.**

exactly. 

in my experience with ubuntu, it *never* crashes. solid as a rock. it is running so flawlessly in fact, that i might not (for the first time) use the next version of ubuntu. 

ram is not an issue when you have 2 gigs.

as far as speed, i have not noticed a big difference. debian *might* be a touch faster, but nothing to lose sleep over.

basically, just use what you prefer.

---

### Post by wdaniels on 2008-08-03
> **LaRoza said:**
> The one thing about Debian that is consistant is its speed, it flies compared to Ubuntu.

Does anybody really know why this is? Aside from a lot of unnecessary (for me) services that Ubuntu includes by default, what other factors are there in this? Different scheduler? Different kernel settings? Different compilation options?

Ubuntu has been a fantastic, reliable distribution for me for day-to-day use on the desktop since I ditched Windows a couple of years ago, but it does feel quite "clunky" at times and I'm wondering myself if it would really be any more trouble to switch to a less polished distro now that I understand Linux in more detail.

But I wouldn't want to make a change like that without really understanding why it's necessary. Is there something fundamental to the compilation/organisation of the distro that makes Debian faster or is it just a case of investing more time into tweaking Ubuntu?

---

### Post by LaRoza on 2008-08-03
> **wdaniels said:**
> Does anybody really know why this is? Aside from a lot of unnecessary (for me) services that Ubuntu includes by default, what other factors are there in this? Different scheduler? Different kernel settings? Different compilation options?

I think it is a combination of less services and probably the lack of compiz. Debian with GNOME works well on 256 MB of RAM, well enough to be better than XP on the same computer.

---

### Post by init1 on 2008-08-03
> **LaRoza said:**
> 
Which version? If you use Lenny it may be a different story.

I'm using Etch, for that exact reason. I'll switch to Lenny when it becomes stable, but if it's not as reliable as Etch, I'll switch back. Yeah, it'll be really old then (it's really old now :D), but it's good enough for most things.

---

### Post by kerry_s on 2008-08-03
> **jualin said:**
> I have been with Ubuntu for over a year and I wanted to know what are the advantages of running Debian over Ubuntu. 
Is it stability?
Better performance?

Someone ask me that on the forums yesterday and I couldn't find a good answer for it. Thank you in advance.

it's just 1 of those things you got to try for yourself.
i'm using debian etch straight gnome install using the net installer. everything just works, the only thing i installed was flash, which was just going to a flash site and clicking "install plugin" in iceweasel(firefox).
of course i am changing the look, i don't need a background or smooth fonts, but other than that it's bone stock. oh, i added crystalcursors from the repo, cause the stock 1 is just to small for me and i don't want animation.


net installer:
[http://cdimage.debian.org/debian-cd/4.0_r4/i386/iso-cd/debian-40r4-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r4/i386/iso-cd/debian-40r4-i386-businesscard.iso)

---

### Post by benerivo on 2008-08-03
> **LaRoza said:**
> It depends on the version of Debian

Yes, and the stable version of debian, uses packages that are 'outdated' (although definitely stable). I think debian stable currently uses Firefox 2 (called iceweasel in debian), rather than Firefox 3. Surely, the user would notice the speed difference in program version performance in this case, as well as others.

Debian unstable is good for a desktop computer with someone who knows a little about linux and is prepared to overcome the odd adversity. The packages are as up to date as you will find (several updates each day). I have used it and have noticed it is slightly faster and takes up less ram than ubuntu, although i did only install a minimal gnome desktop from the debian netinstall cd. I have also tried debian stable on the same hardware and it used little ram, but was obviously slower than the unstable version.

---

### Post by bobbob1016 on 2008-08-03
The speed thing bothers me a bit, wouldn't there be some way to get Ubuntu's add-ons and get it somewhat comprable to Debian's speed?  I mean since Ubuntu is based on Debian.  I know Ubuntu has a bit more bloat, but I'd think there would be some ways to get some of the same speed as Debian.

---

### Post by SunnyRabbiera on 2008-08-03
Well even though debian is more stable and reliable then Ubuntu, I dont like certain thinga about it.
Searching out multimedia is harder, installation of the system itself is harder, plus its pure GPL stance can leave some drawbacks.

---

### Post by jualin on 2008-08-04
Thank you all for the advices. I will mark the thread as solved since I think I got what I was looking for. I will try Debian myself to see if I like it. After all, that's what Linux is about, choosing. Thank you all again. Greetings from Miami, FL!

---

### Post by mitchellcipriano on 2008-08-04
> **wdaniels said:**
> 
Ubuntu has been a fantastic, reliable distribution for me for day-to-day use on the desktop since I ditched Windows a couple of years ago, but it does feel quite "clunky" at times and I'm wondering myself if it would really be any more trouble to switch to a less polished distro now that I understand Linux in more detail.

I am curious, how does it seem clunky? Overall I have had an excellent experience with Ubuntu. It never seems clunky to me, actually quite polished.

---

### Post by wdaniels on 2008-08-05
> **mitchellcipriano said:**
> I am curious, how does it seem clunky? Overall I have had an excellent experience with Ubuntu. It never seems clunky to me, actually quite polished.

I agree that Ubuntu is nicely polished in general - I meant "clunky" in terms of performance really. To be honest, I suspect this has more to do with FireFox and/or Compiz than anything specific to Ubuntu, which is why I'm always interested to know what exactly is it that is "faster" about one distribution or another. People make these statements all the time, but so far as I can reason about it, they should all be the same if you're using the same set of applications (which of course you're free to choose yourself for each distro). I'd really like to know what other things, if any, make one distribution perform better than another. I can think of a few minor things like compiler optimisation settings, but that should barely be detectable 99% of the time.

One thing that I find odd is that I don't use swap (I have 2GB RAM and as far as I'm concerned that ought to be more than enough - if I run out of memory some day I want to know about it so that I can identify the culprit) yet sometimes when I've got 4 workspaces full of stuff and I start switching between programs, I notice a slight "stutter". Now, I know that the kernel's not swapping stuff to/from disk, so perhaps it's a shortage of CPU clock cycles briefly? But none of my programs are really doing anything at the time. I guess it could be all the stupid animations and flash adverts on the various websites that are open, running away in the background, but that sure seems like an insult to a 2.2 GHz (AMD 3500+) CPU. Or maybe 256MB is not enough video memory for compiz to keep all those windows mapped so things are getting shuffled in and out of the graphics card? I've never looked into the internal workings of all this compositing stuff, but I'm assuming that's roughly how it works, in which case couldn't it be more intelligent about what to keep in the GPU memory and what not to? Otherwise, what's the problem?

Probably I'm still stuck in the past where 512KB and a Motorola 68000 were plenty enough resources to do whatever you want and I should go back to doing everything in a terminal like the other dinosaurs :D

---

### Post by jualin on 2008-08-05
> **wdaniels said:**
> I agree that Ubuntu is nicely polished in general - I meant "clunky" in terms of performance really. To be honest, I suspect this has more to do with FireFox and/or Compiz than anything specific to Ubuntu, which is why I'm always interested to know what exactly is it that is "faster" about one distribution or another. People make these statements all the time, but so far as I can reason about it, they should all be the same if you're using the same set of applications (which of course you're free to choose yourself for each distro). I'd really like to know what other things, if any, make one distribution perform better than another. I can think of a few minor things like compiler optimisation settings, but that should barely be detectable 99% of the time.

One thing that I find odd is that I don't use swap (I have 2GB RAM and as far as I'm concerned that ought to be more than enough - if I run out of memory some day I want to know about it so that I can identify the culprit) yet sometimes when I've got 4 workspaces full of stuff and I start switching between programs, I notice a slight "stutter". Now, I know that the kernel's not swapping stuff to/from disk, so perhaps it's a shortage of CPU clock cycles briefly? But none of my programs are really doing anything at the time. I guess it could be all the stupid animations and flash adverts on the various websites that are open, running away in the background, but that sure seems like an insult to a 2.2 GHz (AMD 3500+) CPU. Or maybe 256MB is not enough video memory for compiz to keep all those windows mapped so things are getting shuffled in and out of the graphics card? I've never looked into the internal workings of all this compositing stuff, but I'm assuming that's roughly how it works, in which case couldn't it be more intelligent about what to keep in the GPU memory and what not to? Otherwise, what's the problem?

Probably I'm still stuck in the past where 512KB and a Motorola 68000 were plenty enough resources to do whatever you want and I should go back to doing everything in a terminal like the other dinosaurs :D

Nicely put pal! I sometimes find my Ubuntu running a little slower when I have many applications opened but I don't complain since I only have 512 MB of RAM and an Nvidia 128 MB video card. Something funny is that no matter how "slow" Ubuntu feels sometimes, XP or Vista feel way slower, even with Compiz enabled in Ubuntu.

---

### Post by wdaniels on 2008-08-05
> **jualin said:**
> Nicely put pal! I sometimes find my Ubuntu running a little slower when I have many applications opened but I don't complain since I only have 512 MB of RAM and an Nvidia 128 MB video card. Something funny is that no matter how "slow" Ubuntu feels sometimes, XP or Vista feel way slower, even with Compiz enabled in Ubuntu.

Certainly in comparison to Windows, the demands on system resources are tame, particularly when we compare Compiz to Aero, as you say. But in that case it's only to be expected given the stronger architectural separation between GUI layers that has existed since the beginning in Linux. Window compositing was always going to have to be a major, messy, bolt-on lump in Windows as opposed to a (relatively) natural modular replacement of just the Window Manager (and optionally the Window Decorator) in Linux.

And so far as the underlying system performance goes, Linux has always done much better than Windows for me on the same hardware. But I do have to say that I find that Gtk lets the side down a little. Gtk controls just never seem quite as snappily responsive as Windows.

Anyway, I didn't quite mean to rant about any shortcomings of Linux/Ubuntu performance, only to explain the reason that I was questioning, as a matter of genuine interest, the general consensus that Debian is faster than Ubuntu.

---

### Post by timzak on 2008-08-05
I've never seen an objective measure of how much faster Debian is than Ubuntu.  In my experience, Debian does use less ram, which is nice if you're very limited in that area.  And in that way, it will be faster since you'll be able to load more apps up before swapping starts.  I'd be surprised if a Debian install otherwise identical to an Ubuntu install, on a high memory system, would be measurably faster at all.

I recently installed Debian Etch with XFCE on an old computer with 256 MB ram.  It previously had Xubuntu 7.04.  I configured the two installs as similarly as I could, and the older version of Xubuntu still used more RAM than the Debian install.  It was like 64 MB vs. 53 MB.

---

