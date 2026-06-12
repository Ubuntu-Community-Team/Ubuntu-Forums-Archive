---
title: "looking for another flavor of Linux/Unix"
date: 2008-02-12
forum: Other OS Talk
---

### Post by fissionmailed on 2008-02-12
I'm running Ubuntu 7.10 on my computers now but I'm looking for something new.  I want to move away from depending on a GUI and really learn Linux.   Plus GUIs have been not working great for me in configuring stuff so... haha  Anyway, I'm looking for a more command line run Linux so it'll force me to learn it at a higher speed.  Don't worry, I'm still going to keep Ubuntu on all my computers, it is nice to have don't get me wrong but I want to challenge myself.  I was thinking Linux, but something Unixed based would be fine too, even if they have some different commands)

#1.  The options of never going into a GUI and running it all command line
#2.  Having a GUI is a plus though.
#3.  It would be nice if the distro community was helpful like Ubuntu but also has a lot of stuff in wikis etc so I don't have to bother people(like I am now haha).
#4.  Installation is something I want to be easy but it doesn't have to be brain dead easy.


[This]("http://support.gateway.com/s/PC/R/5041/5041sp3.shtml") is the comp I'll be putting it on, it doesn't have to work straight out of the box but I sort of don't want to spend a month getting it to work(like my laptop).

Thanks in advance guys (and gals).

---

### Post by KCPokes on 2008-02-12
Go with a server version.  You'll get the options of having a GUI, if needed, but by default you'll be working via command line.  

If you want to just play and see what you can accomplish with a distro, I recommend Arch.  It tends to get you more in touch with what the distro is doing while still allowing you to create a standard desktop environment.

---

### Post by fwojciec on 2008-02-12
My suggestions:

1) Gentoo -- source based distro, excellent documentation
2) Slackware -- the venerable plain vanilla linux
3) Arch Linux -- binary distro that gives you full control over the system

---

### Post by fissionmailed on 2008-02-12
> **KCPokes said:**
> Go with a server version.  You'll get the options of having a GUI, if needed, but by default you'll be working via command line.  

If you want to just play and see what you can accomplish with a distro, I recommend Arch.  It tends to get you more in touch with what the distro is doing while still allowing you to create a standard desktop environment.

Hhhmmm I never thought about that, that's a good idea!

From a quick look at their site it looks promising.  I actually don't know too much about the different distros, because I was giving an Ubuntu cd by some and have been running with it.  :o

Arch looks pretty good, any one else have any suggestions?


Edit: just saw your list fwojciec, looking into those now.

---

### Post by Hevoos on 2008-02-12
Slackware is simply the best if you want to learn Linux. It is quite simple to use and the config files are really well commented, which makes it easy to edit those. It has a GUI aswell (KDE, Fluxbox, Blackbox, Xfce) so that's no problem. ;)

One of its goals is to be "Unix-like" and in fact it uses BSD-init scripts for boot. When you learn how to use Slackware you learn how to use Linux.

---

### Post by LaRoza on 2008-02-12
I recommend not installing a server unless you want to run a server.

You can use the Alternative disk to install a command line only system.

You can move

```

/etc/init.d/gdm

```

To another directory, and this will prevent GNOME from starting, but you can run the script manually if you wanted to at any time.

---

### Post by fissionmailed on 2008-02-12
> **Hevoos said:**
> Slackware is simply the best if you want to learn Linux. It is quite simple to use and the config files are really well commented, which makes it easy to edit those. It has a GUI aswell (KDE, Fluxbox, Blackbox, Xfce) so that's no problem. ;)

One of its goals is to be "Unix-like" and in fact it uses BSD-init scripts for boot. When you learn how to use Slackware you learn how to use Linux.

Hhmmm, it does have 6 cds though O_O. I"ll give it a try though, can't hurt. 


> **LaRoza said:**
> I recommend not installing a server unless you want to run a server.

You can use the Alternative disk to install a command line only system.

You can move

```

/etc/init.d/gdm

```

To another directory, and this will prevent GNOME from starting, but you can run the script manually if you wanted to at any time.

hhmmmm thanks for the info, I'll look into that also. 

Thanks again guys. :)

---

### Post by new2*buntu on 2008-02-12
> **fissionmailed said:**
> Hhmmm, it does have 6 cds though O_O. I"ll give it a try though, can't hurt. 




I do not think that you have to download all of the CDs to install. I think the CDs are just addon packages, kind of like Debian's 23 CDs. You only need the first Debian CD to install.

---

### Post by sujoy on 2008-02-12
I agree totally with fwojciec. If you want control on your OS and learn to maually edit config files, then you should choose between gentoo,slackware and arch. However, having used all three, I would recommend arch, installs quick, has good support documentation and a great package manager. 

I have both my desktop and laptop running arch now :), with the laptop dual booting arch and ubuntu.

---

### Post by init1 on 2008-02-13
TTY Linux would be perfect for this. 
[http://www.minimalinux.org/ttylinux/](http://www.minimalinux.org/ttylinux/)
I also recommend Minix3
[www.minix3.org](www.minix3.org)

---

### Post by SunnyRabbiera on 2008-02-13
BSD!
Now there is a challenge :D

---

### Post by rahulthewall3000 on 2008-02-14
If you want to learn Linux - go the Gentoo way. Download the mininal CD and follow the handbook to start installing it. Gentoo has simply the best documentation out there. (it needs it as well :P) Another advice, do not use genkernel, choose the kernel options manually, it is more fun that way. And it does not take that long to setup. The most important part is choosing the right options in the kernel and the right USE flags.

---

### Post by jseiser on 2008-02-14
just another one to through out there.  Try Sourcemage GNU/Linux, I dont want to say its better then Gentoo, its slightly different, both are source based, but i prefer it over gentoo.  You can also try install Solaris 10, thats pretty unix.  Installing everything from source in gentoo or sourcemage etc, doesnt really teach you anything though.  You just look what flags you want(in gentoo) and assign them.  So maybe crux/arch/slack

---

### Post by tommcd on 2008-02-14
For Slackware you only need the first 2 CDs. With 2 CDs you get all of KDE and all of XFCE.
The Slackware forums at linuxquestions.org are very good. Those guys are some of the most knowledgeable linux geeks you will find anywhere.
As for documentation for Slackware:
[http://slackbook.org/](http://slackbook.org/)
[http://www.slackware.com/~alien/](http://www.slackware.com/~alien/)
[http://www.slackbasics.org/html/](http://www.slackbasics.org/html/)
[http://shilo.is-a-geek.com/](http://shilo.is-a-geek.com/)
[http://humanreadable.nfshost.com/sdeg/index.htm](http://humanreadable.nfshost.com/sdeg/index.htm)

---

### Post by mivo on 2008-02-15
BSD isn't so different from Linux. If you go into that direction, FreeBSD is probably the most suited choice, though be prepared for generally worse hardware support than you get with Linux (for newer hardware -- older hardware is good well and even better supported). Also, some typical consumer desktop stuff, like Skype and Flash, is either not available or fairly unstable. But yes, it's an interesting OS. I used FreeBSD for some time. :)

For Linux, I think Arch Linux is the way to go. Hit their wiki and look for the Beginner Guide -- it's a good walkthrough, and you'll learn a lot on your way.

---

### Post by fissionmailed on 2008-03-02
A little late, but thanks.  I'm going to install Archlinux and Slackware this week while on springbreak.  I might try FreeBSD on my old laptop which is about 10 years old. :lolflag:

---

