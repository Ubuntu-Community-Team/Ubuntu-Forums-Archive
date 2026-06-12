---
title: "Good GUI Programming book?"
date: 2007-10-30
forum: Programming Talk
---

### Post by khughitt on 2007-10-30
Hey,

I've recently started teaching myself how to write gui applications using Java Swing and wxPython, however one thing I'm lacking is a good foundation on the proper way to structure a gui application.

Does anyone know of any good books or online material that discusses things like how to design a gui application, how to create a UML diagram, etc?

Any advice would be greatly appreciated :)

Thanks!

---

### Post by jviscosi on 2007-10-30
Most of my design books are at work but I do remember the title of one of the UML books, "UML Weekend Crash Course".  You'd want to use it in conjunction with a thicker UML book (which I also have but can't remember the title of) but it's a good introduction.

---

### Post by pmasiar on 2007-10-30
Learn Model-View-Controller pattern, wikipedia is the start.

Also, go with Python first. Static typing of Java is too cumbersome for research-type development.

---

### Post by slavik on 2007-10-30
If you ever use Python and GTK, consider making all the callback functions in a separate class/package, because for Python (and Perl) libglade has a function to automatically connect to functions from a given class/package (in C, you have to connect each callback explicitly).

---

### Post by khughitt on 2007-10-30
Thanks all for your suggestions. I will check out the books and websites everyone mentioned. I have a book on design patterns that has a section on MVC, so I'll start there. I've actually read a little bit about MVC before, but have never gotten around to actually creating an application using it, so the way you implement it is still kinda blurry  in my mind.

slavik- Do you  know where I might find out more information about automatic callback connections with libglade?

Take care,

---

