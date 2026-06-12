---
title: "Python IDE?"
date: 2011-09-03
forum: Programming Talk
---

### Post by benc1213 on 2011-09-03
I am wondering if there is a good Pythong IDE to use? Is there one or would it be better just to use a text editor like gEdit. Also I would prefer to use an IDE because I can write and run my programs all in the IDE.

---

### Post by memilanuk on 2011-09-03
In no particular order...

IDLE
Eclipse + PyDev
Geany
GNU Emacs
Komodo Edit
SPE
...

You might try looking on the Python.org website... they have a fairly comprehensive list...

---

### Post by benc1213 on 2011-09-03
> **memilanuk said:**
> In no particular order...

IDLE
Eclipse + PyDev
Geany
GNU Emacs
Komodo Edit
SPE
...

You might try looking on the Python.org website... they have a fairly comprehensive list...

What do you recommend?

---

### Post by memilanuk on 2011-09-03
I are not a developer ;) just a hobbyist tinkering with the language for the heck of it!

That said... Geany seems to do pretty much everything I want it to, and is pretty easy to get used to.  Cross platform between Windows and Linux as well.

---

### Post by IWantFroyo on 2011-09-03
1) Gedit
2) Geany
3) Dreampie (does this count as an IDE?)

---

### Post by benc1213 on 2011-09-03
> **IWantFroyo said:**
> 1) Gedit
2) Geany
3) Dreampie (does this count as an IDE?)

Wait so Gedit or Geany?

---

### Post by lykwydchykyn on 2011-09-04
Most python IDEs that I've tried don't offer much more than:
 - Syntax highlighting
 - a python shell
 - a shortcut for launching your script
 - code folding 
 - code completion

Most Linux text editors will give you at least the first four, including geany and gedit.  If you need more features than this, there may very well be a plugin available for it.

Personally I use emacs, though my biggest python project is maybe 500-600 LOC.  I've added on a few modules to make python development better.

If you like gedit, use it.  When you think to yourself "I wish gedit had XYZ feature for python development", then it might be time to look for something else.

---

### Post by benc1213 on 2011-09-04
> **lykwydchykyn said:**
> Most python IDEs that I've tried don't offer much more than:
 - Syntax highlighting
 - a python shell
 - a shortcut for launching your script
 - code folding 
 - code completion

Most Linux text editors will give you at least the first four, including geany and gedit.  If you need more features than this, there may very well be a plugin available for it.

Personally I use emacs, though my biggest python project is maybe 500-600 LOC.  I've added on a few modules to make python development better.

If you like gedit, use it.  When you think to yourself "I wish gedit had XYZ feature for python development", then it might be time to look for something else.

As much as I like gEdit it doesn't let me run the script in it so I'll just use geany.

---

### Post by IWantFroyo on 2011-09-04
You can use:
```
python -c filename.py
```
to run a python app from the command line.
If you want to be able to just click a button, Geany is probably the best choice.

---

### Post by gmargo on 2011-09-04
Eric
[http://eric-ide.python-projects.org/](http://eric-ide.python-projects.org/)

I've not tried it (since I'm a die-hard VIMer) but it looks worthwhile.
An older version is in the repostories as 'eric':
[http://packages.ubuntu.com/natty/eric](http://packages.ubuntu.com/natty/eric)

---

### Post by cgroza on 2011-09-04
I use Emacs. The Python mode is great.

---

### Post by juancarlospaco on 2011-09-04
**[http://ninja-ide.org/](http://ninja-ide.org/)**  :D

---

### Post by JDShu on 2011-09-04
I don't use it but I've heard good things about [Wing IDE]("http://wingware.com/"). It's not free, although if you are using it for an open source project, they will grant you a license at no cost.

---

### Post by MicahCarrick on 2011-09-10
There are as many opinions on this as there are editors, but, I'll give a +1 for Gedit. It may not be obvious at first, but there are tons of plugins available. 

Best part for Python programmers is that if you need a plugin, you can write one in Python. It's pretty easy. [Writing Plugins for gedit 3 with Python]("http://www.micahcarrick.com/writing-plugins-for-gedit-3-in-python.html")

What exactly are you looking for when you say you need to run your script from within the IDE? Gedit's external tools plugin does that pretty well as well as a standard terminal panel or the better python console.

---

