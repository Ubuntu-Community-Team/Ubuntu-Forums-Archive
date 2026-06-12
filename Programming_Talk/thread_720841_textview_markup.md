---
title: "textview markup"
date: 2008-03-10
forum: Programming Talk
---

### Post by shifty2 on 2008-03-10
I'm currently trying to implement a mark-up in a pygtk textview and am wondering if I'm going about it the right way. The end goal of my app is to create something that makes taking maths notes easy on a computer - similar to the tomboy latex plugin.

My current thought process is this:
-user chooses to apply style to selection
-applies style to selection using text iter and text tag
-adds an invisible character to the start and end of the selection (<b>blah</b>) for example that can then be read later when loading the file.

Is this the right way to be doing it or is there an easier way?

---

