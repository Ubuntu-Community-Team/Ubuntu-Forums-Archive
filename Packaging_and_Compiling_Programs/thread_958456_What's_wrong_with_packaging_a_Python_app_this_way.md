---
title: "What's wrong with packaging a Python app this way?"
date: 2008-10-25
forum: Packaging and Compiling Programs
---

### Post by moephan on 2008-10-25
The community documentation includes instructions for making a deb package for a python app here:
[https://help.ubuntu.com/community/PythonRecipes/DebianPackage](https://help.ubuntu.com/community/PythonRecipes/DebianPackage)

These instructions seem to make sense for a python application, and it seems like they are easy to follow and achieve. You basically create a directory structure that you want, and accompanying helper files, and run dpkg over the directory to create the deb archive.

However, someone edited the wiki to say that this was a "bad hack" and linked to a different way of packaging that seems much more tuned for an application written in a language like C, and that requires compilation:
[http://www.debian-administration.org/articles/336](http://www.debian-administration.org/articles/336)

Any thoughts on what makes the first method bad, and I shouldn't package my python apps that way?

TIA

Cheers, Rick

---

### Post by InfinityCircuit on 2008-10-25
That's probably one of the most disgusting descriptions of Debian packaging that I've ever seen...

To actually create a proper Debian package means creating a source package, which can then be uploaded to the buildds and built by them.  This approach creates no source package, and just does a hack job.  It is also illegal to distribute as it lacks a copyright file.

To get a sense of the issues:

```
dmr@kronos:~/Desktop$ lintian -I twisted-zombie-1.0_all.deb 
W: twisted-zombie: binary-without-manpage usr/bin/twisted-zombie
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/ 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/bin/ 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/bin/twisted-zombie 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/ 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/applications/ 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/applications/twisted-zombie.desktop 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/pixmaps/ 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/ 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/README.txt 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/ 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/credits.txt 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/fonts/ 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/fonts/FreeSerifBold.ttf 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/fonts/acquaint.ttf 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/fonts/attic.ttf 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/fonts/tasapainoaisti.ttf 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/fonts/tzpolla.ttf 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/ 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/backgrounds/ 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/backgrounds/bg1.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/backgrounds/bg2-1.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/backgrounds/bg2.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/backgrounds/bg3.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/backgrounds/bg4.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/backgrounds/bg4_old.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/backgrounds/bg5.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/backgrounds/cemetery-moon2.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/backgrounds/credits.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/backgrounds/horror-house2.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/backgrounds/menubg-alt.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/backgrounds/menubg.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/bg.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/body/ 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/body/a1.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/body/b1.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/body/body1.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/body/c1.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/body/d1.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/body/e1.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/body/f1.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/body/g1.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/body/h1.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/body/i1.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/body/j1.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/body/k1.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/body/mold1.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/bottles/ 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/bottles/bottle_blue.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/bottles/bottle_green.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/bottles/bottle_orange.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/bottles/bottle_red.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/gameover.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/help.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/icon.jpg 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/intro/ 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/intro/intro0001.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/intro/intro0009.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/intro/intro0015.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/intro/intro0016.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/intro/intro0017.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/intro/intro0018.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/intro/intro0019.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/intro/intro0020.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/intro/intro0021.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/intro/intro0022.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/intro/intro0023.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/intro/intro0024.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/intro/intro0025.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/intro/intro0032.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/intro/intro0033.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/intro/intro0034.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/intro/intro0035.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/level1.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/level2.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/level3.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/level4.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/level5.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/story.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/story.xcf 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/imgs/win.png 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/sounds/ 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/sounds/21914__Halleck__neck_crack.wav 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/sounds/29613__Erdie__Rubbing_metal03.wav 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/sounds/31818__malexmedia__malexmedia_man_scream.wav 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/sounds/32744__HardPCM__Burp007.wav 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/sounds/37596__hello_flowers__Sword.wav 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/sounds/bach.ogg 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/sounds/bloop.wav 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/sounds/credits.ogg 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/sounds/final.ogg 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/sounds/gameover.ogg 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/sounds/menu.ogg 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/data/sounds/play_music.ogg 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/lib/ 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/lib/body.py 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/lib/bottlemanager.py 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/lib/config.py 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/lib/credits.py 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/lib/data.py 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/lib/explotion.py 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/lib/help.py 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/lib/hero.py 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/lib/level.py 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/lib/main.py 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/lib/menu.py 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/lib/mold.py 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/lib/moldsmanager.py 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/lib/music.py 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/lib/scores.py 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/lib/sprites.py 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/lib/utils.py 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/lib/visual.py 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/lib/wheather.py 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/run_game.py 1000/1000
E: twisted-zombie: wrong-file-owner-uid-or-gid usr/share/twisted-zombie/run_game.pyw 1000/1000
E: twisted-zombie: package-section-games-but-contains-no-game
I: twisted-zombie: package-contains-empty-directory usr/share/pixmaps/
I: twisted-zombie: no-md5sums-control-file
W: twisted-zombie: executable-not-elf-or-script ./usr/share/twisted-zombie/data/sounds/bloop.wav
W: twisted-zombie: executable-not-elf-or-script ./usr/bin/twisted-zombie
W: twisted-zombie: executable-not-elf-or-script ./usr/share/twisted-zombie/data/imgs/backgrounds/bg1.png
W: twisted-zombie: executable-not-elf-or-script ./usr/share/twisted-zombie/data/fonts/attic.ttf
W: twisted-zombie: executable-not-elf-or-script ./usr/share/twisted-zombie/data/fonts/tasapainoaisti.ttf
W: twisted-zombie: executable-not-elf-or-script ./usr/share/twisted-zombie/data/fonts/FreeSerifBold.ttf
E: twisted-zombie: no-copyright-file
I: twisted-zombie: desktop-entry-contains-encoding-key /usr/share/applications/twisted-zombie.desktop:2 Encoding
W: twisted-zombie: desktop-command-not-in-package /usr/share/applications/twisted-zombie.desktop python
W: twisted-zombie: no-priority-field

```

If you want to just package some scripts, check out [https://wiki.ubuntu.com/MOTU/School/PackagingWithoutCompiling](https://wiki.ubuntu.com/MOTU/School/PackagingWithoutCompiling), originally presented on IRC by Emmett Hickory and transcribed to the wiki by yours truly. :)

---

### Post by Nonno Bassotto on 2008-10-25
I'm not sure I really understand what's wrong with the first way. Well, apart that one should add a copyright. I mean, lintian is a tool that checks that a package has been built according to the second way you present, so of course it gives a lot of errors. But what's wrong? What problems could arise from packaging things as in the first link?

---

### Post by nhandler on 2008-10-26
First, let me start by saying that the guide in question is NOT designed to show you how to produce packages that can be added to the repositories. It shows you how to create a .deb for personal use which you can install/remove using the various package management tools available.

When you are packaging for personal use, it doesn't really matter how sloppy the package is; all that matters is that it works. However, when/if if you decide you want to get that application added to the repositories, you will need to follow one of the more advanced packaging guides. This is because every package is required to have certain files: debian/control, debian/changelog, and debian/rules. The source package also must build cleanly in a clean chroot environment (i.e. pbuilder), and it must not produce any errors/warnings from lintian. Finally, you will submit the source package, not the binary package (the .deb) to REVU, where you will receive feedback on the package.

To recap, there really aren't any restrictions for creating a deb that only you will use. However, if you want to get it into the repositories, you will need to make sure it follows certain standars, namely the [Debian Policy]("http://www.debian.org/doc/debian-policy/").

---

### Post by moephan on 2008-10-26
Thanks all for the replies. It seems that the distinction between packaging for personal use and packaging for Repositories is an important and useful distinction.

[edit]
I updated the wiki to reflect this distinction.
[/edit]

---

### Post by Nonno Bassotto on 2008-10-27
Excuse me, but I still don't understand. Every reply seems like "it's better because it's better". I know that the debian policy asks you to create packages a certain way. And I know that there exists a tool, called lintian, which checks that you followed this way.

The question is. Assume that you only have to store some files somewhere. Why should you go through the hassle of creating a makefile and a rules file when there is nothing to compile? I mean, what is the technical real advantage of the second approach over the first? In what sense a package created following the debian policy is better?

---

### Post by nhandler on 2008-10-27
> **Nonno Bassotto said:**
> Excuse me, but I still don't understand. Every reply seems like "it's better because it's better". I know that the debian policy asks you to create packages a certain way. And I know that there exists a tool, called lintian, which checks that you followed this way.

The question is. Assume that you only have to store some files somewhere. Why should you go through the hassle of creating a makefile and a rules file when there is nothing to compile? I mean, what is the technical real advantage of the second approach over the first? In what sense a package created following the debian policy is better?

Once again, it comes down to where the package is designed to be used. If it is for personal use, the first method is fine. There are no strict requirements. However, when you go to get your package added to the Ubuntu/Debian repositories, you need to follow certain rules. I will try to explain why certain files are needed. However, let me start by reminding you that when you add a package to the repositories, you do not upload a .deb. You upload a source package. The buildd daemons then build the binary packages (.deb) that you install with synaptic and apt-get. They build these binary packages by executing the debian/rules file. This file contains all of the commands that need to be executed in order to build the binary packages. Without this file, the buildd daemons would have no idea about what they need to do. debian/changelog is another very important file. In Ubuntu, we do not have specific maintainers for each package. The MOTUs maintain all of the packages (in universe/multiverse). The debian/changelog file is used by these developers to document every change that they make to the package. This makes it easy to see who made each change and why they did it. debian/control is another very important file. I realize that the first guide told you to create this file. However, the way they have you create it is not correct. For one thing, it does not have separate sections for each binary package built by the source package. It also does not have a source section. There are plenty of other things missing from it as well (which you can see by using lintian). As you can see, the main reason for having the Debian Policy is to make sure that all packages meet certain standards. This allows them to be built correctly by the buildd daemons. It also allows applications like synaptic and apt-get to know how to handle them.

---

### Post by Nonno Bassotto on 2008-10-27
Thank you, now I understand better :)

---

