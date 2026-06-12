---
title: "Do not manage to get apt-get build-depend to work"
date: 2005-02-16
forum: Repositories &amp; Backports
---

### Post by fif on 2005-02-16
I am currently trying to rebuilt the freetype library in order to improve character rendering. I am using ubuntu 4.10 Warty with installed freetype 2.1.7-2.1ubuntu1 (don't know the difference with regular 2.1.7 version by the way).

To do so, I launched the following command set:
apt-get --build source freetype=2.1.7-2.1ubuntu1
I get an error mentionning that dependencies are missing for correct build, so I launch the following command:
apt-get build-dep freetype=2.1.7-2.1ubuntu1
Everything goes fine till the construction of the dependency tree, but I get an error afterwards mentionning that dependencies cannot be satisfied.

dsc file mention the following:

[FONT=Courier New]Source: freetype
Version: 2.1.7-2.1ubuntu1
Binary: libfreetype6-udeb, libfreetype6-dev, freetype2-demos, libfreetype6
Maintainer: Anthony Fok <foka@debian.org>
Architecture: any
Standards-Version: 3.6.1
Build-Depends: debhelper (>= 4.0.0), bzip2, gettext (>= 0.10.36-2), xlibs-dev, libz-dev
Files: 
 991ff86e88b075ba363e876f4ea58680 1245623 freetype_2.1.7.orig.tar.gz
 85a89c466e8c6582e248c34d4872269f 52661 freetype_2.1.7-2.1ubuntu1.diff.gz[/FONT]

Using the same command set with bzip2 worked fine.
Do I miss something in my config, or do I have to update all dependencies manually? If so, which package do I have to update: the regular ones or the devel ones?

I am beginning to get lost... :?

---

### Post by az on 2005-02-16
Are you mixing repositories?  You you have only Warty repositories or do you have foreign ones?  Do you have the deb-src entries too?

Are you using universe?

have you done
sudo apt-get -f install
?

---

### Post by fif on 2005-02-17
I retried after a fresh install and it worked. I launched the same commands but:
1) I had not entered a dedicated root password (sudo passwd root), what I did the first time
2) I had the cd-rom in, what I had not the first time.

I guess issue 2 might be the cause of the problem. As I did a reinstall in between (ubuntu is pretty cool for this  :mrgreen: ), I am not able anymore to know really what was the problem.

Thanks for the help however.

---

### Post by fif on 2005-02-17
And last precision, I also had added universe and multiverse in my first try. And yes, I had the deb-src available in both tries.

---

### Post by fif on 2005-02-17
Last thing is that I just realised that installed libfreetype library was already including what I wanted to add :-\"
At least I am less idiot today than I was yesterday...

---

