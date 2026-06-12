---
title: "QTcreator comment out lines"
date: 2013-06-23
forum: Programming Talk
---

### Post by MikeCyber on 2013-06-23
Hi
how to comment out multiple lines in qtcreator?
Thanks

---

### Post by spjackson on 2013-06-23
I'm not quite sure what you are asking here. QtCreator is commonly used for Qt/C++ projects. Are you wanting to comment out multiple lines in C++ source?
```

/*
  Comment
  lines
  here.
*/

```
Or are you wanting to comment out bits of a .pro source or .ui source? Or is it something else?

---

### Post by MikeCyber on 2013-06-24
tools-option-keyboard: comment

I cannot change the default crtl / and the default doesn't work on ubuntu with swiss keys.
A simple solution for c++ files, thanks.

---

### Post by spjackson on 2013-06-24
> **MikeCyber said:**
> tools-option-keyboard: comment

I cannot change the default crtl / and the default doesn't work on ubuntu with swiss keys.
A simple solution for c++ files, thanks.
OK, using the Ctrl+/ method, if you highlight several lines, either with the mouse or using Shift and arrow keys, then press Ctrl+/ it will insert the comment characters at the start of each highlighted line (// in the case of C++).

Why doesn't Ctrl+/ work with a Swiss keyboard? I'm sorry, I can't help you with that.

Why can't you change the default key binding? By tools-option-keyboard, I can change the default Ctrl+/ to anything I like, such as Alt+C. Why doesn't this work for you? I don't know.

---

