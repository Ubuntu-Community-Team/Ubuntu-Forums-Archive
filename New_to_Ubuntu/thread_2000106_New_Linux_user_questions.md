---
title: "New Linux user questions"
date: 2012-06-09
forum: New to Ubuntu
---

### Post by lkz6998 on 2012-06-09
I am new to Linux, just took the plunge and wiped Win7 from my computer and loaded Lubuntu 12.04 on it.  So far so good, everything seems to work right away.  I'm gonna be on this forum a lot for sure and I have some questions to start out with.
1.  Should I go out and look for the latest drivers for my audio, graphics, ethernet, wifi, chipset, etc?  Or just leave everything alone?  The computer is an Acer Aspire Revo AR3700 and is fairly new, I just bought it 6 months ago.
2.  What is the difference between "Lubuntu Software Center", "Synaptic Package Manager", and "GDebi Package Installer"?  If I'm looking for a program should I just go to any of these three or are there advantages of one over the others?

---

### Post by anewguy on 2012-06-09
I can give you an answer on the first question:  if everything is working - video is fine, audio is fine, wireless is fine, etc., then why would you need to?  Being new, you may want to let some things be when they are working okay.  If changes are made to drivers that ubuntu supplies they will normally come down as part of the normal updates running.

I can't give you answer on the second - I just use synaptic package manager.  I know it handles dependencies (you ask to install package "a", and in order for it to run it requires [hence, depends on] packageb -packagen).

Dave ;)

---

### Post by whatthefunk on 2012-06-09
> **lkz6998 said:**
> I am new to Linux, just took the plunge and wiped Win7 from my computer and loaded Lubuntu 12.04 on it.  So far so good, everything seems to work right away.  I'm gonna be on this forum a lot for sure and I have some questions to start out with.
1.  Should I go out and look for the latest drivers for my audio, graphics, ethernet, wifi, chipset, etc?  Or just leave everything alone?  The computer is an Acer Aspire Revo AR3700 and is fairly new, I just bought it 6 months ago.
2.  What is the difference between "Lubuntu Software Center", "Synaptic Package Manager", and "GDebi Package Installer"?  If I'm looking for a program should I just go to any of these three or are there advantages of one over the others?

1.  If everything works fine, you shouldnt need to mess around with drivers.

2.  Lubuntu software center: You can browse for software by category, search for software, and install software
Synaptic: You can search for and install software, install updates, and probably upgrade your OS when the time comes
GDebi: installs .deb packages.  The only time your system will use this is when you double click on a downloaded .deb package.  ,deb packages are similar to .exe in Windows...clicking on it will install the new program.

---

### Post by codemaniac on 2012-06-09
It is always wiser to stick to that setup which works for you .
All you need is just check for regular security updates and get them installed on your system .

---

### Post by Rodney9 on 2012-06-09
For How-To's and Information on Lubuntu

