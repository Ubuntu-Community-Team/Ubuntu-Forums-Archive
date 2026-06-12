---
title: "Baby steps to Slackware"
date: 2007-04-24
forum: Other OS Talk
---

### Post by Shmook on 2007-04-24
My name's Eric, I'm a recovering Windows user...

And thus far I've impressed and excited by the interactive-ness of Linux and I look forward to continuous learning of the processes and mechanisms that MS always kept hidden from me.

I've been reading about other not-as-friendly-as-Ubuntu distros and am very interested in Slackware and Arch, as it seems these allow the most direct & no-nonsense control of a computer, and I'm interested in the analogues to the apt-get, synaptic, grub, etc. I also know I probably wouldn't even get through the installation of these OSes - yet.

So I'm wondering what steps I should take to attain a grasp of the concepts required to operate Slackware and the like. Playing around in BASH? Compiling programs rather than using aptitude? Could FreeBSD be used as a stepping stone? 
Thanks

---

### Post by LaRoza on 2007-04-24
One word SLAX. It is a very good Live distro, in fact, I have it installed as a bootable USB device.

Slax has many versions, I recommend you get several including the text only version:

[http://www.slax.org/](http://www.slax.org/)

It is also extensible, you can add modules so increase its usefulness.

---

### Post by ThinkBuntu on 2007-04-24
I recommend Zenwalk as a stepping stone. You'll have to get your hands dirty a little bit to customize your machine, but it's still a complete workstation out of the box. The support forums are so-so (a handful of dedicated users who really know their stuff. Everyone else is learning) but as a whole I enjoyed using it.

---

### Post by tommcd on 2007-04-24
Yeah, I recommend zenwalk also. It's based on slackware, yet it is easy to install and use. The installer is similar to slackware's also. You can even install most slackware packages on zenwalk if you want. Read the zenwalk manual and wiki first.
Zenwalk runs light and fast and is very up to date. The only downside is that there are a limited number of programs available in their repos, but you can add slackware packages also, and a few users compile extra programs for zenwalk.
[http://zenwalk.org/](http://zenwalk.org/)

---

### Post by RAV TUX on 2007-04-24
> **Shmook said:**
> My name's Eric, I'm a recovering Windows user...

And thus far I've impressed and excited by the interactive-ness of Linux and I look forward to continuous learning of the processes and mechanisms that MS always kept hidden from me.

I've been reading about other not-as-friendly-as-Ubuntu distros and am very interested in Slackware and Arch, as it seems these allow the most direct & no-nonsense control of a computer, and I'm interested in the analogues to the apt-get, synaptic, grub, etc. I also know I probably wouldn't even get through the installation of these OSes - yet.

So I'm wondering what steps I should take to attain a grasp of the concepts required to operate Slackware and the like. Playing around in BASH? Compiling programs rather than using aptitude? Could FreeBSD be used as a stepping stone? 
ThanksI suggest you start with [**Wolvix**]("http://wolvix.org/") (also SLAX/Slackware based)
A lot nicer, and faster then Zenwalk and much easier to install and configure....

---

### Post by saulgoode on 2007-04-24
A very good introduction to Slackware is the [Slackware Basics manual](http://www.slackbasics.org/html/slackware-basics.html).

---

### Post by darweth on 2007-04-25
I don't know how Slackware works, but compiling packages within Ubuntu will not teach you anything relevant to ARCH.  You will be compiling with AUR/ABS there which is different.  I thought I was pretty badass compiling half my apps under Ubuntu for the fun of it, but it did not aid/enrich my ARCH experience at all. ;)  Slackware might be a different story.

---

### Post by ThinkBuntu on 2007-04-25
Also, because there are a limited number of packages available in Zenwalk, you'll have to build from source and hunt down dependencies, etc. Good overall experience for those times when an apt/rpm/pacman binary isn't available.

That being said, most major programs are in netpkg (inkscape, openoffice, etc.)

---

### Post by darweth on 2007-04-25
> **ThinkBuntu said:**
> Also, because there are a limited number of packages available in Zenwalk, you'll have to build from source and hunt down dependencies, etc. Good overall experience for those times when an apt/rpm/pacman binary isn't available.

That being said, most major programs are in netpkg (inkscape, openoffice, etc.)

I don't know.  I would strike pacman binary from the list. :x  If it is not in pacman, it is VERY VERY likely to be in AUR.  If that doesn't work, you will build it with ABS.  To be honest... I've never used ABS but it seems to be different than building from source elsewhere.

---

### Post by manmower on 2007-04-25
Arch has an excellent forum and wiki, I pretty much went in the deep end and learned as I went along. Just reading the install guide alone will teach you a lot about what config files are at the heart of your OS, and how to optimize them. Most things in Arch are different enough from other distros so that they're best learned from within Arch. Some were challenging for a first-timer but you only have to get it right once and hang on to your configs afterwards. :)

I suggest you take the same route (be it with Arch or Slackware) and keep another OS or computer handy in case you run into unforeseen problems. If you mess up too badly, just reformat and reinstall. I predict it will take you maybe a week, two weeks tops to start feeling comfortable with Arch (never used Slackware myself so I have no clue how easy one would pick up on it).

---

