---
title: "Qt Designer - First Time"
date: 2007-09-19
forum: Programming Talk
---

### Post by fourthdimension on 2007-09-19
Hey All

I have a simple program I wrote that I'd like to put a user interface to.  I'm using Qt Designer, but I can't figure out how to write the source so that Designer uses it or how to get my different input/output boxes to work together.  Does anyone know of a good walk-through that talks about this?
Thanks.

---

### Post by Dylock on 2007-09-19
i had this problem too when i was using QT.

im just tryin to remember this from the top of my head but i think you have to use a qt tool called uic to generate the c++ header from the GUI you make in the designer.

You then take the class thats defined in that generated c++ header and declare it in your code, declare a namespace, etc

You should be able to find an example on doc.trolltech.com

Its on there somewhere, but I'll point out that this was one of those things that they really should document more. 

Good luck mate.

---

### Post by tpg on 2007-09-19
> **Dylock said:**
> Its on there somewhere, but I'll point out that this was one of those things that they really should document more.
There are several methods of doing this, all of which are described in the Qt Documentation!

Start [here]("http://doc.trolltech.com/4.3/designer-manual.html") and work your way through - i believe it even has a simple worked example.

---

