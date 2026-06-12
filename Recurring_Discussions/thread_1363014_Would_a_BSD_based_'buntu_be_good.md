---
title: "Would a BSD based 'buntu be good?"
date: 2009-12-23
forum: Recurring Discussions
---

### Post by afroman10496 on 2009-12-23
I want to make one so bad! a user friendly BSD with the Ubuntu spirit :P

---

### Post by schauerlich on 2009-12-23
Go for it.

---

### Post by pwnst*r on 2009-12-23
do it.








now.

---

### Post by juancarlospaco on 2009-12-23
Ubuntu loves GPL
BSD dont like GPL
*(used as last resort)*

---

### Post by Xbehave on 2009-12-23
What's the point?

I mean go for it if you want but why would your objective be?
There is already a debian bsd port so why make a ubuntu one,
The slow release cycle of the bsd kernel fits debian better
I don't know what prop driver support is like for BSD?
I don't know if BSD has DRM for DRI for open drivers?
BSD does have ZFS (but if your objective is ZFS there is already a "ubuntu-port" to open solaris)

By all means go for it but i recommend you set out your goals first, as they may be easier to achieve some other way

---

### Post by renkinjutsu on 2009-12-23
Debian is working on Debian/kfreeBSD, so you can start from there.

---

### Post by DeadSuperHero on 2009-12-24
> **juancarlospaco said:**
> Ubuntu loves GPL
BSD dont like GPL
*(used as last resort)*

Actually, BSD licenses and GPL licenses are compatible. Heck, even BSD-licensed software can be re-licensed as GPL software.

I fail to see the issue here.


EDIT:

More importantly, though: How simple is it to just compile the Ayatana work into Gnome running atop FreeBSD? The 100 papercuts patches? What about the installer? Package manager?

In theory, I'd say these things are quite doable, and FreeBSD would be a great base for it. Does it need to be an official Ubuntu project? Not really, but the resources are there to do such a thing.

---

### Post by K.Mandla on 2009-12-24
> **Afroman10496 said:**
> I want to make one so bad! a user friendly BSD with the Ubuntu spirit :P
If you build it, they will come.

---

### Post by t0p on 2009-12-24
I didn't vote in the poll as there was no suitable option.  Just "Yes" or "No" - no "Don't know" or "Don't care".  Bah! :mad:

---

### Post by Exodist on 2009-12-24
Poll is tied.. Very interesting..

---

### Post by Rhapsody on 2009-12-24
Poll is no longer tied.

