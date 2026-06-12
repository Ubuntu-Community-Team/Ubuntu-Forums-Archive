---
title: "Writing code in Gedit."
date: 2007-05-07
forum: Programming Talk
---

### Post by tylerjames on 2007-05-07
Hey everyone,

Been working through some RoR tutorials and using Gedit to add some code.

Problem is when you load up a pre-generated .rhtml or .rb file it seems that all the functions are only tabbed in about 2 spaces, but when you press the tab key in Gedit it tabs in about 8 spaces. It makes it annoying since I've grown fairly accustomed to keeping things aligned using the Tab key. 

I tried to change the tab distance to 2 spaces but that affected everything aversely by moving the code to the left six spaces so that it was in line with the def and end parts of the function.

Is there another way I should be going about this? Or should I just resign myself to aligning functions using the spacebar?

---

### Post by finer recliner on 2007-05-07
there are better editors out there than gedit. most people will side with emacs or vi. 

while those may not help you either. i recommend either wiriting a perl script to fix the error for you or do it by hand ;)

---

### Post by Wybiral on 2007-05-07
I use GEdit for all of my programming (C, assembly, PHP,  Javascript, Python)...

Use space insertion instead of actual tabs (Gedit had an option for this). You can't go wrong there. You may have to convert the previous tabs to spaces, but you can write a quick RE in python/perl/ruby or something to do this pretty easily.

Tabs are terrible... Not every editor uses the same spacing so there is no way to tell how it will be formated, and if you're like me, I don't exceed 80 characters per line... That's impossible to gauge with tabs, so I only use space-tabs.

---

