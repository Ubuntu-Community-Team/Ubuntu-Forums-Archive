---
title: "Text User Interface Language"
date: 2008-11-13
forum: Programming Talk
---

### Post by Pyro.699 on 2008-11-13
Hello,

Ive been searching for the past few days for a language that supports [TUI](http://en.wikipedia.org/wiki/Text_user_interface), basically i need a 16-bit interface that will allow the user to interact with it, without a mouse. I need the basic colors (blue, red, green, white, gray yellow and black). I know this is a Ubuntu form, but you know how when you go to install Windows XP and you come to the screen that tells you weather to install or repair, an interface that is very similar (if not the same) to that.

Thanks
~Cody Woolaver

---

### Post by snova on 2008-11-13
This is not language specific. Any language, with proper bindings, can be used to do this. Use whatever you are comfortable with.

Look into the ncurses library.

---

### Post by pmasiar on 2008-11-13
python + curses [http://www.amk.ca/python/howto/curses/](http://www.amk.ca/python/howto/curses/)

---

### Post by Pyro.699 on 2008-11-13
Im aware of the curses library but was wondering if there was another method i could use.

---

### Post by snova on 2008-11-13
I don't know of an alternative, but is there any particular reason you're avoiding curses?

---

### Post by mali2297 on 2008-11-13
[dialog]("http://hightek.org/dialog/") lets you make simple interfaces to bash or perl scripts.

For something that's closer to a language, there is [S-Lang]("http://www.jedsoft.org/slang/").

---

### Post by Pyro.699 on 2008-11-13
Thanks, ill look into both of those, i know theres a c++ lib for c++ but i was wondering if there was another libary that goes with c++

---

### Post by JupiterV2 on 2008-11-14
I'm writing a text-based windowing toolkit I call ntk as an ncurses equivalent to gtk. Does that help? =)

---

