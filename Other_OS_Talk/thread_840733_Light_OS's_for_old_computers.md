---
title: "Light OS's for old computers"
date: 2008-06-25
forum: Other OS Talk
---

### Post by Frak on 2008-06-25
I'm looking for a light OS for an old Laptop, I've already tried a few, and I'll list them:

1. Ubuntu - Don't know what I was thinking
2. Xubuntu - Kernel Panics on startup.
3. Kubuntu - The interface hates the graphics card, its very messed up.
4. PCLOS - Lets go to subcategories on this one:
     1. I hate PCLOS with a passion, I like Vista better than this
     2. It feels half-baked
5. All PCLOS derivitives
6. Fluxbuntu - Incredibly hard to use on it
7. Sidux - Too unstable and incomplete for me
8. Debian - It's either too stable (old) or too unstable (incomplete)
9. DSL - Too old
10. Windows XP - Serious, I tried it. It was good, except it couldn't detect the display after first boot (go figure).
11. Zenwalk - It just feels awkward to use
12. Vector - Couldn't load because of some missing battery driver? And then it kernel panics.

Since it has no Network card, and its wireless support has been dropped from just about every OS, it needs to be installed before network can be used (NDISWrapper)

I'm ready for ideas :D


Specs: Intel PIII 900MHz
256 MB of RAM
Some crappy Intel integrated video card
And comes with a hot cup of tea when you purchase within the next 10 minutes

EDIT
Also, nobody say Freespire please.

---

### Post by zmjjmz on 2008-06-25
Specs?

---

### Post by Frak on 2008-06-25
Oh right, let me update my OP

---

### Post by zmjjmz on 2008-06-25
antiX should be nice.

---

### Post by Frak on 2008-06-25
> **zmjjmz said:**
> antiX should be nice.
Tried that, :(

---

### Post by seanc7 on 2008-06-25
I know you already tried Debian but the Lenny testing version should run really well on that.

I've run Lenny in a virtual machine with 128MB of RAM and it's a champ, even running the Gnome DE.

---

### Post by jualin on 2008-06-25
how about  [Puppy Linux]("http://www.puppylinux.org/")?

---

### Post by Frak on 2008-06-25
> **jualin said:**
> how about  [Puppy Linux]("http://www.puppylinux.org/")?
I'll try it. :D

---

### Post by jualin on 2008-06-25
They have some variations of Puppy, there is one called TeenPup which has all the media plugins installed by default.

---

### Post by piousp on 2008-06-25
-Knoppix

-ProtechOne

?

---

### Post by moore.bryan on 2008-06-25
ubuntu server install running [openbox]("http://icculus.org/openbox/index.php/Main_Page")?

[lxde]("http://www.lxde.org/")?

---

### Post by zmjjmz on 2008-06-25
PUD is another option, it's Ubuntu based though.

---

### Post by Frak on 2008-06-25
> **seanc7 said:**
> I know you already tried Debian but the Lenny testing version should run really well on that.

I've run Lenny in a virtual machine with 128MB of RAM and it's a champ, even running the Gnome DE.
All Debian based OS's now suffer from a bug that ONLY affects my version of the Intel graphics:

The resolution refuses to go above 800x600 when even in the BIOS it is registered as 1024x768.

This is due to the fact that 99% of the Debian based OS's (including Ubuntu) just recompile their packages from the Debian upstream. Therefore, any bug Debian has, the derivatives have.

---

### Post by zmjjmz on 2008-06-25
Ouch. Arch then?

---

### Post by Frak on 2008-06-25
> **zmjjmz said:**
> Ouch. Arch then?
Arch doesn't support my wireless until full installation unfortunately. Though, I could try archie.

---

### Post by Hunterjelly on 2008-06-25
Gentoo may be worth checking out. If you can survive having to compile everything, theres a marginal speed boost in it for you.

---

### Post by zmjjmz on 2008-06-25
Something RPM based then?
:/
:\
:/
:]
Stripped down CentOS?

