---
title: "Mount .rar in linux?"
date: 2007-03-30
forum: Programming Talk
---

### Post by jae1227 on 2007-03-30
I have used Xbox Media Center and have always been amassed how it could play the video file within the rar without extracting the rar file. I want to know it something like this is possible in Linux and then cross-platform. There is a windows program called WinMount that can mount rar, zip and iso. I want to make something like this for Linux and need to know if it exist already and how hard it would be. Hope someone can help.

---

### Post by lnostdal on 2007-03-31
dunno how you see this related to programming .. but [http://www.nongnu.org/unpackfs/](http://www.nongnu.org/unpackfs/) .. looks kinda unmaintained/beta'ish though

..maybe more here: [http://fuse.sourceforge.net/wiki/index.php/FileSystems](http://fuse.sourceforge.net/wiki/index.php/FileSystems)

---

### Post by kidders on 2007-03-31
Hi there,

Like lnostdal's link suggests, any *proper* solution to your question would be fuse-based. 

Depending on your needs though, there may be an alternative. A kioslave-style archive browser (which also already exists) would make archives *appear* to be mounted (a little like the way WinXP handles zip archives natively). I realise that isn't really what you want, but I thought I would mention it, since it would be easier to write.

The real answer to your question is to start with fuse.

---

