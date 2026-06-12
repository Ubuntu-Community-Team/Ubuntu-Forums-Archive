---
title: "How did you learn to use Glade?"
date: 2009-08-05
forum: Programming Talk
---

### Post by kpkeerthi on 2009-08-05
I'm fairly comfortable with Python now and want to start developing using PyGTK and Glade. Is there a decent documentation or book that helps understand and use Glade, preferably with Python?

---

### Post by ToyImp on 2009-08-05
I just started doing this as well actually. For GUI developement I didn't start out with Glade at all. I just started out with actually coding it so I can understand the structure of the code. Instead of doing something in Glade then going 'wtf does this line mean'. Before you can use a WYSIWYG app you need to know the code in my opinion. 
[http://www.pygtk.org/pygtk2tutorial/index.html](http://www.pygtk.org/pygtk2tutorial/index.html) - for tutorials

[http://www.ittc.ku.edu/~niehaus/classes/448-s04/448-standard/gtk_gui_examples/](http://www.ittc.ku.edu/~niehaus/classes/448-s04/448-standard/gtk_gui_examples/)
- for reference.

---

### Post by mmix on 2009-08-05
> **ToyImp said:**
> I just started doing this as well actually. For GUI developement I didn't start out with Glade at all. I just started out with actually coding it so I can understand the structure of the code. Instead of doing something in Glade then going 'wtf does this line mean'. Before you can use a WYSIWYG app you need to know the code in my opinion. 
[http://www.pygtk.org/pygtk2tutorial/index.html](http://www.pygtk.org/pygtk2tutorial/index.html) - for tutorials

[http://www.ittc.ku.edu/~niehaus/classes/448-s04/448-standard/gtk_gui_examples/](http://www.ittc.ku.edu/~niehaus/classes/448-s04/448-standard/gtk_gui_examples/)
- for reference.

+1 agreed, i had tried glade in c/c++, but simply gtk code is much easier to me.

---

### Post by ToyImp on 2009-08-05
I just found this in my bookmarks as well. Which is an awesome tutorial. 

[http://www.overclock.net/application-programming/342279-tutorial-using-python-glade-create-simple.html](http://www.overclock.net/application-programming/342279-tutorial-using-python-glade-create-simple.html)

---

### Post by kpkeerthi on 2009-08-05
@ToyImp.
Thanks for the links. 

And yes, you are right. I do not want to jump into Glade straightaway. The PyGTK tutorial seems fairly comprehensive (although I haven't looked into it deeply). 

I just finished reading 'Learning Python' by Mark Lutz and I thoroughly enjoyed reading it. The book covers the 'basics' in-depth. I now need broaden my Python skills and put the concepts learned into practice. 

My ultimate objective is to contribute some useful GUI applications based on Python/PyGTK and eventually involve in the development of one of the existing popular ones in use today. I know its time consuming to reach to that point but I'm making a fairly good progress :)

I believe I made a right choice choosing Python/PyGTK/Glade. Any advice in this regard is welcome.

---

### Post by The Cog on 2009-08-05
As I understand it, something called GtkBuilder is becoming a standard part of libglade, and takes away a lot of the grunt work building a GUI. This tutorial is rather good, I thought:
[http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html](http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html)

---

### Post by kpkeerthi on 2009-08-05
Yes. libglade is the (external) library that is required to parse the glade (xml) file and generate the GTK Widget tree. GTK2.12 and higher has GtkBuilder, that is built right into GTK+, for the same purpose (generating the widgets from xml).

---

### Post by kpkeerthi on 2009-08-05
I was just playing with Glade and I guess I now have a hang of it. I made the mockup of Internet Explorer's **LAN Settings** screen. I'm at work so no access to Linux/Ubuntu. I made this using PyGTK/Glade/GtkBuilder on Windows. Just wanted to try something that has a fairly complex layout and I'm quite happy with the end result , considering this my first encounter with Glade. :)

---

