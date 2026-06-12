---
title: "Any difference between Ubuntu Minimal install vs. Arch Linux install?"
date: 2010-06-02
forum: Recurring Discussions
---

### Post by philthyfill on 2010-06-02
Hello. I'm fairly new to the Linux world. I'm looking into building a lightweight system with either dwm or Openbox as my WM. I've tried using Arch to build a system, but I'm wondering if there are any differences using Ubuntu's minimal install cd and building an Openbox system.

---

### Post by XubuRoxMySox on 2010-06-02
The kernel is a little different, and package management is different. You'll want to check **hardware compatibility** before you try it. That has been a show stopper for alot of people when checking out new distros.

Ubuntu minimal is the basic Ubuntu kernel and system. If you're using Ubuntu and have no hardware issues, I would stick with it. A minimal install with Openbox will absolutely fly at transwarp speed on even a very low-end machine!

Have a look at [Crunchbang]("http://crunchbanglinux.org") if you'd like to try out a minimal Ubuntu/Openbox distro that is ready-made. The current version is based on Ubuntu 9.04. The development version, Statler, is built on Debian and offers both an Openbox version and an Xfce version - both of which are screamin' fast.

Arch is a completely different system, especially with regard to package management. There are arguments back and forth all the time about which is "better," but frankly it just comes down to what you like and what you want.

Minimal Ubuntu is a heckuvalot easier to install for most newbies, and since this question is posed in the Absolute Beginner section, please forgive me if I'm making an incorrect assumption here... but I'd bet that you would find minimal Ubuntu much easier to install and configure.

Enjoy!

-Robin

---

### Post by earthpigg on 2010-06-02
it's a world of difference. i suggest playing around with both in virtualbox.

---

### Post by Shazzam6999 on 2010-06-02
That was a great response.

I just want to throw out that Archbang may be a good choice if you just want to test out Openbox and Arch in a vbox, although I believe it's still kind of unstable (well it's at RC2 apparently) and I haven't tried it myself, but it may be a good way to see if you like Arch + Openbox. Crunchbang is a really great distro too.

---

### Post by vrkalak on 2010-06-02
> **dixiedancer said:**
> 

Have a look at [Crunchbang]("http://crunchbanglinux.org") if you'd like to try out a minimal Ubuntu/Openbox distro that is ready-made. The current version is based on Ubuntu 9.04. The development version, Statler, is built on Debian and offers both an Openbox version and an Xfce version - both of which are screamin' fast.


Either the new **#!Crunchbang** Statler (Debian-based) in either Xfce or Openbox.
I have both.

Have you looked into the new **Archbang**?    [http://www.archbang.org/](http://www.archbang.org/)

An Arch/Linux install with Openbox similar to Crunchbang, except based on Arch instead of Debian.
The easiest and, by far, the fastest Arch build I've ever used or built.  The Archbang devs have done all the set-up and development of Arch.

*On the other hand*  >>  Any Desktop Environment (Xfce, Openbox, LXDE & others) are super fast when NOT installed over a Gnome or KDE base.

---

### Post by snowpine on 2010-06-02
Hi Fill, you would see very little difference in the hours and days after you first installed. Over the course of months and years, you would see there are huge differences between Arch and Ubuntu, including but not limited to: rolling vs. stable release, package management, update policy, culture of the support forums, etc. 

Ubuntu and Arch are both fine distros, and you can't go wrong with either. Like most things in life, if you can clearly articulate the goals ("I need an operating system that does X, Y, and Z.") it will be easier to choose the right tool for the job.

---

### Post by MisfitI38 on 2010-06-02
> **philthyfill said:**
> Hello. I'm fairly new to the Linux world. I'm looking into building a lightweight system with either dwm or Openbox as my WM. I've tried using Arch to build a system, but I'm wondering if there are any differences using Ubuntu's minimal install cd and building an Openbox system.

Though the two resulting systems will be using very similar software, they are nonetheless targeted at very different crowds and have completely different goals.
One tries to keep things simple, while the other tries to keep things easy.
Only you will be able to decide, so give them both a chance.

---

### Post by Tibuda on 2010-06-02
Package management is not really different. There is some correspondence between apt-get commands and pacman commands. The most used commands are:
```
apt-get install = pacman -S
apt-get remove = pacman -R
apt-get update; apt-get upgrade = pacman -Syu
```

But yes, there is a difference. In Arch you have the last software as soon as the new version is released (and packaged by someone). In Ubuntu you only have the last software each six months if you upgrade the system. Both systems have pros and cons.

---

### Post by philthyfill on 2010-06-02
Thanks for all the replies. I guess my real question is how much more automated is the Ubuntu minimal install. I know I would have to install things with the command line which is no problem, but when I was using Arch I would have to delve into config files to setup or tweak things after installs. For Ubuntu, when I install power management tools such as acpid, cpufrequtils, and pm-utils, do I have to add them to DAEMONS or MODULES to have them start up?

---

### Post by Tibuda on 2010-06-02
> **philthyfill said:**
> Thanks for all the replies. I guess my real question is how much more automated is the Ubuntu minimal install. I know I would have to install things with the command line which is no problem, but when I was using Arch I would have to delve into config files to setup or tweak things after installs. For Ubuntu, when I install power management tools such as acpid, cpufrequtils, and pm-utils, do I have to add them to DAEMONS or MODULES to have them start up?

In ubuntu you don't have to do anything. In Arch you have to tweak the rc.conf.

---

### Post by del_diablo on 2010-06-03
In Ubuntu you can't do daemons yourself
In Arch you MUST set up the daemon list yourself

---

### Post by RiceMonster on 2010-06-03
> **del_diablo said:**
> In Ubuntu you can't do daemons yourself

Yes you can.

BootUp Manager, sysv-rc-conf, update-rc.d, etc

---

### Post by del_diablo on 2010-06-03
Still, it geta autoinstalled without your permission. Its a large pain because of that.

---

### Post by kevin01123 on 2010-06-03
> **del_diablo said:**
> Still, it geta autoinstalled without your permission. Its a large pain because of that.

Wait a tic. So, you install a program you want with a daemon, but leave it off?

---

### Post by RedSquirrel on 2010-06-03
> **kevin01123 said:**
> Wait a tic. So, you install a program you want with a daemon, but leave it off?
Sure. cups, for example.

However, I don't consider it to be a problem to turn it off if it was started automatically. I recognize that some systems start these things automatically while others don't and I adapt to whatever I have in front of me. :)

---

### Post by screaminj3sus on 2010-06-05
There is a difference, even  a commandline ubuntu install is more "automatic" and easier than arch. With arch you have to tweak multiple config files.

---

### Post by WinterRain on 2010-06-05
But I doubt there's any appreciable difference in speed between the 2 installs. I did a minimal install of ubuntu on a 700mhz eeepc, and it flew like the wind. You may like arch for other reasons, but I doubt there's much difference in speed as long as you use stock desktop environments. (not ubuntu-desktop)

---

