---
title: "gdc for *-unknow-elf?"
date: 2007-10-01
forum: Programming Talk
---

### Post by Coyote21 on 2007-10-01
Well, I trying to do an operating system kernel, entirely in D ([http://www.digitalmars.com/d/](http://www.digitalmars.com/d/)) (since I plan to use it's class, delegates and interface features to layer my kernel in an modularized way (btw, it will be based in BSD interface as possible, and have something like dash for shell, the story for this is cute, maybe I will make some flash movies about, it and place them on my website...)), but I need an version of gdc, compiled to not produce any elf-targets (elf, because grub supports, the booting of elf binaries), that are based on linux headers (it would be nonsense), but I'm having trouble doing it. Can someone help me, to make an cross tool chains for several targets in unknow-elf? Particularly, arm, amd64 and x86?

---

