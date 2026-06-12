---
title: "Using Glade as a RAD environment"
date: 2008-10-14
forum: Programming Talk
---

### Post by blah569 on 2008-10-14
After you design an interface in Glade, how do you go about actually starting to right the C++ for the application?  Like, I guess "Publish" your interface so you can start to write the C++?

Thanks for any assistance.

---

### Post by errepunto on 2008-10-14
You need to use "libglade" to load the ".glade" file that Glade GUI designer builds. In this link you can found several examples in C and Python:
[http://www.jamesh.id.au/software/libglade/]("http://www.jamesh.id.au/software/libglade/")

---

### Post by samjh on 2008-10-15
> **blah569 said:**
> After you design an interface in Glade, how do you go about actually starting to right the C++ for the application?  Like, I guess "Publish" your interface so you can start to write the C++?

Thanks for any assistance.

Blah569's reply gives you a link to sample code on how to use libglade with C.

For C++, you can either use the C binding, or use libglademm:
[http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/chapter-libglademm.html](http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/chapter-libglademm.html)

---

