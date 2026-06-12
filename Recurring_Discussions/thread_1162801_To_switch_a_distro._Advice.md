---
title: "To switch a distro. Advice?"
date: 2009-05-18
forum: Recurring Discussions
---

### Post by monsterstack on 2009-05-18
I think it's time to Nuke this partition. I want to upgrade to something that makes the most out of my hardware (nothing super duper flashy: bog-standard 64 dualcore AMD + nVidia graphics). I want the benefits that a 64-bit OS with ext4 can bring. But my mind is torn: do I stick with the ease of Ubuntu, or shall I go with Debian? I used Etch for a long time, and I'm no stranger to getting down and dirty with the terminal if I have to. What I did enjoy was the rock-solid stability it brought; even the testing branch never gave me any problems. It also ran quite a bit faster than Jaunty does for me now. Perhaps I should go with something sourcey, like Gentoo, which was terribly fast when I gave it a go a couple of years back. I just don't know!

What would you recommend?

---

### Post by Tipped OuT on 2009-05-18
Can't really say, it's whatever you prefer, I would say Ubuntu, but that's just because I prefer it. :)

---

### Post by kerry_s on 2009-05-18
have you done arch linux yet? you build it from the base up so it's pretty fast from the get go. i use it on my 450mhz 256mb ram laptop.

debian testing is also nice, i run it on my desktop. i did a base expert install + xfce4 and i must say it's pretty nice, gives me no problems, but then again it's only a few days old.

here's the amd64 net installer if you want to give debian a go: [http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/amd64/iso-cd/](http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/amd64/iso-cd/)

i recommend trying debian first, maybe even try a custom install from the base up.
if it don't float your boat, then give arch a go, it's a lot of hands on, but the build is optimized to your needs from the start.

to me there both about the same level, both are very good options.

---

### Post by gnomeuser on 2009-05-18
It depends on what your interest area is.

On the top of my head I would recommend Foresight (mixes binary packages but also gives the option to compile - all managed but the awesome conary package manager). Fedora is good as well. On the pure source side of things I have to say that Exherbo looks to have the most interesting ideas, I am especially fond of the idea of making the package manager, init system and user handling more or less the same fluid concept ([Exherbo lead developer talks about the distribution at FOSDEM 2009](http://mirrors.dotsrc.org/fosdem/2009/maintracks/exherbo.xvid.avi))

---

### Post by monsterstack on 2009-05-18
> **kerry_s said:**
> have you done arch linux yet? you build it from the base up so it's pretty fast from the get go. i use it on my 450mhz 256mb ram laptop.

debian testing is also nice, i run it on my desktop. i did a base expert install + xfce4 and i must say it's pretty nice, gives me no problems, but then again it's only a few days old.

here's the amd64 net installer if you want to give debian a go: [http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/amd64/iso-cd/](http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/amd64/iso-cd/)

i recommend trying debian first, maybe even try a custom install from the base up.
if it don't float your boat, then give arch a go, it's a lot of hands on, but the build is optimized to your needs from the start.

to me there both about the same level, both are very good options.

Never considered using Arch. The thought of building up a distro from scratch *does* sound intriguing. A minimal Debian install would also be good for this, I guess.

---

### Post by monsterstack on 2009-05-18
> **gnomeuser said:**
> It depends on what your interest area is.

On the top of my head I would recommend Foresight (mixes binary packages but also gives the option to compile - all managed but the awesome conary package manager). Fedora is good as well. On the pure source side of things I have to say that Exherbo looks to have the most interesting ideas, I am especially fond of the idea of making the package manager, init system and user handling more or less the same fluid concept ([Exherbo lead developer talks about the distribution at FOSDEM 2009](http://mirrors.dotsrc.org/fosdem/2009/maintracks/exherbo.xvid.avi))

Foresight looks pretty interesting. I think it's time to fire up some downloads and get virtualbox toasting. I have been meaning to look at Fedora for a while now. When I was at sea, we used to get weather facsimiles sent to us: I noticed that quite a few of those weather stations used Fedora for their calculations and image-mapping. Must be pretty sturdy stuff for such an important deployment.

---

### Post by gnomeuser on 2009-05-18
> **monsterstack said:**
> Foresight looks pretty interesting. I think it's time to fire up some downloads and get virtualbox toasting. I have been meaning to look at Fedora for a while now. When I was at sea, we used to get weather facsimiles sent to us: I noticed that quite a few of those weather stations used Fedora for their calculations and image-mapping. Must be pretty sturdy stuff for such an important deployment.

Fedora has good stability and they fix bugs. I would probably not run a production server on it just because I would be upgrading it every 12 months at least to keep on supported software. 

The thing to keep an eye on is though that Fedora tends to ship a bad release every once in a while, Fedora 9 was bad but 10 is good and 11 which will be out in 9 days looks positively amazing.

A good Fedora additional resource is rpmfusion.org for your codec needs and such. and please do file bugs, Fedora developers for the most part actually will work very hard for free to fix them for you.

Foresight really is very interesting, but it lacks developers unfortunately. I really do have a man crush on it.

---

### Post by RSingh on 2009-05-18
well I tried Arch sometime back. It does feel good setting up the system according to your own liking from scratch. I also found the package manager "pacman" to be the fastest i have ever used.
Overall it was a unique experience.

Arch has pretty good 64 bit support and is pretty fast.

---

### Post by monsterstack on 2009-05-18
Thanks for the ideas chaps. I think I'm going to play around with a couple of partitions, starting with Arch and Debian, and then nuke the one I don't like so much and try out Fedora. Might just try Foresight too.

---

