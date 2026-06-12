---
title: "Setting up my first machine, which image to use"
date: 2015-11-21
forum: New to Ubuntu
---

### Post by Jan_Erik on 2015-11-21
[COLOR=#000000][FONT=Consolas]I am new to Ubuntu studio and I am just about to set up my first machine. However I am not quite sure which ISO to choose. I.e 32 vs 64 bit and Trusty Tahr vs Wily Werewolf. The machine is a Thinkpad T61 with 4 gb ram. I will mainly use Pure Data and Supercollider. Any recommendations? Pros and cons?[/FONT][/COLOR]

---

### Post by sudodus on 2015-11-21
Thinkpad T61 has an Intel core2duo processor. With 4 GB RAM, I suggest that you try the 64 bit version of the newest version with long time support, ***Ubuntu Studio 14.04.1 LTS*** and update/upgrade it to be up to date.

Try ***live*** before you decide what to install.

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

I don't know the application programs Pure Data and Supercollider. Do you know if there are linux versions of them? If there are, but only available for 32-bit systems, you should try the 32-bit version of Ubuntu Studio instead. If they are not available in linux at all, you should check if they work well with wine,

[https://appdb.winehq.org/](https://appdb.winehq.org/)

If not, you should consider dual booting with Windows - 'Run the operating system that works with your application program' - or find another tool, that can do what you want to do in linux.

---

### Post by Vladlenin5000 on 2015-11-21
[SupperCollider PPA]("https://launchpad.net/~supercollider/+archive/ubuntu/ppa") (up to 14.04)

Pure Data (pd-vanilla) is already in the repositories. [Additional info and PPAs]("https://puredata.info/docs/faq/debian").

---

