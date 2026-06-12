---
title: "Improving GNOME Planner with Python and an object-oriented database?"
date: 2010-12-10
forum: Programming Talk
---

### Post by zhaotianwu on 2010-12-10
How can I integrate my own customer database into GNOME Planner, and remove some unnecessary features from it?

I'm trying to create a decision making support system, which will organically integrate some degree of graphical visualization with verbal data generated in my decision process. I want to improve on GNOME Planner with some programming and database manipulation. Currently I am considering Python with an object-oriented database called db4o. I am learning while programming so I don't mind whether it is difficult or easy for a beginner, as long as the route is correct. Is it correct? Or, as experienced developers, do you have some advice? I appreciate any advice, thank you very much!

Specifically, because Planner is written in C, should I learn C instead of Python? How about your advice on object-oriented database? Should I just store every customer's information into XML format?

---

### Post by ziekfiguur on 2010-12-11
Planner is written in C, but it supports plugins written in python. So, you should lookup some documentation about how to write plugins for Planner.
However, by writing plugins, you can only add functionality and not remove features that you think are unnecessary.

About the database, apparently Planner uses PostgreSQL itself, so i would advise on using that aswell.

---

### Post by zhaotianwu on 2010-12-13
> **ziekfiguur said:**
> Planner is written in C, but it supports plugins written in python. So, you should lookup some documentation about how to write plugins for Planner.
However, by writing plugins, you can only add functionality and not remove features that you think are unnecessary.

About the database, apparently Planner uses PostgreSQL itself, so i would advise on using that aswell.

 Thank you ziekfiguur!

---

