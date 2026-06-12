---
title: "Soon to be new user? Need some answers"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by Feyhart on 2008-04-22
Okay, so i'm considering atleast partitioning a portion of my hard drive to duel boot Linux. (If I wasn't such a huge gamer, i'd go full linux, but alas..)

So I have a few questions and a problem i ran in to last time i tried to use the live dvd.

I have three hard drives my primary hard drive is a 74 gig Raptor 10k rpm hard drive with windows on it. I have a 300 gig secondary drive, that i install games too, and a 500 gig external that i use for downloads and such. 

My question is this Could I make a 20 gig partition on my secondary(300 gig) hard drive to install linux too, so that i can play around with it and such, or does it need to be on the same hard drive as windows? 

My second question is how would i go about putting Beryl on my system, i found it to be quite interesting when last looking at  it vs vista's aero. 

My third question is related to my problem, does the latest version of Ubuntu work with wide screen monitors?

Here is my problem, last time i tried to use the ubuntu livecd and when it booted up, and i went to the desktop, half of my screen was missing, it was a bizzare problem that i couldn't find any solution too.

My computer specs are as such
4400+ AMD X2
2 Gigs PC3200 Ram
Nvidia 7800 GTX VGA/GPU.\
Audigy 2 Value Soundcard

---

### Post by Rocket2DMn on 2008-04-22
You can install to a 20GB partition if you'd like, just defragment the drive first.  I always recommend backing up all your important data first in case something goes wrong (more importantly, in case YOU do something wrong).  Ubuntu will install GRUB to the MBR so you can dual boot.  If Vista gives you problems, see here - [https://help.ubuntu.com/community/WindowsDualBoot#head-730ae90dd0551e5f762bda8fe0fe0616600f5783](https://help.ubuntu.com/community/WindowsDualBoot#head-730ae90dd0551e5f762bda8fe0fe0616600f5783)
and here - [https://help.ubuntu.com/community/WindowsDualBoot#head-e746e1f17e0fc71f1c95142f2558412cd6b3afe2](https://help.ubuntu.com/community/WindowsDualBoot#head-e746e1f17e0fc71f1c95142f2558412cd6b3afe2)

Beryl no longer exists, it merged with Compiz to become Compiz Fusion - it is installed by default it Gutsy Gibbon and newer (Hardy Heron is due to be released in a couple of days, the Release Candidate is already out and available, you may consider just going straight to this so you don't have to upgrade from Gutsy to Hardy right after installing).

Ubuntu does support widescreen monitors out of the box.  The LiveCD does not work for everybody (usually because of video driver problems with the CD), so if it turns out not to work, you can install using the Alternate Install CD which is an easy to use text-based installer without a live session.  Just check the box at the bottom of [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) ( again, I would wait for Hardy or download the Release Candidate - [http://releases.ubuntu.com/8.04/](http://releases.ubuntu.com/8.04/) ).  After you install your video stuff should be OK, it may prompt you to install restricted drivers which you should do if asked about it.

---

### Post by Ub1476 on 2008-04-22
> My question is this Could I make a 20 gig partition on my secondary(300 gig) hard drive to install linux too, so that i can play around with it and such, or does it need to be on the same hard drive as windows?

There's a good howto on the help.ubuntu.com website [here]("https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs?highlight=(installing)").

Even though, I see no reason to not installing it next to Windows, or in Windows (with help from the new Wubi installer), at least if you store all data on an external HD.

> My second question is how would i go about putting Beryl on my system, i found it to be quite interesting when last looking at it vs vista's aero.

This is included in Ubuntu already. It's called [Compiz-Fusion]("http://www.compiz-fusion.org/") (a merge of Beryl and Compiz). If you want to customize it, you need to install *Advanced Desktop Effects* from add/remove or from terminal:

```
sudo apt-get install ccsm
```

You also need to remember to check for graphic drivers in System>Administration>Hardware Drivers. I can assure you it works very well on my Nvidia 7900GS:)

> My third question is related to my problem, does the latest version of Ubuntu work with wide screen monitors?

It has for me, what you encountered was probably just a bug..? It might be the lack of drivers from nvidia as well (which you install after installation).

I suggest you try the x86_64 version of ubuntu (instead of x86, 32-bit). Unless you use Skype it shouldn't be much of a problem.

Good luck:)

---

### Post by Feyhart on 2008-04-22
> **Ub1476 said:**
> There's a good howto on the help.ubuntu.com website [here]("https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs?highlight=(installing)").

Even though, I see no reason to not installing it next to Windows, or in Windows (with help from the new Wubi installer), at least if you store all data on an external HD. 

If I understand you right, you mean you see no reason not to install it on the same drive as windows? The problem for me with that is i don't have alot of room to use two different OS's on that hard drive, my gaming drive is the one with the significant amount of extra space. ^^



> This is included in Ubuntu already. It's called [Compiz-Fusion]("http://www.compiz-fusion.org/") (a merge of Beryl and Compiz). If you want to customize it, you need to install *Advanced Desktop Effects* from add/remove or from terminal:

```
sudo apt-get install ccsm
```

You also need to remember to check for graphic drivers in System>Administration>Hardware Drivers. I can assure you it works very well on my Nvidia 7900GS:)




Ahhh nice, and silly me i had actually read that about beryl fusing. No doubt i'll be back for help on that stuff, cause i'm a complete noob to linux atm. i've had a long standing interest in it, but never the drive nor the time to learn it; now I suddanly tonight decided 'Hey I want to start a slow transition to linux'

> It has for me, what you encountered was probably just a bug..? It might be the lack of drivers from nvidia as well (which you install after installation).

I suggest you try the x86_64 version of ubuntu (instead of x86, 32-bit). Unless you use Skype it shouldn't be much of a problem.

Good luck:)

