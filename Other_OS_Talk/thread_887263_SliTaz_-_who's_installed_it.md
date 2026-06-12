---
title: "SliTaz - who's installed it?"
date: 2008-08-12
forum: Other OS Talk
---

### Post by cardinals_fan on 2008-08-12
I've realized that Arch is not for me.  It's WAY too bleeding edge.  I'm thinking that I need a new distro.  OpenSolaris (which I'm running right now) is nice, but a bit resource-intensive for me.  I've used SliTaz as a live CD, and it seems like a nice option.  If anyone here has used SliTaz, I'd appreciate answers to the following:

* Does the SliTaz package manager work well?
* Is SliTaz as fast as one would expect from a micro-distro?
* **Can you change the user?**  In the first version of SliTaz, you either had to use root (a bad idea) or deal with the name of "Hacker".
* Anything you think I should know.

---

### Post by chris4585 on 2008-08-12
> **cardinals_fan said:**
> I've realized that Arch is not for me.  It's WAY too bleeding edge.  I'm thinking that I need a new distro.  OpenSolaris (which I'm running right now) is nice, but a bit resource-intensive for me.  I've used SliTaz as a live CD, and it seems like a nice option.  If anyone here has used SliTaz, I'd appreciate answers to the following:

* Does the SliTaz package manager work well?
* Is SliTaz as fast as one would expect from a micro-distro?
* **Can you change the user?**  In the first version of SliTaz, you either had to use root (a bad idea) or deal with the name of "Hacker".
* Anything you think I should know.

I have slitaz installed on my laptop it usually uses 50mbs at boot, and is micro small

The package manager works nice

You can change the user, you just have to do it the command line way, and just edit the slim.conf in /etc/ file if you want have your user on the slim greeter

---

### Post by mauud777 on 2008-08-12
believe me you will come back again to Arch

---

### Post by chris4585 on 2008-08-12
well, the only bad thing about slitaz is the fact it doesnt have too much software for it in its repo's, but other then that when you get the users made and everything it will fly

---

### Post by molom on 2008-08-12
Why not try Gentoo?

---

### Post by wolfen69 on 2008-08-12
> **molom said:**
> Why not try Gentoo?

i'd rather smash my head into a brick wall. 

if you're gonna do arch or gentoo, why not go all out and do Linux From Scratch? just remember to set aside a few months to get it working right. :rolleyes:

---

### Post by cardinals_fan on 2008-08-12
> **mauud777 said:**
> believe me you will come back again to Arch
Doubtful.  The bleeding edge-ness disturbed me.
> **molom said:**
> Why not try Gentoo?
I have tried Gentoo.  The compiling drove me mad.

At the moment, I'm not sure what to do.  SliTaz is an excellent distro, but I haven't gotten my printer working yet (hplip isn't in the repos) and I'm having trouble with the proprietary NVIDIA drivers.

What I need is a very lightweight yet stable distro.  Any ideas?

---

### Post by molom on 2008-08-12
> **wolfen69 said:**
> i'd rather smash my head into a brick wall. 


:lolflag::lolflag::lolflag::lolflag::lolflag:

---

### Post by molom on 2008-08-12
> **cardinals_fan said:**
> Doubtful. What I need is a very lightweight yet stable distro.  Any ideas?

Vector Linux (Light Edition), it will work really nicely and should suit you well, there also is a light version of GoblinX that has fluxbox.

---

### Post by cardinals_fan on 2008-08-12
> **molom said:**
> Vector Linux (Light Edition), it will work really nicely and should suit you well, there also is a light version of GoblinX that has fluxbox.
I'm a former Vector Light beta tester ;)

The package management annoyed me (I despise slapt-get).

SliTaz is really quite good.  I just need to fix my printer and graphics card...

---

### Post by Dr Small on 2008-08-12
> **mauud777 said:**
> believe me you will come back again to Arch
+1
The bleeding edge of Arch is your choice. You can either install by source of an older application, or install from pacman and have [Testing] disabled.

I really don't see why bleeding edge would scare you, as it rarely breaks or has problems.

---

### Post by cardinals_fan on 2008-08-12
> **Dr Small said:**
> +1
The bleeding edge of Arch is your choice. You can either install by source of an older application, or install from pacman and have [Testing] disabled.

I really don't see why bleeding edge would scare you, as it rarely breaks or has problems.
My last upgrade had pretty epic breakage :)

I'm just in the mood for something new...

---

### Post by init1 on 2008-08-12
Actually, I think SliTaz is best run from the CD or a USB drive. Since its all in RAM, apps load almost instantly. As for the user, the "cooking" version now uses "tux" rather than "hacker". They've also added some more apps to the repo.

---

