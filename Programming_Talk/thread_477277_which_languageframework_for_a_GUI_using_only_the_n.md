---
title: "which language/framework for a GUI using only the notification area"
date: 2007-06-18
forum: Programming Talk
---

### Post by guix on 2007-06-18
Hello,

I'd like to build a GUI using only the notification area.
An icon will be constantly in the notification area with 2 possible states.
When the user clicks the icon, a list of clickable choices should appear.
A click on a choice launches a gksudo box which launches a script.
That's all.

Which language and framework should I use in order to minimize the developpment ? I think I have to choose the GUI toolkit / framework at first. Which is the best for notification area use ? Is Glade OK ? Then, the language, I'd like to use Python. What do you think about it ?

By the way it will be a tool to change the network settings, but very light. The only thing it will do is stop the network, symboly link a custom /etc/network/interfaces-custom to /etc/interfaces/interfaces, then start the network again.

I'm planning this tool because all the others I see also make the configuration side and are therefore limited. It's a tool for advanced users, they still would have to write and test their /etc/network/interfaces at hand. The only GUI with this orientation I know is [IFswitch]("http://alephnull.net/software/ifswitch/") which is old.

---

### Post by Max_Might on 2007-06-18
You could try with Python and PyGTK :)

---

### Post by guix on 2007-06-18
Thanks !
I've looked at it quickly, but the area notification support is [quite weak]("http://faq.pygtk.org/index.py?req=show&file=faq19.012.htp")...

---

### Post by pmasiar on 2007-06-18
maybe [http://pypanel.sourceforge.net/](http://pypanel.sourceforge.net/) ?

---

### Post by tr333 on 2007-06-18
Take a look at [GNOME Network Manager](http://www.gnome.org/projects/NetworkManager/).  This looks like it runs only in the notification area, and it's installed by default in ubuntu.

---

### Post by kknd on 2007-06-19
C++ and gtkmm are an alternative too. You could even make a Python module in C/C++ and use it in Python =)

---

### Post by guix on 2007-06-21
I'm looking at the source of Networkmanager and I don't understand something, I read it is an applet however it lives in the notification area... I'm confused.

Otherwise I don't want to use old libs like those that were advised to me. I want to use the most recommanded libs to build a GTK app living in notification area. Is that Glade ? It doesn't really matter if I can't use Python, it's only that I thought Python would make sense for such a project but I want, at the same time, to learn to use the libs of nowadays :-)

I'll have a deeper look at Glade : *By using libglade, Glade XML files can be used in numerous programming languages including C, C++, Java, Perl, Python, C#, Pike, Ruby, Haskell, Objective Caml and Schem*

---

### Post by kknd on 2007-06-21
Glade is a GTK+ UI builder for languages that have libglade binginds.

To use Glade, you will need to use Haskell + gtk2hs, Python + PyGTK, Java + Java-gnome, C++ + gtkmm, C with pure GTK+, you can choose.

---

### Post by guix on 2007-06-21
Thanks, I understand now.
I can build my GUI layout with Glade and use it with PyGTK.
However I'm not sure how to build the pop-up list I want to appear after a click on the icon in the notification area. I'll start with a simple window and in a second stage will try to intergrate it into the notification area.
I'm totally noob you know !

---

### Post by guix on 2007-06-21
I did it and immediatly after realized I don't need Glade for this, gtk.StatusIcon is my friend.
So here's my version working in the system tray.
**Backup your /etc/network/interfaces first !**
Man it works but the code is so awfull, this is my second Python script so a little help to write it well would be cool.
Also, I can't get it to work with the left click, only the right click works...

---

### Post by rugby471 on 2008-02-11
PS: To anyone reading this, the way to get it to work wth the left click is to use the flag "activate"

EG

status_icon.connect("activate", function"

---

### Post by rugby471 on 2008-02-11
PS: To anyone reading this, the way to get it to work wth the left click is to use the flag "activate"

EG

status_icon.connect("activate", function")

---

### Post by guix on 2008-02-11
Sweet, thanks !

---

### Post by guix on 2008-05-10
Rugby, if you're still there, I can't make it work with the left click ! In my script I have
```
statusIcon.connect('popup-menu', popup_menu, menu)
```

I tried to insert your
```
status_icon.connect("activate", function" 
```

I think it misses a " and a ), it should be
```
status_icon.connect("activate", "function")
```

so I wrote
```
status_icon.connect("activate", "menu")
```

but it doesn't work.

---

### Post by ::: on 2008-05-30
It's supposed to be
```

status_icon.connect("activate", function)

```
(*fuction* is not a string, but a reference to the function)

---

