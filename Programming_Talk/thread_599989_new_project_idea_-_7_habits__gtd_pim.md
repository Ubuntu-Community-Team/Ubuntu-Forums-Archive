---
title: "new project idea - 7 habits / gtd pim"
date: 2007-11-01
forum: Programming Talk
---

### Post by brickbat on 2007-11-01
Hi, 

I want to start an open source programming project for a gtk based PIM that incorporates the 7 habits and / or gtd principles.  ie the settings should be flexible enough to allow one, the other or a combination of both.  I have done some simple stuff in python but nothing with a gui.  

1. is there a guide or something to help me get started with building guis and programming them with python.

2. is there an ide that i can use that will let me do the programming in python, design the gui with gtk widgets, and work with the databases  (mysql lite i guess) in 1 spot.


thx
bb

---

### Post by slavik on 2007-11-01
look into libglade :)

---

### Post by LaRoza on 2007-11-01
For learning, my wiki.

---

### Post by nanotube on 2007-11-02
if you just want to code for the fun of it, then go ahead. 

if your goal is to just /have/ a gtd program that you can use, then you can just use an existing one. this one in particular seems fairly complete:
[http://www.thinkingrock.com.au/](http://www.thinkingrock.com.au/)

---

### Post by brickbat on 2007-11-02
I know about thinkingrock.  I have used it for about 4 or 5 months.  Thinkingrock has lots of nice features which I would like to incorporate but

1. Its java and it looks like crap in Ubuntu.  If you will notice in my first post I said gtk.
2. its too gtd focussed and it misses a lot of the 7 habits stuff
3. This project fills a gap in gnome software and I think it would be a good way for me to enhance my participation in Open Source.

---

### Post by pmasiar on 2007-11-02
> **brickbat said:**
> 
1. is there a guide or something to help me get started with building guis and programming them with python.

2. is there an ide that i can use that will let me do the programming in python, design the gui with gtk widgets, and work with the databases  (mysql lite i guess) in 1 spot.


Another GUI framework to consider is wxPython.

SQLite (if you ment that, I am not aware of MySQL Lite) is good choice for single-user SQL data repository, if you want to do it as desktop app.

But you will have hard time to start from scratch with little experience. I would recommend to at least finish PythonChallenge to learn Python modules, and participate in some (any) Python desktop project for a while. You will learn how to design that kind of app, what works, how to run a project, before embarking for a long journey to your own project. Do you realize that implementing it as hobby project in your free time will take you many months (not weeks)?

You may also look at javascript-based implementation of GTD, it may do most/all you want.

---

