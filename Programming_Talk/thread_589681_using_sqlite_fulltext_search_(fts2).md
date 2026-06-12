---
title: "using sqlite fulltext search (fts2)"
date: 2007-10-24
forum: Programming Talk
---

### Post by ywwg on 2007-10-24
I am trying to use sqlite's fulltext module in an application, and I can't for the life of me get it to load. The various docs around the web suggest this syntax:

[FONT="Courier New"]CREATE VIRTUAL TABLE recipe USING fts2(dish, ingredients);[/FONT]

But when I do that I get an error: "no such module: fts2"

Various pages around the web imply that ubuntu's sqlite has fts2 inside it ([https://lists.ubuntu.com/archives/ubuntu-patches/2007-July/011115.html](https://lists.ubuntu.com/archives/ubuntu-patches/2007-July/011115.html),  [https://bugs.launchpad.net/ubuntu/+source/sqlite3/+bug/127223](https://bugs.launchpad.net/ubuntu/+source/sqlite3/+bug/127223))  but I can't find the library on my machine anywhere.  

I even tried compiling sqlite3 from source just to see where it would install the extensions, but I couldn't find a way to even do that!

So my question is, how can I get this working in a way that doesn't require me (or the users of my app) to compile source code manually?

---

### Post by alucard001 on 2009-05-13
you can go to this webpage

[http://phpadvent.org/2008/full-text-searching-with-sqlite-by-scott-macvicar](http://phpadvent.org/2008/full-text-searching-with-sqlite-by-scott-macvicar)

for more FTS3 information.  Actually I have made it work but I am now search for how scoring is done in FTS3.

But hope this helps you out.

Haha, this is a reply to a 2 years ago post...

---

