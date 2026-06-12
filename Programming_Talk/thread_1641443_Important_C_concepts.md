---
title: "Important C concepts"
date: 2010-12-09
forum: Programming Talk
---

### Post by c2tarun on 2010-12-09
I was looking forward in order to fix some bugs on launchpad.net
I was pretty much familiar with C and C++. But after seeing some of the source codes of some packages, I found that I am not familiar with most of the concepts used on that source code ( my confidence is just sinking and sinking and sinking.... :cry: :cry: ).

I am asking that if possible list some of the important concepts of C that are used in developing various packages for ubuntu. (some package examples are: empathy, gnome-panel, totem etc. these all are considered small packages).

Please help!!

---

### Post by saulgoode on 2010-12-09
Many programs written for GNOME make extensive use of the functionality provided by [GLIB]("http://library.gnome.org/devel/glib/2.26/"). GLIB offers standard utility functions for implementing complex data structures, managing memory, using threads, passing messages, and... other stuff :).

Learning GLIB can be rather daunting. I would suggest that you follow some tutorials such as [this one (which focuses on data structures)]("http://www.ibm.com/developerworks/linux/tutorials/l-glib/section2.html").

---

### Post by c2tarun on 2010-12-09
> **saulgoode said:**
> Many programs written for GNOME make extensive use of the functionality provided by [GLIB]("http://library.gnome.org/devel/glib/2.26/"). GLIB offers standard utility functions for implementing complex data structures, managing memory, using threads, passing messages, and... other stuff :).

Learning GLIB can be rather daunting. I would suggest that you follow some tutorials such as [this one (which focuses on data structures)]("http://www.ibm.com/developerworks/linux/tutorials/l-glib/section2.html").

thanks, i actually started reading Gtk+ programming. May be that helps a bit and i am really enjoying it :)

Any other concepts ???

---

### Post by saulgoode on 2010-12-09
> **c2tarun said:**
> Any other concepts ???

RTFM!

Seriously. The man pages provide an excellent reference for most system commands and concepts. Of particular use is the '**-k**' option which shows pages that might be related to the provided keyword (for example, '*man -k permission*'). 

Also, useful is the '**-a**' option which will provide ALL results matching the search term (one-at-a-time). As an example, '*man -a signal*' will first display (in your viewer) the page for the ['*signal()*' system call]("http://linux.die.net/man/2/signal") then (after you quit that view) display the [man page for a signal overview]("http://linux.die.net/man/3/signal").

---

### Post by nvteighen on 2010-12-09
Well, there are some key APIs for GNU/Linux or UNIX development. For example (this list isn't comprehensive...):

0. The POSIX (aka System V) API: fork, filesystem manipulation, pthread, popen, several data types used for system programming, etc.
1. ncurses
2. GTK+ & GLib
3. Qt

Of course, most of these are learned by need... but you should know their basics. For example, everyone that intends to use C or C++ in a UNIX/Unix-like environment should know what fork() does even if you end up never using it.

---

### Post by worseisworser on 2010-12-09
Don't forget GObject (part of the Gnome/Gtk+ project and used a lot); you need to understand object oriented programming even though you might be dealing with C.

---

### Post by c2tarun on 2010-12-09
from your suggestions i figured that first i should start with GTK+.
currently i am referring to this book.
Apress.Foundations.of.GTK.plus.Development
for GTK+
if some better books are there please tell me.
further suggestions for more C concepts will be appreciated.
thanks a lot guys. :)

---

### Post by Mr. Picklesworth on 2010-12-09
It's also [GObject]("http://en.wikipedia.org/wiki/GObject"), which is a joy :b

GObject is an object system, so that crazy looking C code can do fancy stuff you usually see in object oriented languages (like inheritance, and polymorphism). The disadvantage is, as you have seen, piles of boilerplate code (and #DEFINE type things).
For libraries, the advantages far outweigh the disadvantages because that GObject stuff is really portable. (Especially with GObject introspection!)

You may find [Vala]("http://live.gnome.org/Vala") kind of enlightening. It's an object-oriented language with a syntax similar to C#. Its object system is actually GObject and it compiles through C. So, you can get some sense of the GObject system through Vala itself, and through the C code it generates (when you pass the -C flag to valac).

It actually talks with GObjects written in C using its own native syntax. So,
*var map = new HashMap<string, int> ();*
turns into:

```

	GeeHashMap* _tmp0_ = NULL;
	GeeHashMap* map;
	_tmp0_ = gee_hash_map_new (G_TYPE_STRING, (GBoxedCopyFunc) g_strdup, g_free, G_TYPE_INT, NULL, NULL, NULL, NULL, NULL);
	map = _tmp0_;

```

Beware, though: as you can see, the C code isn't pretty, since it's generated only as a middle step to building a program :)

---

