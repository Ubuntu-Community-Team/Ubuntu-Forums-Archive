---
title: "difference between linux bases"
date: 2007-06-20
forum: Other OS Talk
---

### Post by maddot on 2007-06-20
There are a couple of "based of" linuxes on the scene. For example, ubuntu, is based of debian. Opensuse is based of the enterprise suse. Slackware, fedora, gentoo, bsd are some of them. One thing i know is that all of erm use the linux kernal. Which is a big duh...if not they wouldn't be called linux. Is there a particular difference between each and every one of them? Compatibility? Stabability? features?

If i did miss ou on other bases please do add. Forget bout M$...i only want to know bout the linux bases.

---

### Post by blah blah blah on 2007-06-20
All sorts of code really.

---

### Post by ThinkBuntu on 2007-06-20
Some bases off the top of my head:
[LIST]
[*]Debian
[*]SUSE
[*]Red Hat
[*]Mandriva
[*]Slackware
[*]Arch
[*]Gentoo
[*]rPath
[*]FreeBSD
[/LIST]
Those are the most important ones. It could be argued that SUSE and Mandriva are based on Red Hat because they use RPM (Redhat Package Management). Arch and rPath are the least used of all these. The main differences betwen various bases are low-level distro features and package management. Things like GNOME, KDE, etc. are able to run over any base, of course.

---

### Post by Bachstelze on 2007-06-20
BSD is *not* Linux !

---

### Post by ThinkBuntu on 2007-06-20
> **HymnToLife said:**
> BSD is *not* Linux !
I know that. But the two are very close. To the OP, FreeBSD is the base for most other BSD systems, which are Linux' Unix brothers.

---

### Post by maddot on 2007-06-20
There's openbsd, netbsd, and freebsd... but let's not argue on linux vs bsd...going back to the bases... are there any particular definitive diffrence between all of erm?

---

### Post by ThinkBuntu on 2007-06-20
> **maddot said:**
> There's openbsd, netbsd, and freebsd... but let's not argue on linux vs bsd...going back to the bases... are there any particular definitive diffrence between all of erm?
Arch and Slackware are supposed to be the fastest. Slackware and Debian are supposed to be the most stable. Arch is supposed to have the best packaging system, maybe tied with Conary, while Debian has the highest quality packages. But when I talk about that, I'm getting more into the OS fundamentals than the base.

Slackware has little package management support, but there are some features you can overlay such as slapt-get for package management. Zenwalk implements their own package management system over Slackware called netpkg, so you see, packaging could be considered part of the system base or can be built over it.

Gentoo is also very fast because the user compiles the entire thing from scratch, making it optimized for your machine, but it has a unique packaging system that requires you to compile its applications yourself to take advantage of the system's speed.

I know very little about the fundamentals of Redhat, SUSE, and Mandriva.

---

### Post by maddot on 2007-06-20
hmm.. 
packaging system as in like updates and "gets"? I thought that's all what it is. is that what all the bases or distros market on O.o? doesn't seem very "featuring". hmm..any other particular diffrences?

---

### Post by ThinkBuntu on 2007-06-20
> **maddot said:**
> hmm.. 
packaging system as in like updates and "gets"? I thought that's all what it is. is that what all the bases or distros market on O.o? doesn't seem very "featuring". hmm..any other particular diffrences?
Wish I could tell you more, because I know there are major, fundamental differences at this ground level. Don't listen to me!

---

### Post by blah blah blah on 2007-06-20
> **ThinkBuntu said:**
> I know that. But the two are very close. To the OP, FreeBSD is the base for most other BSD systems, which are Linux' Unix brothers.

They're really not close, just look at the code sometime, quite a lot of differences. FreeBSD is _not_ the base for most other BSD systems. There are more not based of it than based of it.

---

### Post by .aku on 2007-06-20
> **ThinkBuntu said:**
> 
It could be argued that SUSE and Mandriva are based on Red Hat because they use RPM (Redhat Package Management). 

RPM was originally developed by Red Hat, for *Red Hat Linux*.
Nowadays it's been forked and adopted to so many distros, that is was renamed from Redhat Package Manager, to RPM (**RPM Package Manager**). Recursive Initialism, u know, it's hip these days ;)..

