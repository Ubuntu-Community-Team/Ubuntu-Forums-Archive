---
title: "iTunes on Lubuntu"
date: 2013-06-15
forum: New to Ubuntu
---

### Post by philpense on 2013-06-15
Followed the guidance found on; [http://www.linuxscrew.com/2007/09/19/install-itunes-72-in-ubuntu-and-other-linux-distros/](http://www.linuxscrew.com/2007/09/19/install-itunes-72-in-ubuntu-and-other-linux-distros/)

Instructions are:
[COLOR=#303E48][FONT=Helvetica]To install latest version of wine download corresponding binary package for you Linux distribution from [here]("http://www.winehq.org/site/download"). Packages for Ubuntu Feisty are available [here]("http://wine.budgetdedicated.com/archive/ubuntu/feisty/").[/FONT][/COLOR]
[LIST=1]
[*]Install deb package:
*sudo dpkg -i wine_0.9.45~winehq0~ubuntu~7.04-1_i386.deb*
[*]Configure by running *winecfg* command in terminal:
[LIST]
[*]In Applications tab, choose **Windows XP** option.
[*]In Drivers tab, click Autodetect button.
[*]In Audio tab, check **ALSA **Driver and uncheck **OSS **Driver.
[/LIST]
Then click OK button.

*statement: sudo dpkg -i wine_0.9.45~winehq0~ubuntu~7.04-1_i386.deb *

result: dpkg: error processing wine_0.9.45~winehq0~ubuntu~7.04-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 wine_0.9.45~winehq0~ubuntu~7.04-1_i386.deb
maurice@maurice-900:~$ 

used the correct password to enter the code

Guidance sought




[/LIST]
[COLOR=#303E48][FONT=Helvetica]
[/FONT][/COLOR]

---

### Post by sgaap on 2013-06-15
Is there a specific reason to use an old wine and itunes version?

It should work just fine with a more recent wine and itunes, so just "sudo apt-get install wine" should get you a recent version (or use playonlinux)

To get info/help for this: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347)

---

### Post by 3rdalbum on 2013-06-15
Don't install that package, it is for Ubuntu 7.04 and is ancient.

If you want to install Wine, get it from Ubuntu Software Center. I don't know whether iTunes runs on Wine currently though.

You definitely can't play DRM media or use your iPod on Wine. You would be much better off using a native Linux media player.

---

### Post by snowpine on 2013-06-15
There is no technological reason why iTunes can't run on Linux. However, Apple has made the business decision not to support this. Why not use one of the excellent open source apps like: Rhythmbox, Amarok, Banshee, etc.?

ps You'll give yourself a headache if you try to follow a 2007 tutorial for an obsolete Ubuntu release from some random guy's blog. Always use trusted, reliable, and current documentation if you value the stability of your system. ;)

---

### Post by philpense on 2013-06-15
Every "how to" offers a different combination of Wine with iTunes.  I seek a combination that will use that actual iTunes.  I will follow the help link but would be satisfied with a combination that works.

---

### Post by 3rdalbum on 2013-06-15
What do you want to do with iTunes? If you came to Linux to use Windows programs, you will be sorely disappointed.

If you can tell us what you want iTunes for we might be able to suggest sometthing native.

---

### Post by sgaap on 2013-06-15
If you really want it the easy way:

1: install playonlinux

```

sudo apt-get install playonlinux

```

2. Start playonlinux

3. Go to File > Install 

4. Select category "Most Downloaded" on the left (for some reason the only place where I could find it)

5. Find Itunes 10, select it and click "Install"

6. It should start downloading a wine version and ask you for the iTunes installer, Ive just downloaded the most recent version (32bit version, altough with recent wine the 64 bit should work too but its generally more hassle) and playonlinux installed it

7. Remember to not start it just yet, usually playonlinux installs some extra dependencies after the install of itunes has finished

8. When everything is installed just select "Itunes 10" in the main playonlinux window and press run

Only issue i have encountered is that you cant add folders, but im sure there is a workaround for that.

//edit: I would advise against running iTunes on linux though, not because its a bad application (I use it frequently when im in OSX) but because with all wine versions i've tested with the idle cpu usage was extremly high (1.5 core on an i5)

---

### Post by Baldrick_NZ on 2013-06-16
I have done some extensive testing with iTunes on Linux.

I can confirm that using wine1.4.1 (stable), there are three older versions of iTunes that will install. None work with the iTunes store. I wouldn't recommend the dev version of wine (1.5), as it's still highly unstable.

If you wish to utilise the iTunes store, you'll have to either...
1/ use iTunes through Windows installed on virtual box
2/ Dual boot into Windows whenever you want to use iTunes, or
3/ (my favourite) Ditch iTunes store altogether and try Google music. Because it's web-based it works on any platform. Not only that, but it has more advanced features than iTunes, like: Bought music is stored on the cloud but can also be downloaded to a PC, tablet, whatever as many times as you like. Pricing is pretty much the same, and all music is high quality mp3 (320kbps) - so can be played on any player - not just an apple product.

Hope that helps.

---

### Post by czgirb on 2013-06-16
I was an iTunes user ... I know iTunes and use it since **4th edition**
iTunes works well in Mac and Windows ... that's right
But remember, **iTunes is not dedicated to works in Linux**

So, maybe:
[B]Within some person's ubuntu, iTunes is works well ... but it never means it will works well on everyone ubuntu
Some people who's having works well iTunes will give it a SILVER or GOLD ... but some who's having not works well iTunes will give it a GARBAGE[/B]

According to my experienced :
I'm one of some that will give it a GARBAGE
 ... used **WINE** and **PLAY-ON-LINUX** ... **7th~v10th iTunes**
So ... I force myself for looking the alternative
Now, I quite happy to works with **DeaDBeeF**

---

### Post by HiImTye on 2013-06-16
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
iTunes always works in VirtualBox, so if you have a Windows CD, that's an option.
sometimes, iTunes sort of works in WINE, but results will vary.

as others have said most functionality of iTunes is available in other, native programs, so let's start with what you're trying to accomplish

---

