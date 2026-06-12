---
title: "[SOLVED] Question about Ubuntu's requirements"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by LinuxFox on 2008-11-04
I have a question about Ubuntu requirements.  Buying a new computer is quite expensive for some people, and Ubuntu is of course free to download, use, and upgrade.

I want to know, how often do the requirements change for Ubuntu?  I know with every new Windows there's always new requirements.  I'm using a Ubuntu 8.04, which is an LTS version that's lasts until 2011.  

I'm just kind of worried if I don't get a new computer by 2011, I can't use Ubuntu.  So far, I'm liking this even more than Windows and MacOS 7 (my first computer), I'd hate to be left out if the repositories go offline and I can't upgrade.

---

### Post by bumanie on 2008-11-04
Ubuntu attempts to make an OS thta can run on older computers as well as new ones. [Look here]("https://help.ubuntu.com/community/Installation/SystemRequirements") for system requirement details. This has been a long term objective and as far as I know will continue into the future. If your present system runs 8.04 - it will run 8.10 and the proposed 9.04.

---

### Post by drs305 on 2008-11-04
I don't think any of us can be absolutely sure where computer hardware will be in 3 years but I feel relatively confident that you will be better off with open source / linux distributions than you will be with Windows or Mac.

Open source will provide many more options should you decide not to upgrade, and of course ubuntu already has Xubuntu which can work with less capable machines.

By the way, here is the Ubuntu documentation page on current system requirements:
[SystemRequirements]("https://help.ubuntu.com/community/Installation/SystemRequirements")

---

### Post by LowSky on 2008-11-04
I am running a computer that is 3 years old and its fine, I also have a 8 year old laptop running Xubuntu and its a little slow but still functional. Anything you buy today will work very well in the next 5 years.

---

### Post by mr_raider on 2008-11-04
You can keep your 8.04 beyond 2011 you know. End of support doesn't mean it'll implode!

---

### Post by snowpine on 2008-11-04
You can continue to use 8.04 Hardy after 2011 if it works well on your computer. You just won't receive any more updates.

I think it is highly likely that minimum system requirements will continue to increase over time. However, I think that Ubuntu will always support lower-spec computers--if not Ubuntu then a branch like Xubuntu--because part of their mission is to spread the technology throughout the world to people who don't have access to the latest hardware.

---

### Post by billgoldberg on 2008-11-04
> **LinuxFox said:**
> I have a question about Ubuntu requirements.  Buying a new computer is quite expensive for some people, and Ubuntu is of course free to download, use, and upgrade.

I want to know, how often do the requirements change for Ubuntu?  I know with every new Windows there's always new requirements.  I'm using a Ubuntu 8.04, which is an LTS version that's lasts until 2011.  

I'm just kind of worried if I don't get a new computer by 2011, I can't use Ubuntu.  So far, I'm liking this even more than Windows and MacOS 7 (my first computer), I'd hate to be left out if the repositories go offline and I can't upgrade.

The requirements will most likely go up by 2011, but if you buy a new pc now, it should still run the latest in 2011.

Should it not (a lot can happen in that time) there are low-end distro's like Xubuntu, Fluxbuntu, Arch, ... that can do just as much, with less.

---

### Post by LinuxFox on 2008-11-04
> **snowpine said:**
> You can continue to use 8.04 Hardy after 2011 if it works well on your computer. You just won't receive any more updates.

I think it is highly likely that minimum system requirements will continue to increase over time. However, I think that Ubuntu will always support lower-spec computers--if not Ubuntu then a branch like Xubuntu--because part of their mission is to spread the technology throughout the world to people who don't have access to the latest hardware.I know I can continue using it, I'm a bit concerned about losing the ability to install software.  Which shouldn't be much of a problem, since I learned about APTonCD and it backed up all the software I installed to CD. Gosh, the Ubuntu community thinks of everything! 8)

Xubuntu for lower end computers, cool.  Does Xubuntu have a Live CD feature?  I'd like to get a feel for it if I can.  Also, does Xubuntu use the same exact software as Ubuntu?  You know the deb packages.

---

### Post by bumanie on 2008-11-04
Instead of installing xubuntu as a separate installation, you can install the xubuntu desktop and choose which desktop to boot into. At the login screen go to options and choose whether you want ubuntu or xubuntu for that session. To install xubuntu desktop > sudo apt-get install xubuntu-desktop

---

### Post by LinuxFox on 2008-11-04
> **bumanie said:**
> Instead of installing xubuntu as a separate installation, you can install the xubuntu desktop and choose which desktop to boot into. At the login screen go to options and choose whether you want ubuntu or xubuntu for that session. To install xubuntu desktopNice, I just did this.  It feels kind of like Ubuntu.  It's cool I can switch between the two. 8)

Though I'm concerned a bit about software packages.  Does a regular Xubuntu install use the same deb packages and package manager as Ubuntu?  I'd like to know if I ever had to use Xubuntu to upgrade, in case the latest Ubuntu would not run on my machine (if I don't have a new computer).  Right now, it feels like I'm using a Xubuntu skin for Ubuntu. It's still Ubuntu, just with a different desktop.

---

### Post by LowSky on 2008-11-04
Ubuntu and Xubuntu can run all the same software

no need to worry

---

### Post by LinuxFox on 2008-11-04
> **LowSky said:**
> Ubuntu and Xubuntu can run all the same software

no need to worryThanks, this what I wanted to know about Xubuntu.  I have software I like that's compatable with Ubuntu, and now I know they'll work if I use Xubuntu.  

At least there's Xubuntu as an option if I can't get a new computer and I want to upgrade to a newer version of Ubuntu.

---

### Post by silverglade00 on 2008-11-04
> Right now, it feels like I'm using a Xubuntu skin for Ubuntu.

That's basically how it works. Underneath everything is the Ubuntu system. X Windows is the part that draws graphics stuff on the screen. Then there are window managers that run on top of X and keep track of your windows. The one used in regular Ubuntu is called Metacity. 

Then there are desktop environments, which are a collection of a window manager and applications that are designed to work together well. Xubuntu uses XFCE, which is lightweight and runs well on older hardware and screamingly fast on newer hardware. The one that a regular Ubuntu install uses by default is called GNOME. Kubuntu uses KDE (K Desktop Environment). You can mix and match them all. There are others as well, but these are the most popular ones. 

In the Ubuntu system, they all use the same packages and underlying systems. Think of it as installing 3 different text editors in Windows. You still have Notepad, but you can also use Notepad++ and Wordpad, with differing feature sets. Underneath it all, you are still running Windows.

---

### Post by LinuxFox on 2008-11-04
Thanks for the reply silverglade00.  That gives me a good idea on how Xubuntu and Kubuntu works.  I thought they were all different because of their names.

---

### Post by louieb on 2008-11-04
A few years ago I installed Ubuntu 5.10 on a P1-200 mHz PC with 128MB ram. It was functional for surfing the internet and email. But a program like gimp would slow it to a crawl. Don't have that PC anymore but doubt Ubuntu 8.10 would run very well if at all.  

[IMG]http://louboldt.com/ptwocents.gif[/IMG] Software of today needs better hardware than the software of the past. But there will be Linux distributions capable of running on older slower hardware. I bet today that 1992 built P1-200 would run several distributions well. Puppy, DSL, and Deli Linux are 3 that come to mind. 

If that old P1 can run Linux today. I bet any machine bought today will run the latest and greatest Linux quite well for several years to come.

---

