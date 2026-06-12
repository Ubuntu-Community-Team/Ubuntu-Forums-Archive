---
title: "What OS should I put on this 233 MHz ThinkPad?"
date: 2008-11-19
forum: Other OS Talk
---

### Post by metroidnemesis13 on 2008-11-19
I just got two 233 MHz with 32 MB and 64 MB of RAM.  One has a 1214 MB hard drive and the other one's hard drive is dead.  For the working one, what distro should I put on it (Windows 98 isn't an option)?  I would like a list of several distros.  I'm used to something like Ubuntu, but I need a smaller distro with a good support group that's updated frequently.  Just a list of what I could put on this comp, with your recommendations (greatest on top, least fav on bottom).  Thanks much!!  I look forward to getting this beast working!

---

### Post by nitehawk777 on 2008-11-19
I'm pretty sure everyone is going to recommend using Puppy Linux from the live CD,....(as well as DSL Linux,....Slitaz,...) etc. etc.

---

### Post by pgatrick on 2008-11-19
On something that old, I'd just go with [Damn Small Linux]("http://www.damnsmalllinux.org/")

It's only 50mb and I had it on an old presario with a 233mhz cyrix proc and 96mb of ram and it fairly flew.

---

### Post by K.Mandla on 2008-11-19
Bah. [Slitaz]("http://slitaz.org") is far superior to DSL, from my perspective. If you're not willing to use something like Arch or Crux, that is.

Of course, to each his own.

---

### Post by smoker on 2008-11-19
hmm, how much time do you have? take your pick:
[http://www.linuxlinks.com/Distributions/Mini_Distributions/](http://www.linuxlinks.com/Distributions/Mini_Distributions/)

if you want a quick choice for a full desktop, i would also recommend damn small linux.

---

### Post by Cracauer on 2008-11-19
It really doesn't matter much which OS.  

As long as you don't use  [list] 
[*] KDE, GNOME etc.  Use fvwm2 
[*] NVidia's binary drivers 
[*] Xorg-7.3 and up
[*] Firefox 
[/list]  

If there's acute RAM shortage even with just the kernel loaded then it might be worth checking out some Linux-2.4.x, NetBSD or OpenBSD, which all have much simpler kernels.

---

### Post by kerry_s on 2008-11-19
pull the ram from the bad laptop, put it in the good laptop and install DSL:
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)
iso:
[http://distro.ibiblio.org/pub/linux/distributions/damnsmall/current/dsl-4.4.10.iso](http://distro.ibiblio.org/pub/linux/distributions/damnsmall/current/dsl-4.4.10.iso)

or you could leave the ram in the bad disk 1 and run DSL from the cdrom.

i once had a laptop with a dead hd, but it had 256mb ram, i ran dsl in ram, with a 128mb flash drive as swap for almost a year, then the motherboard finally gave out.

---

### Post by snowpine on 2008-11-19
If you do try SliTaz, make sure to use the 'loram' flavor. The standard version recommends 128mb and the cooking version 160mb of ram. And try using links instead of firefox for browsing. DSL is another good one.

---

### Post by cardinals_fan on 2008-11-19
SliTaz loram.

---

### Post by zmjjmz on 2008-11-19
DeLi Linux.
I suppose you could also find a hard drive for the other one.

---

### Post by wolfen69 on 2008-11-19
a guess a poll would have been good here. :)  i vote for damn small!

---

