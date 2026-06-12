---
title: "Writing GUI for CLI app"
date: 2009-09-16
forum: Programming Talk
---

### Post by Morat on 2009-09-16
Sorry if this has been asked to death...

I have created a little command-line application (in perl) and would like to write a gui front-end to it.

What tools should I consider? I have glanced at Eclipse and I think it might be what I need but Synaptic lists about 15 packages and I have no idea which ones to install. Any suggestions for an IDE in which I can write GUI tools to interact with a CLI back end?

All I want to do is design the front end windows & dialogs, call the CLI back end and populate the widgets with the results.

btw, I am coming from a Windows & .NET background so ideally I am looking for something like Developer Studio. I am not expecting to get it though!

--- Alistair.

---

### Post by phrostbyte on 2009-09-16
Look at Glade

[http://glade.gnome.org/](http://glade.gnome.org/)

There are probably some glade-perl bindings too if that is what you want.

---

### Post by j7%&lt;RmUg on 2009-09-17
For gnome go with glade and gtk(you can get bindings for ALOT of languages), or for KDE for with the tk toolkit.

A google search will get you all the information you need.

---

### Post by hellmet on 2009-09-17
Similar question : Which combination is the most lightweight option?
I am thinking C++/QT but I'm not sure, I'm very new. 

*Objective : *
I will be writing GUI frontends for some common Linux commands, but for a minimal environment - say Fluxbox or Openbox and I don't want to have to depend on either Gnome or KDE libraries for that.

---

### Post by djbushido on 2009-09-17
Trying to program gui's will inherently lead to lots of dependencies. If you are programming for flux/black box environment, chances are good that they will have the gtk libraries installed. If so, then you can look at the "glade" builder, but I find that much better results are always obtained by doing it yourself.

---

### Post by Bodsda on 2009-09-17
> **djbushido said:**
> but I find that much better results are always obtained by doing it yourself.

I'l +1 you on that.

From experience, the simplest toolkit to use to write it yourself is tkinter. Especially with python but I would expect their to be sufficient perl bindings as well

---

### Post by djbushido on 2009-09-17
Um... TKinter was originally made for perl. It later got adapted as the standard for python, although most gui python apps are written in wx.

---

### Post by matthew.ball on 2009-09-17
This might be interesting: [http://en.wikipedia.org/wiki/WxWidgets](http://en.wikipedia.org/wiki/WxWidgets)

wxFormBuilder sounds kinda fun...

---

### Post by hellmet on 2009-09-18
Glade looks good. Will give it a try, esp. since I'm new to all this. And probably with some experience coding GUI, I might do it myself.
Thanks!

---

### Post by Morat on 2009-09-22
I have had a quick go with Glade, Eclipse and QT Creator

Glade looked good and I was able to create a simple gui and see the event handlers. It was not immediatly obvious how to control the widgets programmatically though.

Eclipe also looked nice but I could not find a wysisyg gui builder in there.

QT Creator is the one I favour at the moment: I was able to create a simple 'hello world' program where a button's event handler set the text of a label widget. I was also able to run the program under a debugger and use the C system() call to run my program. I know it is probably not the best way but it worked!

I think right now, QT Creator is my favourite.

--- Morat

---