[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

For  Screen-Casts on Lubuntu

[http://blip.tv/rss/bookmarks/206798](http://blip.tv/rss/bookmarks/206798)

Rodney

---

### Post by xedi on 2012-06-09
> **lkz6998 said:**
> 
1.  Should I go out and look for the latest drivers for my audio, graphics, ethernet, wifi, chipset, etc?  Or just leave everything alone?  The computer is an Acer Aspire Revo AR3700 and is fairly new, I just bought it 6 months ago.


(L)Ubuntu automatically finds and updates all the drivers you need (with exceptions, but since everything is working fine for you, then that's not the case here). You will notice from time to time that the update manager pops up. If you let it install all the updates, it will update the drivers and apps you have installed on your computer.


> 2.  What is the difference between "Lubuntu Software Center", "Synaptic Package Manager", and "GDebi Package Installer"?  If I'm looking for a program should I just go to any of these three or are there advantages of one over the others?

The software center is the most straight forward place to get new apps, you can browse through different categories, look at reviews and so on. Synaptic gives you more options and better control over packages, e.g. if you want to delete just single packages completely without leaving configuration files behind. I would recommend using the software center if you're new unless you feel that there is something you can't do with it.

---

### Post by The Cog on 2012-06-09
> **lkz6998 said:**
> What is the difference between "Lubuntu Software Center", "Synaptic Package Manager", and "GDebi Package Installer"?  If I'm looking for a program should I just go to any of these three or are there advantages of one over the others?
The Software Center and Synaptic both deal with installing and removing software. They both use the same repositories for the software (they are actually both graphical front-ends to the command-line program apt-get). They are compatible - you can use them alternately without messing things up.

The Software Center is more aimed at an "application" way of thinkning about things. Synaptic is more of a "package" way of thinking of things. Large applications tend to be composed of several packages, and to require other packages to be installed. Software Center only shows you the broad applications. Synaptic shows all the individual packages. Both applications automatically handle dependencies where one package need others to work, but Software Center doesn't even tell you about the extra bits it's installing. 

If you're unsure, use Software Center. But it can be interesting to look at Synaptic. If someone tells you that you need a specific package by name, then you will need to use synaptic (or go straight to the command-line apt-get).

Gdebi is a graphical program for installing .deb files that you have downloaded from sources other than the official repositories. It is a front-end to the command-line program dpkg. You are unlikely to want to use gdebi.

For extra detail, remember that both Software Center and Synaptic use apt-get behind the scenes to do their work. Well after it has downloaded them, apt-get calls dpkg to install the package files (and to remove them again if required).

---

### Post by Rex Bouwense on 2012-06-09
Some excellent advice has been offered.  I just want to say welcome to the forums.  We all took the plunge at one time or another.  Mine was a while ago and I haven't looked back since.
Have some popcorn :popcorn: and enjoy the ride.

---

### Post by lkz6998 on 2012-06-09
So, when Lubuntu was installing on my computer, did it detect all of my hardware and then automatically download the correct drivers? (If so, where did it download drivers from?)  Or were the drivers already included on the install ISO? 

I've loaded Windows many times and I always had to go to the manufacturers web site and manually download and install drivers after an OS install.  So I'm amazed that installing Lubuntu was so painless...

---

### Post by sudodus on 2012-06-09
> **lkz6998 said:**
> So, when Lubuntu was installing on my computer, did it detect all of my hardware and then automatically download the correct drivers? (If so, where did it download drivers from?)  Or were the drivers already included on the install ISO? 

I've loaded Windows many times and I always had to go to the manufacturers web site and manually download and install drivers after an OS install.  So I'm amazed that installing Lubuntu was so painless...
Hardware detection and many drivers are included in the linux kernel. But there are exceptions: some graphics chips/cards and wifi chips/cards and printers need proprietary drivers. And in some cases there are no drivers at all. As many other people you were lucky :-) And now that you are running Lubuntu, I suggest that you ask here at the Ubuntu Forums before buying new hardware, so that you get something that works out of the box.

---

### Post by Paqman on 2012-06-09
> **lkz6998 said:**
> 
2.  What is the difference between "Lubuntu Software Center", "Synaptic Package Manager", and "GDebi Package Installer"?  If I'm looking for a program should I just go to any of these three or are there advantages of one over the others?

They're all just different ways of using the package manager built into your system. Synaptic and Software Centre overlap a bit. Synaptic used to be the main package manager tool, but it was considered a bit geeky, so they created Software Centre to provide something a bit more user-friendly. Gdebi is an old tool for installing packages manually, it's been largely superseded by Software Centre, but is still useful because it's small and quick.

---

### Post by Paqman on 2012-06-09
> **lkz6998 said:**
> So, when Lubuntu was installing on my computer, did it detect all of my hardware and then automatically download the correct drivers? (If so, where did it download drivers from?)  Or were the drivers already included on the install ISO?


Yep. 

> I'm amazed that installing Lubuntu was so painless...

Good isn't it? Welcome to Linux, you may well find using a computer much less of a pain from now on ;)

---

