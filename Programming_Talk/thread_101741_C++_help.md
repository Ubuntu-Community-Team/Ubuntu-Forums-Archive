---
title: "C++ help"
date: 2005-12-10
forum: Programming Talk
---

### Post by grim918 on 2005-12-10
im want to learn GUI programming for linux but it seems like everywhere i turn to they only teach microsoft stuff. does anyone know where i can find an online site where i can learn C++ programming for linux or where i can find a good book. i would appreciate any help thank you.

---

### Post by tonysathre on 2005-12-10
check this:

[http://www.comptechdoc.org/os/linux/programming/c/linux_pgc.html](http://www.comptechdoc.org/os/linux/programming/c/linux_pgc.html)
and this:
[http://www.cyberdiem.com/vin/learn.html](http://www.cyberdiem.com/vin/learn.html)

---

### Post by Burke on 2005-12-10
The only thing I can think of right now is [http://gtk.org/tutorial/](http://gtk.org/tutorial/)

You will also want to use Glade for all the boring parts of the design. (apt-get install glade, i think) 

If anyone knows of a good book for GTK, I would be interested as well.

---

### Post by Adrian on 2005-12-10
[QUOTE=Burke]If anyone knows of a good book for GTK, I would be interested as well.[/QUOTE]

[The Official GNOME 2 Developer's Guide]("http://www.nostarch.com/frameset.php?startat=gnome_foundation") is nice. It's available as an ebook at my local library, so you might check your own library to see if they have it before you buy (it's always nice to take a look before buying).

---

### Post by gord on 2005-12-10
if you want to build cross platform stuff (linux windows [maybe mac..]) you might want to try out [wxWidgets](http://www.wxwidgets.org/), it uses gtk for linux and whatever is native for everything else.

personally i prefer just making command line based applications... less hassle ;)

---

### Post by capi on 2005-12-10
You could look into wxWidgets(they have a decent book out) and find some online tutorials for autotools. The wxWidgets lightly covers setting up your Linux System, but you'll really need to do some outside reading too.

wxWidgets is cross-platform, so it's not neccessarily Linux, but it's not really Mac or Windows either. :D 

BTW. I'm assuming you already know c++, just not linux programming, right?

Hint: wxWidgets used to be called wxWindows, and you'll see old references to it as such.

[http://sources.redhat.com/autobook/](http://sources.redhat.com/autobook/)
[http://www.wxwidgets.org/](http://www.wxwidgets.org/)

---

### Post by Adrian on 2005-12-10
[QUOTE=grim918]im want to learn GUI programming for linux but it seems like everywhere i turn to they only teach microsoft stuff. does anyone know where i can find an online site where i can learn C++ programming for linux or where i can find a good book. i would appreciate any help thank you.[/QUOTE]

If you know the C++ basics and want to learn Linux GUI programming, I strongly recommend you to take a look at [QT]("http://www.trolltech.com/products/qt/index.html") (upon which KDE is built). It's easy to learn, and Trolltech just made [their official programming book]("http://www.amazon.com/gp/product/0131240722/ref=ase_trolltech/104-2859535-6171158?s=books&v=glance&n=283155") available for downloading:
[http://phptr.com/content/images/0131240722/downloads/blanchette_book.pdf](http://phptr.com/content/images/0131240722/downloads/blanchette_book.pdf)

---

### Post by Burke on 2005-12-10
Oh yeah, I had forgot about wxWidgets... I'm going to have another look at that.  Thanks!

---