Does Nvidia have drivers that support linux?

Also alas I do use Skype, not so much for it's phone service, but it's instant messaging capabilities, as a larger part of a community that i admin we have a chatroom there. 

All though i would enjoy using X64 I need to be able to use skype too haha

Thanks for the help, thinking i'll wait for H.H. to come out before installing, that way i have time to research a bit more on partitioning, and stuff like that.

---

### Post by lswest on 2008-04-22
answering your question about linux drivers from Nvidia, yup, they exist and work pretty well (people usually have less problems with nvidia drivers than ATI drivers).  There are open-source "restricted" drivers that are easily installed via the hardware manager in Hardy, or you can use Envy (see [here]("http://albertomilone.com/nvidia_scripts1.html")) to install the propriety drivers (those made and supported by Nvidia itself).  Or do it the hard way and install them by hand, up to you

---

### Post by ad_267 on 2008-04-22
```
E: Couldn't find package ccsm
```
To be able to customize your compiz-fusion the package is called compizconfig-settings-manager, not ccsm. So you would type:
```
sudo apt-get install compizconfig-settings-manager
```
Once you've got that you can select the custom option for your visual effects and enable things like the cube. (Make sure you set your horizontal virtual size to 4 and the other two options to one under the general options - desktop size)

And if you are new to linux you may be happier doing things the gui way, so you can go to System - Administration - Synaptic Package Manager to install software and search for compizconfig-settings-manager

The nVidia drivers work well for me and I have a dual monitor setup.

I'm pretty sure can install Ubuntu on any of the hard drives just fine.

---

### Post by Ub1476 on 2008-04-22
Well, Skype do work in x86_64, but it's better in -x86:)

Sound is a bit "choppy", but everything else works fine.

---

### Post by 3rdalbum on 2008-04-22
I just installed Ubuntu onto a computer with a square 17 inch LCD monitor, which worked fine. Then I plugged in a widescreen 19 inch monitor, and that also immediately worked properly.

There were issues in previous versions with detecting the resolution of your monitor, but it looks like everything works now.

Your computer looks a little bit behind the times, so it's likely to work perfectly out-of-the-box (once you open the Hardware Drivers program).

---

### Post by billgoldberg on 2008-04-22
> **Feyhart said:**
> Okay, so i'm considering atleast partitioning a portion of my hard drive to duel boot Linux. (If I wasn't such a huge gamer, i'd go full linux, but alas..)

So I have a few questions and a problem i ran in to last time i tried to use the live dvd.

I have three hard drives my primary hard drive is a 74 gig Raptor 10k rpm hard drive with windows on it. I have a 300 gig secondary drive, that i install games too, and a 500 gig external that i use for downloads and such. 

My question is this Could I make a 20 gig partition on my secondary(300 gig) hard drive to install linux too, so that i can play around with it and such, or does it need to be on the same hard drive as windows? 

My second question is how would i go about putting Beryl on my system, i found it to be quite interesting when last looking at  it vs vista's aero. 

