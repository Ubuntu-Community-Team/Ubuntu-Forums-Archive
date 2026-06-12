---
title: "How to create a toggle button  with 2 custom images on GLADE?"
date: 2012-09-14
forum: Programming Talk
---

### Post by JJHK on 2012-09-14
I would like to create a toggle button which shows an image for button up and shows another image for button down.

I am new to GTK+ and Glade, and I wonder if someone can help to give me a pointer on it.

Thx in advance.

---

### Post by DarkAmbient on 2012-09-14
I think you need to define a callback-function on the toggle-signal, and set the other image in the callback. Not sure if it's possible to do this from inside Glade (only) though.

---

