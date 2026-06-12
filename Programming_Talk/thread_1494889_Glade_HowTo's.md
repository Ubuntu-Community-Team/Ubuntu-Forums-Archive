---
title: "Glade HowTo's?"
date: 2010-05-27
forum: Programming Talk
---

### Post by hawaiian1der on 2010-05-27
My friend and I want to make a front-end for his program and he put me in charge of making the GUI. I know that Glade or Gazpacho are what I would use, but I really don't know how to work either of them to their full potential. Are there any HowTo's in the forums ( I could not find any ) or and good ones on the internet ( Could not find any good ones here either :/ )?

---

### Post by saulgoode on 2010-05-27
[http://tadeboro.blogspot.com/2009/09/glade3-tutorial-1-introduction.html]("http://tadeboro.blogspot.com/2009/09/glade3-tutorial-1-introduction.html")

---

### Post by hawaiian1der on 2010-05-27
Thanks! Just in case, are there any more good ones?

---

### Post by twisted_steel on 2010-05-27
> **hawaiian1der said:**
> Thanks! Just in case, are there any more good ones?

Both of these use pygtk (python) with glade, so they may not be as applicable if you are using other languages.  However, the general usage is still the same for glade itself.

1. [http://www.learningpython.com/2006/05/07/creating-a-gui-using-pygtk-and-glade/](http://www.learningpython.com/2006/05/07/creating-a-gui-using-pygtk-and-glade/)
2. [http://www.learningpython.com/2006/05/30/building-an-application-with-pygtk-and-glade/](http://www.learningpython.com/2006/05/30/building-an-application-with-pygtk-and-glade/)

I haven't seen much on Gazpacho in a while.  The other thing that is out there is the gtkbuilder format.  Here is some information on the differences between the two formats: [http://www.learnpygtk.org/libglade-vs-gtkbuilder.html](http://www.learnpygtk.org/libglade-vs-gtkbuilder.html).  Glade3 can work with both libglade and gtkbuilder formats; you just need to set up the file format properties via Edit->Preferences.

---

