---
title: "Ncurses with C++"
date: 2007-06-11
forum: Programming Talk
---

### Post by ankursethi on 2007-06-11
Any pointers to tutorials that explain using Ncurses with C++? A Google search turns up nothing much because it truncates the "++" resulting in a search for "ncurses c" instead of "ncurses c++". Most of the documentation seems to be for C (I wouldn't mind using C, though).

Another question : is it possible to get full screen mode with Ncurses, instead of running in the Gnome terminal?

---

### Post by -Rick- on 2007-06-11
Just use it like you would with C, afterall C++ is mostly compatible with C. If you want to use ncurses in 'full screen' you need to start the application outside X (press ctrl+alt+fN to login to a terminal outside X).

---

### Post by pmasiar on 2007-06-11
Not sure what you did to google, but for me it *did not* stripped ++ from C:

[http://www.google.com/search?q=ncurses+C%2B%2B](http://www.google.com/search?q=ncurses+C%2B%2B)

---

### Post by danhm on 2007-06-11
I found three guides that may be useful:

[http://www.writeka.com/ed/ncurses_library.html](http://www.writeka.com/ed/ncurses_library.html)
[http://tldp.org/HOWTO/NCURSES-Programming-HOWTO/](http://tldp.org/HOWTO/NCURSES-Programming-HOWTO/)
[http://invisible-island.net/ncurses/ncurses-intro.html](http://invisible-island.net/ncurses/ncurses-intro.html)

---

### Post by ankursethi on 2007-06-11
Okay, thanks a lot everybody. But can somebody tell me about the fullscreen thingy? It's been bothering me because I intend my app to be full screen. Isn't there a way to make the GNOME Terminal fullscreen just temporarily? Or is it possible, through code, to launch the app under a different virtual terminal outside of X?

---

### Post by danhm on 2007-06-11
Click View, then unclick "show menu bar", and then hit full screen. F11 will toggle full screen if you need it to be a window again.

---

### Post by ankursethi on 2007-06-12
Well, that's possible, but I want my program to run in fullscreen mode by default. Isn't it possible to just launch it outside of X on another virtual terminal?

---