### Post by cardinals_fan on 2008-08-12
> **init1 said:**
> Actually, I think SliTaz is best run from the CD or a USB drive. Since its all in RAM, apps load almost instantly. As for the user, the "cooking" version now uses "tux" rather than "hacker". They've also added some more apps to the repo.
SliTaz seems fast to me on the installed system.

Against my better judgement, I have Gentoo downloading in the background.  I'll install it tomorrow (if I don't regain my sanity first).

---

### Post by dmm1285 on 2008-08-12
Things I like:
Very fast boot times (<20 secs) and very responsive on a P3 with 128MB of RAM.

The OpenBox setup is very sleek. This is what I expected when I used Xubuntu. I could never go back to a full blown Gnome after using it.

The package management is nice as well, much nicer than DSL's in my opinion.

Things that I dislike:

Not enough packages. I don't blame the distro at all for this, it has a great amount of packages for a live CD distro. But for everyday use, I want more packages then are what offered.

Busybox. Again, I'm glad they use BusyBox when looking at it from a live CD perspective, but I really miss some of Bash's features (especially reverse lookup).

No tiling WMs! This is the biggest negative to me, and why I planning on throwing Arch on there when I get the time. Using the mouse to move around little xterms is doubly annoying when you are using a touchpad. If there was a tiling WM in the repository, I would probabaly keep using it.

All in all, I really do like Slitaz, and actually ran it for about a week straight in ram on my desktop, but I can't go back to managing my windows with a mouse.

Why do you find Arch to bleeding edge?

---

### Post by picpak on 2008-08-13
Have you tried TinyMe? I use it on my dad's old computer. There was some trouble with things like sound and internet, but it all works now and it *flies*. It's based off of PCLinuxOS and uses Openbox. I say give it a try :)

---

### Post by cardinals_fan on 2008-08-13
> **dmm1285 said:**
> Things I like:
Very fast boot times (<20 secs) and very responsive on a P3 with 128MB of RAM.

The OpenBox setup is very sleek. This is what I expected when I used Xubuntu. I could never go back to a full blown Gnome after using it.

The package management is nice as well, much nicer than DSL's in my opinion.

Things that I dislike:

Not enough packages. I don't blame the distro at all for this, it has a great amount of packages for a live CD distro. But for everyday use, I want more packages then are what offered.

Busybox. Again, I'm glad they use BusyBox when looking at it from a live CD perspective, but I really miss some of Bash's features (especially reverse lookup).

No tiling WMs! This is the biggest negative to me, and why I planning on throwing Arch on there when I get the time. Using the mouse to move around little xterms is doubly annoying when you are using a touchpad. If there was a tiling WM in the repository, I would probabaly keep using it.

All in all, I really do like Slitaz, and actually ran it for about a week straight in ram on my desktop, but I can't go back to managing my windows with a mouse.

Why do you find Arch to bleeding edge?
You could always install dwm - very few dependencies :)

I've used Slackware more thoroughly than any other distro, so I have very high expectations when it comes to stability.  I experience problems upgrading on Arch far too often for my liking.

I'm considering sticking with SliTaz.  If I can get my printer drivers set up, the graphics card isn't that important.

---

### Post by sujoy on 2008-08-13
well, why did ya leave slackware? its one of favourites :) I am using mini-slack aka zenwalk at the moment. netpkg has improved a lot since old times

---

### Post by cardinals_fan on 2008-08-13
> **sujoy said:**
> well, why did ya leave slackware? its one of favourites :) I am using mini-slack aka zenwalk at the moment. netpkg has improved a lot since old times
I've used just about every Slack derivative out there.  Zenwalk is nice, but it's getting pretty hefty (~500 MB for standard!).

I've remembered why I hate Gentoo.  While Pkgsrc and FreeBSD's Ports have always felt elegant and powerful to me, Portage feels polluted and abused.  Scratch this one!

I have an aversion to PCLinuxOS/derivatives, but I've heard enough good stuff about TinyMe that I'll consider trying it.

I'm going to tackle the printer drivers today.  If I get them working, SliTaz just might turn out OK.

---

### Post by cardinals_fan on 2008-08-13
I've hit a wall with the printing.  It's too bad, because I **really** like SliTaz as an installed distro.  Ah well :(

Despite its reputation for bugginess, I've always had good luck with Fedora.  I might go that route and just remove GNOME and OpenOffice...

EDIT: Fedora is burning as I write.  NetBSD is the only other OS I've ever used that affected me more than SliTaz has - I'm actually feeling genuine sadness as I leave.  This is disturbing...

---

### Post by cardinals_fan on 2008-08-13
Fedora was just too bloated.  I installed the light version of CrunchBang (an Ubuntu derivative).  I don't like it much, but I've kept it (after removing about half of the distro).  I can use SliTaz as my main OS and boot up CrunchBang when I need to print.  It's not a permanent solution, but it'll work for now.

---

