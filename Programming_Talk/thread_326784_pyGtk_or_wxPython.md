---
title: "pyGtk or wxPython?"
date: 2006-12-28
forum: Programming Talk
---

### Post by tzulberti on 2006-12-28
Hi. I am finishing reading Dive into Python, and i would love to learn howto program for X (Gnome, KDE, etc...). I have looked around and the most two interesting for me are: pyGTk and wxPython. 

I would like if you could tell me which do you use, and why.

Thanks,
Tomas

---

### Post by kperkins on 2006-12-28
If you're going to program just for Gnome or Linux then go with GTK, if you want cross-platform compatibility, then wx is the way to go.
I actually find wxPython easier, myself, but that's just me.
They both have excellent gui buiders (glade and wxglade, although the code that wxglade generates does need some tweaking to be usable, I don't remember how glade is, since I haven't used it for a while.)

---

### Post by nephish on 2006-12-28
i like python-gtk, has excellent documentation, it's own mailing list, etc...
glade is a dream to work with. There is even a simple app out there called tepache that will parse your glade file and build a simple python file skeleton that you can modify pretty easily.

i use it for everything GUI

hth

---

### Post by mexlinux on 2006-12-28
I personally prefer PyQt, I found it easies, very well documented and extreamly portable. (and in general I fouod Qt widgets nicer than GTK ones)

---

### Post by maddog39 on 2006-12-28
Hmm.. PyQt is for the Qt toolkit which is KDE only though. I'm pretty sure it still works in GNOME but developing Qt in GNOME is not recommended or doesnt make sense to say the least. I personally really like and use wxPython, I think it's the easiest to use and requires MUCH less code than PyGTK. I've been thinking about trying PyGTK with glade although I wish it was as easy to use as the PHP-GTK glade system.

---

### Post by nephish on 2006-12-28
maddog39,
really, check out tepache. it does a whole lot of the code for you. 
basically it reduces your work to filling in events.

---

### Post by gummibaerchen on 2006-12-28
As I have seen pygtk hard-code sucks for bigger apps.

You should really use Glade.

Are there any tutorials for dive into PyQt**4**? (nice ones i mean)

I use pygtk + glade, but sometimes the code is far too long, as some options are missing in glade which i then have to set in the source-code itself...

If you consider using python + gtk have a look at Kiwi, as it makes development faster and leads to sweeter code :)

---

