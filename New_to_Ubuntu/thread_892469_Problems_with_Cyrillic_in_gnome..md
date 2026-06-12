---
title: "Problems with Cyrillic in gnome."
date: 2008-08-17
forum: New to Ubuntu
---

### Post by Mr0wyx on 2008-08-17
Hello!

Some folders named cyrillic, for example on desktop, are shown as "Ìåñòî âñòðå÷è èçìåíèòü íåëüçÿ". Also in gnome commander and so on. But in firefox and few files are shown as they used to be. Is it possible to correct this problem? 

Thx!

---

### Post by Mud.Knee.Havoc on 2008-08-17
I'd say that the incorrectly displayed filenames are written in win-1251 encoding instead of UTF-8.  Some programs (possibly gnome commander?) have difficulty displaying UTF-8 characters, whereas Nautilus has no problem (and firefox will read pretty much anything).  I've had to convert any Russian mp3 id3 tags to UTF-8 before they display properly, too.

---

