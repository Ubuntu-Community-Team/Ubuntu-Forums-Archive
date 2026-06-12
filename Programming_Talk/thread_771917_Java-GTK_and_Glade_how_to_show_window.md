---
title: "Java-GTK and Glade: how to show window ?"
date: 2008-04-28
forum: Programming Talk
---

### Post by sloggerkhan on 2008-04-28
So because I've pretty much only had java programming experience and because swing is ugly and annoys me, I'm trying to figure out how to use java .glade interpreter to build a GUIs that look better on ubuntu.

However, I am not getting anywhere.
I've successfully compiled the *.jar files for the Gnome-Java-GTK think and put them in the project build path.
No trouble with referencing them or using them.

I've got a .glade file.
I use
```

Gtk.init(null);
final XML glade;
final Window window;
window = (Window) glade.getWidget("window1");
wondow.show();

```
Which seems to execute and seems pretty much like the only example I found...
However, nothing happens!
I can't seem to find any comprehensive explanation of how to use Glade with the java GTK lib... 
Any info, advice, explaination, or anything would be appreciated.
I'm sure I'm somehow doing something completely stupid as I've never used GTK before, let alone in java....

---

### Post by midnightray on 2008-04-28
you might want to google look and feel for java. There is a GTK theme that can be set with a few lines of Java that makes it look much nicer.

nvm the google heres the link i used:
[http://java.sun.com/docs/books/tutorial/uiswing/lookandfeel/plaf.html](http://java.sun.com/docs/books/tutorial/uiswing/lookandfeel/plaf.html)

---

### Post by sloggerkhan on 2008-04-28
Oh, wow, that was pretty easy, I guess.
Of course that way still using Java's layout managers and whatnot, but it's definately ages improved. 

I'd still like to learn how to use regular GTK with Java, but I guess this gives me an excuse not to.

---

### Post by gator on 2008-07-01
Did you forget to load the glade file?

glade = Glade.parse ("data/simple.glade","window1");

then you can implement the window delete event, something like this :-

window.connect(new Window.DELETE_EVENT() {
	            public boolean onDeleteEvent(Widget source, Event event) {
	            	System.out.println("quitting");
	                Gtk.mainQuit();
	                return false;
	            }
	        });

hope this helps

---

### Post by dtmilano on 2008-07-01
You can find packages available in the repositories:
> $ apt-cache search libg[ntl].*java$

---

