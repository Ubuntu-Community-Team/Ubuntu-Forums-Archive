---
title: "Linux From Scratch"
date: 2007-01-10
forum: Other OS Talk
---

### Post by jd65pl on 2007-01-10
Has anyone had a go at the Linux From Scratch project? I'm going to give it a go and was wondering about other peoples experiences and time scales for achieving a working system.

I think it will be a good learning curve and hopefully provide me with a system that is perfect for my needs.

J

---

### Post by Lord Illidan on 2007-01-10
> **jd65pl said:**
> Has anyone had a go at the Linux From Scratch project? I'm going to give it a go and was wondering about other peoples experiences and time scales for achieving a working system.

I think it will be a good learning curve and hopefully provide me with a system that is perfect for my needs.

J

If I were you, I'd try Arch Linux, Slackware, or Gentoo Linux first.

---

### Post by G Morgan on 2007-01-10
I intend having a go after my CS exams this month.

The way I figure it I will try it in a VM. You have to have an initial install to bootstrap the process by allowing you to compile your kernel and such. How much experience do you have with ./configure, make, make install since its all source. Not to mention that you'll have to edit the init scripts etc. It's all documented though.

You could probably achieve a system that does exactly what you want using Slack, Gentoo or even a Debian based system, LFS seems to really be a learning exercise or for making a new distro that has a particular quality or method.

---

### Post by reza81 on 2007-01-10
I remember making a firewall with it wich ran on a floppydisk ( PII 233 or somthing with 32 MB RAM & 120MB HD ) about 4 or 5 years ago.

I followed the manual instructions to install & it worked great! after 2 weeks there whas a storm goingon and my litle system burned out. (thunder)

---

### Post by jd65pl on 2007-01-10
I have used various other distros, the main benefit would be the knowledge gained from the process. 

I don't think I'm going to be going into the blind I have a few yrs of C programming experience. I hope I know how to compile from source! I have read up on the process and feel I can undertake it.

I am aware there are other ways of achieving a custom built OS and have indeed been using a custom configured debian based system for my file server (which was a bugger on a p2 333mhz with 64mb ram)

I would like to hear from anyone what has tried to work through the documentation and their experiences or has built a linux based system from scratch. As helpful as suggestions to use an existing are, they miss the point of learning more about the underlying operations of the kernel.

Thanks

J

---

