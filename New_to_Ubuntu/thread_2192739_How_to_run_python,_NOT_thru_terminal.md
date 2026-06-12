---
title: "How to run python, NOT thru terminal"
date: 2013-12-09
forum: New to Ubuntu
---

### Post by adam20 on 2013-12-09
I can't even remember where or when I downloaded python onto my Ubuntu 12.04 LTS.  It may have even come with the operating system, for all I know.  Anyway, I'm trying to run python through the program itself rather than through terminal so that I can save things and whatnot.  How would I do this?  I've found the executable in usr/bin but when I click on it nothing happens (don't laugh, I'm very new to Linux).

---

### Post by steeldriver on 2013-12-09
Are you maybe thinking of IDLE (the python **I**ntegrated **D**evelopment **E**nvironment)?

---

### Post by adam20 on 2013-12-09
essentially I'm looking for the python shell, I guess it's called.

---

### Post by ian-weisser on 2013-12-09
I don't understand what you mean by "through the program itself" and "the python shell" if you don't mean the terminal.
The interactive Python interpreter is text-only, and you access it through the terminal.
The interactive Python development environments open non-terminal windows, including one usually called the "Python shell" window. That particular "shell" functions identically to the interactive interpreter you access from the terminal.

When I write python applications in Linux, I use a text editor and the terminal.

Perhaps a longer explanation of what you are trying to do or looking for may help?

---

### Post by adam20 on 2013-12-09
> **ian-weisser said:**
> I don't understand what you mean by "through the program itself" and "the python shell" if you don't mean the terminal.
The interactive Python interpreter is text-only, and you access it through the terminal.
The interactive Python development environments open non-terminal windows, including one usually called the "Python shell" window. That particular "shell" functions identically to the interactive interpreter you access from the terminal.

When I write python applications in Linux, I use a text editor and the terminal.

Perhaps a longer explanation of what you are trying to do or looking for may help?

So do you use gedit?  How to you get the colors of the variables to change (e.g "print", "return")

---

### Post by asus-user on 2013-12-09
> **adam20 said:**
> I can't even remember where or when I downloaded python onto my Ubuntu 12.04 LTS.  It may have even come with the operating system, for all I know.  Anyway, I'm trying to run python through the program itself rather than through terminal so that I can save things and whatnot.  How would I do this?  I've found the executable in usr/bin but when I click on it nothing happens (don't laugh, I'm very new to Linux).

use the following command in Terminal to see the path for all directories that are related to the installed Python on your Ubuntu:
```
 dpkg -L python
``` 

and I think you will find what you want there in the output.
for more details and useful documentation refer to the main site: [http://www.python.org/doc/](http://www.python.org/doc/)

There you can find almost everything you need to know about Python, and there are also Tutorials for beginners.

P.S. I don't think you can run Python Shell directly (by double click), you need to run it from terminal. If you don't like it, use a Python IDE.

---

### Post by ian-weisser on 2013-12-09
> **adam20 said:**
> So do you use gedit?  How to you get the colors of the variables to change (e.g "print", "return")

The text editor application autocolors the key names, phrases, punctuation, etc. I just let the text editor figure it out.
I have used (and still use) Gedit and Mousepad. They are both very good. My favorite text editor is Bluefish.

---

### Post by newb85 on 2013-12-09
In gedit, look at View>Highlight Mode>...

Also, if you go to Edit>Preferences and the Plugins tab, there's a Python Console plugin as well.

---

### Post by dondiego2 on 2013-12-10
I have Ubuntu 13.1. I have IDLE set up for Python 2.7 and anither IDLE set up for Python 3.1.

I also have set up Eclipse for Python - that took a little longer - but I finally have it working. I just started this so I am not sure which one I prefer yet. IDLE seems pretty easy and Eclipse has a lot more options and I am still playing with both. I just got PyGame installed so I can play with GUI stuff now.

Both IDLE and Eclipse I can run from the progam list with a mouse click. I think this is what you are looking for. Let me know if it sounds like what you want and I might be able to help.

---

