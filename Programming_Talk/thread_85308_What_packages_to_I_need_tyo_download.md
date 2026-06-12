---
title: "What packages to I need tyo download"
date: 2005-11-02
forum: Programming Talk
---

### Post by idn on 2005-11-02
I just isntalled breezy and I want to start developing under gnome again, I was wondering what packages I need to download, I am working with anjuta and what to develop a gtk based application.

I also want to start developing a gaim plugin. 

Cheers for any help you can give me, the vast majority of my development work has been with python or java under windows.

---

### Post by psychicdragon on 2005-11-02
It depends on what language you're going to be developing in really. 

If you want to continue using Python, you can start writing GTK apps without installing any additional packages. A lot of the programs that make up the Ubuntu desktop are written in Python & PyGTK. You'll probably want glade-2 so that you can design your GUI's though.

If you want to start coding in C/C++ in Anjuta, you'll need build-essential, libgtk2.0-dev, glade-2, libglade2-dev.

---

### Post by idn on 2005-11-02
For apps I am writing from scratch I will use python, for plugins I am writing (for gaim) I need to write them in c, although its possible to write them in python, but the API is not as extensive.

I'm at work now (win00bs), but when I went to compile a program I think I got an error because it couldnt find gnome.h?

Would this be included in one of the packages you lsited? Do I have to do anything after I downloaded them?

---

### Post by idn on 2005-11-02
I installed the packages you recommended and it still cant find gnome.h, any dieas?

---

### Post by idn on 2005-11-03
Any  ideas anyone?

---

### Post by psychicdragon on 2005-11-04
libgnome2-dev ?

---

### Post by idn on 2005-11-04
[QUOTE=psychicdragon]libgnome2-dev ?[/QUOTE]

No I have that installed

---

### Post by kperkins on 2005-11-05
libgda2-dev?

---

### Post by idn on 2005-11-05
installed it, still no go :(

---