### Post by meng on 2007-01-10
My personal experience (and I don't pretend to speak for anyone else in this forum):
LFS: building this was just too slow!
Gentoo: not as bad as LFS, but again just too slow to get this going!

---

### Post by po0f on 2007-01-10
[quote=meng]My personal experience (and I don't pretend to speak for anyone else in this forum):
LFS: building this was just too slow!
Gentoo: not as bad as LFS, but again just too slow to get this going![/quote]

Yeah, I can see how it would be slow for you, but I'm running a quad-core 10GHz Pentium 6 with 32 gigs of RAM.  I go from a stage1 to a full-blown KDE install in 10 minutes flat.  :)
</sarcasm>

---

### Post by meng on 2007-01-10
> **po0f said:**
> Yeah, I can see how it would be slow for you, but I'm running a quad-core 10GHz Pentium 6 with 32 gigs of RAM.  I go from a stage1 to a full-blown KDE install in 10 minutes flat.  :)
</sarcasm>
Don't stand too close to that machine, it probably emits enough radiation to make you sterile in 30 minutes or less! :p

---

### Post by G Morgan on 2007-01-10
> **po0f said:**
> Yeah, I can see how it would be slow for you, but I'm running a quad-core 10GHz Pentium 6 with 32 gigs of RAM.  I go from a stage1 to a full-blown KDE install in 10 minutes flat.  :)
</sarcasm>

Do you use the -omg-optimised flag on this machine or are you just content with the boring stable -funroll-every-loop.

Personally I'm not content unless I'm running at least 50 optimisation flags.

---

### Post by Lord Illidan on 2007-01-10
> **po0f said:**
> Yeah, I can see how it would be slow for you, but I'm running a quad-core 10GHz Pentium 6 with 32 gigs of RAM.  I go from a stage1 to a full-blown KDE install in 10 minutes flat.  :)
</sarcasm>

pah...I prefer IBM's newest supercomputer. Open office takes 10 seconds to load on it!!

---

### Post by meng on 2007-01-10
Well, if you're not specifying useflags, what's the point? Just go with Ubuntu if you're going to be boring!

---

### Post by insane_alien on 2007-01-10
> pah...I prefer IBM's newest supercomputer. Open office takes 10 seconds to load on it!!

it takes you 10 sec to open open office? i've got it down to 1.325 seconds.

and on a 1.5GHz celeron M with 512MB

 i spent 6 hours tweaking it to do that though.

---

### Post by meng on 2007-01-10
> **insane_alien said:**
>  i spent 6 hours tweaking it to do that though.
6 hours of tweaking ... let's assume that it saved you 20 seconds per opening. That's 1080 times you'll have to use OpenOffice just to get that time back. :)

---

### Post by G Morgan on 2007-01-10
> **meng said:**
> Well, if you're not specifying useflags, what's the point? Just go with Ubuntu if you're going to be boring!

Well naturally I compile with as few use flags as possible to keep the system clean for example.

USE="-X" emerge =openoffice-3.0-a1

I pull in the lastest test version for the optimised exhaust pipes they use for IPC and naturally I never print capital X's not having any friends who's names begin with X so I see no reason for X to take up space on my HDD.

---

### Post by RAV TUX on 2007-01-10
moving to "Other OS" forum

---

### Post by g2g591 on 2007-09-16
I think now I'll have a crack at building it, too bad I only have 128k dsl (free upgrade from dialup) Anyone built this then build kde into it?

---

### Post by ryno519 on 2007-09-16
When I did it it took me a few days to get everythig installed and configured correctly, including gnome, my sound drivers, applications, etc. It's fairly time consuming. Unless you really want to learn what goes into a GNU/Linux build I'd try out Gentoo. :)

I've been thinking about creating a new LFS system for my new PC, but I haven't had the time lately. I'm definately going to get around to it some day. It feels good putting togethor an entire operating system from source like that and knowing just where everything is. I also found it a little easier to fix problems knowing which programs did what after I finished the installation. :)

---

### Post by g2g591 on 2007-09-16
I did run into an unpleasant snag with LFS, i think I will try geentoo (darn why do I keep mispelling it, gentoo, gentoo, gentoo)

---

### Post by rsambuca on 2007-09-17
> **insane_alien said:**
> it takes you 10 sec to open open office? i've got it down to 1.325 seconds.

and on a 1.5GHz celeron M with 512MB

 i spent 6 hours tweaking it to do that though.

Gotta love spending 6 hours to save 8.675 seconds!

---

### Post by jaybombalous on 2007-11-08
> **g2g591 said:**
> I did run into an unpleasant snag with LFS, i think I will try geentoo (darn why do I keep mispelling it, gentoo, gentoo, gentoo)

what snag did you run into? I made it to the make bootstrap for the gcc 4.12 compiler but then things went to ****. Something about it doesn't get the file type of libc.so.6????

Anyone else on here get this working, liveCD or not?

---

### Post by matthewschwimmer on 2008-02-09
How is gentoo?  too much of a n00b to even begin to understand LFS. I tried, and the only thing i knew how to do was "startx":(   (gimme a break, i barely started ubuntu)

I want to understand linux, so is gentoo a good starting block?

---

### Post by jd65pl on 2008-02-10
I think you should try to work out how to do stuff in a distro like ubuntu before moving on to the likes o gentoo.

Try Arch linux if you have the urge to progess

---

### Post by matthewschwimmer on 2008-02-10
ok, thanks. I have dual booted slackware and ubuntu on my computer, but if it gets too difficult, Ill replace slackware with arch.

---

### Post by Kopachris on 2008-12-23
What happened to discussing LFS?  Anyway, I tried LFS using Ubuntu 7.10 as a host a year ago.  It gave an error saying that there weren't enough PTYs and to contact a system administrator to make more.  I never figured out how to make more PTYs short of recompiling the kernel, which I tried.  After I recompiled the kernel, neither kernel would boot.  Has anyone figured out how to make more PTYs?

EDIT:  I finally found out how here: [http://www.linuxfromscratch.org/lfs/faq.html#no-ptys](http://www.linuxfromscratch.org/lfs/faq.html#no-ptys)
I'm going to start working on LFS again.  I hope it works!

---

### Post by gjoellee on 2008-12-24
Hey! Did you know that Arch Linux was made from Linux From Scratch?

---

### Post by mohitchawla on 2008-12-24
LFS is really cool. I suggest using their live cd as the host, it can make things really simple.

---

### Post by hardyn on 2008-12-24
It OOo really that slow?  its not something i have ever noticed; or is it that simply does not have a preloader and does not have 50mb of program memory resident at all times?



> **rsambuca said:**
> Gotta love spending 6 hours to save 8.675 seconds!

---

### Post by smartboyathome on 2008-12-24
I might try it again when they come out with the 6.4 version of the livecd. What I like about LFS is that its one of the only ways to get real dirty with your OS and make it completely how you want it, as in you can even compile it with a custom file structure (with proper symlinks, of course, and with the proper symlinks you may want Gobohide to hide them).

---

### Post by jrusso2 on 2008-12-25
> **jd65pl said:**
> Has anyone had a go at the Linux From Scratch project? I'm going to give it a go and was wondering about other peoples experiences and time scales for achieving a working system.

I think it will be a good learning curve and hopefully provide me with a system that is perfect for my needs.

J

I would not recommend it unless you have a strong background in Linux, close to being a Linux power user.  I would try arch or gentoo first like someone else suggested if you wanted more of a challenge.

---

### Post by Kopachris on 2008-12-28
Okay, I was having a few problems with it, so I tried jhalfs, but I had a few problems with that.  Now I've started over and am explicitly following the instructions.  I think the beginning problem was with mke2fs in the beginning.  I didn't really read that part because I used GParted to make and format the partition.

---

### Post by chris200x9 on 2008-12-28
I tried it but I didn't get too far, a couple tarballs failed to extract and I was like "screw this" and just went back to gentoo :P (in case you can't tell I REALLY like gentoo) so in short why not try gentoo? :guitar:

---

### Post by smartboyathome on 2008-12-28
> **chris200x9 said:**
> I tried it but I didn't get too far, a couple tarballs failed to extract and I was like "screw this" and just went back to gentoo :P (in case you can't tell I REALLY like gentoo) so in short why not try gentoo? :guitar:

Because gentoo won't let me customize my file system structure, so I can have my applications in /Applications and such. ;)

---

### Post by Kopachris on 2008-12-28
LFS seems to be working just fine as long as you follow ALL the instructions TO THE LETTER.  I think my big problem was that I used GParted to make and format the partition, and so then the default mke2fs program didn't work right.  Oh, yeah, and the instructions for fixing PTYs (in the FAQ) works just fine.

---

### Post by icecruncher on 2008-12-28
> **Kopachris said:**
> LFS seems to be working just fine as long as you follow ALL the instructions TO THE LETTER.  I think my big problem was that I used GParted to make and format the partition, and so then the default mke2fs program didn't work right.  Oh, yeah, and the instructions for fixing PTYs (in the FAQ) works just fine.

cool.  I'll try it then. in vbox

---

### Post by LinuxGuy1234 on 2008-12-30
> **jd65pl said:**
> Has anyone had a go at the Linux From Scratch project? I'm going to give it a go and was wondering about other peoples experiences and time scales for achieving a working system.

I think it will be a good learning curve and hopefully provide me with a system that is perfect for my needs.

J

I've gave it a try. In fact, in my sig, you'll use that user number!

---

### Post by fistfullofroses on 2008-12-30
Look into GoboLinux

---

### Post by fistfullofroses on 2008-12-30
I wouldn't recommend this just for learning purposes. If you wanted to use LFS as a blank Linux system, from which to build a distribution I would say sure... but otherwise you can customize any distribution of Linux to da** near rediculous point. GNU/Linux distributions have always been about customizability, and freedom of choice. You can easily take Slackware, Arch, Gentoo, Ubuntu minimal, or Debian netInstall and create a completely customized Linux installation. Using LFS to do this same thing reminds me of trying to use a hammer to kill a gnat.

---

### Post by smartboyathome on 2008-12-30
> **fistfullofroses said:**
> Look into GoboLinux

Already did. I like the file system, but package management is horrible there imo. That is why I want to go LFS, so I can use libalpm and pacman with the filesystem structure I like. :)

