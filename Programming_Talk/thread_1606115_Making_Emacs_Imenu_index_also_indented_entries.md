---
title: "Making Emacs Imenu index also indented entries"
date: 2010-10-26
forum: Programming Talk
---

### Post by jazzgossen on 2010-10-26
I'm using Emacs with Imenu to easily navigating between functions in C++ files, etc. However, I've noticed that Imenu only indexes functions that are not indented.

For example, this will work
```
void f1()
{;}
```
but not this
```
  void f1()
  {;}
```
or this (which is what I have in most of my source files)
```
namespace NS{
  void f1()
  {;}
}
```

Is there a way to change this behaviour?

---

