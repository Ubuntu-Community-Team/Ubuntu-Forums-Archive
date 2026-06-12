---
title: "&quot;Linux From Scratch&quot; Talk"
date: 2006-08-07
forum: Other OS Talk
---

### Post by RAV TUX on 2006-08-07
I have decided to start a series of threads specifically for technical help for other Distros...the Distro is listed in the thread title. This is primarily for Ubuntu users who test or use other distros and feel most comfortable seeking help in our own community. In no way does this superceed the help you should also be getting from the perspective Distro., in fact I encourage you to be as active in their forums as you are here and post ideas, knowledge and solutions here to provide a reference point to share, reference links are encouraged.

*****Distros based on "Linux From Scratch" Tech Talk*****

---

### Post by RAV TUX on 2006-08-07
I have decided to start a series of threads specifically for technical help for other Distros...the Distro is listed in the thread title. This is primarily for Ubuntu users who test or use other distros and feel most comfortable seeking help in our own community. In no way does this superceed the help you should also be getting from the perspective Distro., in fact I encourage you to be as active in their forums as you are here and post ideas, knowledge and solutions here to provide a reference point to share, reference links are encouraged.

***Linux From Scratch Tech Talk***

---

### Post by RAV TUX on 2006-08-07
I have decided to start a series of threads specifically for technical help for other Distros...the Distro is listed in the thread title. This is primarily for Ubuntu users who test or use other distros and feel most comfortable seeking help in our own community. In no way does this superceed the help you should also be getting from the perspective Distro., in fact I encourage you to be as active in their forums as you are here and post ideas, knowledge and solutions here to provide a reference point to share, reference links are encouraged.

***Devil Tech Talk***

---

### Post by Iandefor on 2006-08-07
How do you do tech support for a distro that doesn't exist?

---

### Post by Archlyric on 2006-08-07
maybe some people cant read? :P  i remember doing the whole lfs guide and dual booting debian (when sarge was still unstable) with lfs... and to be honest, its almost as bad a gentoo... :)

---

### Post by RAV TUX on 2006-08-07
> **Iandefor said:**
> How do you do tech support for a distro that doesn't exist?

this is basically for the 12 distros based on Linux from Scratch:


[The Athene Operating System]("http://distrowatch.com/athene") &#8226; [Core Linux]("http://distrowatch.com/core") &#8226; [Devil-Linux]("http://distrowatch.com/devil") &#8226; [IPCop Firewall]("http://distrowatch.com/ipcop") &#8226; [Lonix]("http://distrowatch.com/lonix") &#8226; [Murix Linux]("http://distrowatch.com/murix") &#8226; [Nasgaïa GNU/Linux]("http://distrowatch.com/nasgaia") &#8226; [Phayoune Linux]("http://distrowatch.com/phayoune") &#8226; [Sentinix]("http://distrowatch.com/sentinix") &#8226; [TA-Linux]("http://distrowatch.com/ta") &#8226; [Yoper Linux]("http://distrowatch.com/yoper") &#8226; [ZENIX GNU/Linux]("http://distrowatch.com/zenix")

Threads merged:

