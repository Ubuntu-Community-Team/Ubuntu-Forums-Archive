---
title: "pyGtk tutorials?"
date: 2007-08-16
forum: Programming Talk
---

### Post by Hex_Mandos on 2007-08-16
I'm trying to learn Python, and having some fun in the process. There are some great resources out there to learn Python, but I haven't been as lucky with GUI toolkits. Is there a good pyGtk tutorial for beginners to both Python and GTK? (not necessarily for programming beginners, I'm no hacker but I've fooled around with Clipper, C, VB5/6 and PHP at several points in my life.. not that I can do anything useful with most of them today)

---

### Post by AlexThomson_NZ on 2007-08-16
Googling for 'pyGtk tutorials' gives [http://www.pygtk.org/pygtk2tutorial/index.html](http://www.pygtk.org/pygtk2tutorial/index.html)

Any good?

---

### Post by Hex_Mandos on 2007-08-16
I checked it out, but I'm trying to use Glade for my GUIs, and I'm finding it hard to separate "pure" pyGtk and "Gladeified" pyGtk. Thanks anyway.

---

### Post by Moobert on 2007-08-16
a few glade tutorials I've used in the past:

[http://www.gnome.org/~newren/tutorials/developing-with-gnome/html/apc.html](http://www.gnome.org/~newren/tutorials/developing-with-gnome/html/apc.html)

[http://interactive.linuxjournal.com/article/6586](http://interactive.linuxjournal.com/article/6586)

---

### Post by pmasiar on 2007-08-17
> **Hex_Mandos said:**
> I'm trying to learn Python, and having some fun in the process. 

Yup, it is very helpful you mentioned your other experience, so I can skip advice for beginners. "dive into Python" is book for you, free online. 

What kind of apps you want to create?

For fun, there is pygame, and pyweek competition (make a game in a week).

To be more pragmatic, I would recommend: forget about GUI, browser is new desktop. Focus on web applications, with your knowledge of databases it might be more productive and smarter career-wise.

Django is (says Guido) best web app framework for beginners, but Guido knows nothing about web apps and hates XML - he rejected TurboGears' Kid templating because of that, and pure-XML is it's best feature.
Many (including me) like Turbogears more: more flexible, "best-of-breed" selection is more to my liking! :-)

---

### Post by aks_! on 2007-08-17
A good beginner article can be found here: [http://www.learningpython.com/2006/05/07/creating-a-gui-using-pygtk-and-glade/](http://www.learningpython.com/2006/05/07/creating-a-gui-using-pygtk-and-glade/)

> Django is (says Guido) best web app framework for beginners, but Guido knows nothing about web apps and hates XML - he rejected TurboGears' Kid templating because of that, and pure-XML is it's best feature.
Many (including me) like Turbogears more: more flexible, "best-of-breed" selection is more to my liking!

In my opinion, the best way for web programming is by using apache's mod_python and not some framework. In this way, one gets to learn more about the language itself and also become more efficient.

---

### Post by pmasiar on 2007-08-17
> **aks_! said:**
> In my opinion, the best way for web programming is by using apache's mod_python and not some framework. In this way, one gets to learn more about the language itself and also become more efficient.

Yes, but your way you need to do lot of work - reinventing the wheel all the time. And you will reuse half of the code for next project anyway - in a sense having custom framework, only done badly :-) I hope  that your code will be as efficient as code done by best Python experts -- sometime, but not soon I am afraid :-)

Good framework solves recurring problems and stays out of the way, like: mapping between URL and functions, object-relation mapper, integrating templates, error handling, etc. Why do your own if you can use existing modules? Why integrate them yourselves if someone did it for you? 

Of course you are free what you want to on your time, I just feel to warn anyone reading your advice.

---

### Post by Hex_Mandos on 2007-08-18
@Moobert: Thanks! That's exactly what I was looking for.

As for web apps, I might look into them in the near future. What's Python's biggest advantage over PHP for web apps (other than just having to learn a single language)?

---

### Post by pmasiar on 2007-08-18
> **Hex_Mandos said:**
> What's Python's biggest advantage over PHP for web apps (other than just having to learn a single language)?

PHP was designed for web apps, is  simple and cheap to host, so it is popular with webhosting companies. But in opinion of many, code created is messy and hard to maintain.

Python is generic OOP language, which is used mostly outside of web apps. It means more libraries for anything you can imagine. Leading Python frameworks nudge you gently to use [Model-view-controller](http://en.wikipedia.org/wiki/Model-view-controller) approach, which is by opinion of experts the only meaningful approach to GUI (like OOP is for modularization), by creating you empty project (following best practices) which you just need to enhance here and there.

I need to mention I use TurboGears web apps framework, not exactly sure how Django works but should be fine too. 

**Edit: Summary:** Python is clean widely used OOP language. PHP is kinda messy, kinda not OOP, and struggling to get used outside web apps (although all this can be overcome with some efforts, but often is not). Python is popular for scripting, and increasingly more web hosting companies are ready for Python - less than PHP, but more than for Ruby. :-)

---

