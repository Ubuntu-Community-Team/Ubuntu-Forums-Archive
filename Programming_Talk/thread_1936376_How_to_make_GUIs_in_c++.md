---
title: "How to make GUIs in c++"
date: 2012-03-05
forum: Programming Talk
---

### Post by rafaelcbf on 2012-03-05
Is it even possible? Any informative things I should be reading? Or am I barking up the wrong tree?

---

### Post by lisati on 2012-03-05
I haven't actually used them for a programming project, but GTk and Qt seem to be popular.

---

### Post by rafaelcbf on 2012-03-06
Thank you, I'll look into them, anything else? Any and all help is appreciated.


edit: Oh wow, GUIs are a whole other thing, lol, nothing I can't learn.

---

### Post by stchman on 2012-03-06
Yes it's possible.

Programming GUIs in C or C++ is platform dependent.  You need to decide which API win32(windows) GTK+(Gnome, framework available for Windows) Qt(framework available for all 3 OSes).

The Qt would probably be your best bet.  There are numerous IDEs out there.

---

### Post by xytron on 2012-03-06
My recommendation is FLTK, it's a fairly easy to use small library for C++.  QT could be a good one, I've not used it, but it is much larger than FLTK.

---

### Post by r-senior on 2012-03-06
Apart from the suggestions above, I'd suggest the Zetcode tutorials as a resource to see what's possible and try out a few simple examples:

[http://zetcode.com/](http://zetcode.com/)

For C++, the cross-platform ones to look at are:

[LIST]
[*]wxWidgets
[*]Qt4
[/LIST]

You can use GTK with C++ but if you want to write GTK-based applications (which integrate best with Gnome), consider gtkmm3 as the official C++ binding for GTK3:

[http://developer.gnome.org/gtkmm/unstable/](http://developer.gnome.org/gtkmm/unstable/)
[http://developer.gnome.org/gtkmm-tutorial/stable/](http://developer.gnome.org/gtkmm-tutorial/stable/)

If you are going down the GTK route, be aware that there is the difference between GTK2 and GTK3. You should really be looking at GTK3 for new applications and gtkmm3 supports that.

---

### Post by rafaelcbf on 2012-03-06
Muahaha, Thank you for all the help, I think that'll be enough for me to choose a platform for making my GUI, I'll try a little bit of everything, se what works best. THANK YOU SO MUCH.

---

### Post by 3Miro on 2012-03-06
QT and GTK are good for programs with buttons/menus and applications. If you want to make something simple like a small game with a few moving pictures, then SDL would be easier. I don't know how cross platform is SDL.

---

### Post by winh8r on 2012-03-06
If you choose to try FLTK as suggested earlier , there is a directory in the package named "examples" which has templates of various functions which are useful for getting you started as you can use them and just modify each part as you become more proficient with the commands.

Hope this helps you

---

### Post by rafaelcbf on 2012-03-07
No, I'm not trying to make a small game, it's more of a gag, here in mexico we there's this little person named "Margarito", and because of this Pic: [http://quetemetes.net16.net/wp-content/uploads/2012/01/medicion-en-margaritos.jpg](http://quetemetes.net16.net/wp-content/uploads/2012/01/medicion-en-margaritos.jpg) I decided to make a converter, it converts only meters, for now, to "Margaritos" (85cm), but I want to make a nice GUI to go with it, and try to incorporate more than just meters.

---

