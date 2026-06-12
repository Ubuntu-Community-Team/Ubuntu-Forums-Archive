---
title: "10 Meg OS - Tiny Core Linux is great"
date: 2008-12-03
forum: Other OS Talk
---

### Post by ronnielsen1 on 2008-12-03
> Tiny Core Linux is a very small (10 MB) minimal Linux Desktop. It is based on Linux 2.6 kernel, Busybox, Tiny X, Fltk, and Jwm. The core runs entirely in ram and boots very quickly. 

It is not a complete desktop nor is all hardware completely supported. It represents only the core needed to boot into a very minimal X desktop typically with wired internet access. 

The user has complete control over which applications and/or additional hardware to have supported, be it for a desktop, a nettop, an appliance, or server, selectable from our online repository.

[http://www.tinycorelinux.com/](http://www.tinycorelinux.com/)

Been playing with it this morning and it's super fast. You install the apps you want like Opera. I'm currently using it.

---

### Post by stinger30au on 2008-12-03
handy, thanks

---

### Post by kerry_s on 2008-12-03
i got to check that out, it sounds just like the DSL-core people have been asking robert for.

---

### Post by mentallaxative on 2008-12-03
Oh my god.... they keep getting smaller!

---

### Post by Sorivenul on 2008-12-03
Excellent. Looks solid - downloading now to try.

---

### Post by cmay on 2008-12-03
thanks. i have been looking for something like that. i have the linux from scratch book and live cd i got from a online store that prints free books and burn cd and i have not had anytime yet to start on it. i usealy do minimal custom debian installs but i would like to try a little alternative and especially one that can fit on a floppy disk. i have a old laptop that has no hardrive and it has very little ressurce but the boot floppy from freedos can run on it. its little of use but i could like to see if one can have a absolutely small linux system running on it before i get rid of the laptop. it is really very very old and i cant find any parts for it at all. and the effort for trying would be more expensive than just accept it has lived its laptop live and get over with it. i found it in the trash section at the recycling center.

---

### Post by nitehawk777 on 2008-12-03
What is it based on?  Slackware? Debian?   I mean,...would it be easy to add apps (via little dialup) after downloading the core?
If it would be fairly easy,...that could be a simple way of building a small, usable system.  DSL just installs on the hard drive as Debian Woody.
What does this do????

---

### Post by cardinals_fan on 2008-12-03
Doesn't look like you can perform a full install.  Still a cool project.

---

### Post by init1 on 2008-12-03
> **cardinals_fan said:**
> Doesn't look like you can perform a full install.  Still a cool project.
You can, actually
```

gunzip tinycore.gz
cpio -i <tinycore

```
That extracts the "/" tree. The grub code is
```

title Tinycore
root (hd0,0)
kernel /bzImage root=/dev/sda1
boot

```
Of course, you'll need to put the "/" files in a partition and edit the grub code depending on your setup. 

This is a really cool Distro. It reminds me of SliTaz, but even more basic. I'm posting with it right now :D

---

### Post by Twitch6000 on 2008-12-03
Now this is the kind of distro you can put on an old windows 3.1 machine :popcorn:.

One question though is it based on anything or is it its own distro?(I hardly see that anymore)

---

### Post by Sorivenul on 2008-12-03
> **Twitch6000 said:**
> Now this is the kind of distro you can put on an old windows 3.1 machine :popcorn:.

One question though is it based on anything or is it its own distro?(I hardly see that anymore)

Looks to be its own distribution, AFAIK.  Rare, I know.

---

### Post by cardinals_fan on 2008-12-03
> **init1 said:**
> You can, actually
```

gunzip tinycore.gz
cpio -i <tinycore

```
That extracts the "/" tree. The grub code is
```

title Tinycore
root (hd0,0)
kernel /bzImage root=/dev/sda1
boot

```
Of course, you'll need to put the "/" files in a partition and edit the grub code depending on your setup. 

This is a really cool Distro. It reminds me of SliTaz, but even more basic. I'm posting with it right now :D
Thanks for the tip, but does that actually perform a traditional Linux install, or does it just copy the live data to the disk (a frugal install)?

---

### Post by kagashe on 2008-12-04
I am posting this from Opera downloaded on Tiny core Linux.

Colors are funny. Ubuntu Logo on this forum is looking Blue.

How can I see original colors on this Opera?

kagashe

NB: Xvesa does not work properly on this hardware. I could see proper colors on 640x480x16. Later on I installed Xorg and it is working at 1024x768.

---

### Post by cmay on 2008-12-04
i downloaded and burned the iso last night. i tested it and it is very cool. the thing is that i have a danish keyboard which is not supported yet. so i am thinking that if i could figure out how to create such one i would give it it a try and maybe if i have luck wiht the keyboard layout then submit the keyboard layout to the developers. i do not know how to do this yet. but i really like the look and feel of this little distro and for that matter if only i could use the danish keyboard i could say it would be one of my most used live cd maybe. thanks for the links.

---

### Post by smoker on 2008-12-04
will have to give this a try, is it an rpm or deb distro, or something unique?

---

### Post by ronnielsen1 on 2008-12-04
>  it an rpm or deb distro, or something unique? 	
appears to be it's own packager using .tce extensions :confused: Don't know whether downloading from source would work.
[http://www.tinycorelinux.com/files/extensions/](http://www.tinycorelinux.com/files/extensions/)

---

### Post by notwen on 2008-12-04
Wow, interesting to see a small/low system resource distro that I haven't heard of/seen before.  Thanks for this.  Hopefully have time to check it out over the weekend.  =]

---

### Post by Bungo Pony on 2008-12-04
Sounds interesing, and I'll probably give it a try. I've been wanting a stripped-down version of DSL, but this may be a good substitute.

---

### Post by init1 on 2008-12-04
> **cardinals_fan said:**
> Thanks for the tip, but does that actually perform a traditional Linux install, or does it just copy the live data to the disk (a frugal install)?
It's not compressed, so I guess it would be a full install rather than a frugal install.

---

### Post by cdwillis on 2008-12-04
This is really cool. Thanks for the heads up.

---

### Post by ronnielsen1 on 2008-12-04
I think I'll have to play with this one some more. I've got some free hard drive space. It's new and they don't have too much in their repositories yet but it looks promising. What gets me is the sheer speed and user friendliness. I know I'll end up ruining it with trying to make it run resource hungry but wonderful amarok but oh well. It can be fixed real quick - so glad I adopted Linux. I never imagined half of the things that I can do was possible when I was using Windows.

---

### Post by ke4nt on 2008-12-05
TinyCoreLinux is completely assembled from the sources available for download from 
[http://www.tinycorelinux.com/files/release/src/](http://www.tinycorelinux.com/files/release/src/) .

It is not based on any other "distro" although much of the core and
extensions have been compiled using sources found at various sites
such as kernel.org, LFS, etc.. and those sources can be found here:
[http://www.tinycorelinux.com/files/tce/src/](http://www.tinycorelinux.com/files/tce/src/)

It boots extremely fast, and entirely into ram.  The initrd IS the OS!

With the compiletc addon, it will recompile its own kernel,
as well as a host of other apps, with proper lib support 
also available for download in the extensions section.

Read the "Getting Started" guide for more info on the number of ways this
small and light OS can work and grow.
[http://www.tinycorelinux.com/getting_started.html](http://www.tinycorelinux.com/getting_started.html)

Best of all, it is designed from the ground up by Robert Shingledecker,
famous for his lead development in many other small light linux distros and linux development,
and a crew of developers and volunteers who are well known for their contributions in the linux community.

73 de ke4nt

---

### Post by kagashe on 2008-12-05
I tried it. Default Xvesa was giving funny colors on 1024x768 and working well on 640x480x16. Then I tried Xorg and it was not working (fatal xserver errors). I [posted on their forums]("http://tinycorelinux.com/forum/index.php?topic=131.0") and got prompt replies. Following modules were required to be loaded manually before startx:
> $ sudo modprobe agpgart
$ sudo modprobe intel-agp
$ sudo modprobe drm
$ startx

Xorg now works at 1024x768.

kagashe

---

### Post by chris4585 on 2008-12-05
I must try this....

---

### Post by kagashe on 2008-12-13
I have been using Tinycorelinux for more than a week now.

Initially I used .tce extensions then switched to .tcz extensions as they use less memory.

Firefox is available as minefield there. I added Flash Player 9 to Firefox.

I like to see Hindi fonts on web pages I added ttf-indic fonts to /home/tc/.fonts and it worked.

I compiled fbxkb the Keyboard_Indicator/Switcher for Tinycore.

kagashe

---

### Post by chris4585 on 2008-12-13
I've had tc installed on a hard drive on a old computer, but it started up as a LiveCD, not what I was expecting, anyway around this? like a normal install?

---

### Post by init1 on 2008-12-13
> **chris4585 said:**
> I've had tc installed on a hard drive on a old computer, but it started up as a LiveCD, not what I was expecting, anyway around this? like a normal install?
You'll need to extract the archive into a partition, and point Grub to the kernel. There's no installer, so you'll have to do it manually.

---

### Post by chris4585 on 2008-12-13
> **init1 said:**
> You'll need to extract the archive into a partition, and point Grub to the kernel. There's no installer, so you'll have to do it manually.

the part where I said I had it installed, this is what I meant

what I did:

used another livecd to create the partitions using cfdisk

then formatted them using mk.ext3

then installed grub from the same livecd

extracted the livecd's archive onto the hard drive

set grub like so:

```
title Tinycore
root (hd0,1)
kernel /bzImage root=/dev/hda1
initrd /tinycore.gz
boot
```

(probably where I went wrong)

without initrd /tinycore.gz I kept getting a kernel panic, cannot find init try passing init=

---

### Post by markp1989 on 2008-12-13
looks rather nice, if i could install the nvidia drivers, i would be happy to use this ever day

---

### Post by cardinals_fan on 2008-12-13
> **init1 said:**
> You'll need to extract the archive into a partition, and point Grub to the kernel. There's no installer, so you'll have to do it manually.
I'm still not sure if that constitutes a "real" install.  Wouldn't that just boot the live system from the hard drive instead of the CD?

---

### Post by markp1989 on 2008-12-13
> **cardinals_fan said:**
> I'm still not sure if that constitutes a "real" install.  Wouldn't that just boot the live system from the hard drive instead of the CD?

i tried it my self, and it seems to be a real install , i tried installing opera, then rebooting, and it was still installed

---

### Post by cardinals_fan on 2008-12-13
> **markp1989 said:**
> i tried it my self, and it seems to be a real install , i tried installing opera, then rebooting, and it was still installed
Interesting.

---

### Post by chris4585 on 2008-12-13
would someone explain what to do with grub to not get the livecd like effect from the hdd?

---

### Post by Sorivenul on 2008-12-13
> **chris4585 said:**
> would someone explain what to do with grub to not get the livecd like effect from the hdd?

Use init1's method from [here]("http://ubuntuforums.org/showpost.php?p=6303965&postcount=9"). Worked for me.

---

### Post by RJARRRPCGP on 2008-12-18
What's keeping me from SliTaz is there appears to be major problems with Nvidia 3D support, it looks like even when you compile them, 3D fails. 

Thus, the smallest distro I tried so far was TinyMe 2008.1. But the folks of TinyMe seem to need a scolding, for not including Firefox 3 and using Opera instead! 

Opera is *proprietary*! Unnecessary, because Firefox 3 does the job! 

Even worse, I couldn't get a version of Firefox higher than 3.0.0 or 3.0.1 with Synaptic!

I don't want to see anything other than the Nvidia driver and Flash for proprietary components!

---

### Post by john_spiral on 2009-02-09
> **RJARRRPCGP said:**
> What's keeping me from SliTaz is there appears to be major problems with Nvidia 3D support, it looks like even when you compile them, 3D fails. 

Thus, the smallest distro I tried so far was TinyMe 2008.1. But the folks of TinyMe seem to need a scolding, for not including Firefox 3 and using Opera instead! 

Opera is *proprietary*! Unnecessary, because Firefox 3 does the job! 

Even worse, I couldn't get a version of Firefox higher than 3.0.0 or 3.0.1 with Synaptic!

I don't want to see anything other than the Nvidia driver and Flash for proprietary components!

The sad fact is that proprietary Opera is faster than open Firefox. Check out an article in Linux format magazine that discussed various different browsers and their pros and cons.
 
If you need to get an old system running like a new beast try Opera.

---

