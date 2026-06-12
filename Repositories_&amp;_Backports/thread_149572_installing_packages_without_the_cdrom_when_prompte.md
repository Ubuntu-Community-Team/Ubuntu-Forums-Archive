---
title: "installing packages without the cdrom when prompted for it?"
date: 2006-03-24
forum: Repositories &amp; Backports
---

### Post by joop on 2006-03-24
Hi,

i'm new here so sorry if this question was already asked which easily could be the case. Although i couldn't find it with the search option.

I'm trying to get some packages installed on a server with the package manager but it keeps asking for the cd and i don't have a cdrom drive on the server, so i can't access the files he's looking for on the cd.
Is there a way to make the package manager look for these files in another directory  so i don't need a cdrom drive to install the packages?

grtz,
Joop

---

### Post by Aewheros on 2006-03-24
All packages on the CD are in the main repositories. If your server is connected to the internet, they will be downloaded from there upon install. That is, unless it looks for them on a cd instead...

To make it stop looking for the CD, open up a terminal and write:
```
sudo gedit /etc/apt/sources.list
```
This is a list of repositories, sources from where you get packages. Remove the one for the cd-rom, it should be the topmost.

Alternatively, replace your entire list with the one found in [this thread]("http://www.ubuntuforums.org/showthread.php?t=92672").

---

