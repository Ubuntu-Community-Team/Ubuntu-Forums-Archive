---
title: "Folding at home GUI installer..."
date: 2008-06-03
forum: Programming Talk
---

### Post by Godofgrunts on 2008-06-03
It's done... finally... enjoy...
Please read the install document before doing anything...
Still in Alpha fill free to make it better...

When I first started using Ubuntu I was having a hard time learning how to install things. Thankfully I'm much better now. This is mostly for those people who want to get folding started and are having a hard time doing it.

***_PLEASE GO DOWN TO POST 4!!!!_***

---

### Post by Ebuntor on 2008-06-03
Hi,

Thanks for the work, sounds great.
I tried running it but I got the following error:
```
Traceback (most recent call last):
  File "./Testgui", line 5, in <module>
    import wx
ImportError: No module named wx

```

---

### Post by Godofgrunts on 2008-06-03
I am told this is a problem. Someone else complained about this on another site...

Can you tell me **exactly** what you did, what version Ubuntu you are running, whether its 32 or 64 bits and if you have wxGlade installed.

---

### Post by Godofgrunts on 2008-06-03
WOW! I'm retarded... I used an old version of Testgui for the archive... Here's the fixed version. Try it for me.

---

### Post by Ebuntor on 2008-06-04
Installing python-wxglade did the trick. :) I installed it successfully and it seems F&H is running.

---

### Post by Vadi on 2008-06-04
It's a good start. You should look into using zenity for completely guificating the installation process, and using "uname -m" to determine if the user is 32bit or 64bit (64bit reports "x86_64", and 32bit I think "i386". It is possible that you might get something other than that (ppc, ia64...)).

---

### Post by Godofgrunts on 2008-06-06
Thanks for the ideas. I'm actually going to document the rest of the updates at this location:
[http://www.overclock.net/overclock-net-folding-home-team/339776-gui-f-h-installer-linux.html](http://www.overclock.net/overclock-net-folding-home-team/339776-gui-f-h-installer-linux.html)
I get input faster and from a variety of Linux distro users so it helps production become faster. Please feel free to join the forums there and help out. :D

EDIT: How do I open/use Zenity? Do I need to open it?

> **Ebuntor said:**
> Installing python-wxglade did the trick. :) I installed it successfully and it seems F&H is running.
I find it strange that wx-glade wasn't already installed...


PS. NEW VERSION IS AVAILABLE AT THE LINK ABOVE.

---

### Post by Vadi on 2008-06-06
[http://library.gnome.org/users/zenity/stable/](http://library.gnome.org/users/zenity/stable/)

---

### Post by Godofgrunts on 2008-06-07
Hey thanks! I'll give this a try! Will it work in Mac though? (I'm hopeing to develope this so that Linux, Mac, and Windows can use it)

---

### Post by Vadi on 2008-06-07
No, it won't. You'll want to learn PyGTK (since as I see your program atm uses Glade-made GTK gui + Python) to continue further. There's a very good tutorial available here ([click]("http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html")).

---

