---
title: "Opinions please..."
date: 2006-08-21
forum: Other OS Talk
---

### Post by hizaguchi on 2006-08-21
I've spent the last month looking for the perfect distro for my new dual-core 64-bit laptop, and I've come to the conclusion that there isn't one and I'm going to have to make some sacrifices.  That's where I need some advice.  I can find distros that support each of my laptop's features, but none that does it all.

So my question to you is, what is most importat to you in a (laptop) distro?

64-bit?
Dual-core?
Suspend to ram?
Package management?
Overall performance?
Up-to-dateness?
XGL?


Right now it's looking like this for me:

Ubuntu has the best package management around, hands down, but 64-bit support is questionable and (for whatever reason) it won't suspend to ram when I'm using any (32 or 64 bit) SMP kernel.  Do I use this distro?  If so, do I sacrifice half my processing power, or do I sacrifice suspend to ram for extra speed?

Suse handles 64-bit and SMP perfectly, and suspends to ram without any troubles.  But the package management is TERRIBLE.  Things often break after an upgrade, and several packages I need are only in the "complete" repos, which take >10 minutes to refresh in Yast.  Downloads are also painfully slow.  The combined result is that I can actually upgrade a FreeBSD system (compiling with ports) as fast as I can Suse and with far less risk of problems.

Most other highly reccomended distros have their own other problems.  PClinuxOS boots but gives me just a blank screen, Dreamlinux freezes when I try to install, Sabayon is both slow and unstable on my system, and I can't think of any other's I've tried recently that are really worth mentioning.

What would you do?

---

### Post by Rumor on 2006-08-21
I'd give Arch Linux a whirl. [http://www.archlinux.org/](http://www.archlinux.org/)

The package manager, Pacman is every bit as good as apt.
The control you get over your system is tremendous.
The speed is unreal.

I don't have any experience with trying to put Arch on a 64-bit platform, so you will probably want to poke around the Arch forums for a bit.

---

### Post by xXx 0wn3d xXx on 2006-08-21
> **Rumor said:**
> I'd give Arch Linux a whirl. [http://www.archlinux.org/](http://www.archlinux.org/)

The package manager, Pacman is every bit as good as apt.
The control you get over your system is tremendous.
The speed is unreal.

I don't have any experience with trying to put Arch on a 64-bit platform, so you will probably want to poke around the Arch forums for a bit.

I will also recommend Archlinux. There is a 64 bit version of Arch but it is new and experimential. I would wait until trying it. I also have a 64 but processor and Arch (32 bit) works fine and is extreamly fast.

---

### Post by hizaguchi on 2006-08-21
Thanks guys, but I actually just wrote a review of Arch 64.  It is lacking some power management packages (and I can't get them to compile), so it doesn't suspend either.  Maybe 32-bit Arch though.  I just have a really hard time getting in the mood to do that much manual configuration.  I love the way Ubuntu sets everything up.

Installed Ubuntu again this morning and spent a while trying to get suspend to work.  Still no luck.  So I installed Suse again, upgraded everything, and Yast stopped working.  Now I'm sitting here trying to get a different package manager installed and thinking manual configuration isn't so bad.

edit: Went with Arch.  Swiped my Suse xorg.conf and spent a whole day reading the wiki and forums and setting things up, and now I have a fully functional desktop.  It suspends, it scales the processors, I got knetworkmanager working, and even Xgl runs!  As long as I never have to do all that again, I'm a happy camper. :)

---

### Post by richbarna on 2006-08-24
Here's a good place to keep an eye on 64bit progress :-
[http://www.start64.com/index.php?option=com_content&task=view&id=142&Itemid=1](http://www.start64.com/index.php?option=com_content&task=view&id=142&Itemid=1)

---

### Post by hizaguchi on 2006-08-24
Spiffy, thanks!  I didn't know there was a Kororaa 64.  Handy page.  Now I'll hide it from myself because classes start today and I don't need to be tempted to install a whole new distro. :)

---

### Post by hizaguchi on 2006-08-28
Turns out the powernow-k8 module needed for processor scaling loses control of one of the cores after suspending in Arch.  This prompted me to reinstall Kubuntu and spend a whole day trying to get suspend to work.  I failed.  Now I'm looking at Suse again because it's the only distro where I know everything will work.  But that's not much good if it breaks constantly.  Ahhh, the frustration!  I wish suspend wasn't so important.

---

