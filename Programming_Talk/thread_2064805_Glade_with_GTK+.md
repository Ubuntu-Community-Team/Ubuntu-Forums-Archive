---
title: "Glade with GTK+"
date: 2012-09-30
forum: Programming Talk
---

### Post by Dr Berta on 2012-09-30
Hi all,
I'm trying to evaluate the usage of glade + GTK+ 3.0 to design user interfaces in C applications.
I tried to design with glade a simple program with a windows where I instantiated an image and two buttons. Then I wrote a simple C program to show the windows and use the buttons.
The compilation goes well, but when I run the application I see the image but the two buttons are disabled.

Attached you can see the code.

Where is my mistake? 

Thanks for the help

---

### Post by MG&amp;TL on 2012-09-30
Your code needs to be needlessly obfuscated. I don't know about anyone else, but I wouldn't put translation support in an evaluation, for one thing.

Anyway, you seem to have commented out the calls to gtk_widget_show(), which will result in the buttons not appearing. How do you mean 'disabled'?

---

### Post by Dr Berta on 2012-10-13
I apologize if my code is bad.  The code has been automatically created by Anjuta I only added the callbacks functions, the widget get object instructions and the signal connect instructions.
About the translation support, it is present because I was playing with the different types of project that could be created using Anjuta.
 
About the commented gtk_widget_show() instructions, I commented them , after I saw that were useless. In any case the buttons are always present, but grayed and not active (this means "disabled").

Anyway, I solved that problem selecting in Glade the property "sensible". Only in this way the buttons can work properly.

I can say that the problem is solved.

Bye

---

