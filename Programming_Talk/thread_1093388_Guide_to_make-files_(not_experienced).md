---
title: "Guide to make-files (not experienced)"
date: 2009-03-11
forum: Programming Talk
---

### Post by ChrisBuchholz on 2009-03-11
Hi,

I have set my self a goal; I want to learn how to make those make-files, therefter pack them and send it to a repository.

Now, I have been programming for a while, but I have never done something useful in anyway (general-purpose oriented), so I have never had to make the installation scripts (make-file) and pack it or anything, but I think its time I learn how to do that.

I've found different packaging guides ([https://wiki.ubuntu.com/PackagingGuide/Complete](https://wiki.ubuntu.com/PackagingGuide/Complete) for example), but first I have to create the make-files, and I can't find anything that feels like a good guide, so I'm hoping you guys know some guide og reference I can use.

I look forward to your answers!

---

### Post by cabalas on 2009-03-11
I learnt how to do makefiles I used this guide, found it really good and still refer back to it every now and then.

[http://wlug.org.nz/MakefileHowto](http://wlug.org.nz/MakefileHowto)

---

### Post by nvteighen on 2009-03-11
This is a great ressource too: [http://crasseux.com/books/ctutorial/Writing-a-makefile.html](http://crasseux.com/books/ctutorial/Writing-a-makefile.html)

---

### Post by ChrisBuchholz on 2009-03-11
Thanks for the links, guys! I'm a little confused though...

Let me explain it to you;
I have a folder and inside that folder I have a gn.py, user.conf, emails.db, man_conf/__init__.py, man_cron/__init__.py, man_db/__init__.py. I also have a symbolink link to gn.py in /usr/local/bin/.

Now I need to make those things so I have, lets say, a folder called foobar, and inside that, one can do ./configure -- make -- make install, and then everything get's setup the right way - some files goes to ~/.gn and one to /usr/local/bin/.

Is that the make file that does those things? For what I can see from your links, it's not, but I haven't read em, just looked through to find out what it was.

Can you guys explain the process to me, of what does what?

---

### Post by cabalas on 2009-03-11
It seems that what you are after is actually autotools the one source I generally refer people to is this one:

[http://www.developingprogrammers.com/index.php/2006/01/05/autotools-tutorial/](http://www.developingprogrammers.com/index.php/2006/01/05/autotools-tutorial/) 

but seeing as you are using python this one will probably also be useful:

[http://www.pygtk.org/articles/applets_arturogf/x207.html](http://www.pygtk.org/articles/applets_arturogf/x207.html)

---