As some other posters said, [Debian GNU/kFreeBSD](http://www.debian.org/ports/kfreebsd-gnu/) seems like a good place to start, given that Ubuntu Linux is based on Debian GNU/Linux. This seems like a pretty good time to be making an Ubuntu BSD as well, since the Debian Project think Debian GNU/kFreeBSD is now stable enough to be part of the [Squeeze release goals](http://lists.debian.org/debian-announce/2009/msg00010.html).

---

### Post by Xbehave on 2009-12-24
> **Mr. Psychopath said:**
> Actually, BSD licenses and GPL licenses are compatible. Heck, even BSD-licensed software can be re-licensed as GPL software.

I fail to see the issue here.
>    1. Redistributions of source code must retain the above copyright notice, this list ofconditions and the following disclaimer.
If you retain that notice you can not license it GPL which imposes additional restrictions.

---

### Post by Psumi on 2009-12-24
I hope you make it so that it doesn't take over your CD-ROM Drive and won't eject or anything like all the other linux (but not ubuntu) distros do.

---

### Post by Xbehave on 2009-12-24
> **Psumi said:**
> I hope you make it so that it doesn't take over your CD-ROM Drive and won't eject or anything like all the other linux (but not ubuntu) distros do.
Quit you jibba jabber, ofc a liveCD needs to be in the CD drive if your using it (unless your on a real liveCD distro which probably has a toram option, like knopix since 5 years ago)

---

### Post by Psumi on 2009-12-24
> **Xbehave said:**
> Quit you jibba jabber, ofc a liveCD needs to be in the CD drive if your using it (unless your on a real liveCD distro which probably has a toram option, like knopix since 5 years ago)

When I reboot, the system still won't eject, even when in the BIOS. I had to shut down the computer rather than reboot.

---

### Post by Zeemvel on 2009-12-24
A BSD based ubuntu would be really interesting!

---

### Post by afroman10496 on 2009-12-24
[offer]I wish someone would help me...[/offer]

---

### Post by dragos240 on 2009-12-24
Why not. There's nothing stopping you.

---

### Post by afroman10496 on 2009-12-24
I really want to. I don't know how though...

---

### Post by earthpigg on 2009-12-24
i voted 'no'.

something as low level as this would fit better with one of the handfull of "Father Distros" on which the vast majority of other distros are based:

slack
debian (already working on it -- but only using the kernel.)
red hat
suse

or maybe even gentoo. gentoo is already heavily inspired by *bsd, so it would be an easier 'sell' on the gentoo community... meaning you would be more likely to get help from them.

---

### Post by Bachstelze on 2009-12-24
> **Xbehave said:**
> If you retain that notice you can not license it GPL which imposes additional restrictions.

But if you modify the software, you can release your modifications under the GPL, effectively making the whole thing GPL. this is also the case if you re-use some BSD-licensed code in a GPL project.

Of course you can't just change the licensing terms of something, only the copyright owner can.

---

### Post by alphaniner on 2009-12-24
> **earthpigg said:**
> something as low level as this...

What do you mean by low level?  Edit: NM, Bachstelze's post cleared it up.

@poll

I voted none of the above.  Oh, wait, no I didn't.  But I'm not sure.  I think BSD is best suited to remain a server OS.  I'm putting my desktop eggs into the Haiku basket.

---

### Post by Bachstelze on 2009-12-24
> **earthpigg said:**
> i voted 'no'.

something as low level as this would fit better with one of the handfull of "Father Distros" on which the vast majority of other distros are based:

slack
debian (already working on it -- but only using the kernel.)
red hat
suse

Debian does it already, all that is needed is build from there, just like the normal Ubuntu was built from Debian GNU/Linux. The former is no more "low level" than the latter.

> or maybe even gentoo. gentoo is already heavily inspired by *bsd, so it would be an easier 'sell' on the gentoo community... meaning you would be more likely to get help from them.

There is a Gentoo/kFreeBSD already.

Anyway, I thought about that too, but got laughed at by our favourite jdong. Maybe I'll start working on it when I have time, just to prove him wrong (wish me luck with that).

---

### Post by earthpigg on 2009-12-24
> What do you mean by low level?

modifying a kernel is very low level. modifying a package manager is somewhere in the middle. moving buttons around on a GUI is high level.

if you where to work with a 'father' distro for this, that means any changes you make would find there way into more distros and onto more people's computers.

example:

say you want to use apt-get for this project. maybe part of making this work with the FreeBSD kernel results in you making dpkg handle errors better? this could also very possibly make apt-get, synaptic, etc, all work better. maybe only a smidgen, but an improvement regardless. that wasn't the goal, of course, just a pleasant accident... but your 'accidental' discovery would certainly be beneficial to anyone using a system that manages packages with dpkg, apt-get, ubuntu software center, etc.

if your project was working directly with debian, you could submit that patch and -- if accepted -- it would work its way down to all of the children of debian with no further intervention from you. including ubuntu.

if your project was working with ubuntu, submitting that patch to ubuntu would be great... but additional work would need to be done for it to make its way to other distros.

---

### Post by schauerlich on 2009-12-24
Why not fork PC-BSD and make it more Ubuntu-like? If you actually want a *BSD system, that'd be your best bet. The only thing different between Debian GNU/kFreeBSD and Debian GNU/Linux is the kernel - not the userland (other than patches to make the GNU userland work on the FreeBSD kernel).

---

### Post by Penguin Guy on 2010-04-21
I voted yes, not because I think lots of people would use it (because GNU > BSD), but because all the apps that would get ported to BSD because of Bubuntu would greatly benefit BSD.

---

