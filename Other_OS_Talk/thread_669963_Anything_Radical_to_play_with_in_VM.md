---
title: "Anything Radical to play with in VM?"
date: 2008-01-16
forum: Other OS Talk
---

### Post by Wiebelhaus on 2008-01-16
Is there a radical distro out there to play with that you know of? I'm looking for something really left field.

I'm bored with EyeOS & ReactOS

---

### Post by saulgoode on 2008-01-16
Have you tried out [OLPC's Sugar]("http://wiki.laptop.org/go/Emulating_the_XO")?

---

### Post by Wiebelhaus on 2008-01-16
> **saulgoode said:**
> Have you tried out [OLPC's Sugar]("http://wiki.laptop.org/go/Emulating_the_XO")?

HA! I have not , thanks for the suggestion mate.

---

### Post by Darkhack on 2008-01-16
[SymphonyOS]("http://www.symphonyos.com/") uses the Mezzo desktop environment, which might be interesting to look at.  You could also try building your own with [Linux From Scratch]("http://www.linuxfromscratch.org/") which is a good educational opportunity to learn how the internals of a Linux distro work.  There is also [Nexenta]("http://www.nexenta.org/os") which uses the [OpenSolaris]("http://opensolaris.org/os/") (another option) kernel with a GNU userland and Debian tools like APT.  Think of it like the Ubuntu of OpenSolaris.  And of course a variety of [choices for BSD]("http://en.wikipedia.org/wiki/Comparison_of_BSD_operating_systems") based operating systems.  [Minix]("http://www.minix3.org/") is also very interesting.  It's the OS that LInus Torvalds used while he was developing Linux.  It's a free UNIX-like OS, but it is a [microkernel]("http://en.wikipedia.org/wiki/Microkernel") where as LInux is [monolithic]("http://en.wikipedia.org/wiki/Monolithic_kernel").  [Syllable]("http://web.syllable.org/pages/about.html") is a non-UNIX OS which has made great progress.  [FreeDOS]("http://www.freedos.org/") is a MS-DOS type operating system which (I believe) has binary compatibility.  Bell Labs, the creators of the original UNIX, also have a project called [Plan 9]("http://plan9.bell-labs.com/plan9/") to improve upon UNIX and make an even better system.

---

### Post by Wiebelhaus on 2008-01-16
> **Darkhack said:**
> [SymphonyOS]("http://www.symphonyos.com/") uses the Mezzo desktop environment, which might be interesting to look at.  You could also try building your own with [Linux From Scratch]("http://www.linuxfromscratch.org/") which is a good educational opportunity to learn how the internals of a Linux distro work.  There is also [Nexenta]("http://www.nexenta.org/os") which uses the [OpenSolaris]("http://opensolaris.org/os/") (another option) kernel with a GNU userland and Debian tools like APT.  Think of it like the Ubuntu of OpenSolaris.  And of course a variety of [choices for BSD]("http://en.wikipedia.org/wiki/Comparison_of_BSD_operating_systems") based operating systems.  [Minix]("http://www.minix3.org/") is also very interesting.  It's the OS that LInus Torvalds used while he was developing Linux.  It's a free UNIX-like OS, but it is a [microkernel]("http://en.wikipedia.org/wiki/Microkernel") where as LInux is [monolithic]("http://en.wikipedia.org/wiki/Monolithic_kernel").  [Syllable]("http://web.syllable.org/pages/about.html") is a non-UNIX OS which has made great progress.  [FreeDOS]("http://www.freedos.org/") is a MS-DOS type operating system which (I believe) has binary compatibility.  Bell Labs, the creators of the original UNIX, also have a project called [Plan 9]("http://plan9.bell-labs.com/plan9/") to improve upon UNIX and make an even better system.

Nice post man! I've a few of my own doing specific jobs but you've given me lots of stuff to play with thanks!.

EDIT: ohh now I see why you linked Linux from scratch , how did I ever miss that site? zomg thanks.

---

### Post by jinx099 on 2008-01-19
How about Sun's Project Indiana?  [http://opensolaris.org/os/project/indiana/](http://opensolaris.org/os/project/indiana/)

It is Sun's openSolaris "distro" that is supposed to be much more userfriendly than Solaris and openSolaris.  It has a package manager somewhat like apt and uses ZFS for the root filesystem.  Really interesting OS, I have my eye on it for sure.  Still in development, but very interesting.

---

### Post by 3rdalbum on 2008-01-19
Syllable is interesting to play with, as is Haiku (a binary-compatible BeOS clone for Intel x86 machines). I think there's a bit of friendly rivalry between the two communities even though they're not really in competition. So try them both and have your say!

---

### Post by mips on 2008-01-19
OpenVMS would be cool but you cannot run it in a VM though. You can run it in an emulator though using [SIMH]("http://simh.trailing-edge.com/")

Pretty hardcore OS if you ask me.

---

### Post by init1 on 2008-01-19
I would recommend [Solar OS]("http://www.oby.ro/os/os_main.htm")

---

### Post by madmetal on 2008-02-06
> **sx66gns said:**
> Nice post man! I've a few of my own doing specific jobs but you've given me lots of stuff to play with thanks!.

EDIT: ohh now I see why you linked Linux from scratch , how did I ever miss that site? zomg thanks.

instead of minix try minix3 really interesting to pass some time..

---

### Post by D-EJ915 on 2008-02-07
> **mips said:**
> OpenVMS would be cool but you cannot run it in a VM though. You can run it in an emulator though using [SIMH]("http://simh.trailing-edge.com/")

Pretty hardcore OS if you ask me.
VMS is pretty cool, definitely not what most people are used to.

> **jinx099 said:**
> How about Sun's Project Indiana?  [http://opensolaris.org/os/project/indiana/](http://opensolaris.org/os/project/indiana/)

It is Sun's openSolaris "distro" that is supposed to be much more userfriendly than Solaris and openSolaris.  It has a package manager somewhat like apt and uses ZFS for the root filesystem.  Really interesting OS, I have my eye on it for sure.  Still in development, but very interesting.The Indiana live-cd preview is pretty limited right now, I wouldn't really waste a CD burning it right now, SXCE would be much better to download albeit huge.

---

### Post by samwyse on 2008-02-07
[http://en.wikipedia.org/wiki/AROS_Research_Operating_System](http://en.wikipedia.org/wiki/AROS_Research_Operating_System)

"a free software/open source implementation of the AmigaOS 3.1 APIs". I've played it with a live cd earlier. It doesn't seem to work with Virtualbox. Works in other VM's I guess.

---

