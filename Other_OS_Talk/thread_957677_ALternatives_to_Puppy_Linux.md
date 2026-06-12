---
title: "ALternatives to Puppy Linux?"
date: 2008-10-24
forum: Other OS Talk
---

### Post by MasterNetra on 2008-10-24
Yea is there a Linux distro for beginners that have a celeron processor and only 192 mb of ram? I have a friend who never used linux before and thats the only pc he has and Xubuntu isn't exactly behaving off its live cd and Puppy Linux isn't quite as user friendly as one would like.

---

### Post by TeoBigusGeekus on 2008-10-24
Damn Small Linux!
[http://www.damnsmalllinux.org/]("http://www.damnsmalllinux.org/")

---

### Post by melojo on 2008-10-24
Dream Linux
[www.dreamlinux.com.br](www.dreamlinux.com.br)

---

### Post by gjoellee on 2008-10-24
SliTaz
[http://www.slitaz.org/en/](http://www.slitaz.org/en/)

(under 30mb)!!!

---

### Post by snowpine on 2008-10-24
SliTaz is great, no doubt about it!
Not sure I would call it "for beginners" though--what about Puppy does your friend find not user friendly?

---

### Post by MasterNetra on 2008-10-24
Could you also include how much ram these distro's run when idle?

---

### Post by snowpine on 2008-10-24
> **MasterNetra said:**
> Could you also include how much ram these distro's run when idle?

Those numbers vary considerably from computer to computer, so unless my computer is identical to your friend's...

But since you asked: The cooking version of SliTaz uses just over 80mb from the live CD and 30mb as a hard drive install, on my laptop with 256mb of ram. 160mb is the recommended minimum.

---

### Post by MasterNetra on 2008-10-24
What about Dreamlinux 3.5 RC4? What are its ram requirements?

---

### Post by bodhi.zazen on 2008-10-24
There is a nice listing here :

[http://ubuntuforums.org/showthread.php?t=575456](http://ubuntuforums.org/showthread.php?t=575456)

---

### Post by namegame on 2008-10-24
> **MasterNetra said:**
> What about Dreamlinux 3.5 RC4? What are its ram requirements?

I would imagine that Dreamlinux would consume quite a bit of RAM by default as it has the whole Mac OS appearance going for it.

---

### Post by MasterNetra on 2008-10-24
> **namegame said:**
> I would imagine that Dreamlinux would consume quite a bit of RAM by default as it has the whole Mac OS appearance going for it.

Well Macpup looks like it can pull it off with little ram usage?

Anyway i almost forgot, thanks everyone who is replying and yet to reply but do.

---

### Post by namegame on 2008-10-25
> **MasterNetra said:**
> Well Macpup looks like it can pull it off with little ram usage?


Oh, ok. I didn't even know Macpup existed. I might give it a try in a VM just to see what it is like.

---

### Post by cardinals_fan on 2008-10-26
SliTaz is my distro of choice for very old machines (or NetBSD, but that's not for "beginners").

---

### Post by Bungo Pony on 2008-10-26
For anything around 128M of RAM, I'd suggest TinyMe. It's based on PCLinuxOS, it's very easy to use, and it looks good too.

---

### Post by zmjjmz on 2008-10-27
What's the processor speed?
I don't recommend Dreamlinux by the way, it's far too heavy.
I would recommend using AntiX.

---

### Post by wolfen69 on 2008-10-27
> **namegame said:**
> **I would imagine that Dreamlinux would consume quite a bit of RAM **by default as it has the whole Mac OS appearance going for it.

not true. i had it running on 128mb and it wasn't bad. with 196, it should run decent. give it a shot.

---

### Post by dldev on 2008-11-07
> **namegame said:**
> I would imagine that Dreamlinux would consume quite a bit of RAM by default as it has the whole Mac OS appearance going for it.

Ouch! "I would imagine", seems to imply you haven't actually tried it. "I would imagine" is often typed at the beginning of a post which is often of no use at all.

What I would have done, as a Dreamlinux Developer and Forum Member, if I were in  your shoes, would be to use Google to find some information for your fellow Ubuntu user.

Ok, I have run Dreamlinux on a laptop with 64Mb and a 650 processor. Slow but acceptable. Many users have tried with 1 Gb processor and 128 Mb, still runs good.

I, however, would recomend 256Mb RAM and a minimum 1Gb processor to have a comfortable experience.

By the way, just so you know, a Mac theme does NOT affect desktop performance.;)

Here is the Hardware Profile of one of the Dreamlinux Forums Staff members and the Distros he is currently using (Ubuntu included).

[[COLOR="Blue"]Hardware profile of Resa[/COLOR]]("http://dreamlinuxforums.org/index.php/topic,846.msg5032.html#msg5032")

The Distros he runs (from his signature):
[color=red]Ubuntu Hardy 8.04[/color] | [color=blue]Xubuntu Intrepid 8.10[/color] | [color=red]Dreamlinux 3.5 RCx[/color] | [color=blue]Archlinux 2008.6[/color] | [color=red]OpenGEU 8.04[/color] | [color=blue]OzOs 0.5[/color]

Please test a distro before posting misinformation, also, do yourself a favour and buy Linux-compatible hardware. It makes the life of Linux developers so much easier ;)

dl-dev

---

### Post by ugm6hr on 2008-11-08
> **MasterNetra said:**
>  and Puppy Linux isn't quite as user friendly as one would like.

Really?  I haven't used it since it's 2.14 incarnation, but I found that it was very easy to use for simple tasks.

Only downside was running as root all the time.  And the single-click ROX file-manager took a bit of getting used to.

Anyway - if you're going to be supporting your friend, and you're an Ubuntu user, something like u-lite (currently undergoing name change - so website offline: [http://ubuntulite.tuxfamily.org/](http://ubuntulite.tuxfamily.org/)) might be sensible.  It is basically Hardy kernel with LXDE/OpenBox and some lightweight apps.

I haven't tried it, but PUD is also Ubuntu based LXDE distro (I found it is listed as the LXDE Live distro: [http://lxde.org/](http://lxde.org/) - more detail: [http://pud-linux.sourceforge.net/index.en.html](http://pud-linux.sourceforge.net/index.en.html))

EDIT: In fact, LXDE in the Intrepid repo is basically the latest version (except the Network Manager).  Perhaps a minimal install Ubuntu Intrepid+LXDE is an option too? [http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)
If you installed Xubuntu intrepid - why not just try "sudo aptitude install lxde lxnm" to try it out.  Just select LXDE in sessions on the login screen.
If you installed Hardy Xubuntu: [http://www.ubuntugeek.com/lxde-lightweight-x11-desktop-environment-for-ubuntu.html](http://www.ubuntugeek.com/lxde-lightweight-x11-desktop-environment-for-ubuntu.html) and "sudo aptitude install lxde lxnm" for the LX network manager to replace Gnome's NM.
If you install lxnm - you may lose your network connection though!

---

