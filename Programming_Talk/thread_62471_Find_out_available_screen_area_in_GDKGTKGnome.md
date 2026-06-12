---
title: "Find out available screen area in GDK/GTK/Gnome"
date: 2005-09-04
forum: Programming Talk
---

### Post by stoffe on 2005-09-04
Hello, I'm sitting here and experimenting a little with ruby-GTK, and I've run into a small issue: I'd like for the application window to be maximized vertically but not horizontally, that is I would like for it to cover all available height. The problem is that there doesn't seem to be a way to find out how high that is?

All methods I've tried for quering screens and root windows return the size of the whole screen, which isn't correct because there are panels on the screen too, that overlap the application if those values are used. A regular maximize takes this in account and resizes appropriately inside those. Maximizing the application and querying it for size yields nothing of value.

I can, and have, found a value to subtract that seems to work on my screen, but that is hardly useful, if I want anybody else to be able to use the same function. :)

I've been googling and searching and looking through the docs, but all I've found is that some window managers support maximizing in one direction only, but most don't - so that doesn't help either.

Has anybody any good solutions for a problem like this? Any functions I've missed in the API, or even clever routines for finding all panels and subtracting their sizes.. or whatever. I want to find the actual, usable Desktop size I guess you could say. And it probably doesn't matter what language the solution is for, as longas it is GDK/GTK/Gnome based I can probably convert it. =)

---