---

### Post by Frak on 2008-06-25
> **Hunterjelly said:**
> Gentoo may be worth checking out. If you can survive having to compile everything, theres a marginal speed boost in it for you.
I've had BAD experiences with Gentoo

And I've never really found an advantage to custom compiling packages in the first place. (When you crunch the numbers, the only difference between a pre-compiled optimized 686 package, such as one distributed by Arch, and one compiled by Gentoo, with the appropriate small libraries, the speed increase is usually barely 1%, sometimes even 2%, 10% if the packager didn't know how to compile Firefox)

---

### Post by zmjjmz on 2008-06-25
Just realized, you could try a SLAX distro.

---

### Post by Frak on 2008-06-25
> **zmjjmz said:**
> Just realized, you could try a SLAX distro.
I'll try it.

---

### Post by Dr Small on 2008-06-25
> **Frak said:**
> Arch doesn't support my wireless until full installation unfortunately. Though, I could try archie.
Why would that matter? Don't you want to install it?

---

### Post by jrusso2 on 2008-06-25
Puppy Linux, Zenwalk, Slackware, deli linux would all work.

---

### Post by Frak on 2008-06-25
> **Dr Small said:**
> Why would that matter? Don't you want to install it?
Well, I planned on having a GUI. Happens to be that isn't included with Arch ;)

---

### Post by Hunterjelly on 2008-06-25
Build your own from scratch.

[http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)

(Though if you didn't like Gentoo, this probably won't be much better)

---

### Post by Dr Small on 2008-06-25
> **Frak said:**
> Well, I planned on having a GUI. Happens to be that isn't included with Arch ;)
No, not included. But once you get it installed and your wireless card working, then you could install whatever GUI you wanted.

---

### Post by angryfirelord on 2008-06-25
FreeBSD. :twisted:

---

### Post by Frak on 2008-06-25
> **angryfirelord said:**
> FreeBSD. :twisted:
Don't know why, but every computer I've ever bought, BSD has never worked completely right on it.

---

### Post by cardinals_fan on 2008-06-25
> **zmjjmz said:**
> Just realized, you could try a SLAX distro.
+1

Slackware is amazing, and SLAX makes Slack easy.
> **Frak said:**
> Don't know why, but every computer I've ever bought, BSD has never worked completely right on it.
Sadly, +1.

NetBSD gets no support :-({|=

---

### Post by Twitch6000 on 2008-06-26
You can try fedora <.<.
Although I must say why hate PClinuxOS,it meets all my needs and looks great =[.
Also you could try knoppix.

---

### Post by Frak on 2008-06-26
> **Twitch6000 said:**
> Although I must say why hate PClinuxOS,it meets all my needs and looks great =[.

It feels like a half-baked scheme that gives no attention to any legalities in the mass market (United States, for which it was made) with a, again my opinion, mimicked theme, and led by a person who just cannot keep their opinion to themselves.

I say it again, my opinion.

---

### Post by mikjp on 2008-06-26
Slackware or [Absolute Linux](http://www.pcbypaul.com/absolute/). FreeBSD.

---

### Post by anticapitalista on 2008-06-26
> **Frak said:**
> Tried that, :(

and what was the problem with antiX?

---

### Post by Frak on 2008-06-26
> **anticapitalista said:**
> and what was the problem with antiX?
I can't quite remember, but I think it was a network issue and I was just too lazy to fix it.

---

### Post by anticapitalista on 2008-06-26
> **Frak said:**
> I can't quite remember, but I think it was a network issue and I was just too lazy to fix it.

Ok, so it did boot ok. Just checking.

---

### Post by Frak on 2008-06-26
> **anticapitalista said:**
> Ok, so it did boot ok. Just checking.
Oh yeah, boot just fine. I just suffer from procrastination and laziness.

---

