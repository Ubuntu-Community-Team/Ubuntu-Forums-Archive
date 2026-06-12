---
title: "Packaging a game, easiest way to make it easy for ubuntu users to install?"
date: 2008-05-12
forum: Packaging and Compiling Programs
---

### Post by eedok on 2008-05-12
Well I've nearly finished making a game using python/pygame, on windows I used NSIS to make an installer, and am looking for a solution for ubuntu that would be similar.

My end goal is to make it so the person who wants to play my game can download it from my site then just double click, possibly answer yes/no to install along with possibly an install directory(not necessary though), then have the game show up in the application menu under games.

So I'm wondering what would be the easiest way to do this?
Thanks

---

### Post by Jadd on 2008-05-13
For Ubuntu, packaging your game as a deb package is definately the preferred way to distribute your program. Ubuntu users prefer debs by far. If you want to be extra nice to Ubuntu people, make your own deb repository. If you want to be very, very nice to Ubuntu people, get your deb package on [getdeb.net](http://getdeb.net), or even better, in the universe repository (presuming of course that your game is free and open source)

---

### Post by WW on 2008-05-15
I wrote a short description of how to package a simply python program using **epm** in [this thread](http://ubuntuforums.org/showthread.php?t=406069).

Read the whole thread--someone pointed out that my "quick and dirty" use of epm might leave behind extraneous .pyc files if and when the package is ever removed.

---

