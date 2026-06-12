---
title: "[SOLVED] [C++] - load files from archive?"
date: 2008-10-26
forum: Programming Talk
---

### Post by Ferrat on 2008-10-26
As the topic says I want to load files from an archive, doesn't really matter what archive typ and no compression just want more or less a database where I can sort the stuff. 

I want to load stuff like sprites, scripts etc and I would prefer not to have then just laying about in folders, so far I've only found stuff on fstream but from what I've found I haven't found a way to do what I want.

---

### Post by cl333r on 2008-10-26
I think what you need is actually a lightweight database, I would recomment SQLite (Firefox uses it as well):
[http://www.sqlite.org/](http://www.sqlite.org/)
To the right there's a menu you'll find instructions for people programming in C++.

---

### Post by Ferrat on 2008-10-26
Ah thank you :), will look in to it how ever can it archive files like images and not just raw data? 

On my mobile now so cant check.

---

### Post by cl333r on 2008-10-26
Yes, it supports the BLOB type, which is how people store binary files, such as images, images are raw data anyway.

---

### Post by Ferrat on 2008-10-26
ah thx :)

---

