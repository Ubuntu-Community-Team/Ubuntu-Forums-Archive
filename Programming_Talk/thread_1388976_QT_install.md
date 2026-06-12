---
title: "QT install"
date: 2010-01-23
forum: Programming Talk
---

### Post by gnometorule on 2010-01-23
I'm running Ubuntu 9.10. and would like to install QT. I find several libraries etc in the software repositories, but don't seem to see one that looks like the core package. Could someone who is using QT under Ubuntu please tell me how this is supposed to best done? (aka, i can always go to their web page, but would prefer to use the Ubuntu apt system to benefit from automatic updates and removal, if possible). 

Thanks much.

---

### Post by not_a_phd on 2010-01-23
It may be frowned upon, but I use the Qt library bundled with the QtCreator SDK downloaded from the web. The hard fact is that the library and the development IDE are changing faster than the good folks maintaining the Ubuntu packages can keep up. 

Though, I would certainly like to hear if there is a partner PPA repository out  there that I could install to get the best of both worlds: the latest and greatest library files + integration with my distro package manager.

---

### Post by gnometorule on 2010-01-24
That sounds reasonable. As I'm curious still, I close this here and will check with the beginners' forum to see if someone there has figured out if you could also use apt-get for both parts.

---

### Post by Zorael on 2010-01-24
The [Kubuntu ppas](https://launchpad.net/~kubuntu-ppa), where we get our unsupported updates and general KDE fix, get Qt updates as often as is warranted.

Its Qt4 packages (in [**ppa:kubuntu-ppa/beta**](https://launchpad.net/~kubuntu-ppa/+archive/beta/+packages)) are at "4:4.6.0-1ubuntu3~karmic1~ppa1" currently.

It also has KDE SC 4.4rc2 (4.3.95), not yet even released on kde.org. But you could just add it and nick the Qt4 packages, ignoring KDE.

---

### Post by CptPicard on 2010-01-24
> **not_a_phd said:**
> The hard fact is that the library and the development IDE are changing faster than the good folks maintaining the Ubuntu packages can keep up. 


How so? Qt is quite stable and you should be developing against something that is actually deployed as production libraries on desktops (think KDE shipped with Kubuntu) anyway.

Based on a quick apt-cache search, I would just

```

sudo aptitude install libqt4-dev qt4-dev-tools

```

---

### Post by gnometorule on 2010-01-24
Thank you very much, everyone. As I'm (very) new to Ubuntu/Linux, this actually led me to another round of imitating apt-get dist-install - you alluded to related topics i soooort of know, but not really, and i followed the tree up (aptitude vs apt-get? apt-cache? qt modules? etc. pp.). 

I opted to download the current Library/Creator package from the web page. Just to document this for anyone in the future equally new to Linux as I am, after download from the official QT web site, all you need to do is to

- make the downloaded bin file executable (chmod ...), then
- run it.

After that, a very 'Windows Installer' like gui will walk you through.

---

### Post by CptPicard on 2010-01-24
Seriously, there is almost never a need to download anything off the web and to sidestep the package manager, and certainly not in the case of a major, complex and ubiquitous library such as Qt...

---

### Post by gnometorule on 2010-01-24
I particularly wanted the Creator. In the various packages in Ubuntu etc., I find one 'unsupported maybe supported by community', which is a couple of version numbers back (to understand what precisely this means, I would have to dig up version history etc.). In this particular case, going to the web site meant

- download
- make executable
- run

Hellofa... easier. I'm entirely new to QT (have used W. Express (free) and gcc so far); and to understand what really I need among the multitude of packages and version numbers offered here, frankly, I found this VERY hard. It's like everything in LINUX (and to underline, I don't mind this, in fact it's nice to geek out): it's awesome if you already sorta know it. And it hits you over the head if you don't.

---

### Post by CptPicard on 2010-01-25
> **gnometorule said:**
> I particularly wanted the Creator.

Ok, I guess if you specifically must have the newest QtCreator version that is not in the repos that may be a valid point. Even in that case I would most definitely recommend relying on the Qt development libraries that come with the distribution; in particular, I am a bit worried about the trend of people not using the package manager even when it is there to be used (it happens far too much), and some n00bs who may read this even potentially messing up their system installing their own variants of libraries from source when they don't have to...

> 
 In the various packages in Ubuntu etc., I find one 'unsupported maybe supported by community',


```

picard@bridge:~$ apt-cache search qtcreator
qt-creator - Transitional package
qtcreator - lightweight integrated development environment (IDE) for Qt
qtcreator-doc - documentation for Qt Creator IDE

```

Shouldn't be too hard? I don't understand the problem :)


> In this particular case, going to the web site meant

- download
- make executable
- run

Hellofa... easier.

Easier than

```

sudo aptitude install qtcreator

```

Which should give you all the dependencies also? :)

> and to understand what really I need among the multitude of packages and version numbers offered here, frankly, I found this VERY hard.

Use the package manager, it will resolve your dependencies and version numbers and so on for you.

Even if you used a QtCreator from an external source, the exact minor version of the Qt libraries shouldn't matter.

> it's awesome if you already sorta know it. And it hits you over the head if you don't.

Well, I sometimes get the impression that people carry over from Windows habits that just don't apply on Linux. It's not hard here, it's just better :)

---

