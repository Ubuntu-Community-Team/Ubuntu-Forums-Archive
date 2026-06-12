---
title: "GUI design"
date: 2007-02-27
forum: Programming Talk
---

### Post by jtapper on 2007-02-27
Background first:

I am fairly experienced programmer in Java and I recently (2 years ago) found the .NET framework and its IDEs.

So.. I have made the move to completely move over to Linux which means that I have to rewrite bunch of my existing code. So far I have found python to be _the_ language,as it is very easy to learn and is far more powerful than Java. But there is but..

During last 2 years I have found that M$ way of GUI design is very nice, on the other hand with Java I used to write GUIs straight to the editor. Now that I am facing situation where I need to remake plenty of GUIs along with the whole programs, the M$ way of GUI design is the thing that I am looking for.

A quick nor a little more time consuming search didn't result in any results that would help me in my quest for WYSIWYG GUI editor that would be suitable. Anyone has any suggestions?

What do you guys write your python GUIs with? It doesn't have to be free,  I have payed money for my visual studio too.

---

### Post by christhemonkey on 2007-02-27
Glade maybe?
Along with Pygtk (which you can do by hand)

---

### Post by lnostdal on 2007-02-27
oh, you should try glade-3  (the version in feisty is great; does edgy have glade-3?)

here is some guides showing (in part 3) how to use gtk+/glade: [http://nostdal.org/~lars/writings/](http://nostdal.org/~lars/writings/) (edit: oh .. sorry; those are for C .. for Python you'd want PyGTK which surely also has libglade-support :))

---

### Post by jtapper on 2007-02-28
Thanks for tips, I'll try Glade w/ PyGTK.

---

### Post by jtapper on 2007-03-01
I tried Glade and unfortunately it wasn't quite what I was looking for. You certainly can make GUIs with Glade easily, but something was missing..

I found Qt designer and it seems to be perfect for my needs.

---