My third question is related to my problem, does the latest version of Ubuntu work with wide screen monitors?

Here is my problem, last time i tried to use the ubuntu livecd and when it booted up, and i went to the desktop, half of my screen was missing, it was a bizzare problem that i couldn't find any solution too.

My computer specs are as such
4400+ AMD X2
2 Gigs PC3200 Ram
Nvidia 7800 GTX VGA/GPU.\
Audigy 2 Value Soundcard

1. I never tried it but I don't think that will be a problem.
You can always assign a few gb for the operating system and put your /home folder on another hard drive.

2. Ubuntu 7.10 and ubuntu 8.04 (comes out in 2 days !!) come with compiz fusion installed by default (you will need to add the compizconfig manager). Compiz fusion is the newer version of beryl (to keep it simple) and has much more to offer than beryl did in that beryl vs aero video.

3. Sure. 

4. Live cd's don't run good on all systems. 

ps: in 2 days the new ubuntu version comes out, I would install that one as they only become better and better.

---

### Post by Feyhart on 2008-04-22
> **3rdalbum said:**
> I just installed Ubuntu onto a computer with a square 17 inch LCD monitor, which worked fine. Then I plugged in a widescreen 19 inch monitor, and that also immediately worked properly.

There were issues in previous versions with detecting the resolution of your monitor, but it looks like everything works now.

**Your computer looks a little bit behind the times, so it's likely to work perfectly out-of-the-box (once you open the Hardware Drivers program)**.

that makes me sad. lol 

as when i had it built (for TES: Oblivion, and F.E.A.R.) I was able to take it to lanparties, and people DROOLED over it. ^^ 

It still runs anything pre-crysis era at basically full speed. it's only a couple years old, but i'll be upgrading soon, 8800GTX, 4 gig memory, and a higher end processer(still dual core, not wasting my money on a quad until we can even use dual cores.. lol) 

Back on topic there, that's refreshing. 

Regarding above, the /home folder as I mentioned i'm ***_really_*** new to linux. I don't understand some of the termonology yet.

---

### Post by billgoldberg on 2008-04-22
> **Feyhart said:**
> that makes me sad. lol 

as when i had it built (for TES: Oblivion, and F.E.A.R.) I was able to take it to lanparties, and people DROOLED over it. ^^ 

It still runs anything pre-crysis era at basically full speed. it's only a couple years old, but i'll be upgrading soon, 8800GTX, 4 gig memory, and a higher end processer(still dual core, not wasting my money on a quad until we can even use dual cores.. lol) 

Back on topic there, that's refreshing. 

Regarding above, the /home folder as I mentioned i'm ***_really_*** new to linux. I don't understand some of the termonology yet.

The /home folder is the folder where are your files are stored in. All you videos, music, documents, ... This can be on another partition than the OS itself (easier to make backups, to upgrade your ubuntu version to a new version, ...)

---

### Post by ad_267 on 2008-04-22
In Linux you don't have a C: drive and a D: drive etc, all partitions are mounted at a point in the file structure. The root directory is / (think of that as like C:\ in windows). If you don't set a specific point to mount a partition Ubuntu will mount it automatically in /media. People often choose a partition to be mounted at /home so that all of your user settings and documents, music etc can be on a separate partition, but this is not required.

This might be useful reading: [http://en.wikipedia.org/wiki/Filesystem_hierarchy_standard](http://en.wikipedia.org/wiki/Filesystem_hierarchy_standard)

---

### Post by boxcar451 on 2011-01-08
I am thinking of changing from windows xp 32 to linix. I have a 320gb hdd that I'd like to get hooked from this 100gb factory installed.  My system specs are:
100gb hdd, 2gb ram, nvidia ge force 8400 gs 512mb ram, cd rw dvd rom, 3.20ghz, 533mhz fsb, 512kb/L2chache. I'm running windows xp home edition that was factory installed but have done the updates to win xp sp3. Thanks all

---

### Post by 3rdalbum on 2011-01-08
Boxcar, if you have a question please put it into a new thread rather than bumping this ancient one :-)

Also, it's not clear what your question is; I don't see a problem with your system for Linux, and if you're thinking about switching you should definitely try it.

---

### Post by 3rdalbum on 2011-01-08
Boxcar, if you have a question please put it into a new thread rather than bumping this ancient one :-)

Also, it's not clear what your question is; I don't see a problem with your system for Linux, and if you're thinking about switching you should definitely try it.

---

