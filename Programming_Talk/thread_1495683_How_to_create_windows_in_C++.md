---
title: "How to create windows in C++?"
date: 2010-05-28
forum: Programming Talk
---

### Post by smdawson on 2010-05-28
I have been trying to figure out how to create windows in C++ that look nice and function well to add some dimension to my programs. I have been seeing lots of referals to GUI creator application, but I don't know if that is the best way to go about this or if I should be learning how to do it as seen here:
 
[http://www.bluesfear.com/tutorials/C%2B%2Bwindow_p1.php]("http://www.bluesfear.com/tutorials/C%2B%2Bwindow_p1.php")
 
If anyone has advice or links I would greatly appreciate it. Cheers

---

### Post by Simian Man on 2010-05-28
> **smdawson said:**
> 
[http://www.bluesfear.com/tutorials/C%2B%2Bwindow_p1.php]("http://www.bluesfear.com/tutorials/C%2B%2Bwindow_p1.php")
 
If anyone has advice or links I would greatly appreciate it. Cheers

That code will only work on MS Windows.  C++ does not provide any way to create windows or other GUI controls in and of itself, you will need a separate library to do that.

I'd recommend something that will work on more than one operating system such as wxWidgets or Qt.

---

### Post by crazyfuturamanoob on 2010-05-28
I have used GTK+ in the past for my GUI programs, and SDL or GLUT for games.

GTK+ has all sorts of buttons, text fields, sliders, checkboxes etc. 95% of applications in Ubuntu use GTK+.
SDL just creates a window and lets you mess with invidual pixels and do other low-level stuff. No any GUI features.
GLUT is for use with OpenGL. It has just a simple right-click menu.

They're all cross-platform.

---

### Post by KdotJ on 2010-05-28
If you want to get in quick, Qt Creator is a good GUI building IDE which as the name suggets uses the Qt framework and libraries. It's in the ubuntu repos so it's easy to get hold of. You could always have a go at it and look at how the code works, I believe there is also some sort of explaination pane where you can look up how it works

---

### Post by sheperson on 2010-05-28
+1 for Qt.
It gives you more than a GUI library.

---

### Post by mmix on 2010-05-28
GUI in linux is weakness, compare to windows.

If you start to create window with gtk/qt,
there will be library dependency problem.

Even if you don't programming gui with Xlib,
you have to learn basic knowledge of x windows system(Xorg),
All is dumb wrapped libraries of it in linux.

[http://www.ultimatepp.org/](http://www.ultimatepp.org/)
[http://qt.nokia.com/products](http://qt.nokia.com/products)
[http://www.newplanetsoftware.com/jx/](http://www.newplanetsoftware.com/jx/)
[http://www.gtkmm.org/](http://www.gtkmm.org/)

FBUI in linux 1992, heh.

---

### Post by nvteighen on 2010-05-29
> **mmix said:**
> GUI in linux is weakness, compare to windows.

If you start to create window with gtk/qt,
there will be library dependency problem.

Even if you don't programming gui with Xlib,
you have to learn basic knowledge of x windows system(Xorg),
All is dumb wrapped libraries of it in linux.

[http://www.ultimatepp.org/](http://www.ultimatepp.org/)
[http://qt.nokia.com/products](http://qt.nokia.com/products)
[http://www.newplanetsoftware.com/jx/](http://www.newplanetsoftware.com/jx/)
[http://www.gtkmm.org/](http://www.gtkmm.org/)

FBUI in linux 1992, heh.

No different in Windows... you also have to link to the WinAPI or .NET libraries... ok, they will be automatically linked, but you still have the same issue.

Come on: if it's not part of the language, it's part of a library, therefore, you have a dependency to resolve.

Now, you don't need any Xlib knowledge to code a good GUI in GTK+ or Qt, because both are examples of how to develop a great library, even being both very different in their philosophy. Actually, you don't need Xlib for them as both work in Windows too!

---

