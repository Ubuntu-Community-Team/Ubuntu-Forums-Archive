---
title: "Want To Learn More About Linux. Need Distro Suggestion"
date: 2007-08-25
forum: Other OS Talk
---

### Post by tdrusk on 2007-08-25
I want to make a project. I want to use an os like gentoo or arch because I heard you have to compile everything so it is really fast. Any suggestions for which I should use or another one? I am not amazing with Linux yet, so a guide would be necessary for the OS. Any ideas?

---

### Post by b0ng0 on 2007-08-25
I know that with Arch you don't need to compile everything but you do get a very minimal base install so you have to add things to it yourself. 

For example, if you want USB devices to automount when plugged in you have to create your own daemon for that. But I have seen it in action and it is VERY fast and with KDEmod it looks fantastic.

Gentoo you have to compile everything from source which can take a rather long time but ends up with everythign tailored to your system and so cuts out a lot of the crap that you might normally have. I was considering installing Gentoo myself but it seems like a lot of effot :p

---

### Post by Fonon on 2007-08-25
This is the only Linux distro I have ever used, but perhaps Debian, Fedora, or possibly OpenSuSE would be good for learning?

---

### Post by PhatStreet on 2007-08-25
> **b0ng0 said:**
> I know that with Arch you don't need to compile everything but you do get a very minimal base install so you have to add things to it yourself. 

For example, if you want USB devices to automount when plugged in you have to create your own daemon for that. But I have seen it in action and it is VERY fast and with KDEmod it looks fantastic.
Yep, before I tried Arch, Ubuntu was the only distro I had really used. And Arch taught me **a lot** about the system and all the individual daemons and how they're supposed to be configured.

---

### Post by init1 on 2007-08-25
I learned lots from TTY Linux
[http://www.minimalinux.org/ttylinux/showpage.php?pid=1](http://www.minimalinux.org/ttylinux/showpage.php?pid=1)

---

### Post by revford on 2007-08-25
I've learned lots about the internals and workings of Linux systems by running Slackware for many years.

It's very lean, everything is configured by hand and the config files are very well commented.

---

### Post by fistfullofroses on 2007-08-25
All of the "harder" Linux systems are going to give you better performance. They are configured by you for your system. Easier distros are adding tons of memory resident programs, and daemons that load during boot. The fastest distributions I have seen are Arch, Gobo, and Gentoo. I have used all three, and in my opinion I found Gobo to have the fastest boot time. I found Arch to have the best performance on things like Sauerbraten. Gentoo came in with the fastest compile times.

---

### Post by SOULRiDER on 2007-08-25
Right now im running Ubuntu and Gentoo. Ive ran Arch for a while so I feel I should tell you about my experience with it.

Arch is fast... very fast. You dont need to compile anything if you dont want to, but the PKGBUILDs in the AUR are scripts that youc an run and just compile whatever package you want. The install is very minimal so in order to get xorg and a DE you have to do some work yourself but its nothard to the point where it becomes annoying, ts just hard enough for you to learn how some things are done and understand your system more.
If you want to learn more i HIGHLY RECOMMEND Archlinux.

Gentoo is another story, while it is fast it can be really frustrating, you need to compile EVERYTHING, it takes a liong time and many times, too often for my taste you need to re compile things simply because you updated a single library... While gentoo is also good for learning, i think arch is more learner friendly. Also remember, if youre trying thiongs out its a bitch having to compile stuff just to test a single program.

I suggets you go with arch and then maybe move on to Gentoo.

---

### Post by angryfirelord on 2007-08-25
Also, you could do a minimal install of Ubuntu Server or Debian and apt-get what you need. I find this is the fastest way to gain a performance boost, but won't gain a substantial performance boost.

---

### Post by s26c.sayan on 2007-08-31
> **PhatStreet said:**
> Yep, before I tried Arch, Ubuntu was the only distro I had really used. And Arch taught me **a lot** about the system and all the individual daemons and how they're supposed to be configured.

Same here!!

+1 Arch, if you really want to learn Linux!

I guess Gentoo and Slackware both can claim similarly, but IMHO Arch is better than both in a sense!

Better than Gentoo since Arch offers pre-compiled binaries as default (though there is option to easily custom compile all packages!)
Better than Slackware only because of the great pacman, the package manager of Arch!

---

### Post by wolfen69 on 2007-09-01
try Linux From Scratch. and have alot of patience.

---

### Post by rsambuca on 2007-09-01
+1 [[COLOR="Red"]Linux From Scratch[/COLOR]]("http://www.linuxfromscratch.org/") if you want to learn the inner workings of your system.

By the way, I have never understood the complaints about the compile times in gentoo.  It isn't like you have to sit there and watch it while it is compiling.  You simply type in "emerge <program name>" and you can still do what ever you want with your computer while it compiles the program in the background.

---

### Post by Fbot1 on 2007-09-01
I really don't think that installing and maintaining a distro is really going to teach you much. I think you would be better off looking at code.

> **rsambuca said:**
> By the way, I have never understood the complaints about the compile times in gentoo.  It isn't like you have to sit there and watch it while it is compiling.  You simply type in "emerge <program name>" and you can still do what ever you want with your computer while it compiles the program in the background.

People want to use the program immediately.

---

### Post by rsambuca on 2007-09-01
But other than the Desktop Environment and something like OpenOffice, most of them compile in less than two minutes.

---

### Post by Fbot1 on 2007-09-01
> **rsambuca said:**
> But other than the Desktop Environment and something like OpenOffice, most of them compile in less than two minutes.

Well obliviously it's going to vary between computers but there are other apps that take a long time to compile (a lot of those have bin ebuilds but some don't).

---

### Post by YoungGods on 2007-09-02
+1 [Arch]("http://www.archlinux.org/") I'm sure you will learn a lot from it. I'm currently using it with [kdemod]("http://kdemod.ath.cx/") and it's great.

---

### Post by raul_ on 2007-09-02
I would stick with Arch, but I don't consider it a hard distribution. The cool thing is that every config file is very well commented, but you only have to mess with one file, that is rc.conf. That little single file contains almost every major configuration about your system: network, locale, daemons to run at boot, modules to be loaded, etc. It's similar to Slackware.

I tried Gentoo (Actually Sabayon) but it didn't convince me. I tried to install firefox with emerge, and i stood there for half hour until i cancelled and reinstalled Arch

---

### Post by raul_ on 2007-09-02
> **b0ng0 said:**
> 
For example, if you want USB devices to automount when plugged in you have to create your own daemon for that.

Now that works out of the box.

---

### Post by regomodo on 2007-09-04
> **Fonon said:**
> This is the only Linux distro I have ever used, but perhaps Debian, Fedora, or possibly OpenSuSE would be good for learning?

I'm not too sure about Debian. I use it on my laptop and i find it to be faster. TBH i find it almost like Ubuntu but more stable and faster.

I'm toying with LFS, Arch and Gentoo. I've just played around with LFS but i'm going to try liveLFS instead.

---

### Post by kazuya on 2007-09-07
> **YoungGods said:**
> +1 [Arch]("http://www.archlinux.org/") I'm sure you will learn a lot from it. I'm currently using it with [kdemod]("http://kdemod.ath.cx/") and it's great.

Thanks YoungGods, I am using this now. Arch is a dream. I know much more now than I did before. I probably give some credit to vector or slackware though. But arch is a very good distro to learn linux and still have the benefit of some lightening quickness on an older machine..

---

### Post by rsambuca on 2007-09-07
I wonder if the OP ever did pick one!

---

