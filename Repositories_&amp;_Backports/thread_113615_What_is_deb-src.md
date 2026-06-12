---
title: "What is deb-src?"
date: 2006-01-06
forum: Repositories &amp; Backports
---

### Post by Zerlinna on 2006-01-06
Hey there,

I'm just aksing myself what is the difference between lines beginning with "deb" and those beginning with "deb-src"? Do I always need the deb-src line, too? 

Thank you,

Z.

---

### Post by Zerlinna on 2006-01-06
Lol, I've just found it myself: those are sources and not packages :-) 

> # Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

:rolleyes: 

Z.

---

### Post by Scifer on 2010-08-17
Is it safe to comment all deb-src lines since I'm not a developer.

---

### Post by uRock on 2010-08-17
> **Scifer said:**
> Is it safe to comment all deb-src lines since I'm not a developer.
As long as the non-src sources are being used, you'll be fine with doing that.

---

### Post by RainCT on 2010-08-22
The lines starting with "deb" are binary package repositories (ie. the place where the ".deb" packages which get installed are downloaded from).

The ones starting with "deb-src" are source package repositories, which provide access to the source code of the applications and the files needed to create a ".deb" package out of them.

So, unless you are involved with packaging work, or you want this as a convenient way to access the application's source code (if you have the appropriate "deb-src" lines you can get the code for, eg., gbrainy, by running "apt-get source gbrainy"), you can just comment out those lines.

If you don't want to edit the sources.list file directly, you can disable them through a graphical interface by going to System -> Administration -> Software Sources, and in the first tab, under "Downloadable from the Internet", uncheck the "Source code" box.

---

### Post by gregzeng on 2010-10-30
> **RainCT said:**
> The lines starting with "deb" are binary package repositories (ie. the place where the ".deb" packages which get installed are downloaded from).

The ones starting with "deb-src" are source package repositories, which provide access to the source code of the applications and the files needed to create a ".deb" package out of them.

So, unless you are involved with packaging work, or you want this as a convenient way to access the application's source code (if you have the appropriate "deb-src" lines you can get the code for, eg., gbrainy, by running "apt-get source gbrainy"), you can just comment out those lines.

If you don't want to edit the sources.list file directly, you can disable them through a graphical interface by going to System -> Administration -> Software Sources, and in the first tab, under "Downloadable from the Internet", uncheck the "Source code" box.

I tried to add the sources listed above to Synaptic but could not.

I need the Linux equivalent to NORTON GHOST.  When I follow the instructions in the below URL, the Linux "expert" fails, cos I get the message that I have no sources.  Checking Synaptic, I do.

"Build your own packages (all architectures)

To manually build packages of the current versions you need a "deb-src ..." entry in your apt sources.list and you need to update the package list"

[http://moblock-deb.sourceforge.net/](http://moblock-deb.sourceforge.net/)

Still trying to duplicate my existing Ubuntu system, b4 installing a new HDD.  Can Linux do this?

---

### Post by jre on 2010-11-01
Have you[LIST=1]
[*]replaced the "..." with the correct line (e.g. ```
deb-src http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu maverick main
```
[*]updated your package list ```
sudo aptitude -u
```
[/LIST]

BTW, I doubt that moblock is the equivalent to Norton Ghost, but I don't know the latter application.

BTW2: Please start a new thread for your own questions and do not hijack an old one.

---

