---
title: "Talk to me about Archlinux"
date: 2007-11-03
forum: Other OS Talk
---

### Post by PurposeOfReason on 2007-11-03
I started using Ubuntu, and linux, in about February of this year and since them I've become fairly confident that I can get around doing just about anything without much difficulty. I've seen lots of people using Archlinux and am curious to know what's so great about it and how it differs from Ubuntu. Basically, could someone talk to me about everything? How it's installed, what do I start with? Right now I'm using Ubuntu with fluxbox, is it worth a switch for someone who really likes to tweak?

---

### Post by meborc on 2007-11-03
> **PurposeOfReason said:**
> I started using Ubuntu, and linux, in about February of this year and since them I've become fairly confident that I can get around doing just about anything without much difficulty. I've seen lots of people using Archlinux and am curious to know what's so great about it and how it differs from Ubuntu. Basically, could someone talk to me about everything? How it's installed, what do I start with? Right now I'm using Ubuntu with fluxbox, is it worth a switch for someone who really likes to tweak?

i use ubuntu+fluxbox as well... and i like to tweak :)

i have tried arch before, but always turned back to ubuntu... i like to tweak, but when i break my system, i also like to be able to reinstall everything easily... using arch was a bigger learning curve then i expected... i suggest you free some space and create a separate partition for testing arch.... 

the best thing about arch is that you start with very little, but you can build it to anything... and since you configure practicly everything to your box, it will run like a wind

try it out!

ps read the archlinux wiki page for more info!

---

### Post by mindtrick on 2007-11-03
I didn't use Arch for a long time but I've installed it and used a bit so I'm writing what I've observed.

- There are two cd images, core and ftp. Core has a base linux system and ftp pulls everything from the net. I did a ftp install. Installing is harder than any other binary distro I've tried. You have to edit configuration files rather than doing it with gui wizards. 

[http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide](http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide)

this page has info about what you need to do. It's not as hard as it looks though.

- Installing xorg and kde (or gnome or any other de o wm) will not automatically result as a working desktop environment. You have install xf86-input-mouse and keyboard for making your mouse and keyboard work with X. You also need drivers for vesa or nv (vesa doesn't work for my Nvidia card so I use nv) and change the driver in xorg.conf to add your driver. By the way you need to generate a xorg.conf by hwd or xorgconfig

I used kdemod, an optimized and beautified KDE modificiation. It was really fast. Programs start very quickly and system boots very fast. Packages are optimized of i686 so it's faster than i386 distros. It has a really good package manager, pacman. Installing packages were faster than any other distro I tried (except Slackware)

Can't say it's very stable, it's rolling release distro kind of like Debian Sid, and there are always new bugs with newer packages,  you update your system with a single command pacman -Syu. And one more thing, be careful what repository you choose for installing packages because most of the repositories are dead slow and it can take hours to pull all needed packages. I used hosteurope server, it's not very fast but faster than other ones I tried. 

Good luck! 

By the way if you find Arch too complex and buggy there's also Frugalware which has a stable branch and also uses pacman for package management. (It has a current branch as well) And it's as fast as Arch. (i686)

---

### Post by fwojciec on 2007-11-03
Read the Arch wiki is good recommendation  - that would be proper [Arch way]("http://wiki.archlinux.org/index.php/The_Arch_Way") :)  The philosophy in Arch is very practical and pragmatic, and to use Arch properly one has to learn how to do it in accordance with it - since it is reflected in how the system is designed and expected to operate.

It's definitely true that Arch, in comparison to Ubuntu, makes different assumptions about the user.  Whether Arch or Ubuntu would be better for you depends on how you prefer to use your computer.  This is also from [Arch wiki]("http://wiki.archlinux.org/index.php/Arch_vs_Others#Arch_vs_Ubuntu"):
> Arch has a simpler foundation than Ubuntu. If you like to compile your own kernels, try out bleeding-edge CVS-only projects, or build a program from source every once in a while, Arch is better suited. If you want to get up and running quickly and not fiddle around with the guts of the system, Ubuntu is better suited. In general, developers and tinkerers will probably like Arch better than Ubuntu.
In Ubuntu you get a stable default that's customizable to an extent and just works for a good percentage of people.  In Arch you get a very transparent system that, by design, gives you full control over how things work.  If you are unwilling to learn the system, then you will be disappointed because Arch does not "just work".  If you do learn the system Arch can be very stable (it depends on how you use it), it makes it easy for the user to get things to work, it is easy to troubleshoot, and, in the long run, almost banal to maintain in the flux of open source development.

