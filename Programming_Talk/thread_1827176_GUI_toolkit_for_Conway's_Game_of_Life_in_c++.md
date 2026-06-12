---
title: "GUI toolkit for Conway's Game of Life in c++ ?"
date: 2011-08-17
forum: Programming Talk
---

### Post by damnated on 2011-08-17
Hi, I just finished writing a c++ implementation of [Conway's Game of Life]("http://en.wikipedia.org/wiki/Conway%27s_Game_of_Life") but it has an ascii output and I don't really like it. 

I would like to make a GUI version of this, but I never used any GUI toolkits and I don't know where to start. 

Any recommendations?

---

### Post by NovaAesa on 2011-08-17
I would suggest having a look at SDL. It allows you to open a window and write directly to each pixel (which you would obviously put as black or white). It also allows you to capture keystrokes, which you can use to change the speed of the simulation etc.

---

### Post by unknownPoster on 2011-08-18
You can also add in tkinter, wx, gtk, or qt to add functionality such as dialogs or other things if you need them.

---

### Post by cgroza on 2011-08-18
> **unknownPoster said:**
> You can also add in tkinter, wx, gtk, or qt to add functionality such as dialogs or other things if you need them.
I think one can find widgets made in SDL. They even provide events and all you need to interact with them. Except there are no standard ones, as far as I know.

---

### Post by unknownPoster on 2011-08-18
> **cgroza said:**
> I think one can find widgets made in SDL. They even provide events and all you need to interact with them. Except there are no standard ones, as far as I know.

I know that you can't.

If you want your typical dialog type windows among other things, you will need to use another GUI toolkit. 

Just for reference, you will find no features available in a standard GUI toolkit in the SDL API.

[http://wiki.libsdl.org/moin.cgi/CategoryAPI](http://wiki.libsdl.org/moin.cgi/CategoryAPI)

---

### Post by cgroza on 2011-08-18
> **unknownPoster said:**
> I know that you can't.

If you want your typical dialog type windows among other things, you will need to use another GUI toolkit. 

Just for reference, you will find no features available in a standard GUI toolkit in the SDL API.

[http://wiki.libsdl.org/moin.cgi/CategoryAPI](http://wiki.libsdl.org/moin.cgi/CategoryAPI)
I am sure I have seen some on the Internet. It is true that it is nothing official and all of them are home brewed.

---

