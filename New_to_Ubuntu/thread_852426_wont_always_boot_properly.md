---
title: "wont always boot properly"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by mustard greens on 2008-07-07
ubuntu doesnt want to boot.  I have to try ten or fifteen times sometimes before I get a good boot.  is this a common problem?  I just watch the "night rider" lights swoop back and forth forever.  when it works it boots in seconds.  I am have a duel boot with ubuntu and XP on a dell desktop.  I also cant seem to find my system specs (graphics card etc.) or I would have posted them.  thanks for the help.

---

### Post by Cypher on 2008-07-07
What version of Ubuntu and how long has it been doing this? It is not normal to take that many attemps to boot into Linux. There is likely something that's causing Ubuntu to stall.

In the GRUB menu, hit ESC if you don't get the list of boot option and then hit 'e' to edit the first entry, you will find the boot arguments here like "quiet splash"..just backspace those two arguments out and boot up. The "Knight Rider" lights will be replaced by more verbose text indicating what's really happening..keep an eye on what's taking forever to load and perhaps we can help you further..

---

