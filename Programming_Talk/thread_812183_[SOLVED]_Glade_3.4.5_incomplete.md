---
title: "[SOLVED] Glade 3.4.5 incomplete"
date: 2008-05-29
forum: Programming Talk
---

### Post by Tony Flury on 2008-05-29
It may be that i have installed it wrong - or i do not have all the packages i need - but when i run Glade 3.4.5, i do not get the Build or Project Options items in the File Menu.

Do i need another package installed or am i missing something ?

---

### Post by sq377 on 2008-05-29
Glade no longer manages code.  It just generates a .glade files now (as opposed to glade-2).

---

### Post by Tony Flury on 2008-05-29
So all the online documentation sets that i have found about how it generates code etc is incorrect ? That is shame.

Is there an online documentation showing how to use Glade 3 ? 

or is it easier to stick with Glad 2 ?

---

### Post by sq377 on 2008-05-29
This one looks pretty good:
[http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html](http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html)

---

### Post by slavik on 2008-05-29
glade3 is pretty much like glade2 when creating an interface, the end-product is different. IMO, using libglade to load glade xml files is better.

---

### Post by MicahCarrick on 2008-05-29
Glade 3.x removed the "Build" feature as it had long been a deprecated means of using Glade. Although it may seem odd to remove it to a new user, it allows Glade to be MUCH, MUCH, more flexible (ie. you could design a GUI without knowing or caring which language your are going to use to implement that design) as well as many other setbacks. Even with glade 2, most developers were not using the Build feature.

The first part of my tutorial which somebody linked to above ([http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html](http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html)) shows how to design a basic text editor in Glade and then implement it in C or Python without having to change the design (the part Glade does) at all.

If you find tutorials online in which code generation is being used, then those tutorials are likely to be quite old. As GTK+ has evolved, so has Glade.

You use glade to design a GUI. This GUI is descibed in an XML format (the .glade file) which your application will parse and build the GUI from.

You can use Libglade to do the parsing and GUI building or, GtkBuilder which is already built in to GTK+ 2.12 and above and thus doesn't require an additional library. However, lots of people have not yet made the transition to GtkBuilder (as is reflected in many tutorials) and Glade does not yet save to GtkBuilder (it should by 3.6) but it's almost identical in it's API and using GtkBuilder now will be get you a head start on where we're all headed.


So, in short: 

1. Glade creates a file which describes a GUI in XML format.
2. An application parses and builds that GUI using a library; either Libglade (separate library) or GtkBuilder (part of GTK+). When reading tutorials and you see Libglade, just remember that they work almost exactly the same and GtkBuilder is replacing Libglade in the future.
3. Until Glade 3.6 is released, you will have to use a script (installed with GTK+) called gtk-builder-convert to convert the .glade file created with Glade to a GtkBuilder format.

---

### Post by slavik on 2008-05-29
I am interested, what does GtkBuilder provide that is not available in libglade?

---

### Post by MicahCarrick on 2008-05-30
Here's my personal, non-official, response...

[_Libglade to GtkBuilder F.A.Q. - Why Is Libglade being replaced by GtkBuilder... what's wrong with Libglade?_]("http://www.micahcarrick.com/05-30-2008/gtk-builder-libglade-faq.html#3")

---

### Post by slavik on 2008-05-31
> **MicahCarrick said:**
> Here's my personal, non-official, response...

[_Libglade to GtkBuilder F.A.Q. - Why Is Libglade being replaced by GtkBuilder... what's wrong with Libglade?_]("http://www.micahcarrick.com/05-30-2008/gtk-builder-libglade-faq.html#3")
that clears it up, thanks :)

---

### Post by Tony Flury on 2008-06-01
Just wanted to say a big thank you to all who replied so rapidly to my initial question. Greatly appreciated that you would help with such a basic question.

---

