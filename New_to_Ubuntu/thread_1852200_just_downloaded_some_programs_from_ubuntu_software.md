---
title: "just downloaded some programs from ubuntu software center, where are they"
date: 2011-09-29
forum: New to Ubuntu
---

### Post by dan0804smith on 2011-09-29
just downloaded some programs from ubuntu software center, where are they?

downloaded sensord and nvclock

10.04 lts

---

### Post by abedayyad on 2011-09-29
Try the command: 

```
sudo dpkg --getselections | grep "[the name of the program here]"
```

It might also be helpful to use 

```
which name_of_command 
```

Anything other than that, you might want to try giving more details.

---

### Post by anewguy on 2011-09-29
Package nvclock is command line only.  There are GUI'd version - see nvclock-gtk.  To access just the command line version you need to open a terminal window and type nvclock --help and press enter.  I would download and try it but I don't have an nVidia card and even if I did I would have no desire to overclock it.

I did install sensord just to see what it takes to run it, and it appears to be command line only as well.  Open a terminal window, type sensord --help and press enter.


Dave ;)

---

