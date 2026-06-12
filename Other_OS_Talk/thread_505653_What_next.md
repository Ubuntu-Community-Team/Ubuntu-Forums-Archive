---
title: "What next?"
date: 2007-07-20
forum: Other OS Talk
---

### Post by bonzodog on 2007-07-20
Ok, now I have a laptop for my wife that runs feisty and does everything we need as the stable machine, it leaves the AMD64 3000+ desktop machine available for a Linux project.

I have always wanted to build a distro from the ground up, highly customised, but I really wonder whether a source-build distro is worth it.

So, I have whittled it down to a few choices: -

a)Arch Linux - I know I could package build a distro to a very customised spec with this

b)Slackware Expert Install

c)Zenwalk core + Custom packages

d)Sourcemage Linux

e)Free BSD

f)Open BSD

As you can see from my choices above, I am not a massive fan of the Debian Tree for really taking distros apart, or building fast and light. Feisty just makes a good Just Works distro for a Laptop machine is all.

---

### Post by ThinkBuntu on 2007-07-20
If you want  ground-up package build, do a Debian netinstall. Arch actually has the tools to control building from source called the ABS (Arch Build System), so if you wanted to, you could certainly compile your whole system much like Gentoo. The same goes for Slackware, but I don't know which one (Slack or Arch) has a better build system.

If you want a custom Slack system, you really should use Slackware and not Zenwalk core.

---

### Post by RAV TUX on 2007-07-20
> **bonzodog said:**
> Ok, now I have a laptop for my wife that runs feisty and does everything we need as the stable machine, it leaves the AMD64 3000+ desktop machine available for a Linux project.

I have always wanted to build a distro from the ground up, highly customised, but I really wonder whether a source-build distro is worth it.

So, I have whittled it down to a few choices: -

a)Arch Linux - I know I could package build a distro to a very customised spec with this

b)Slackware Expert Install

c)Zenwalk core + Custom packages

d)Sourcemage Linux

e)Free BSD

f)Open BSD

As you can see from my choices above, I am not a massive fan of the Debian Tree for really taking distros apart, or building fast and light. Feisty just makes a good Just Works distro for a Laptop machine is all.

Go with Slackware.

---

### Post by bonzodog on 2007-07-21
You know I think I may well do an Arch Linux Base or FTP Install, then build it from there. 

I have become rather attached to the idea of proper Package repositories, where I can run it right on the bleeding edge using pre-built packages, or have a command line tool that builds the packages on the fly.

Arch linux feels like it's able to cross the Gentoo/Slackware boundary lines.

My build will have only Openbox, and possibly Slim as the login manager. ("But...But..it's a 64 bit Machine with oogles of RAM and a HUGE HDD!!" I hear you cry)

heh..well, something of the geek in me appeals to the idea of how fast and light you can build, only using the tools that you pick and choose yourself.

---

### Post by 5-HT on 2007-07-22
If you're looking for a rolling release distro with a sweet package manager and the ability to integrate custom compiled apps with it using one single command (just a simple: makepkg :)  ) for ease of administration (not to mention a single config file that handles most everything) that you can build up from a barebones base to your hearts content, Arch is a great candidate! They also have some really clear guides on their wiki for installation and getting your feet wet with the 'arch way'.
cheers,

---

### Post by jrusso2 on 2007-07-22
People seem to love ArchLinux.  Source mage is a source distribution, I know one guy who swears by it.

---

### Post by miggols99 on 2007-07-23
Arch Linux. The package manager is really fast and loads of packages are available. Also there are loads of extra packages in the AUR (Arch User Repositories). Programs open really fast too. I use KDEmod, a fast, split packaged KDE for Arch.

---

### Post by ThinkBuntu on 2007-07-23
I still have yet to use a package manager as quick or comprehensive as apt. Keep in mind you can use apt-build and other tools to automate package building. So...you might want to give Debian a go too :^)

---

### Post by bread eyes on 2007-07-23
Frugalware?

---

### Post by kellemes on 2007-07-23
Im an Archer and can give you a lot of reasons for using it, but if building a system from the ground up was my wish, I would probably choose Gentoo, it gives the control you have with ANY GNU/Linux-brand (including Arch) only with Gentoo this control is default.
Great stuff..

---

### Post by Ptero-4 on 2007-07-24
If you&#341;e serious about building from the ground up. You should give linux from scratch a try.

---

### Post by bonzodog on 2007-07-24
I want to avoid source builds, and go for a package distro based on Slackware ( The init system for BSD and Slack rocks!), that I can do a working install to sort of Kernel + toolchain + binutils, then add pre-built packages one by one from a curses based package manager with lists and menus.

It's important for me to also get a distro that makes use of repos and package dependencies.

The two in close contention at the moment are Arch Base (Duke 2007-05), or Zenwalk 4.6.1 Core + Custom packages.

---