### Post by RealG187 on 2008-11-21
I was reccomended the GTK Remix found here:
[http://ubuntuforums.org/showthread.php?t=575456&page=18](http://ubuntuforums.org/showthread.php?t=575456&page=18)

---

### Post by LinuxGuy1234 on 2008-11-25
Put FreeDOS on it. [http://www.freedos.org]("http://www.freedos")

---

### Post by RealG187 on 2008-11-25
> **LinuxGuy1234 said:**
> Put FreeDOS on it. [http://www.freedos.org]("http://www.freedos")
Is DOS even useful anymore except for managing files?

---

### Post by zmjjmz on 2008-11-25
> **RealG187 said:**
> Is DOS even useful anymore except for managing files?

Well it can do a lot, but a 233MHz Thinkpad is capable of far more.

I would run FreeDOS on my 486, not my PII.

---

### Post by djdarrin91 on 2008-11-25
I would say Puppy but DSL would perform better with those specs.

---

### Post by EV500B on 2008-11-26
Huh!? NetBSD with fluxbox.

---

### Post by Bungo Pony on 2008-11-27
For ANYTHING with less than 128M RAM, I would suggest Damn Small Linux.

---

### Post by glotz on 2008-11-27
[http://www.kolibrios.org/](http://www.kolibrios.org/) :)

---

### Post by notwen on 2008-11-27
No mention of [AntiX]("http://antix.mepis.org/") yet?  =]

---

### Post by metroidnemesis13 on 2008-11-27
What about... fluxbuntu?

---

### Post by zmjjmz on 2008-11-27
> **metroidnemesis13 said:**
> What about... fluxbuntu?

Just... no.
It won't be fun.

---

### Post by snowpine on 2008-11-28
> **metroidnemesis13 said:**
> What about... fluxbuntu?

Fluxbuntu, like anything in the Ubuntu family, is quite a bit "heavier" than DSL, Puppy, SliTaz, etc. I definitely would not recommend it in this instance. I've had some difficulties in the past installing it on 64mb of ram virtual machines.

---

### Post by metroidnemesis13 on 2008-11-28
Ok I just ordered a 64 MB stick so now it has 96 MB total.  It still can't install fluxbuntu?  Even with a large swap partition?  I mean if it can run Windows 98 I assume it would be able to at least install some sort of very low level Ubuntu.  How much ram/mhz does it require?  Xubuntu is 128ish and I assume fluxbuntu would be a lot smaller, otherwise who would bother to make it.

---

### Post by metroidnemesis13 on 2008-11-28
"What is Fluxbuntu?

    Fluxbuntu is an LPAE (Lightweight, Productive, Agile, Efficient) compliant distribution based on Ubuntu. We've chosen Ubuntu for reasons of compatibility, but strive to empower all the legacy machines left behind. 

Minimum Specs?

    Fluxbuntu uses 35-46mb of ram. If you have 64MB of ram we would definitely recommend having adequate swap space."

That was pulled from their Wiki.  

FAQ:

[http://wiki.fluxbuntu.org/index.php?title=FAQ](http://wiki.fluxbuntu.org/index.php?title=FAQ)

---

### Post by kk0sse54 on 2008-11-28
Edit: stupid me I forgot Arch is only available for i686 and x86_64. You could still try out a netinstall of Slackware, Puppy Linux, Slitaz, and I would recommend Fluxbuntu since I've enjoyed using it on some of my older machines

---

### Post by zmjjmz on 2008-11-28
> **metroidnemesis13 said:**
> "What is Fluxbuntu?

    Fluxbuntu is an LPAE (Lightweight, Productive, Agile, Efficient) compliant distribution based on Ubuntu. We've chosen Ubuntu for reasons of compatibility, but strive to empower all the legacy machines left behind. 

Minimum Specs?

    Fluxbuntu uses 35-46mb of ram. If you have 64MB of ram we would definitely recommend having adequate swap space."

That was pulled from their Wiki.  

FAQ:

[http://wiki.fluxbuntu.org/index.php?title=FAQ](http://wiki.fluxbuntu.org/index.php?title=FAQ)
It will run, but at 233MHz it will be painfully slow.
I ran Fluxbuntu at 400MHz with 160MB RAM, and it was usually too slow for normal use.

---

### Post by anticapitalista on 2008-11-28
With 96MB RAM and a 233 MHz processor, I would go for DSl, Puppy or SliTaz, or a net-install of whatever distro you are comfortable with ie Debian, Ubuntu, Slack, Arch... or maybe try antiX-base.

---

### Post by mikjp on 2008-11-29
Slackware

Greetings,

mikko

---

### Post by linuxguymarshall on 2008-11-29
A HAMMER!!! that thing is worth 25 cents at best. have at it

---

### Post by metroidnemesis13 on 2008-11-29
Very insane.  Hey, I'm poor, and I'm bored.  I have a Compaq 1.8 dual core but I figured I might be able to put fluxbuntu on one of these things and sell them on eBay.  People always pay way too much on there for trash.  Plus, I really don't like taking my expensive laptops and junk around public places where they are easily stolen, etc. and I figured if I had some ghetto piece of trash it would be less appealing, and at the same time attract attention (junky and chunky technology always gets more attention in my experience for whatever reason).  Maybe I'd even attempt a custom paint job.  But I refuse to use Windows 98.

---

### Post by maybeway36 on 2008-11-29
FeeeDOS could at least let you play some old games on there.

---

### Post by zmjjmz on 2008-11-29
> **metroidnemesis13 said:**
> Very insane.  Hey, I'm poor, and I'm bored.  I have a Compaq 1.8 dual core but I figured I might be able to put fluxbuntu on one of these things and sell them on eBay.  People always pay way too much on there for trash.  Plus, I really don't like taking my expensive laptops and junk around public places where they are easily stolen, etc. and I figured if I had some ghetto piece of trash it would be less appealing, and at the same time attract attention (junky and chunky technology always gets more attention in my experience for whatever reason).  Maybe I'd even attempt a custom paint job.  But I refuse to use Windows 98.

You'll really be just fine with DSL.

---

### Post by metroidnemesis13 on 2008-11-30
Yeah that's what I'm thinking.  I think I'm gonna try Puppy, DSL, and Fluxbuntu before I decide which one I want.

---

### Post by anticapitalista on 2008-11-30
If you're going to sell them, forget fluxbuntu. It will be too painful for the buyer.
Give the latest antiX-base a try and then install what you want.

---

### Post by init1 on 2008-12-01
> **maybeway36 said:**
> FeeeDOS could at least let you play some old games on there.
Yeah I put FreeDOS on my old laptop with similar specs. It's extremely fast and great for games.

---

### Post by zmjjmz on 2008-12-01
> **init1 said:**
> Yeah I put FreeDOS on my old laptop with similar specs. It's extremely fast and great for games.

But why bother with that when one could easily run DOSBox or DOSEmu?

---

### Post by handy on 2008-12-01
[***_IPCop_***]("http://www.ipcop.org/") with [***_Advanced Proxy_***]("http://www.advproxy.net/") add-on.

---

### Post by init1 on 2008-12-01
> **zmjjmz said:**
> But why bother with that when one could easily run DOSBox or DOSEmu?
Eh, FreeDOS boots much quicker than Linux, and it's faster than using DOSBox.

---

### Post by anticapitalista on 2008-12-02
In very early stages of development, but this looks very interesting.

[http://www.tinycorelinux.com/](http://www.tinycorelinux.com/)
> 
Tiny Core Linux is a very small (10 MB) minimal Linux Desktop. It is based on Linux 2.6 kernel, Busybox, Tiny X, Fltk, and Jwm. The core runs entirely in ram and boots very quickly.

It is not a complete desktop nor is all hardware completely supported. It represents only the core needed to boot into a very minimal X desktop typically with wired internet access.

The user has complete control over which applications and/or additional hardware to have supported, be it for a desktop, a nettop, an appliance, or server, selectable from our online repository. 

---

