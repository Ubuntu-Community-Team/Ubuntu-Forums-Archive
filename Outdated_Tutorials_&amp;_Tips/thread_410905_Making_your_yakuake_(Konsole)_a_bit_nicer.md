---
title: "Making your yakuake (Konsole) a bit nicer"
date: 2007-04-16
forum: Outdated Tutorials &amp; Tips
---

### Post by dgorchak on 2007-04-16
Yakuake is a Quake-style terminal for KDE that can hide and appear by pressing F12 (by default).

Yakuake's features:
* Smoothly rolls down from the top of your screen
* Tabbed interface
* Configurable dimensions and animation speed
* Skinnable
* Sophisticated DCOP interface

Yakuake is based on Konsole from KDE. Allthough it's almost perfect, yakuake lacks some features like autorenaming tabs and its title. So I went to Google for some help and found some workarounds to share with you.

First I'd like to say big thanks to Sami Vento, who created these patches.
Here we go! Follow this link
* _[COLOR=Blue][http://ota.tr.spt.fi/~fisu81/stuff/yakuake/]("http://ota.tr.spt.fi/%7Efisu81/stuff/yakuake/")[/COLOR]_
and download two patches. Than let's download yakuake source from Ubuntu repository:
* _[COLOR=Blue][http://packages.ubuntu.com/feisty/kde/yakuake](http://packages.ubuntu.com/feisty/kde/yakuake)[/COLOR]_
(as for me it's Feisty, you choose your Ubuntu version). Also get .diff.gz file clicking the link next to the source link. Let's place all the files in one directory.

Go on:
**tar -xzf yakuake_2.7.5.orig.tar.gz** #unpack
**zcat yakuake_2.7.5-4ubuntu2.diff.gz | patch -p0** #patch to current version in Ubuntu repos

Now let's get sure you are ready to compile the package:
**sudo apt-get build-dep yakuake **#install packages needed to compile yakuake

And now we start rebuilding the package in a Debian way:
[B]mkdir yakuake-2.7.5/debian
cat yakuake-doubleClickAdd.diff | patch -p0 [/B]#adds ability to open new tab by double-clicking the tab bar
**cat yakuake-getSessionName.diff | patch -p0 **#this one is what's I'm talking about

Rock on:
[B]cd yakuake-2.7.5
chmod +x debian/rules
make -f debian/rules build
sudo make -f debian/rules binary
[/B]
Now you get a new debian package. OK, but we're not done yet.

Download
* _[COLOR=Blue][http://ota.tr.spt.fi/~fisu81/stuff/konsolescripts/konsolescripts-beta]("http://ota.tr.spt.fi/%7Efisu81/stuff/konsolescripts/konsolescripts-beta")[/COLOR]_
Save this file somewhere, e.g. ~/.konsolescripts (check that it must be executable - **chmod +x .konsolescripts**). Then open your ~/.bashrc file (hope you use bash :)) and paste the following string at the end of the file:
**. <your path to "konsolescripts" file>** #e.g. . /home/zodiac/scripts/konsolescripts

This script renames yakuake/Konsole tabs according to current actions in the terminal. If you are a skilled bash user, you surely will add some actions that you like.

Restart yakuake/konsole and enjoy. If you are lazy, you can download the attached package: it was compiled for Feisty.

---

