---
title: "Minimal Clean Distro"
date: 2008-05-11
forum: Other OS Talk
---

### Post by DarkZyzx on 2008-05-11
I was wondering, what is the fastest, minimalistic, most beautiful, simple, relaxing, no-problem linux distro? I have tried so many distros; e17 distros are usually beautiful and relaxing but complicated and full of problems, xfce distros are usually simple and minimalistic, but not beautiful. Is there a distro out there that is all of the above. 
:popcorn:

---

### Post by LaRoza on 2008-05-11
> **DarkZyzx said:**
> I was wondering, what is the fastest, minimalistic, most beautiful, simple, relaxing, no-problem linux distro? I have tried so many distros; e17 distros are usually beautiful and relaxing but complicated and full of problems, xfce distros are usually simple and minimalistic, but not beautiful. Is there a distro out there that is all of the above. 
:popcorn:

Arch.

---

### Post by kerry_s on 2008-05-11
debian base install build up, make it what you want it to be.
[http://cdimage.debian.org/cdimage/lenny_di_beta1/i386/iso-cd/debian-testing-i386-businesscard.iso](http://cdimage.debian.org/cdimage/lenny_di_beta1/i386/iso-cd/debian-testing-i386-businesscard.iso)

do a base install, that means when it gets to package selection uncheck everything.

after it installs grub and ejects the cd, log in as root
install X:
apt-get install xorg

then you need to pick a window manager:
apt-get install your-wm

that's enough for the gui
type> exit
to get out of root
log in as your user
type> startx

just keep building from there, you can install synaptic to make it easier to browse through the packages and decide what else you want.

this is what i used after the base for this install->
apt-get install xorg synaptic jwm clex rungetty

---

### Post by cardinals_fan on 2008-05-11
Zenwalk.  Enough said.

---

### Post by DreamcastJack on 2008-05-11
PCLinuxOS MiniMe 2008

---

### Post by smoker on 2008-05-11
have a look at puppy: [http://www.puppylinux.com/](http://www.puppylinux.com/)

---

### Post by Rumor on 2008-05-11
> **LaRoza said:**
> Arch.

+1

[The Arch Way]("http://wiki.archlinux.org/index.php/The_Arch_Way") is to keep it simple.

---

### Post by Hallvor on 2008-05-11
1. Base install of Ubuntu and add just the things you need, or
2. install PCLinuxOS 2008 Minime and add just the things you need.

---

### Post by will1911a1 on 2008-05-11
> **LaRoza said:**
> Arch.

/thread. :D

---

### Post by pelle.k on 2008-05-11
> fastest, minimalistic, most beautiful, simple, relaxing, no-problem linux distro? 
I'm shooting myself in the foot by saying this (i enjoy arch linux), but seriously, a debian or ubuntu *base* (aka command line install) install is easily the most trouble free solution unless you're after the cutting edge packages. You said you were after something "relaxing, no problems", and that is simply not always true with the cutting edge nature of, say, arch linux. Not that is hasn't got it's upsides.

---

### Post by Dr Small on 2008-05-11
> **Rumor said:**
> +1

[The Arch Way]("http://wiki.archlinux.org/index.php/The_Arch_Way") is to keep it simple.
+2
Arch all the way :)

---

### Post by Barrucadu on 2008-05-11
Arch and Zenwalk are my favourite minimal distros.

---

### Post by smartboyathome on 2008-05-11
I would say Arch if you want the most up to date, Debian minimal if you want ultra stable, or Ubuntu minimal LTS with backports enabled if you want a little of both.

---

### Post by sujoy on 2008-05-11
ArchLinux.



you still haven't installed it?!!!!

---

### Post by regomodo on 2008-05-11
Sabayon

---

### Post by MONODA on 2008-05-11
first of all, sabayon is everything but simple, second:
> Arch.
i think he is going to end up downloading arch, installing it and then booting up only to be very very surprised ;)

---

### Post by wolfen69 on 2008-05-11
> **DreamcastJack said:**
> PCLinuxOS MiniMe 2008

or its cousin, Tinyflux.

---

### Post by LaRoza on 2008-05-11
> **MONODA said:**
> 
i think he is going to end up downloading arch, installing it and then booting up only to be very very surprised ;)

It will soon pass.

---

### Post by chris4585 on 2008-05-11
Possibly crunchbang, the uses Openbox, but everything else is still ubuntu, so i guess it isn't that small, but it is still nice

---

### Post by wolfen69 on 2008-05-12
i dont know if puppy  could be considered minimal, but it is extremely lightweight and fast.

---

### Post by sujoy on 2008-05-12
> **MONODA said:**
> first of all, sabayon is everything but simple, second:

i think he is going to end up downloading arch, installing it and then booting up only to be very very surprised ;)

yes surprised and then go on to use till eternity :)

---

### Post by marquee moon on 2008-05-12
> **cardinals_fan said:**
> Zenwalk.  Enough said.

[QUOTE=DreamcastJack] PCLinuxOS MiniMe 2008 [/QUOTE]

I like both of these, but would say that Vector Linux is better than both (at least on my hardware). 

Vector is very small, very light, and has a really beautiful feel to it. I love the way I can personlise my desktop really easily. I find myself using in preference to ubuntu much of the time now. The installation proccess is a little tricky in parts buty at least its been scripted by someone with a sense of humour!

---

