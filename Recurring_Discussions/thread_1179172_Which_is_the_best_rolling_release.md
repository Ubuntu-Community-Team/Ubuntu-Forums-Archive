---
title: "Which is the best rolling release?"
date: 2009-06-05
forum: Recurring Discussions
---

### Post by ukripper on 2009-06-05
I am looking to install the best rolling release with bleeding edge packages, somewhere between unstable and stable, preferably stable! looked around SIDUX and ARCH (Arch seems good but i prefer apt management). I would like some more suggestions.

Thanks in advance guys.

---

### Post by eldragon on 2009-06-05
> **ukripper said:**
> I am looking to install the best rolling release with bleeding edge packages, somewhere between unstable and stable, preferably stable! looked around SIDUX and ARCH (Arch seems good but i prefer apt management). I would like some more suggestions.

Thanks in advance guys.

if you could express why you prefer apt i can try and convince you to use pacman

---

### Post by binbash on 2009-06-05
Gentoo is the best rolling distro i have ever used.And emerge > apt, it is easier and better.

---

### Post by snowpine on 2009-06-05
I think you are going to get a lot of votes for Arch. :) I personally have not used either of them long enough to say which is "better," but Arch seems more flexible than Sidux. (Sidux does not have a minimal install, so you'd better like KDE or Xfce.) Sidux, however, comes as a live CD and "just works" on most hardware, so it is more like Ubuntu in that sense. I would say that Sidux is the closest thing to "rolling release Ubuntu" in my opinion, and Arch is "hands on for users who want total control." Basically, just read the Arch Beginner's Guide, and then you should have a pretty good idea whether or not it's the right distro for you.

Pacman is a great package manager; it only takes about 5 minutes to learn how it works. So don't worry about leaving apt behind if you switch to Arch.

One rolling release distro you did not mention is Debian Testing (currently Squeeze). It is not "bleeding edge" like Sid, but it is exactly halfway "between unstable and stable." :)

---

### Post by Eisenwinter on 2009-06-05
CRUX. It's similar to Gentoo in the concept of installing everything from source. 

(I've never used it, because it doesn't have an x86_64 image, but I've heard good things about it)

Arch was inspired by CRUX, too. No, not built on top of it, but inspired by its' minimalistic concept.

I've also heard many Gentoo users who now use CRUX say that Gentoo makes everything a lot more complicated than it should be.

---

### Post by ukripper on 2009-06-05
> **eldragon said:**
> if you could express why you prefer apt i can try and convince you to use pacman

Thanks for replying. I am just used to apt and dpkg alot and got many scripts prepared for installations/maintanence on over 20 machines which i think would be tedious task to rewrite for some other package manager. Hope you could suggest something in that boundary. I am still open to other package manager suggestions. What would you suggest?

---

### Post by ukripper on 2009-06-05
> **snowpine said:**
> 

One rolling release distro you did not mention is Debian Testing (currently Squeeze). It is not "bleeding edge" like Sid, but it is exactly halfway "between unstable and stable." :)

Thanks, very interesting. "Debian squeeze" - I'll read some more on it.

---

### Post by ukripper on 2009-06-05
> **binbash said:**
> Gentoo is the best rolling distro i have ever used.And emerge > apt, it is easier and better.

Gentoo heard alot about it but didn't know it is rolling release?

---

### Post by eldragon on 2009-06-05
> **ukripper said:**
> Thanks for replying. I am just used to apt and dpkg alot and got many scripts prepared for installations/maintanence on over 20 machines which i think would be tedious task to rewrite for some other package manager. Hope you could suggest something in that boundary. I am still open to other package manager suggestions. What would you suggest?

well, since you are stuck with apt, your only choice is debian, and its far from a rolling release. i dont know of any rolling release that uses apt or dpkg.

if you plan on moving into a rolling release distro, you will need to replace your package manager, so your scripts will need to be replaced anyway

---

### Post by kk0sse54 on 2009-06-05
Another vote for Gentoo, for me portage/emerge trumps pacman any day. Hope you like compiling though...

---

### Post by Daisuke_Aramaki on 2009-06-05
I use Lunar , a source based rolling distro, that i am extremely comfortable with. CRUX and Sorcerer are my other favorites. They just use very simple bash scripts to do everything, from updating to installing programs, which is simplistic, rather than using tools that are extremely distro specific.

---

### Post by monsterstack on 2009-06-05
Squeeze is pretty good. It'll feel rather familiar if you're a long-time Ubuntu user. Aside from a few fancy GUI-helpers, it's largely identical to Ubuntu, except a little bit leaner and a little bit faster. It's also incredibly stable for a rolling release. Newer software can be somewhat slow to arrive on Debian's testing distribution, mind you.

Sid should be out of the question. It's far too unstable for regular use, in my experience. I used it for a month or two, and during that time "apt-get upgrade" was a command that scared me to death. You never knew what was going to happen. A lot of the time bad stuff happened!

Sidux, on the other hand, is a really great distro. I used it for six months. If you get a kernel upgrade that feels a bit twitchy, then it's just a case of rolling back to the one before which you know you can rely on. They keep pretty up to date with some of the latest software. On the whole it's remarkably well put together. When I used it, there were a few problems with using Gnome, which there might still be, so it's KDE for you if so.

---

