---
title: "Very basic GTK GUI's - how do I make them?"
date: 2006-09-25
forum: Programming Talk
---

### Post by IYY on 2006-09-25
I know C and C++ fairly well, but I never designed any interfaces in them (I did interfaces in Visual Basic :mad: and Java a long time ago, but that's obviously a whole other story). What I am working on right now is a simple program called gNovel for writers. The program is very simple: create a plain text file for each chapter, and when the export button is clicked, generate a nice LaTeX PDF out of it.

The PDF generation is done through a BASH script which I've already written, so all I really need to do is make an interface which will include:

1) A list structure for chapters, with the ability to add, remove and switch order.

2) A plain text editor to edit the currently selected chapter.

I made an interface in Glade to show what I want it to look like:

[[IMG]http://img180.imageshack.us/img180/5434/mockupgj8.th.png[/IMG]](http://img180.imageshack.us/my.php?image=mockupgj8.png)

... But I don't know where to go from here! Is there an easy tutorial on ho w to make very basic operations? What I need to know is how to make the program do something when a certain button is pressed, and how to read the text in the textbox (in order to export it to the text file).

I know the tutorial which explains all of GTK on the official GTK site, but I am a student with a very busy schedule and really don't have time to learn all of this right now, especially since all I need is very basic functionality.

---

### Post by loell on 2006-09-25
there seems to be no shortcut in gtk with c

[http://bo.majewski.name/bluear/gnu/GTK/plain/index.htm]("http://bo.majewski.name/bluear/gnu/GTK/plain/index.htm")

you have to deal with makefiles before actually making a basic app, 

this might be easier if you do this in python with pygtk.

---

### Post by DavidBell on 2006-09-26
I haven't done any linux gui stuff, just looking trying to get my bearings, but the yolinux site is the most helpful I've found so far. 

The tutorial at [http://yolinux.com/TUTORIALS/GTK+ProgrammingTips.html](http://yolinux.com/TUTORIALS/GTK+ProgrammingTips.html) may help you. Seems gtk gui programming is similar to Win32, at some point you need to set a loop listening for system messages, that activates callbacks to the functions you want to run when the user does things. In VB the system messages are called 'Events', in Win32/C++ 'Messages', in Linux 'Signals(?)' I may be completely wrong about that, anyway hope the link helps.


EDIT: BTW my experience is Win32 programming so probably a bit skewed, but if you remember back to VB, the main difference between VB & C++ GUIs is that ... in VB you just write the callback functions and VB handles the listener; in C++ you write the functions as well as the listener (often done for you by wizards thoough)

David

---

### Post by moma on 2006-09-26
Consider to use wxWidgets + Code::Blocks IDE. 
Code::Blocks itself is a wxWidget, multiplattform product.

[http://www.wxwidgets.org](http://www.wxwidgets.org)
+
[http://codeblocks.org](http://codeblocks.org)

---

