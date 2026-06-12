---
title: "Good tutorials for GUI programming in python?"
date: 2007-01-06
forum: Programming Talk
---

### Post by luca.b on 2007-01-06
Hello there!
In my course to learn Python I stumbled about GUI programming. I haven't read much about it yet, but as I'm trying to put a GUI on a stupid small program I wrote, I'm trying to find good tutorials and guides.

Tkinter seems the easiest to set up, but at least on Linux the font rendering quality is abysmal (untl Tk8.5 is out). I'm not a big fan of GTK so I'm leaving out pyGTK at the moment. What's left is PyQt and wxPython probably. Does anyone have good links to at least get an insight?
Thanks.

---

### Post by Mirrorball on 2007-01-06
Install Qt Designer and read the official Qt Designer documentation. PyQt has a script (pyuic) that converts Qt Designer forms into Python code. It's super simple.

---

### Post by luca.b on 2007-01-06
Yes, that's part of PyQt. However good documentation on PyQt 4 is lacking (I would like to use that instead of 3 in order to use some stuff provided by third-party modules I use), until a good book is published (if you check riverbankcomputing it says around Autumn 2007). I may check B.Rempt's good PyQt book though (even if the Python version used back then is quite outdated)
Does anyone here have experience with PyQt 3?

---

### Post by Mirrorball on 2007-01-06
I still recommend you read the official Qt documentation, even though it's for C++.

---

### Post by pmasiar on 2007-01-06
[wikipedia]("http://en.wikipedia.org/wiki/WxPython") has links to WxPython screencast tutorials. BTW PyQt users might want to add link to PyQt as another alternative (article mentions only Tk.

Another option doing something interactive and pretty-looking might be web-based app. I recently posted  (shameless self-promotion): [Hello Web - simplest web app in python]("http://ubuntuforums.org/showthread.php?t=332041")

---

