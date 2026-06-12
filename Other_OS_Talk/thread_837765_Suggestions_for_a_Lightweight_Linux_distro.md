---
title: "Suggestions for a Lightweight Linux distro?"
date: 2008-06-22
forum: Other OS Talk
---

### Post by DeadSuperHero on 2008-06-22
My mom gave me this *extremely* old laptop designed to run Windows 95/98. Booting Puppy Linux on it can be a chore.
I've seen some lightweight distros out there, but I'm looking for a command-line based distro with APT support. What distro would work best for me?

---

### Post by wh0rd on 2008-06-22
I would give [Fluxbuntu]("http://fluxbuntu.org/js.html") a try.

---

### Post by kerry_s on 2008-06-22
sounds like all you need is debian base.
[http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso)

when it gets to package selection uncheck everything, that gives you just the base.

what are the specs?
there's also dsl, built for the old & slow->
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

i use a 450mhz 256mb ram laptop, i use a custom etch/lenny install built from the debian base up. i've set it up to be as low resource as possible.

---

### Post by angryfirelord on 2008-06-22
DSL claims to boot from a 486 with 16mb RAM, but that's in text mode. If you want some speed and Puppy is slowly chugging along, you'll want to stay with the 2.4 kernel, which DSL has.

---

### Post by MONODA on 2008-06-23
You should check out arch linux, it is really fast but takes some time to set up. If you want something even faster, try CRUX. There is also syllable which isnt linux but is very fast:
[http://web.syllable.org/pages/index.html](http://web.syllable.org/pages/index.html)

---

### Post by zmjjmz on 2008-06-23
Try DSL.
You have to enable apt-get btw, doesn't work from the start.

---

### Post by smartboyathome on 2008-06-23
Another one: Slitaz. It is smaller than DSL, but from what I hear it holds the same amout of power (have to check it out).

---

### Post by zmjjmz on 2008-06-23
Slitaz is just compressed more. It really isn't good for that.

---

### Post by angryfirelord on 2008-06-23
> **zmjjmz said:**
> Try DSL.
You have to enable apt-get btw, doesn't work from the start.
I've had problems with apt-get on DSL because some of the packages are old and updating it can break things. DSL has its own special repository called MyDSL.

[http://www.damnsmalllinux.org/wiki/index.php/Installing_MyDSL_Extensions]("http://www.damnsmalllinux.org/wiki/index.php/Installing_MyDSL_Extensions")

---

### Post by tel93 on 2008-06-23
> **kerry_s said:**
> sounds like all you need is debian base.
[http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso)


I like the way you think :)

Anyway once etch is installed try dist-upgrading. You get the etch kernel with lenny software :)

---

### Post by mikjp on 2008-06-24
Without knowing the exact specifications I would suggest Debian, or maybe some BSD. I myself have used a P100 laptop with 40 MB RAM to run Debian 3.1 (with X windows) and Slackware 11.0 (console only).

The most important question is: what do you want to do with that old computer? 

You might check out my new blog [posting](http://lightlinux.blogspot.com/2008/06/top-10-of-lightweight-linux_24.html) on the top 10 lightweight distros.

Mikko
[http://lightlinux.blogspot.com/](http://lightlinux.blogspot.com/)

---

