---
title: "Help making a simple program"
date: 2012-09-16
forum: Programming Talk
---

### Post by FRodrigues on 2012-09-16
Hi,

I'm trying to create a (maybe?) simple program for Ubuntu.
But I don't know where to start and what to do...

What I want is to make a simple "box" in my desktop to write anything I want, like kde's note widget:
[IMG]http://l.yimg.com/ck/image/A1405/1405394/300_1405394.jpg[/IMG]

But, for now, with less features, something like [this]("http://i.imgur.com/svkF8.png").

Thanks in advance,
Fernando Rodrigues.

---

### Post by slooksterpsv on 2012-09-16
The first thing to look at is language you want to use; you can use Python, C++, C, Java, C#, Gambas, etc.

After the language; what toolkit (API for windowed applications) e.g. WxWidgets, QT, GTK, Glide, etc.

A lot to choose from, but not as bad as you would think.

I personally use Python and QT.

---

### Post by whatthefunk on 2012-09-16
Something like this might already be available.  Check out Screenlets:
[http://helpdeskgeek.com/linux-tips/install-desktop-widgets-in-ubuntu/](http://helpdeskgeek.com/linux-tips/install-desktop-widgets-in-ubuntu/)

---

### Post by FRodrigues on 2012-09-16
> **slooksterpsv said:**
> The first thing to look at is language you want to use; you can use Python, C++, C, Java, C#, Gambas, etc.

After the language; what toolkit (API for windowed applications) e.g. WxWidgets, QT, GTK, Glide, etc.

A lot to choose from, but not as bad as you would think.

I personally use Python and QT.

I'm not worried about languages, but I would like to program with Python.
And can I really choose all of those toolkits to make that box?
Or do I need to do some hacking to make it work?
If It's easy I would choose QT or GTK whatever the most easier to learn and to work.

> **whatthefunk said:**
> Something like this might already be available.  Check out Screenlets:
[http://helpdeskgeek.com/linux-tips/install-desktop-widgets-in-ubuntu/](http://helpdeskgeek.com/linux-tips/install-desktop-widgets-in-ubuntu/)

It's something like that what I want, but I don't want to be dependent of compiz...

---

### Post by slooksterpsv on 2012-09-16
No you can choose what toolkit you want to use. If you want variable opacity, I'd stick with QT or GTK. I think Ubuntu and Unity are shifting more to QT style apps, (I could be wrong).

---

### Post by Vaphell on 2012-09-16
> I think Ubuntu and Unity are shifting more to QT style apps, (I could be wrong).

using gtk3 and axing ubuntu2d (Qt) don't really support that notion :)

---

### Post by FRodrigues on 2012-09-17
I read that QT is easier but maybe I'm going to choose GTK+ because It's the Ubuntu's native UI toolkit.
What do you think?

And what do you recommend me to read aside from:
[Learn Python The Hard Way]("http://learnpythonthehardway.org/book/")
[The Python Tutorial]("http://docs.python.org/tutorial/index.html")
[The Python GTK+ 3 Tutorial]("http://python-gtk-3-tutorial.readthedocs.org/en/latest/index.html")
[Gnome Dev Center's Tutorials, code samples and platform demos in Python]("http://developer.gnome.org/gnome-devel-demos/3.5/py.html.en")

---

### Post by stinkeye on 2012-09-17
> **FRodrigues said:**
> Hi,

What I want is to make a simple "box" in my desktop to write anything I want, like kde's note widget:


Try xpad.
```
sudo apt-get install xpad
```

**Tip:** When right clicking in the note to bring up the context menu,
you also need to right click on the menu item. Left click doesn't work.

---

### Post by FRodrigues on 2012-09-17
> **stinkeye said:**
> Try xpad.
```
sudo apt-get install xpad
```

**Tip:** When right clicking in the note to bring up the context menu,
you also need to right click on the menu item. Left click doesn't work.

I saw the source code and it was in C.
Never learned how to make a GUI in C so I didn't understand much. : /

---

