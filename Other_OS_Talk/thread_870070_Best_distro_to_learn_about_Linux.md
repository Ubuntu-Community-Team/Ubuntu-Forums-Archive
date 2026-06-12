---
title: "Best distro to learn about Linux?"
date: 2008-07-25
forum: Other OS Talk
---

### Post by spencercarran on 2008-07-25
I would like to learn more about how Linux works. I have absolutely no programming experience whatsoever. My experience with Linux thus far consists of installing Ubuntu on my Macbook and just getting a usable system out of it after always having used Mac OS. So... what's the best Linux distro for learning more about how it actually works? Or, what would be the best way to get into learning more, irrespective of the specific distro? Right now I know essentially nothing about it, but I'm a fairly quick learner.

Thanks in advance for any tips.

---

### Post by fiddledd on 2008-07-25
How about [this](http://www.linuxfromscratch.org/)

---

### Post by spencercarran on 2008-07-25
> **fiddledd said:**
> How about [this](http://www.linuxfromscratch.org/)

:shock: That could be fun... kind of a jump straight into the deep end. I could probably install it on a spare flash drive to avoid the hassle of repartitioning my hard drive, since it's so compact. Or I could just steal some more space from my unused OSX partition.

Another question: how does rEFIt do with multi-boot systems? I know it's fairly easy to dual-boot (I managed to get it working, so it can't be that tough;)), but will rEFIt start acting up if I add more OSes?

---

### Post by Barrucadu on 2008-07-25
LFS, Gentoo, Slackware, perhaps CRUX and Arch.

---

### Post by L815 on 2008-07-25
- Debian 
- OpenSUSE
- Fedora
- Arch 

- Slackware
- Gentoo

The top 3 can be learned from without spending all your time configuring it first. Arch on the other hand is from the core up, but it's fairly straightforward, and will be a learning experience. (I had a running Arch install with Gnome in about 2 hours)

The last 2, are more complicated in the sense that you have to do everything, all the time. Probably the best options for serious (deep) learning.

---

### Post by fiddledd on 2008-07-25
> **spencercarran said:**
> :shock: That could be fun... kind of a jump straight into the deep end. I could probably install it on a spare flash drive to avoid the hassle of repartitioning my hard drive, since it's so compact. Or I could just steal some more space from my unused OSX partition.

Another question: how does rEFIt do with multi-boot systems? I know it's fairly easy to dual-boot (I managed to get it working, so it can't be that tough;)), but will rEFIt start acting up if I add more OSes?

There's plenty of help on that site, also guides. So it's not quite as daunting as it might seem. Sorry, no experience at all using rEFIt, it's a Mac bootloader is all I know/think.

---

### Post by emix on 2008-07-25
Arch or Gentoo!

---

### Post by spencercarran on 2008-07-25
Thanks all. I think I'll try out Debian or Arch first, then maybe slackware. I downloaded a livecd of Suse but it's KDE4 and looks like a mess, and I think Fedora also defaults to KDE. LFS will probably wait until I have a lot of free time and a bit more experience. In any case, I can't install any of them for about the next 3 weeks because of bizarre wireless issues in my house- long story.

---

### Post by chucky chuckaluck on 2008-07-25
you can probably learn about linux on any distro. why not learn about it on the one you're using? you could get a copy of 'linux in a nutshell' and start plowing through that. with limited experience, if you use a distro that will force you to learn because you have no choice, you're apt to learn more about bashing your skull open with a hammer.

---

### Post by RiceMonster on 2008-07-25
I'd recommend Slackware, Arch, or Gentoo.

---

### Post by spencercarran on 2008-07-25
> **chucky chuckaluck said:**
> you can probably learn about linux on any distro. why not learn about it on the one you're using? you could get a copy of 'linux in a nutshell' and start plowing through that. with limited experience, if you use a distro that will force you to learn because you have no choice, you're apt to learn more about bashing your skull open with a hammer.

lol, "In a nutshell" and it's 942 pages. Still, I should probably look into that and you have a good point about that probably being a better way of learning.

---

### Post by SunnyRabbiera on 2008-07-25
For the beginner there is none better then Ubuntu in learning the more complex natures of linux.
My process of learning linux is by starting with a simplistic distro like Linux Mint and Mepis (in my case Mepis) and then learn what you can before going to Ubuntu.
Then from Ubuntu go to debian to learn even more, debian might be a harder nut then ubuntu but its still very easy to figure out in the long run.
After debian try arch, then move up to gentoo and slack.

---

### Post by cardinals_fan on 2008-07-25
Slackware is THE learning distro.

---

### Post by tel93 on 2008-07-26
Go with arch linux.

---

### Post by Mr. Turkey Vulture on 2008-07-26
To all the good people recommending Arch as a good ground-up distro for learning:

why?  what makes Arch, Gentoo, or Slackware optimal?  thanks.

---

### Post by chucky chuckaluck on 2008-07-26
> **spencercarran said:**
> lol, "In a nutshell" and it's 942 pages. Still, I should probably look into that and you have a good point about that probably being a better way of learning.

the 'pocket guide' is pretty good and full of good, basic stuff.

[IMG]http://www.linux-stuff.com/book11.jpg[/IMG]


> **Mr. Turkey Vulture said:**
> To all the good people recommending Arch as a good ground-up distro for learning:

why?  what makes Arch, Gentoo, or Slackware optimal?  thanks.

i think it goes along with the notion of being forced to learn in order to get things working. i'd leave arch off that list as there are some automated bailouts that save people who are less than thorough, like me.

---

### Post by Themaister on 2008-07-26
I'd say Arch, I've leared alot in just about a week =) I guess Gentoo and Slack are good ones too to learn with.

---

### Post by rndmluser on 2008-09-06
As I have used most of the aforementioned distros with the exception of Arch, my advice is to go with Slackware. If your intention is to learn GNU/Linux, this is my advice: Stay away from Debian as everything is done "The Debian Way". In regards to Gentoo, it gives mosts of its users a false perception of thinking they know what they are doing -- although some do. LFS is great, but it won't teach you anything the other distrubitions can't (having mentioned no progamming experience). This is because knowledge in C programming is a requisite for understanding as almost all system software is written in C. Sure you could follow the book to a "T" but you wouldn't really understand what you are doing. This is where Slackware bridges the gap; it doesn't make you bootstrap an initial toolchain as the core system is provided precompiled. You need only worry about system administration and it encourages doing things the Linux way (no distro ******** hacks). That, in my opinion, is the route to *learn*. Once you get a grip on things, then you will see the beauty in LFS, and even more so in Gentoo.

---

### Post by molom on 2008-09-08
I would say any base distro without all the 'easy' crap. You normally learn how it works when having to work without the Ubuntu-like GUI's.

So:
- Arch
- Slackware
- Debian
- Gentoo
- Frugalware

Cheers,
molom

---

