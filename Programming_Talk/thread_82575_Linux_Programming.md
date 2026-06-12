---
title: "Linux Programming"
date: 2005-10-26
forum: Programming Talk
---

### Post by p1r0 on 2005-10-26
Hi everyone!
First of all I'm not shure if this is the right place to ask this question, if not a apologize.
Now the question: I'm a windows progrmmer (not ashamed by that) and I really want to start programming for Linux, Ubuntu particularly, and I cannot find any good introductory tutorial/manual. 
I'm very confortable programming with C/C++ so I guess that that's the language I want to start coding with.

Thank you all-

p1r0 - :confused:

---

### Post by darth_vector on 2005-10-26
hi,

the gcc wiki is a great place to start. all you really need is your fav text editor (viva la vi!), gcc and cvs for source control. the main differences in the language are in OS specific libraries (like the thread libraries, for example), but the above should be enough to get you started :)

---

### Post by 23meg on 2005-10-26
A lot of Ubuntu-specific programming is done in Python, so you might consider diving into it. There's a book called "Dive Into Python" that will let you do just that. It's online at [http://www.diveintopython.org](http://www.diveintopython.org) .

---

### Post by darth_vector on 2005-10-26
oh, there is a book called

C programming in a unix environment
by: judy kay and bob kumberfeld
published by addison wesley
isbn 0201129124

great book!

---

### Post by p1r0 on 2005-10-27
Thank you both for your help.
I will look into it right away.

p1r0 - :D

---

### Post by David Marrs on 2005-10-27
[QUOTE=p1r0]I'm a windows progrmmer (not ashamed by that)[/QUOTE]
hehe, nor should you be. You probably want to be using the gnome libs and the gtk+ widget set (unless you're developing for KDE). Probably the easiest thing to do is install the glade-gnome-2 package via synaptic. That will give you the glade interface designer, and then you can use a text editor like gedit for code-behind. You could also install Anjuta for a full IDE. They both automate tasks like building makefiles for compiling projects.

As for tutorials, I still haven't found anything really good, but you should read (or at least glance over) the manuals for make, automake and autoconf at [www.gnu.org](www.gnu.org). You can also find basic tutorials on make by googling. You would also benefit from learning some basic bash scripting. To be honest, I've found the process of learning this stuff to be a long one. It's much easier to leverage the power of something like Anjuta.

---

### Post by kakashi on 2005-10-27
[QUOTE=23meg]A lot of Ubuntu-specific programming is done in Python, so you might consider diving into it. There's a book called "Dive Into Python" that will let you do just that. It's online at [http://www.diveintopython.org](http://www.diveintopython.org) .[/QUOTE]

yeah dive into python is the best. i was  a complete proggramming noob yet even i mangaed to learn the basics of python with that book.

---

### Post by az on 2005-10-27
[QUOTE=23meg]A lot of Ubuntu-specific programming is done in Python, so you might consider diving into it. There's a book called "Dive Into Python" that will let you do just that. It's online at [http://www.diveintopython.org](http://www.diveintopython.org) .[/QUOTE]

In Warty and Hoary, it was installed with the base system.  I would have to check to see if this is still the case with Breezy....

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=diveintopython](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=diveintopython)

(/usr/share/doc/diveintopython or something like that....)

##edit##
Yep!  it sure is!
emma@ubuntu:~$ dpkg -l |grep dive
ii  diveintopython                                      5.4-2ubuntu1            free Python book for experienced programmers

---

### Post by p1r0 on 2005-10-27
[QUOTE=kakashi]yeah dive into python is the best. i was  a complete proggramming noob yet even i mangaed to learn the basics of python with that book.[/QUOTE]

I will thank everyone for your help and in advance to anyone who posts.

Now you are getting me interested in python but I don't have a compliler on Ubuntu , or do I?? 
I anyone could sujest me one I'll be thankful.

p1r0 - :D

---

### Post by Pathogenix on 2005-10-27
As far as I'm aware the python interpreter is installed as part of Ubuntu. Try opening a terminal and typing "python" - that should bring up the interactive shell.

Python's an awful lot of fun.

---