---

### Post by pelle.k on 2007-11-03
Why do we need another thread, when there's "[Arch Linux Talk]("http://ubuntuforums.org/showthread.php?t=231311")" ?

---

### Post by n3tfury on 2007-11-03
i've seen worse offenses.  take a look at the cafe on any given day.

---

### Post by david_2001 on 2007-11-03
An Arch Linux core install gives you a blank canvas (= just the console), so before you start you really do need to know where you want to go and not be afraid get there with only the command line, a text editor and the excellent Arch Wiki to help you.

Personally, I decided to replicate my Ubuntu feisty desktop in Arch64 and it took a weekend to achieve - that's a core install from CD followed by xorg, gnome, compiz-fusion from source, cups, hplip for the printer, a 32-bit chroot for the scanner driver, OpenOffice.org, Crossover Linux, VirtualBox and sundry other applications that I use regularly.  Stability has been rock solid so far and responsiveness can only be matched by the likes of Slackware.

---

### Post by Rumor on 2007-11-03
I've been using Arch exclusively for quite a while and have found that for me, it is the ideal distro.

Read the beginner's guide, or at least those parts that would be pertinent to you before you install: [http://wiki.archlinux.org/index.php/Beginners_Guide](http://wiki.archlinux.org/index.php/Beginners_Guide)

A base install will bring you to a command prompt where you login as root and begin to install the programs you want and get your system set up the way you want. I read a recent review where the reviewer says that probably no two Arch systems are identical.

What's so great about Arch? There are several things about Arch that suit me just fine.

1) Pacman, Arch's package manager is a really great piece of software. It is fast, versatile, powerful and easy to use. I've found it consistently faster than aptitude.
[http://wiki.archlinux.org/index.php/Pacman](http://wiki.archlinux.org/index.php/Pacman)

2) Rolling release system - Arch is a "rolling release" meaning that there are no real versions or major new releases. New packages become more or less immediately available and a single "pacman -Syu" will update every package in your system to the current snapshot. So if you use Firefox, it will always be current. You don't have to wait six months for it to be included in the next release. I think this was the single most determining factor for me choosing Arch. The monolithic updates for Ubuntu were always tense, and the periodic updates to the restricted modules alway broke my X because I was using the non-free nVidia drivers. That doesn't happen with Arch.
[http://wiki.archlinux.org/index.php/Arch_Compared_To_Other_Distros](http://wiki.archlinux.org/index.php/Arch_Compared_To_Other_Distros)

3) ABS and AUR - Is your favorite package not in the core or extra repositories? It may be in the AUR (Arch User Repository) where user made packages are available, and anyone can contribute using ABS, the Arch Build System. And, if the package you want is in the aur, you can use yaourt, a pacman wrapper to install it.
[http://wiki.archlinux.org/index.php/AUR](http://wiki.archlinux.org/index.php/AUR)
[http://wiki.archlinux.org/index.php/ABS](http://wiki.archlinux.org/index.php/ABS)

4) the community - The Arch community is smaller than the Ubuntu community, but I have found it to be friendly, for the most part. They are knowledgeable and very helpful. I appreciate that the developers participate in the forums and the users have a real say in what goes on with Arch as a whole.

But, no distro is right for everyone. Give it a try and see what you think.

---

### Post by PurposeOfReason on 2007-11-03
Yeah, I saw the beginners guide earlier. I've been reading it through at I've been messing with my partitions and it isn't as bad as I've heard it made out to be. I **should** have a fully working system this time tomorrow though it'll take a while until I have it just as I like it.

---

