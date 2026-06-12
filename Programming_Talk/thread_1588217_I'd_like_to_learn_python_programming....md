---
title: "I'd like to learn python programming..."
date: 2010-10-04
forum: Programming Talk
---

### Post by dkjMusic on 2010-10-04
and was wondering what IDE is recommended. I've used Delphi extensively, so something similar would be great. Would wxWidgets be the way to go to write full-fledged windowed, interactive applications for Ubuntu?

In other words, I want an IDE for Python that is as similar to Delphi for Object Pascal as possible; i.e., drag-and-drop components for the GUI and Python for event handling, database connections, etc.

---

### Post by juancarlospaco on 2010-10-04
IDE is matter of personal tastes, i use a simple text editor.
GUI toolkits the same, you can use anything you like, i use TKinter and Web2Py.
:)

---

### Post by SoftwareExplorer on 2010-10-04
I've heard that pygtk is nice because it lets you keep the code and interface separate (ie you can redisign the UI without rewriting a lot of code). You can use the Glade interface designer to design the gui for the program from a graphical interface.

---

### Post by doorknob60 on 2010-10-05
PyGTK is nice, but I also have some experience with PyQT, and it's pretty good too. And QT Designer is pretty good (haven't tried Glade for GTK, but I know QT Designer is good).

---

### Post by soapytheclown on 2010-10-05
pyqt was so easy to learn, i actually learnt it really fast from this book

[http://www.amazon.co.uk/Rapid-GUI-Programming-Python-Development/dp/0132354187/ref=sr_1_1?ie=UTF8&s=books&qid=1286293163&sr=8-1](http://www.amazon.co.uk/Rapid-GUI-Programming-Python-Development/dp/0132354187/ref=sr_1_1?ie=UTF8&s=books&qid=1286293163&sr=8-1)

which also has an awesome python primer at the start!!

---

### Post by nvteighen on 2010-10-05
Qt and GTK+ are the two "big boys" of GNU/Linux GUI toolkits. And they are equally powerful. So, it's really only a matter of:

1) What platform you're targeting to: GTK+ for GNOME and Qt for KDE... OK, you can run a GTK+ app in KDE or a Qt one in GNOME, but it might not look completely good.

2) Taste. Being both equally useful, both have their style and you have the right to choose which you like better :P

---

### Post by juancarlospaco on 2010-10-05
I use TKinter, it looks the same on KDE and Gnome, 
plus it dont install GTK on KDE, and dont install QT/KDELibs on Gnome.

:)

---

### Post by spjackson on 2010-10-06
> **juancarlospaco said:**
> I use TKinter, it looks the same on KDE and Gnome, 
plus it dont install GTK on KDE, and dont install QT/KDELibs on Gnome.

Perhaps I've just been unlucky but all the Tk applications I have tried have looked ugly. It seems to me that Tk enables you to make applications that are equally ugly across all platforms. ;-) A GTK application under KDE or a Qt application under Gnome might look out of place, but they don't look as ugly (at least to me) as Tk.

Could you please point me to an example of a Tk application that looks OK on either KDE, Gnome or Microsoft Windows? I'd really be interested in giving Tk another go if I could be persuaded that it will look OK.

---

### Post by OgreProgrammer on 2010-10-06
I like geany as an editor. You might want to use quickly if you are interested in developing with gtk.

---

### Post by soapytheclown on 2010-10-06
> **spjackson said:**
> Perhaps I've just been unlucky but all the Tk applications I have tried have looked ugly. It seems to me that Tk enables you to make applications that are equally ugly across all platforms. ;-) A GTK application under KDE or a Qt application under Gnome might look out of place, but they don't look as ugly (at least to me) as Tk.

Could you please point me to an example of a Tk application that looks OK on either KDE, Gnome or Microsoft Windows? I'd really be interested in giving Tk another go if I could be persuaded that it will look OK.

no you're right tk looks like ***, qt looks good is x plat even in windows and mac and is easier than the rest to learn IMO

---

### Post by juancarlospaco on 2010-10-06
> **spjackson said:**
> Perhaps I've just been unlucky but all the Tk applications I have tried have looked ugly. It seems to me that Tk enables you to make applications that are equally ugly across all platforms. ;-) A GTK application under KDE or a Qt application under Gnome might look out of place, but they don't look as ugly (at least to me) as Tk.

Could you please point me to an example of a Tk application that looks OK on either KDE, Gnome or Microsoft Windows? I'd really be interested in giving Tk another go if I could be persuaded that it will look OK.

