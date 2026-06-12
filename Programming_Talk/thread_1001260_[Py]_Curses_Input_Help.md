---
title: "[Py] Curses Input Help"
date: 2008-12-03
forum: Programming Talk
---

### Post by linkmaster03 on 2008-12-03
I have a Python script that tries to retrieve input through curses. It is located at this paste: [http://pastebin.com/m5068cd7c](http://pastebin.com/m5068cd7c)

Run the program and press 'n'. Now, see where the cursor is? Try to type something in. It moves to the bottom. How do I fix that, and get input from that location?

---

### Post by tempel on 2008-12-03
Phreow.  This program has some problems.  Can't blame you; i just recently tried figuring out python curses, and it's not exactly fun times.

In regards to your immediate question, i think the issue is your use of curses.setsyx(y,x).  From reading the [module's documentation]("http://docs.python.org/library/curses.html"), i'm not certain that this function will move the cursor at all.  Instead, try making use of scr.move(y,x); it's worked for me in the past.

More importantly, you may seriously benefit from using the curses.wrapper(func, ...) convenience function.  You need only write the main part of your program as a function where the first argument is the screen.  This avoids the issues of having to initialize and deinitialize the screen manually.

Also, if you'd like a good tutorial on curses in python, [this one]("http://www.amk.ca/python/howto/curses/curses.html") really helped me.

Anyways, without really knowing what the game is supposed to do, i can't really offer any further advice.  But i can point out that, in ScreenDraw.menu and ScreenDraw.game, you call draw.clear(), where draw is an instance of ScreenDraw; you should be calling self.clear().  Also, it's good practice to use new style classes (change the line "class ScreenDraw:" to "class ScreenDraw(object):" to indicate that it is a type of object; same for Loops).  Also also, you've defined quit(config) as a function, whereas you seem to try to call it as a method of a ScreenDraw object later (that issue hijacked my terminal, and is one of the reasons you should use curses.wrapper!).

If you'd like any further help with this, i'm always here.  That is, presuming i haven't already driven you away with my nitpicking.

---

### Post by nvteighen on 2008-12-04
<rant>
Ncurses is a disastrous library... but well, sadly we don't have anything else for that functionality. I can say that even GTK+ is easier to manage, because it's logically constructed, but ncurses...
</rant>

A tip: install the libncurses5-dev package. Ok, it's the package for ncurses development in C, but it includes the documentation (installed at /usr/share/doc/libncurses5-dev). You'll have to translate it into Python, but it's not that difficult (almost all will be curses.* except those refered to a screen... and the fact that Python brings all variants of a same function into a single one). (I wonder why there is no libncurses5-doc package instead...)

---

### Post by wmcbrine on 2008-12-04
> **tempel said:**
> In regards to your immediate question, i think the issue is your use of curses.setsyx(y,x). ... Instead, try making use of scr.move(y,x)I was just coming here to post that. That indeed fixes it.

The reason this happens is that, when you call getch() on a window, it first updates that window, including moving the cursor to the position it last had within that window. So the "global" cursor position that you set with setsyx() is overridden.

The correct time to use setsyx() is, basically, never; and sadly, this is true of many curses functions. But please, don't blame ncurses; it has to conform to [this](http://www.opengroup.org/onlinepubs/007908799/xcurses/curses.h.html), which in turn is the way it is for historical reasons that go back to the 1970's.

At least the Python interface is a bit cleaner than the C original.

---

### Post by linkmaster03 on 2008-12-04
tempel: Thanks for the tip, it worked! The reason that the code doesn't really function is because I stripped everything except what I needed to present my problem. I didn't realize self.clear(), it makes perfect sense now. What exactly does the (object) addition do? Also, the tutorial you linked me to was the one I was using. It is in fact very good.

nvteighen: Thanks, I'll definitely check out the documentation there.

---

### Post by tempel on 2008-12-04
The (object) addition isn't strictly necessary in python 2.x, but it is required in the recently-released python 3, which i expect will eventually become standard.

Until then, the brackets indicate from what class to inherit; if none is specified, the basic "object" is assumed, but it's good practice (and eventually required) to explicitly state that.

Also, regarding your clear method, i just recalled that there is, already included as a method on window objects, the scr.clear() and scr.erase() methods (mostly identical to each other).  Furthermore, since you define the whole screen with each redraw, you probably don't even need to use these.

---

### Post by wmcbrine on 2008-12-05
> **tempel said:**
> The (object) addition isn't strictly necessary in python 2.x, but it is required in the recently-released python 3,Eh, not unless that's changed since RC1.

In 2.x, deriving from object makes it a "new-style" class, while leaving that off makes it old-style. In 3.x, every class is new-style, whether you declare the derivation from object or not.

```
Python 2.5.2 (r252:60911, Oct  5 2008, 19:29:17) 
[GCC 4.3.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> class Test:
...     pass
... 
>>> Test
<class __main__.Test at 0x7f86f15497d0>
>>> class Test2(object):
...     pass
... 
>>> Test2
<class '__main__.Test2'>
>>> type(Test)
<type 'classobj'>
>>> type(Test2)
<type 'type'>

Python 3.0rc1+ (py3k, Oct 28 2008, 09:22:29) 
[GCC 4.3.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> class Test:
...     pass
... 
>>> Test
<class '__main__.Test'>
>>> class Test2(object):
...     pass
... 
>>> Test2
<class '__main__.Test2'>
>>> type(Test)
<class 'type'>
>>> type(Test2)
<class 'type'>

```

---

