---
title: "Trying Oneiric: risks ? which version ?"
date: 2011-09-14
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Gnurfos on 2011-09-14
Hi,

I understand that there are currently bugs, and that anyway there will be bugs in any version, but:

Is there a list of the currently known bugs in oneiric ? possibly sorted by "importance" ? is there a way to know which ones will be fixed before the final release ?

If I get a beta version now, will I "automatically" get updates catching up with the final release ?

Also, if I take some random daily build, is there a chance that it could be worse than, say beta1, or are things always progressing positively ?

Thanks.

---

### Post by howefield on 2011-09-14
Thread moved to the development forum "*Ubuntu +1 (Oneiric Ocelot)*"

---

### Post by meborc on 2011-09-14
> **Gnurfos said:**
> Hi,
Hello

> **Gnurfos said:**
> I understand that there are currently bugs, and that anyway there will be bugs in any version, but:

Is there a list of the currently known bugs in oneiric ? possibly sorted by "importance" ? is there a way to know which ones will be fixed before the final release ?

You can check out the launchpad page here - [https://bugs.launchpad.net/ubuntu/oneiric](https://bugs.launchpad.net/ubuntu/oneiric) you can search for a specific package you are interested in to see what bugs have been filed against it.

> **Gnurfos said:**
> If I get a beta version now, will I "automatically" get updates catching up with the final release ?

Yes, you will be able to upgrade to the latest (final) version

> **Gnurfos said:**
> Also, if I take some random daily build, is there a chance that it could be worse than, say beta1, or are things always progressing positively ?

Yes, although major breakage is already over, daily builds are not as well tested as a beta or RC release. I would still go for the daily though, if it fails to install, try another daily or latest beta.


> **Gnurfos said:**
> Thanks.
no problem

ps - also read this - [http://ubuntuforums.org/showthread.php?t=1751289](http://ubuntuforums.org/showthread.php?t=1751289)

---

### Post by Gnurfos on 2011-09-15
Hi,

I just tried the Sep14 build, with "live CD", and am a bit disappointed (flash plugin install did not "just work", and the desktop was kind of slow and crashed badly on my first attempt).

So my current objective is to determine if I ran into some temporary bugs, of if something in my computer is kind of incompatible. Or maybe the live CD is not supposed to work as smoothly as a regular install ?

Is there a way to see a changelog between different builds ? (or a diff in the packages versions).

Thanks !

---

### Post by meborc on 2011-09-15
> **Gnurfos said:**
> Hi,

I just tried the Sep14 build, with "live CD", and am a bit disappointed (flash plugin install did not "just work", and the desktop was kind of slow and crashed badly on my first attempt).

So my current objective is to determine if I ran into some temporary bugs, of if something in my computer is kind of incompatible. Or maybe the live CD is not supposed to work as smoothly as a regular install ?

Is there a way to see a changelog between different builds ? (or a diff in the packages versions).

Thanks !

If you check the forums, people are reporting all kinds of trouble with 11.10 at the moment. That said, a full install (with proper video drivers installed) will give you a better idea of how the system feels. If you have a separate partition/HDD free, install and see if it is any better.

You can go to packages.ubuntu.com to search for a package you wish to examinate. There is a link to the changelog on the package page.

---

### Post by Gnurfos on 2011-09-15
I'm not used to these forums, so I just thought they were always so active :)

Is there a way to get a high level view of the quantity of problems for a given version ?

And for the changelog too, it would be nice if we could get first a list of package changes between 2 versions, before checking individual changes. Does this exist ?

Thanks.

---

### Post by dino99 on 2011-09-15
before to be able to report bugs and help other users, you need yourself to learn and draw your way, so you may start like all others: the beginning, meaning reading forums with their stickies at least.

---

### Post by Gnurfos on 2011-09-15
The stickies look quite old. I see that one of my original questions is answered in one of them (sorry for that one), but can't find for the others.

To elaborate: I love to report bugs, I'm doing it all the time at work. But for Ubuntu I'm not ready to dedicate time to testing, so I thought I would just test by using the system (I have to install some soon anyway). The only thing is, I don't want to accidentally fall into having an unusable system for weeks, so I'm just trying to evaluate if I can afford to go for Oneiric (I would love to!).

---

### Post by meborc on 2011-09-15
> **Gnurfos said:**
> I'm not used to these forums, so I just thought they were always so active :)

Is there a way to get a high level view of the quantity of problems for a given version ?

And for the changelog too, it would be nice if we could get first a list of package changes between 2 versions, before checking individual changes. Does this exist ?

Thanks.

I usually don't care so much for ALL changes, so I tend to just look up the package I have trouble with and check what has been changing with it and the dependencies

To have a better overview of what is happening at the moment join the oneiric-changes and ubuntu-devel mailing lists ([https://lists.ubuntu.com/](https://lists.ubuntu.com/))

---

### Post by cariboo on 2011-09-15
> **Gnurfos said:**
> The stickies look quite old. I see that one of my original questions is answered in one of them (sorry for that one), but can't find for the others.

To elaborate: I love to report bugs, I'm doing it all the time at work. But for Ubuntu I'm not ready to dedicate time to testing, so I thought I would just test by using the system (I have to install some soon anyway). The only thing is, I don't want to accidentally fall into having an unusable system for weeks, so I'm just trying to evaluate if I can afford to go for Oneiric (I would love to!).

Most of us here, run a stable version, in most cases Natty, and have Oneiric installed on another partition just in case something happens to make the system unusable. That being said, I haven't booted into Natty in about a month, as with my well supported hardware, Oneiric is running as well as can be expected for a beta release.

---

### Post by Gnurfos on 2011-09-16
Thanks for your answers. I will check the lists, and probably install this weekend !

---

