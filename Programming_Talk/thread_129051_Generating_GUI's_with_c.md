---
title: "Generating GUI's with c"
date: 2006-02-12
forum: Programming Talk
---

### Post by orlox on 2006-02-12
I've programmed in c lately, and I'd like to make programs that work with a GUI. I'm pretty much tired of only being able to use the standard output and input...
Any help?

---

### Post by Retrix on 2006-02-12
You're going to have to choose a toolkit to use. I would recommend [GTK]("http://www.gtk.org"), which is what Gnome uses.
There are plenty of tutorials on the GTK site and around the Internet. Be warned though that it is a big step up to GUI programming in a language such as C, but it is well worth the effort in learning it.

Good luck!
-Sam

---

### Post by orlox on 2006-02-12
Thanks for the tip, I'll take a look at that later...any advice on a good tutorial or book on GTK?

---

### Post by Adrian on 2006-02-12
[QUOTE=orlox]Thanks for the tip, I'll take a look at that later...any advice on a good tutorial or book on GTK?[/QUOTE]

Tutorial:
[http://www.gtk.org/tutorial/](http://www.gtk.org/tutorial/)

The Official GNOME 2 Developer's Guide:
[http://www.nostarch.com/frameset.php?startat=gnome_foundation](http://www.nostarch.com/frameset.php?startat=gnome_foundation)

---

### Post by Vegettex on 2006-02-13
I don't know if you want a gui for applications or for games but i always use allegro for my gamesdevelopment with c. Pretty cool :) [http://alleg.sourceforge.net](http://alleg.sourceforge.net)

---

### Post by ebash on 2006-02-13
[QUOTE=orlox]Thanks for the tip, I'll take a look at that later...any advice on a good tutorial or book on GTK?[/QUOTE]

Take a look at Glade, it's a tool that where you generate your GUI through a palette of existing widgets, then from your C program all that you have to do is to load the Glade XML file and provide all the callbacks.

---

### Post by orlox on 2006-02-13
Thanks for all the posts, already checked on GTK and it seem nice enough for many of the things I pretend. At a first glance, it gives the impression it works somewhat a la C# (with all that of event handling and widgets), and im pretty used to that language. I'll be sure to check on the other options also, guess this will keep me busy quite a time:-D

---