Mandriva is not based on Red Hat, neither is Suse. 
Suse was originally only a translation of Slackware. Later they adopted stuff from Redhat (including /etc/sysconfig and RPM).

Mandriva RPMs differ from Red Hat and/or Suse RPMs.
The RedHat (Fedora) RPM is being developed by Fedora development team, while the other one used by Mandriva and PLD is being developed by one of the long-time RPM project maintainers.
Generally, IIRC, these aren't compatible with each other...

So, there's my arguments.. :)

//aku

---

### Post by ThinkBuntu on 2007-06-20
I recall reading once that SUSE was from Slackware back in 1993 or so. You're right.

---

### Post by Nikron on 2007-06-20
Also, initscripts are a big difference between distros.  Some are simple (Arch is super straight forward), some are a bit more complex like Ubuntu (I forgot what it was called, it does asynchronous startup though)

---

### Post by .aku on 2007-06-20
> **Nikron said:**
> Also, initscripts are a big difference between distros.  Some are simple (Arch is super straight forward), some are a bit more complex like Ubuntu (I forgot what it was called, it does asynchronous startup though)

Upstart ?

//aku

---

### Post by RAV TUX on 2007-06-21
> **ThinkBuntu said:**
> Some bases off the top of my head:
[LIST]
[*]Debian
[*]SUSE
[*]Red Hat
[*]Mandriva
[*]Slackware
[*]Arch
[*]Gentoo
[*]rPath
[*]FreeBSD
[/LIST]
Those are the most important ones. It could be argued that SUSE and Mandriva are based on Red Hat because they use RPM (Redhat Package Management). Arch and rPath are the least used of all these. The main differences betwen various bases are low-level distro features and package management. Things like GNOME, KDE, etc. are able to run over any base, of course.

> **ThinkBuntu said:**
> Arch and Slackware are supposed to be the fastest. Slackware and Debian are supposed to be the most stable. Arch is supposed to have the best packaging system, maybe tied with Conary, while Debian has the highest quality packages. But when I talk about that, I'm getting more into the OS fundamentals than the base.

Slackware has little package management support, but there are some features you can overlay such as slapt-get for package management. Zenwalk implements their own package management system over Slackware called netpkg, so you see, packaging could be considered part of the system base or can be built over it.

Gentoo is also very fast because the user compiles the entire thing from scratch, making it optimized for your machine, but it has a unique packaging system that requires you to compile its applications yourself to take advantage of the system's speed.

I know very little about the fundamentals of Redhat, SUSE, and Mandriva.

> **.aku said:**
> RPM was originally developed by Red Hat, for *Red Hat Linux*.
Nowadays it's been forked and adopted to so many distros, that is was renamed from Redhat Package Manager, to RPM (**RPM Package Manager**). Recursive Initialism, u know, it's hip these days ;)..

Mandriva is not based on Red Hat, neither is Suse. 
Suse was originally only a translation of Slackware. Later they adopted stuff from Redhat (including /etc/sysconfig and RPM).

Mandriva RPMs differ from Red Hat and/or Suse RPMs.
The RedHat (Fedora) RPM is being developed by Fedora development team, while the other one used by Mandriva and PLD is being developed by one of the long-time RPM project maintainers.
Generally, IIRC, these aren't compatible with each other...

So, there's my arguments.. :)

//aku

After using and testing over 500 distributions and every base that does exist, the most advanced is not the most popular...good thing.

The most advanced base is rPath, the most advanced Pakage Manager is Conary. This is why I choose to build Oz Enterprise and Linux Nirvana on an rPath/Conary base.

As far as the SUSE/RED HAT/Mandriva origin question see the distro timeline below:

(Note: rPath formally Specifix is based on Red Hat: from rPath comes Foresight and Oz)

---

### Post by RAV TUX on 2007-06-21
The BIG four Linux bases are technically:

1. Debian
2. SUSE
3. Red Hat
4. Slackware

and their derivatives.....

There are some great independents that are also out:

such as:

1. Yoper
2. Sorceror>Lunar
3. Gentoo>Sabayon
4. Puppy
5. CRUX>Arch
6. GoboLinux
7. dyne:bolic
8. Ark

---

