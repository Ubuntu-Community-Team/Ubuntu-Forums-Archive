---
title: "KDevelop/C++/Qt3 - embedded images"
date: 2006-08-31
forum: Programming Talk
---

### Post by mycelo on 2006-08-31
My apps currently load their images via QCanvasPixmapArray, but I really dislike to have my binaries being carried out with a bunch of image files. 

I am searching everywhere for days, but I can't find a good explanation on how to (1) link/embed images into my executables, and also how to (2) load them into QCanvasSprite. 

I am using KDevelop 3.3.4, C++, Qt3+KDE classes. 

Can someone explain that to me? Please consider that I'm only asking here as a last resort, and KDevelop forums weren't of much help.

Thank you in advance. 

mycelo

---

### Post by mycelo on 2006-09-01
bump...

---

### Post by mycelo on 2006-09-04
bump...

---

### Post by mycelo on 2006-09-06
Common, my Qt book will take over a month to ship... :(

---

### Post by feloneouscat on 2008-03-27
If you are using QMake, I found this site has a reasonable solution...

link-> [Hack QT3 to compile embedded images cleanly]("http://www.cannasoftware.com/content/view/31/1/")

Again, this is all dependent on using QMake (or at least that is what I use). If you use anything else, you milage may vary.

---