### Post by snowpine on 2009-06-05
Here is a fun little parable that explains the different branches of Debian: [http://sidux.com/PNphpBB2-viewtopic-t-2508.html](http://sidux.com/PNphpBB2-viewtopic-t-2508.html)

---

### Post by ukripper on 2009-06-05
Looks like options for me are drilling down to Arch, debian squeeze, Gentoo, Crux ,Lunar. I hope I haven't missed anything else important rolling release?

is SIDUX rolling release?

---

### Post by liamnixon on 2009-06-05
I can't speak for Crux (though I hear great things), but I'll cast another vote for Gentoo, as I've actually used it a fair bit.  A bit unstable (that could've just been my PC), but a good operating system all around.

---

### Post by ukripper on 2009-06-05
i wonder why no one mention Sabayon based on Gentoo. It is always rated good in Linux format! is it not a rolling release?

---

### Post by kelvin spratt on 2009-06-05
Once Arch is installed its a great distro I've used Sidux it was Ok. Gentoo you spend more time compiling than doing any work, I can do anything with Arch and Pacman is easier to use in my opinion than Apt,

---

### Post by ukripper on 2009-06-05
> **kelvin spratt said:**
> Once Arch is installed its a great distro I've used Sidux it was Ok. Gentoo you spend more time compiling than doing any work, I can do anything with Arch and Pacman is easier to use in my opinion than Apt,

I am growing liking towards Arch also, just reading all comments in here and their wiki and documentation seems well polished. I think i have to rule out option of GENTOO as i won't have that much time to compile from source when i need to do things productive.

---

### Post by kk0sse54 on 2009-06-05
> **ukripper said:**
> GENTOO as i won't have that much time to compile from source when i need to do things productive.

Compiling from source isn't this hideous long process as most people describe it to be. Portage is a fantastic package management system, some people see it as too complicated but I just see it as being much more advanced than your average package manager. Simple fact is though, that compiling will always be longer than installing a binary package. However after you get by that first phase of configuration and compiling (installing X and a DE etc etc) you won't have to sit compiling for that long as long as you keep up with updates. Things like firefox and openoffice take a while to compile however there are binaries available for each in order to save time. Emerge will also download the source of each package in the background while it's compiling in order to save time (something I'd love to see in FreeBSD ports). Productivity is a subjective opinion that is different for each person however if you properly configure your system you'll be fine.

---

### Post by usergentoo on 2009-06-05
Yes Sabayon is a great rolling release its a binary form of Gentoo. Im thinking of switching myself I grow tired of these 6month release cycles, in Ubuntu. What really bugs me cause alot breaks or older things no longer compatible and I loose settings when I upgrade. Like my Ati card no fglrx drivers for it any more. That puts me either using an older version of Ubuntu that dont have all the new bells and whistles or upgrade and try to compile the software myself and fix the issue. Sure we have open source drivers that work somewhat but when will they be as good as the others, many years from now? 

What about other new software no one is porting it to the older versions of Ubuntu. What about that new dropbox like service only for Jaunty and above? It dont work with Intrepid and below, so what do you do? With a rolling release I could stay with the older xserver and still get the bells and whistles from other newer software.

---

### Post by CJ Master on 2009-06-05
If you can stand to move away from APT, Arch blows away most other distros mentioned here.

Rolling release (duh), simplistic, fast, etc etc. You've already heard it from all of the other Arch fanbois.

Pacman blows away apt imo...

To install something:
```
pacman -Sy application
```

To totally upgrade everything on your system:
```
pacman -Syu
```

Plus, Yaourt+AUR just makes it awesome.

I recently wanted to try out the WING IDE for python, and so I typed it:

```
yaourt -Ss wingide
```

It then searched the AUR (Arch user repository) for it, and it showed me all the different versions I could choose from, and their package names. I decided I wanted the free edidtion so I typed in:

```
yaourt -Sy wingide-101
```

As you can see, yaourt has the same syntax as pacman.

But I can see how it'd be a pain for you to reprogram your scrips, but arch is worth it. :)

---

### Post by unknownPoster on 2009-06-05
I'm also a fan of Lunar Linux. The "package-manager" of Lunar is one of my favorites out there. I never had a problem running Lunar. I just like to distro-hop a lot, so I did not stay with it for long...

---

### Post by ukripper on 2009-06-08
Thanks everyone for your helpful comments. So far Arch seems to be the better option for a rolling release or perhaps i'll look into sabayon as well which is in binary form. I believe Sabayon provides the best out of Gentoo to the user. 

It is Arch or Sabayon. I've a lot of reading on them to do.

Thanks again.:)

---

### Post by ukripper on 2009-06-08
Here is an interesting thread if anyone is looking for Sabayon discussion.
[http://bbs.archlinux.org/viewtopic.php?id=42835](http://bbs.archlinux.org/viewtopic.php?id=42835)

---

### Post by sultanoswing on 2009-06-08
I installed Arch 32-bit on my desktop over a year ago and have never even considered going back to Ubuntu since. Rolling release, customisable, and the keep it simple philosophy (rc.conf is great!) is a winner. Vanilla, non-branded packaging of various packages (GNOME, OpenOffice, Firefox) is another nice feature. The arch build system and arch user repository are further icing on the cake, and rolling your own kernel should you need/want to is (almost) child's play.

I'm seriously considering switching my XPS m1330 from Jaunty 64-bit to Arch - the 6-monthly upgrade cycle just to have fresh fersions of software - firefox, open office and amarok for example - is beginning to get old. Although I do like keeping tabs on how Ubuntu is developing too :)

Having said all this I put a friend onto Arch, but as a Gentoo user he couldn't stand the *lack* of customisation, so go figure - the old story of horses for courses applies in full.

For a comparison of Arch vs others: [http://wiki.archlinux.org/index.php/Arch_vs_Others](http://wiki.archlinux.org/index.php/Arch_vs_Others)

---

