---
title: "Bare canvas distro of choice?"
date: 2008-12-23
forum: Other OS Talk
---

### Post by .ben on 2008-12-23
First off, hello to everyone at the Ubuntu forums.
This being my first post, it might be considered rude that I start with a question. So if I offend anyone, I apologize in advance.

Either way, it is great to be here. And I hope we will all get along well.

Regarding the thread title, I was wondering which distro would get your vote (simplicity, ease of use/maintenance..).
Arch? Slack? Gent? ..?

I have been _distro-hopping_ for quite some time now, and I thought it would be nice to finally find a _niche_ so to speak, to fit into. That said, I have looked at Arch/Gentoo and both caught my attention. Yet the fact that it seems they do not have a LiveCD available is kind of a downer, since I currently do not have a CD reader available (please do not shoot me).

Kind regards,
Ben.

---

### Post by WaeV on 2008-12-23
Arch is simple to set up, and you will learn a lot.  Speed tests I remember seeing show that it is actually faster than gentoo which takes a LONG time to compile.

As long as you have a USB drive, you can use unetbootin to make it act like a liveCD.

---

### Post by Rotaj on 2008-12-23
First off, you should look into [The Chakra Project]("http://chakra-project.org/") for a live arch based distro. Also, [Sabayon]("http://www.sabayonlinux.org/") is based off of Gentoo.

Secondly, do you have a preference regarding the desktop envionnment?

Lastly, [Distrowatch ]("http://distrowatch.com/")is a distro-hoppers friend.

---

### Post by Sorivenul on 2008-12-23
This is, as always about personal needs and preferences.  That said, if you want some "blank canavas" or "do-it-yourself" systems:

[LIST]
[*]Ubuntu - the minimal CLI install from the Alternate CD or Mini ISO offer an easy-to-use Ubuntu base for you to do what you want with.
[*]Debian - arguably more stable and a hair faster than Ubuntu, but with a little less handholding, especially from a CLI netinstall.
[*]Arch - appears to be the distribution of choice for those moving away from Ubuntu and many other users, with great package management and rolling releases.
[*]FreeBSD - IMO, the easiest BSD system to set up and maintain, and while not Linux, it has excellent documentation and is rock-solid.
[*]LFS - for the advanced or adventurous, it offers what is arguably the most custom distribution available, especially if you deviate from the handbook.
[/LIST]

Again, these are only my opinions, and your mileage may vary.

---

### Post by namegame on 2008-12-23
> **Rotaj said:**
> First off, you should look into [The Chakra Project]("http://chakra-project.org/") for a live arch based distro.

I would really recommend that you install Arch yourself. The process really teaches you about how Arch works.

Chakra does everything for you, which is good for an experienced arch user that needs a system very quickly, but can be bad for Arch "newbies."

For example, the arch install process teaches you to function without a GUI, so in the the event that your GUI breaks, you know how to recover without freaking out.

Chakra does nothing to teach you about /etc/rc.conf or even pacman (arch package management) for that matter.

For example, some packages require that you add the daemon to your /etc/rc.conf. Unfortunately, Chakra doesn't teach you how to do this. So when this happens some users won't know what to do.

A normal Arch installation will teach you the process.

I'm not normally one to discourage use of a particular distribution, but Chakra seems to be a blessing and a curse combined.

---

### Post by wolfen69 on 2008-12-23
> **Sorivenul said:**
> 
[*]Debian - arguably more stable and a hair faster than Ubuntu, but with a little less handholding, especially from a CLI netinstall.


this gets my vote.

---

### Post by Xiong Chiamiov on 2008-12-24
> **namegame said:**
> I would really recommend that you install Arch yourself. The process really teaches you about how Arch works.

...

For example, the arch install process teaches you to function without a GUI, so in the the event that your GUI breaks, you know how to recover without freaking out.

++

Arch is very nice, and very simple and clean.  It stopped me from distro-hopping.

---

### Post by .ben on 2008-12-24
> **Rotaj said:**
> First off, you should look into [The Chakra Project]("http://chakra-project.org/") for a live arch based distro. Also, [Sabayon]("http://www.sabayonlinux.org/") is based off of Gentoo.

Secondly, do you have a preference regarding the desktop envionnment?

Lastly, [Distrowatch ]("http://distrowatch.com/")is a distro-hoppers friend.

Xfce by far. Either that or Gnome.
Sabayon seems great, but it uses KDE 4.x, no?

---

### Post by billgoldberg on 2008-12-25
I would recommend Arch or Ubuntu (bare install available on alternate cd).

I use Arch myself and it's better than Ubuntu for me.

Too bad it's repos aren't that big.

---

### Post by mips on 2008-12-26
Arch.

---

### Post by RedSquirrel on 2008-12-27
In the past, I've gotten good mileage from minimal installations of Ubuntu and Debian. These days, I prefer either Gentoo or Slackware for a minimal base.

---

### Post by Kinetic Being on 2008-12-27
> **.ben said:**
> 
I have been _distro-hopping_ for quite some time now, and I thought it would be nice to finally find a _niche_ so to speak, to fit into. That said, I have looked at Arch/Gentoo and both caught my attention.** Yet the fact that it seems they do not have a LiveCD available is kind of a downer, since I currently do not have a CD reader available (please do not shoot me).**

Kind regards,
Ben.

You don't even need a Live CD to install Gentoo.

Just use the Ubuntu one to resize your partition for another one for Gentoo, then go back into your regular Ubuntu (or other) installation, and just follow the steps in the guide for a stage3 tarball. You do everything in a chroot environment anyway, it doesn't matter where you are at that point. You can use the Ubuntu Live CD if you want, but I prefer to be in my regular setup to listen to music and such...

This way you have all the comforts of your current setup, while installing Gentoo. Plus, you can take your time and do it right, because you can still use your computer to watch movies, listen to music, or surf the web. The whole installation is just done through the terminal.

---

### Post by sub2007 on 2008-12-27
I'd definitely recommend Arch - I think it's an excellent bare canvas distro and provided you follow the guide shouldn't have too much difficulty installing it. This will help a lot if you are looking to make the switch to Arch: [http://wiki.archlinux.org/index.php/Beginners_Guide](http://wiki.archlinux.org/index.php/Beginners_Guide). 

I believe that there's a way of installing Arch via FTP without a CD using UNetBootin ([http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)) but I've never used it so I'm not sure of the details of how to do it - there are instructions at the site.

---

### Post by init1 on 2008-12-29
TTYLinux
[http://www.minimalinux.org/ttylinux/](http://www.minimalinux.org/ttylinux/)

---

