---
title: "anjuta configure.am including library, need help"
date: 2010-02-04
forum: Programming Talk
---

### Post by rat in a cage on 2010-02-04
I am creating music player app using gtkmm in anjuta. I needed package taglib and I included it using Project->Properties->Packages then selected it from list and my project was compiling ok (i was really happy how easy that was since i don't now much about autotools :) ).
Now I need to include package audiere([http://audiere.sourceforge.net/](http://audiere.sourceforge.net/)) and i'm stuck here.
I can compile program in terminal using -laudiere option with g++.

How to do it in anjuta? (since audiere is not using pkg-config and* "Anjuta has no real support for library not                 using pkg-config.                 You need to edit the configure.ac directly to add all necessary                 macros"*)

need simple answer. plz :(

---

