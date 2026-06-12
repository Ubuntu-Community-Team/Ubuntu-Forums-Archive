---
title: "wxWidgets vs gtk (wxPython vs PyGTK, specifically)"
date: 2010-03-05
forum: Programming Talk
---

### Post by murderslastcrow on 2010-03-05
I'm just getting my foot in the door with cross-platform programming and toolkits. I'm just wondering if there are any clear advantages of using PyGTK or a GTK-centric toolkit that wouldn't be provided if I went with wxWidgets?

I just want an opinion from someone who's been there before, but if it works well enough and has support for all the functionality I need, I would think wxWidgets was the best for the job, since it can support every mainstream desktop OS available.

Thanks for your responses in advance, I know this is kind of a noobish question. ^^;

---

### Post by kknd on 2010-03-05
GTK+ is portable, but have issues in Windows (2.16 works fine, 2.18 is weird) and MacOs (never tested myself). When targeting only Linux, I prefer GTK+ for it's nice API and set of features.

---

### Post by murderslastcrow on 2010-03-06
Hm, wxWidgets claims to have a natural feel for each set of toolkits. I'm sure there are certain elements I might want to implement in GTK specifically, but until I can find some feature that isn't implemented well by wxWidgets, I might only look at PyGTK for reference.

Thanks for the advice, though. We'll see what happens.

---

