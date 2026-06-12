---
title: "MySQL++ Successes?"
date: 2006-04-02
forum: Programming Talk
---

### Post by Lightmywifire on 2006-04-02
Hey there. I've been trying to Google through every site known to man (including this one) on help with MySQL++ programming. All I can find is information on how old the Ubuntu despository version is (everything says around 4 years). Has anyone successfully programmed MySQL queries into C++? I've found a good number of wrappers that should work, but never seem to.

My issues include anything from linking problems to simply not being able to find a certain .h. At this point, I've got nothing. If anyone has any pointers on how to make this thing work, I would gladly appreciate it.

---

### Post by Azrael on 2006-04-02
This may not be helpful to you, but I think MySQL sucks. I recommend using PostgreSQL over MySQL. Or SQLite if you want do something small/simple.

---

### Post by Lightmywifire on 2006-04-02
I'm open to any ideas. I'm just trying to interface an SQL server with C++. Do you have a guide to the SQLite and C++?

---

### Post by Lightmywifire on 2006-04-02
Aliright, I'm hoping that I can do this with SQLite, but I have no idea how to get   the API though.

---

### Post by Azrael on 2006-04-02
Does this help: [http://www.sqlite.org/capi3.html]("http://www.sqlite.org/capi3.html") ?
I'm afraid I can't give any more detailed info than what's to be found on the sqlite website, because I have never used sqlite from c or c++ (yet).

---

### Post by Lightmywifire on 2006-04-02
Well, i found out that to install the dev you gotta:

"apt-get install libsqlite3-dev"

and you get the package. still having problems tho. this should be pretty trivial, but it seems as though i am having more problems than i should be. I'm finding wrappers online, but i can't compile a single thing correctly.

---

### Post by Lightmywifire on 2006-04-02
Holy hell!!! I got a compilation!!!

[http://freshmeat.net/articles/view/1428/](http://freshmeat.net/articles/view/1428/)

There's where to look for some example code.

---

