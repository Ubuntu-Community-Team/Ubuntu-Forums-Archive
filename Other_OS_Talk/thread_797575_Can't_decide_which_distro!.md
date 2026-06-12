---
title: "Can't decide which distro!"
date: 2008-05-17
forum: Other OS Talk
---

### Post by miggols99 on 2008-05-17
I've started distro hopping again...and I don't know which distro to go with! Here are my requirements:

[LIST]
[*]64 bit - I like to take advantage of my 64 bit processor...please don't give me "64 bit only lets you have more than 4 GB of RAM"...
[*]No Gnome
[*]Not source based - Compiling takes too long...
[*]Works well with laptops
[*]The following distros don't work for me: sidux, Zenwalk, PC-BSD. Sidux is waaay to much work to maintain, Zenwalk doesn't work well with my laptop and PC-BSD can't detect quite a few pieces of hardware...
[*]Works well out of the box
[*]Rolling release if possible (doesn't have to be)
[*]Doesn't include **any** Gnome. That includes Xubuntu. They seem to like to make it bloated by adding lots of Gnome stuff to it...(although just a few Gnome libs are fine, but I don't want big things like gnome-panel or something...)
[/LIST]

Any distros out there for me?

---

### Post by Half-Left on 2008-05-17
Linux Mint KDE edition [http://www.linuxmint.com/rel_daryna_kde.php](http://www.linuxmint.com/rel_daryna_kde.php)

Ugh sorry, it's not 64bit.

---

### Post by kerry_s on 2008-05-17
here's the list of x86 64
[http://distrowatch.com/search.php?category=Desktop&origin=All&basedon=All&desktop=KDE&architecture=x86_64&status=Active](http://distrowatch.com/search.php?category=Desktop&origin=All&basedon=All&desktop=KDE&architecture=x86_64&status=Active)

---

### Post by mintcoffee on 2008-05-17
I was going to suggest Arch Linux, but then I saw your username and realized you already use it.

Your requirements are quite specific and I don't think many of the mainstream distros will suit your needs. Arch / Gentoo and the like will probably suit you best. But, since you don't want source-based, then that leaves my only suggestion as... Arch.

---

### Post by cardinals_fan on 2008-05-17
How about Frugalware?  They have a x86_64 version, and since Pacman is used for package management, it should be familiar for an Arch user.

---

### Post by miggols99 on 2008-05-17
> **cardinals_fan said:**
> How about Frugalware?  They have a x86_64 version, and since Pacman is used for package management, it should be familiar for an Arch user.
Does it have a good, easy to use installer? And does it have a good networking program? When I tried PC-BSD, it made me use some horrible built-in (to KDE) program that didn't even show any interfaces! Not even the wired one!

---

### Post by NightwishFan on 2008-05-17
Try Ubuntu minimal with kde-core/icewm or Debian.

---

### Post by cardinals_fan on 2008-05-17
> **miggols99 said:**
> Does it have a good, easy to use installer? And does it have a good networking program? When I tried PC-BSD, it made me use some horrible built-in (to KDE) program that didn't even show any interfaces! Not even the wired one!
Read this: [http://frugalware.org/about](http://frugalware.org/about)

They have wifi-radar in the repos, so you should be able to download that before installing Frugalware, install it on the new Frugalware box, and use it.

---

### Post by p_quarles on 2008-05-17
Debian Testing. Just de-select "desktop environment" during the installation phase, and you will be able to choose your own X packages later on. 

What you want is really specialized, so the only things that will really meet the requirements are the ones you have to roll yourself. Discounting Gentoo, you're looking at Debian, Slackware and Arch. Of those, Debian will be the easiest to set up, in the sense that most if not all hardware will work with only minor configuration adjustments.

---

### Post by miggols99 on 2008-05-18
I have been thinking about Debian testing (please not stable...it's just too out of date for me) as it's rolling release and pretty fast. How is their KDE? It's modular, which is pretty nice. But the last time I tried it, I had a horrible problem with KDM not being able to change the theme. No matter what I did, it just stayed on the (ugly IMO) default Debian theme...and I like splashy :D I haven't been able to get a decent bootsplash for Arch, because of their initscripts killing Splashy/Fbsplash when shutting down, and also it shows loads of text before as well. Ubuntu/Debian show just a few lines :)

---

### Post by miggols99 on 2008-05-18
Well I have a few problems with Debian. I've got it running now with KDE, but some things aren't going too great for me.

[LIST]
[*]No subpixel hinting - I hate ugly fonts!
[*]Horrible apt frontend - KPackage is the most unintuitive program I have ever seen! Synaptic brings in way too many Gnome dependencies...
[/LIST]
Fortunately, I've been able to get my wireless working. Anyone know how to fix these issues?

---

### Post by Raccoon1400 on 2008-05-18
What do you have against gnome anyway?

I think arch would be best. What are you using now? Arch?

---

### Post by miggols99 on 2008-05-18
> **Raccoon1400 said:**
> What do you have against gnome anyway?

I think arch would be best. What are you using now? Arch?
I just like to keep my system "clean". Like if I have Gnome installed I don't like to install KDE apps because it makes it feel bloated. And the other way around.

Yes, I think I might start using Arch again. I've been using Ubuntu...been favouring easy distros recently.

---

### Post by p_quarles on 2008-05-18
> **miggols99 said:**
> Well I have a few problems with Debian. I've got it running now with KDE, but some things aren't going too great for me.

No subpixel hinting - I hate ugly fonts!
That can be fixed the same way you would in Ubuntu -- open KControl and set font hinting. 

> [Horrible apt frontend - KPackage is the most unintuitive program I have ever seen! Synaptic brings in way too many Gnome dependencies.
Adept? Aptitude? 

One thing that you cannot say about Debian is that it lacks packaged software. It has the largest repositories of any distro, after all.

---

### Post by init1 on 2008-05-18
> **miggols99 said:**
> I have been thinking about Debian testing (please not stable...it's just too out of date for me) as it's rolling release and pretty fast. How is their KDE? It's modular, which is pretty nice. But the last time I tried it, I had a horrible problem with KDM not being able to change the theme. No matter what I did, it just stayed on the (ugly IMO) default Debian theme...and I like splashy :D I haven't been able to get a decent bootsplash for Arch, because of their initscripts killing Splashy/Fbsplash when shutting down, and also it shows loads of text before as well. Ubuntu/Debian show just a few lines :)
Yeah stable is old, but it's...well...stable. Testing apps may be newer, but they won't always work correctly.

---

### Post by miggols99 on 2008-05-18
> **p_quarles said:**
> That can be fixed the same way you would in Ubuntu -- open KControl and set font hinting. 


Adept? Aptitude? 

One thing that you cannot say about Debian is that it lacks packaged software. It has the largest repositories of any distro, after all.
Adept isn't available in testing, only in stable. The subpixel hinting part of KControl is greyed out...

---

### Post by Raccoon1400 on 2008-05-19
> **miggols99 said:**
> I just like to keep my system "clean". Like if I have Gnome installed I don't like to install KDE apps because it makes it feel bloated. And the other way around.

Yes, I think I might start using Arch again. I've been using Ubuntu...been favouring easy distros recently.

In that case, kde sounds best. I find kde has better apps, like k3b. I prefer just installing them on gnome because I like gnome better.

---

### Post by Cap'n Skyler on 2008-05-20
try knoppix?
maybe try sabayon too.
search for live cd for the distros.there are a LOT of them out there

:popcorn:

---

### Post by NightwishFan on 2008-05-20
I do not mind kpackage if I need it since I use aptitude in the cli. At first I really did not like Debian since it was a hassle to get nvidia drivers. Once I did and I saw that my cpu was reported as "100% idle" I was hooked. Besides a little challenge is interesting, and standard kde is very fast.

---

### Post by chucky chuckaluck on 2008-05-20
i don't know how up to date this little distro picker is, but you might find it helpful - [http://www.zegeniestudios.net/ldc/](http://www.zegeniestudios.net/ldc/)

---

### Post by freduardo on 2008-05-20
The "problem" with being an Arch user **imho** is that, if/when you're in a distro-hopping mood, you'll have trouble finding something that's better.

(Maybe because there just isn't ? :D)

Like p_quarles already suggested; there's only Arch, Debian and Slackware that I can think of. So if Debian wasn't your cup of tee, maybe take a look at Slackware?

---

