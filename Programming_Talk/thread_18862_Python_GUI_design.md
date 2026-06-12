---
title: "Python GUI design"
date: 2005-03-09
forum: Programming Talk
---

### Post by nocturn on 2005-03-09
Hello all

Does anyone know a good place to start learning GUI design with Python?  Or any good IDE's (I checked out Gazpatcho, but it is not very straight forward)?

I'm looking to pick this up fast to make cross-platform (Linux/Windows) apps instead of using VB for Windows only.  I already know perl, but I've mostly done webapps in the past...

Thanks

---

### Post by Quest-Master on 2005-03-09
Use the wxPython toolkit, and use the wxGlade to design your fancy GUIs.

Find it all at [http://www.wxpython.org](http://www.wxpython.org). You can apt-get for it, btw.

sudo apt-cache search wxpython

---

### Post by psychic on 2005-03-13
Here ya go  :D 

[list]
[*][http://higgs.djpig.de/ubuntu/www/hoary/python/python-qt3](http://higgs.djpig.de/ubuntu/www/hoary/python/python-qt3) pyqt
[*][http://higgs.djpig.de/ubuntu/www/hoary/python/python-qt-dev](http://higgs.djpig.de/ubuntu/www/hoary/python/python-qt-dev) pyqt
[*][http://higgs.djpig.de/ubuntu/www/hoary/python/python-gtk2](http://higgs.djpig.de/ubuntu/www/hoary/python/python-gtk2) pygtk
[*][http://higgs.djpig.de/ubuntu/www/hoary/python/python-gtk2-dev](http://higgs.djpig.de/ubuntu/www/hoary/python/python-gtk2-dev) pygtk
[*][http://higgs.djpig.de/ubuntu/www/hoary/python/python-tk](http://higgs.djpig.de/ubuntu/www/hoary/python/python-tk) py-tk
[/list]

More than just one lib, to suit your needs  8-)

---

### Post by DirtDawg on 2005-03-15
There's also Python Card, though I can't say I've tried it.
[http://pythoncard.sourceforge.net/](http://pythoncard.sourceforge.net/)

---

### Post by jdong on 2005-03-15
I personally recommend using WxPython... It's a nice toolkit that is very cross-platform and adaptable. It's well worth the time to learn!

---

### Post by lee_connell on 2005-03-15
Does wxPython using the GTK2 widget style yet?  otherwise it's too ugly!!!!!

---

### Post by elwis on 2005-03-17
Aha!

I started to play around in PyGTK, I'm a GNOME guy. But actually, now my plan was to get out of the boring job (which is deveolping business applications on that "other OS") and write a small system for small customers. So, I thought, maybe some of these will refuse to use a better, brown desktop OS and wants to stick with the playbox from Redmond for yet another year.

Let's face it .. GTK didn't look too good on windoze last time I tried.. so wxWidgets started to bubble around in my brain. i downloaded, I looked att the documentation that didn't exist (that wiki isn't too good if you ask me) but still managed to get some apps going. But yeeeiiak - it really looks terrible on my Gnome 2 desk!? It looks a lot more native with the XP-stylish manifest on the other OS.

So.. now what.. go GTK and demand everyone to run the Hedgehog or.. try to ignore the ugly GTK look of WxWidgets?
*sigh*...

---

### Post by elwis on 2005-03-18
Now I start to wonder? The WxPython guys tells med it looks ugly cause I'm not using wxGTK2 package? I better call in sick and run home to check that out.

---

### Post by HungSquirrel on 2005-03-18
> Let's face it .. GTK didn't look too good on windoze last time I tried..
One wonders when you last tried.  I use Gaim and The GIMP's latest GTK2-Win32 builds and I think they blend in fairly well with the Windows environment when using the Wimp theme.

---

### Post by elwis on 2005-03-18
One wonders again (we are really wondering a lot in this thread ;) )
"Wimp" theme? 

I'm running Dia on my winmachine, and of course the Gimp and I wouldn't say they look "Xp-ish" in their style? Maybe there's something I don't know..... *errrhmm - okay, there's actually A LOT that I don't know*

---

### Post by elwis on 2005-03-18
[QUOTE=Quest-Master]Use the wxPython toolkit, and use the wxGlade to design your fancy GUIs.

Find it all at [http://www.wxpython.org](http://www.wxpython.org). You can apt-get for it, btw.

sudo apt-cache search wxpython[/QUOTE]

Actually, I never found any wxGlade when apt-getting like a madman yesterday :(

---

### Post by lee_connell on 2005-03-19
[QUOTE=elwis]Now I start to wonder? The WxPython guys tells med it looks ugly cause I'm not using wxGTK2 package? I better call in sick and run home to check that out.[/QUOTE]


so how did it turn out with your testing?  when i use wxpython 2.x and run something like boa or audacity its ugly.

---

### Post by Quest-Master on 2005-03-21
Hoary's wxPython uses GTK2, and wxPython is in the repos. but not wxGlade (yet?).

So, just hang tight for Hoary final or upgrade now. :)

I prefer wxPython so much more over something like PyGTK. There is a lot less to code and it's a bit cleaner as well.

---

