---
title: "GUI creation"
date: 2007-11-20
forum: Programming Talk
---

### Post by kaervas59 on 2007-11-20
1) What do you prefer? Why?

2) What is better? Why?

---- Between ----

A) Gui creation with an utility (like netBeans)

---- or -----

B) GUI creation without an utility.

Thanks for you opinion ^_^

---

### Post by slavik on 2007-11-21
1. Glade. Glade focuses completely on the GUI. Then you use C/C++/Perl/Python/Ruby (or anything with libglade bindings) to put code in.

2. A, because you can see what it will look like without guessing what goes where. That and people aren't the libglade library :)

---

### Post by u04f061 on 2007-11-21
I would prefer GUI creation in netbeans because 
1- It is very fast
2- It keeps me away from digging into layout designs
3- It removes lot of error arising due to coding.

---

### Post by samjh on 2007-11-21
For small GUIs: hand-coded is better.

For complex or large GUIs: designer-generated is better.

Reason is that most GUI form designers are good for complex GUIs, but create a lot of unnecessary scaffolding for smaller GUI projects.  For these, just hand-coding the GUI is often cleaner.  But if the complexity of your GUI is such that hand-coding is probably going to take more time and effort than a form designer solution, then use a form designer.

---

### Post by MicahCarrick on 2007-11-21
1) What do you prefer? Why?

Glade because (as was mentioned, it is independent of language). I can layout an entire GUI (for most of my needs). Being able to see the results of various properties allows me to learn GTK+ more quickly--specifically, what properties control what. I did not understand "packing" until I tinkered around in Glade.

Furthermore, a single XML file representing my UI provides a very clean, simple solution in my opinion. It also allows me to tweak the UI without having to re-compile my application. This comes quite in handy for one particular application I have in which my user-base (co-workers in the remote office) want "this text to say this" or "move this up here". I simply email them a new .glade file and tell them where to copy it.

However, if GTK+ is not the toolkit you want to work with, then obviously Glade is not ideal. 

2) What is better? Why?

Question is not multiple choice. It's an essay question. neither is better--they are used for different circumstances.

---

