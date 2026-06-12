---
title: "c++ GUI interface programming"
date: 2007-04-27
forum: Programming Talk
---

### Post by dhruva023 on 2007-04-27
can any one give me link for c++ graphical user interface programming tutorial,

i done all turminal programming tutorial.

can any one please help me.

thanks.

---

### Post by russell.h on 2007-04-27
[http://www.wxwidgets.org/docs/tutorials/hello.htm](http://www.wxwidgets.org/docs/tutorials/hello.htm)

Of course you'll have to install the appropriate libraries first.

---

### Post by tkjacobsen on 2007-04-27
For KDE (Qt)
[http://doc.trolltech.com/4.2/examples.html](http://doc.trolltech.com/4.2/examples.html)
([http://techbase.kde.org/Development/Tutorials](http://techbase.kde.org/Development/Tutorials))
([http://techbase.kde.org/Development/FAQs](http://techbase.kde.org/Development/FAQs))

For Gnome (Gtk)
[http://www.gtk.org/tutorial/](http://www.gtk.org/tutorial/)

As said above you can also use wxwidigts..

---

### Post by WW on 2007-04-27
There is also [FLTK]("http://www.fltk.org/").

---

### Post by rekahsoft on 2007-04-27
> **tkjacobsen said:**
> For Gnome (Gtk)
[http://www.gtk.org/tutorial/](http://www.gtk.org/tutorial/)Note that you will be using the gtkmm wrapper of the gtk+ library ;) :P

---

### Post by octoberdan on 2007-04-27
> **dhruva023 said:**
> can any one give me link for c++ graphical user interface programming tutorial,

i done all turminal programming tutorial.

can any one please help me.

thanks.

Although it has been awhile since I've done graphical C++ work, I enjoyed great success using qt (qt3 at the time, now qt4 is out) to write a simple front-end controlling a steganography engine I wrote. Perhaps apt-get qt4-designer? 
Googling found me [http://sector.ynet.sk/qt4-tutorial/](http://sector.ynet.sk/qt4-tutorial/) . Good luck and happy geeking!

---

### Post by rekahsoft on 2007-04-27
since octoberdan mentioned qt4-designed i have to mention glade and glademm :D ```
sudo aptitude install glade-3 glade-gnome-3 glademm
```

---

