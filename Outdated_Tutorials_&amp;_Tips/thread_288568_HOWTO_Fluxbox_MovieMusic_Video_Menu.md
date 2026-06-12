---
title: "HOWTO: Fluxbox Movie/Music Video Menu"
date: 2006-10-30
forum: Outdated Tutorials &amp; Tips
---

### Post by jr.gotti on 2006-10-30
I was trying to figure out how to have a menu in my fluxbox menu that could list all of my music videos, and play them when clicked. Right now I am working on a script to automatically write the menu file and update it, but for now you have to do it manually. Anyway, this is how I set it up:

In my main ~.fluxbox/menu file, I placed a pointer to my music video menu:

```
 [include] (/home/jason/mvideos/.fluxboxmenu) {} <>
```(Of course, you will replace this with the path to your movi menu.)

Inside of that menufile, I have the following format:

```

[submenu]  (Music Videos) {}
[submenu]  (Band 1 {}
[exec] (Song 1) {mplayer /path/to/song/1}
[exec] (Song 2) {mplayer /path/to/song/2}
[end]
[submenu]  (Band 2) {}
[exec] (Song 1) {mplayer /path/to/song/1}
[exec] (Song 2) {mplayer /path/to/song/2}
[exec] (Song 3) {mplayer /path/to/song/3}
[exec] (Song 4) {mplayer /path/to/song/4}
[end]
(etc...)
[end]

```Pretty easy to figure out, but I thought I would share in case anyone else was interested.

Anyway, heres a screenshot:

---