[http://www.ubuntuforums.org/showthread.php?t=231322](http://www.ubuntuforums.org/showthread.php?t=231322)
[http://www.ubuntuforums.org/showthread.php?t=231320](http://www.ubuntuforums.org/showthread.php?t=231320)

---

### Post by zxee on 2006-08-15
I downloaded the live cd of LFS the other day available here[http://www.linuxfromscratch.org/livecd/download.html]("http://www.linuxfromscratch.org/livecd/download.html")
and I'm running it right now. The live cd replaces the older method of needing an installed system to use as your base + it, the live cd, has xfce and the sea monkey browser (netscape really). 
It's kind of fun and I'm thinking about replacing one of my installs with it. ppp set up went rather smoothly via the net-setup command although I had to tweak some chat files-it's always a selling point for me when I can get dial up working.
What else? # uname -a returns:
Linux lfslivecd 2.6.16.27 #1 SMP Thu Aug 3 08:07:04 GMT 2006 i686 athlon-4 i386 GNU/Linux

---

### Post by bjweeks on 2006-08-15
> and to be honest, its almost as bad a gentoo...

Yeah, because compiling everything by hand is some how better than gentoo :rolleyes:

---

### Post by zxee on 2006-08-16
If anyone else is interested in the lfs live cd-it seems excellant for learning more about how linux works there's a lfs hints page here: [http://www.linuxfromscratch.org/hints/](http://www.linuxfromscratch.org/hints/)
You would need this hint: [http://www.linuxfromscratch.org/hints/downloads/files/install-lfs-from-livecd.txt](http://www.linuxfromscratch.org/hints/downloads/files/install-lfs-from-livecd.txt)
to build from the live cd because the lfs book uses an already installed system so there are differences between that an a live cd build/install.

From my experiance so far the arangement and explanations are very clear. I've already gained a better understanding of what is happening as the system/system tools are built.
It also gives me a greater appreciation for a integrated system with package management +.

---

### Post by maniacmusician on 2006-11-13
Well, thanksgiving is coming up. That means that the blessed week of relaxation is coming as well; time off from school, even suspend my brain to RAM if I so please (ready to boot back up at a moment's notice).

So, I decided that in that time, I will take my old p3 laptop with 300 something MBs of RAM and install LFS on it. I was thinking Gentoo at first, but LFS seems to be more of a learning experience. It'll be a challenge, given I can just barely even compile stuff. I hope there's some good documentation out there as well to help me along.

I'm looking forward the most to the speed increase it will give me (assuming I succeed). I might finally be able to enjoy that old beast :)

So I just thought I'd share. Have any of you done this? How was the experience? good/bad/not worth it? It'd be cool to hear some opinions and then to add my own after I'm done.

---

### Post by shining on 2006-11-13
LFS is indeed a good choice if you want to learn. And the installation book is the documentation, there is already plenty to read there.
The introduction of the [book]("http://www.linuxfromscratch.org/lfs/view/stable/") has a [Prerequisites]("http://www.linuxfromscratch.org/lfs/view/stable/prologue/prerequisites.html") section, with already links to a big amount of documentations to read before even starting.
Overall, I found the installation very instructive, and flawless (I don't remember having any problems).
However, installing every little lib and application is very time consuming, and starts to be very repetitive after a while.

```

tar xvzf foo.tar.bz2 && cd foo && ./configure --prefix=/usr && make && sudo make install

```

That's neither hard (because you're following the book, so everything is taken care of and works fine), not particularly exciting, and after doing this 20 times and more, I was getting crazy :)
And completing the LFS install will leave you with nothing but a minimal system. You need to follow the BLFS book then, to install the applications you will really use.
Though, you don't want to install everything there, just the apps you need. You just start getting a little overview of dependencies hell by doing so. It's not so bad though, because every deps are documented and linked inside the BLFS book.
It becomes more fun when you try to install an application that isn't listed in the book, where you've to figure out the dependencies yourself, sort out the autotools obscure errors, and other compilation problems, version incompatibilities, etc... :d
Therein lies the reason why I gave up on LFS, I guess. 
That just made me understand how great package managers are, and how much user time is saved by using emerge, and both user time and pc time / power by using apt-get.
It also made me discover several things that other distributions do, and that I had no idea about, like cflags filtering for gentoo.

It's not all so dark of course. The LFS book is really well done and written, and the informations you can learn is really amazing. And building your own linux system, even by following a book, is always quite exciting :)

---

### Post by kuja on 2006-11-13
I imagine the lazy guy's way of doing LFS involves copying over a few archives and a couple well-written python scripts running over night :P

---

### Post by shining on 2006-11-13
> **kuja said:**
> I imagine the lazy guy's way of doing LFS involves copying over a few archives and a couple well-written python scripts running over night :P

Well, actually, there is something like that, it's Automated LFS :
[http://www.linuxfromscratch.org/alfs/](http://www.linuxfromscratch.org/alfs/)

---

### Post by maniacmusician on 2006-11-13
cool. I was pretty excited, but now I'm blanching at having to install every package of KDE manually, lol.

---

### Post by kuja on 2006-11-13
Well, you could use Konstruct to essentially get "kde-core" (or much more if you so desire). That should take some of the work out of it.

---

### Post by RAV TUX on 2006-11-13
Moving to other OS forum.

---

### Post by shining on 2006-11-16
> **maniacmusician said:**
> cool. I was pretty excited, but now I'm blanching at having to install every package of KDE manually, lol.

Well, I guess that's why the kde source isn't totally split up, but there are several group of packages:
[http://www.linuxfromscratch.org/blfs/view/stable/kde/kde.html](http://www.linuxfromscratch.org/blfs/view/stable/kde/kde.html)

Having these groups will indeed makes kde compilation less painful, but there is also a downside.
In Debian and Ubuntu, as well as most other distribs I think, the source packages are just like kde ones (kdebase, kdelibs, kdenetwork,..), but the packages itself are splitted, so it gives you more control.
You can install kopete alone, without installing all other apps from kdenetwork.
On the other hand, if you want to apply a patch to kopete, you do "apt-get source kopete", but it'll give you the whole kdenetwork. So you'll have to recompile the whole kdenetwork.

Maybe it would be better to have a full split on both source and binary packages, for distribs with a package manager.
But on LFS, it's probably better to have these groups.

---

