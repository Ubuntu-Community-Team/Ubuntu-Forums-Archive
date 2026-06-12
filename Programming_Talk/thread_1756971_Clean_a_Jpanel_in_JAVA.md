---
title: "Clean a Jpanel in JAVA"
date: 2011-05-12
forum: Programming Talk
---

### Post by raac on 2011-05-12
Hello guys, I've got a question. I'm putting labels inside a panel, and I have a button that suppose to clean up the panel (leave it blank again). How can I do that?

I tried to add the panel again (a new one), but it is actually adding a different panel next to the old panel (with the labels on it).

---

### Post by PaulM1985 on 2011-05-13
You could use the removeAll() method on the panel.  Incase you didn't know, there is plenty of info in the API describing methods are available to Java classes.  It is worth having a look if you aren't aware of it:
[http://download.oracle.com/javase/1,5.0/docs/api/](http://download.oracle.com/javase/1,5.0/docs/api/)

Paul

---

### Post by cgroza on 2011-05-13
Check the APIs. You need to make a habit out of that.

---

