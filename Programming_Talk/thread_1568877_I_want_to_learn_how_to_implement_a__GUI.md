---
title: "I want to learn how to implement a  GUI"
date: 2010-09-06
forum: Programming Talk
---

### Post by Søren on 2010-09-06
in c++. i dont mean something like QT or gtk where you are passing code to prebuilt widgets. I want to know how those sort of things are implemented. Like drawing the whole thing and building it up from a really low level. how would i go about this?

---

### Post by d3v1150m471c on 2010-09-06
it's all libraries. find a library you want to use, lol like gtk, and find a tutorial. most things work with C++

---

### Post by schauerlich on 2010-09-06
> **Søren said:**
> in c++. i dont mean something like QT or gtk where you are passing code to prebuilt widgets. I want to know how those sort of things are implemented. Like drawing the whole thing and building it up from a really low level. how would i go about this?

Read the source code.

---

### Post by nvteighen on 2010-09-06
> **Søren said:**
> in c++. i dont mean something like QT or gtk where you are passing code to prebuilt widgets. I want to know how those sort of things are implemented. Like drawing the whole thing and building it up from a really low level. how would i go about this?

In GNU/Linux, that would lead you to X lib. The widget toolkits are implemented on top of that (plus some other stuff like threading, signal systems, etc.).

---

### Post by MarkieB on 2010-09-06
no longer participating in ubuntuforums.org

---

### Post by juancarlospaco on 2010-09-06
XLibs, or if you use TK you can try TCL

---

### Post by StephenF on 2010-09-07
Xine-ui uses XLib directly therefore I recommend you look at the source.

---

### Post by hakermania on 2010-09-08
In Qt you can create all your own widgets as you wish

---

### Post by nvteighen on 2010-09-08
> **hakermania said:**
> In Qt you can create all your own widgets as you wish

As in GTK+, though it is a bit more difficult because GTK+ is C and C structs make inheritance a little harder. But, in PyGtk this is quite easy (and even recommended).

---

### Post by hakermania on 2010-09-08
What about PyQt?

---

### Post by mmix on 2010-09-08
[http://stackoverflow.com/questions/235826/learning-about-low-level-graphics-programming/235838#235838](http://stackoverflow.com/questions/235826/learning-about-low-level-graphics-programming/235838#235838)

HTH

---