My apps intentionally dont run on Windows.
My apps actually use GTK/KDE Themes by default.
My apps allow user to change title, skin, font, hide widgets.

Random Examples *(old versions)*:
[IMG]http://file.status.net/identica/juancarlospaco-20100624T021321-qapycyp.jpeg[/IMG]

[IMG]http://img268.imageshack.us/img268/9053/qrgui.jpg[/IMG]


I point you, i just use common sense, so in LiGNUx everything is a file,
then parse the theme file, get the theme values, copy the theme on your app.
:)

---

### Post by apetresc on 2010-10-06
I'm surprised nobody has yet mentioned [PyDev](http://pydev.org/), the Eclipse extension for Python development. It's in active development and quite mature. I can tell you it's being used at quite a few large companies.

---

### Post by spjackson on 2010-10-06
> **juancarlospaco said:**
> My apps intentionally dont run on Windows.
My apps actually use GTK/KDE Themes by default.
My apps allow user to change title, skin, font, hide widgets.

Random Examples *(old versions)*:

I tried your cvfacil2 application (under Gnome) and appreciate the hard work you have put into the GUI. While it is a big improvement over some Tk applications I have seen, it still looks like Tk I'm afraid. So I think Tk is still not something I'll be using. Thanks anyway.

---

### Post by Vox754 on 2010-10-06
> **spjackson said:**
> Perhaps I've just been unlucky but all the Tk applications I have tried have looked ugly. It seems to me that Tk enables you to make applications that are equally ugly across all platforms. ;-) A GTK application under KDE or a Qt application under Gnome might look out of place, but they don't look as ugly (at least to me) as Tk.

...
The issue with Tk is that it was purposely designed, in the early 1990s, to look and emulate Motif, which was one of the first common, "standard" GUI toolkits in Unix.

If anything GTK+ and QT, try to emulate the successful GUI of Windows 98 and Macintosh systems, now seemingly "natural" to younger generations. Of course, GTK+ and QT are now independent beasts themselves.

The idea of a "native" toolkit is entirely subjective, as everything is just a library, which can be replaced by another one.

With this I'm not defending Tk as saying it is "pretty". I just try to explain its origins, as I don't like outright bashing of it, merely because of appearances, and the perceived idea that it is not "native".

Also, recently Tk has implemented the concept of "themes", which means it should be possible to globally adjust the widgets' appearances to look almost like GTK+, QT, Windows, or Mac OS X widgets. It could be thought as similar to the layer that is WxWidgets.

With that said... juancarlospaco's programs always look like those crappy hax0r program's (all in black and neon) used to crack passwords, common in the former sowjetunion, as far as I can tell.

---

### Post by Vox754 on 2010-10-06
> **nvteighen said:**
> Qt and GTK+ are the two "big boys" of GNU/Linux GUI toolkits. And they are equally powerful. So, it's really only a matter of:

1) What platform you're targeting to: GTK+ for GNOME and Qt for KDE... OK, you can run a GTK+ app in KDE or a Qt one in GNOME, but it might not look completely good.

2) Taste. Being both equally useful, both have their style and you have the right to choose which you like better :P
I agree.

However, upon reading again the opening post, I have this strange feeling the poster doesn't want to learn a lot, and just wants a GUI creator. In that case, he may as well use Gambas and be done with it. But whatever.

---

### Post by dkjMusic on 2010-10-07
> **Vox754 said:**
> I agree.

However, upon reading again the opening post, I have this strange feeling the poster doesn't want to learn a lot, and just wants a GUI creator. In that case, he may as well use Gambas and be done with it. But whatever.

Vox754, my opening post could(should) have been worded as "I want an IDE for Python that is as similar to Delphi for Object Pascal as possible; i.e., drag-and-drop components for the GUI and Python for event handling, database connections, etc."

I edited the original post accordingly. Thanks for helping me make it clearer.

---

### Post by dkjMusic on 2010-10-10
Thanks for everyone's input.

It looks like **Boa Constructor** is what I'm looking for.

---

### Post by Ozitraveller on 2010-10-10
I'm trying to learn Python too.

And I'm struggling with the idea of putting a project together with all those .py files.

I'm coming from an MS dev environment so when I do a compile I get an .exe file to run. SO all the .cs or .vb or .c files get built into the exe.

So far I have only seen really small examples of python code so I'm not sure how to build a more substantial application.

So how does this work in python where in a application I have a bunch of .py files? How do I call a class method in one .py file from another .py file?

I've decided to go with boa constructor too and I have eclipse + pydev installed.

Any help would be greatly appreciated.

Cheers

---