---

### Post by Kopachris on 2008-12-30
> **fistfullofroses said:**
> I wouldn't recommend this just for learning purposes. If you wanted to use LFS as a blank Linux system, from which to build a distribution I would say sure... but otherwise you can customize any distribution of Linux to da** near rediculous point. GNU/Linux distributions have always been about customizability, and freedom of choice. You can easily take Slackware, Arch, Gentoo, Ubuntu minimal, or Debian netInstall and create a completely customized Linux installation. Using LFS to do this same thing reminds me of trying to use a hammer to kill a gnat.
I would've based my distro off of Ubuntu, but the removal of some things was just too messy.  Plus, I didn't particularly want all those "ubuntu" version numbers floating around (you know, like "4.2ubuntu05").  It's just too messy.  Thus, LFS and BLFS.  (and HLFS, too)

---

### Post by MisfitI38 on 2008-12-30
> **fistfullofroses said:**
> I wouldn't recommend this just for learning purposes. If you wanted to use LFS as a blank Linux system, from which to build a distribution I would say sure... but otherwise you can customize any distribution of Linux to da** near rediculous point. GNU/Linux distributions have always been about customizability, and freedom of choice. You can easily take Slackware, Arch, Gentoo, Ubuntu minimal, or Debian netInstall and create a completely customized Linux installation. Using LFS to do this same thing reminds me of trying to use a hammer to kill a gnat.

You bring up an interesting point, namely, LFS and source based operating systems are fine for people who have the time.
I don't usually recommend them, because personally I find them impractical and too time-consuming.
However, some people do actually have the time, and even prefer to do things from a very basic level.
There's much to glean from using LFS, certainly, but it's not for everyone- only those who can 'afford' it, I'd say.

---

### Post by ha65li646 on 2008-12-31
how much about a [nike shoes](http://www.smkings.com) ??every one know??

---

