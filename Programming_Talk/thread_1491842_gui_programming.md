---
title: "gui programming"
date: 2010-05-24
forum: Programming Talk
---

### Post by aracky on 2010-05-24
Hello,
 
1) Do the developers of ubuntu os use an ide for the gui programming? if yes' then which one?
 
2) I'd like to hear recommendations from ubuntu programmers about favourite ide for developing programs with gui (gtk, of course).
 
thanks...

---

### Post by splicerr on 2010-05-24
I think you somehow got the wrong idea about Ubuntu.  Ubuntu is a Linux distro that mostly packages software developed by others.

---

### Post by nvteighen on 2010-05-24
Modern GUI programming uses libraries to do the job. In GNU/Linux, we've got plenty of them such as GTK+, Qt, wxWidgets, Tk, GNUStep, etc. GTK+ and Qt are peculiar because they are used consistently through GNOME and KDE, respectively, in order to have a consistent look in the DE default configuration, but you can start using GTK+ stuff in KDE or Qt in GNOME without any trouble (well, it might look a bit bad) or even GNUStep stuff in any of both! (it will look utterly bad, though). And remember Xfce also uses GTK+ as its "official" library.

So, it boils down to the fact that each program uses its own GUI libraries. And as any library, you can write code for it manually in a text editor. IDEs are actually just a useful tool for not to write ugly-as-hell GUI code by hand, so it actually doesn't matter what IDE you use, as long as the generated code compiles.

---

### Post by MadCow108 on 2010-05-24
glade is a gtk gui builder
[http://glade.gnome.org/](http://glade.gnome.org/)

---

### Post by snip3r8 on 2010-06-23
> **MadCow108 said:**
> glade is a gtk gui builder
[http://glade.gnome.org/](http://glade.gnome.org/)
glade is rocket science...

---

