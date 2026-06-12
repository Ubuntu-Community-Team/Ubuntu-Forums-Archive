---
title: "Python User..."
date: 2011-06-15
forum: Programming Talk
---

### Post by Dhiraj Thakur(Invincible) on 2011-06-15
I want to capture a keypress in my progam......
like Enter or Escape..... in a single keypress......**_without using any library that must be externally installed_** like _**Pygtk or Tkinter**_ etc.. i mean thres a way to capture using tkinter etc. but i want to knw is threre any lib func that can perform this task........

and i know about the msvcrt solution in windows....but i need something that is available on linux systems

Thanks in advance.... ;)

---

### Post by simeon87 on 2011-06-15
From what I know Tkinter is included in Python by default.

---

### Post by Dhiraj Thakur(Invincible) on 2011-06-15
Yeah i know but .... i dont wanna use that ... is thre any other way...??

Let's say i m using portable python then...what should i do??

---

### Post by simeon87 on 2011-06-15
Why not? It's installed by default and it gets the job done.

I'm not aware of a function in the Python library that can do this either. Or you have to install a library along with your program, then there are many possibilities.

---

### Post by Dhiraj Thakur(Invincible) on 2011-06-15
Thanks fr ur help... :)

---

### Post by tgm4883 on 2011-06-15
> **Dhiraj Thakur(Invincible) said:**
> I want to capture a keypress in my progam......
like Enter or Escape..... in a single keypress......**_without using any library that must be externally installed_** like _**Pygtk or Tkinter**_ etc.. i mean thres a way to capture using tkinter etc. but i want to knw is threre any lib func that can perform this task........

and i know about the msvcrt solution in windows....but i need something that is available on linux systems

Thanks in advance.... ;)

You mean like raw_input()?

---

### Post by Dhiraj Thakur(Invincible) on 2011-06-15
yeah but raw_input() cant capute 'Enter' or 'Escape'.... :(

---

### Post by tgm4883 on 2011-06-15
> **Dhiraj Thakur(Invincible) said:**
> yeah but raw_input() cant capute 'Enter' or 'Escape'.... :(

A quick bit of research shows people saying that curses can capture ESC. Not sure about Enter but I wouldn't think it was far off.

---

### Post by cgroza on 2011-06-15
You need something like a key logger functionality, that runs in the background and caches every key press?

---

### Post by tgm4883 on 2011-06-15
> **tgm4883 said:**
> A quick bit of research shows people saying that curses can capture ESC. Not sure about Enter but I wouldn't think it was far off.

Looking at this site, it shows how to do it with both mscvrt (Windows) and curses (Linux). Look at the Event driven programming section

[http://www.freenetpages.co.uk/hp/alan.gauld/](http://www.freenetpages.co.uk/hp/alan.gauld/)

---

### Post by Dhiraj Thakur(Invincible) on 2011-06-15
Thanks fr ur help.....got it now......

actually i am working in pygtk nd i came across a line that captured the key that user presses....so i did a bit of googling to find if thres any other way to capture keypresses......

i myself made a small program using pygtk to capture keypresses...

code:

import pygtk,gtk
def on_key_press_event(widget, event):
    keyname = gtk.gdk.keyval_name(event.keyval)
    print "Key %s (%d) was pressed" % (keyname, event.keyval)

w = gtk.Window()
w.connect('key_press_event', on_key_press_event)
w.show_all()
w.connect("destroy",lambda wid:gtk.main_quit())
gtk.main()

---

