---
title: "I need a non-web language that utilizes a database"
date: 2008-01-12
forum: Programming Talk
---

### Post by pofigster on 2008-01-12
Howdy!  I've had some programming experience (mostly in PHP, some Java) and I've got a program I want to write but I don't know what language would let me do what I want to do.

My fiancee and I do a lot of cooking and we use a lot of recipes, I wanted to write a program that would let us enter recipes and then search for them by various criteria.

I could use PHP and MySQL to do this, but I'd rather have it be a program that ran in the OS instead so I could distribute it to our families who also do a lot of cooking.

So, what I'm looking for is a language that can use some kind of database...

Any ideas or pointers would be very much appreciated!  Thanks!

---

### Post by pmasiar on 2008-01-12
Python and SQLite is your best bet IMHO.

SQLite is fully SQL but it is just library accessing file, no server running, no overhead. Included in core Python libraries since 2.5.

To make your life simpler, use smart Object-relational mapper, like SQLAlchemy.

---

### Post by CptPicard on 2008-01-12
Why not a web app? If you want to be sharing recipes with other people with cooking as a hobby, wouldn't it be cool if it were website instead of a standalone desktop app? :)

---

### Post by zipperback on 2008-01-12
Perl would be a good option for you and if want to build a gui for the system you could use gtk-perl. 

[http://en.wikipedia.org/wiki/Gtk2-perl](http://en.wikipedia.org/wiki/Gtk2-perl)

I would also go with something l ike mysql because it is fairly easy to work with.

- zipperback
:popcorn:

---

### Post by ghostdog74 on 2008-01-12
> **pofigster said:**
> 
I could use PHP and MySQL to do this, but I'd rather have it be a program that ran in the OS instead so I could distribute it to our families who also do a lot of cooking.


PHP can be scripted to run as standalone app. you can also develop gui apps in PHP. As for database, it also supports sqlite if you want to use it

---

### Post by YourSurrogateGod on 2008-01-12
> **pofigster said:**
> Howdy!  I've had some programming experience (mostly in PHP, some Java) and I've got a program I want to write but I don't know what language would let me do what I want to do.

My fiancee and I do a lot of cooking and we use a lot of recipes, I wanted to write a program that would let us enter recipes and then search for them by various criteria.

I could use PHP and MySQL to do this, but I'd rather have it be a program that ran in the OS instead so I could distribute it to our families who also do a lot of cooking.

So, what I'm looking for is a language that can use some kind of database...

Any ideas or pointers would be very much appreciated!  Thanks!

Then just make a stand-alone Java app :) . Given you have some experience in Java, I figured that it would play well on your strength.

---

### Post by LaRoza on 2008-01-13
All options stated here are good.

I see two workable solutions:

* Make a web app, you can use anything for this
* Python, Perl, PHP, with SQLite

Python, Perl and PHP can be used for GUI desktop applications, and all can use SQLite. My wiki has references for all those languages and the GUI toolkits for them.

(I personally would use Python and SQLite, but that is just me)

---

### Post by pofigster on 2008-01-13
I would write a web app, but I'm not sure about the "Fair Use" of a recipe from say a magazine or some other source that we try.  I figure, if it's a stand-alone app then there's fewer legal issues with it...

Thanks to everybody for the quick answers, I think I'll look into Python with SQlite - I've been wanting to learn Python anyway...

---

### Post by Balazs_noob on 2008-01-13
> **YourSurrogateGod said:**
> Then just make a stand-alone Java app :) . Given you have some experience in Java, I figured that it would play well on your strength.
+1
also the jdk6 comes with a built-in database (Derby)
you can package the database in a runnable jar file
so it is very easy to use and no worry about install
since in is just 1 jar file :D
( if you chose  Java it would be simpler to use only
a serialized text file )

or

find a free web host and make it in php and whatever
database it supports, this way everybody can access it
and it is a lot easier to update the database since
you only have to go it on the server....

good luck

---

### Post by xlinuks on 2008-01-13
> **pofigster said:**
> Howdy!  I've had some programming experience (mostly in PHP, some Java) and I've got a program I want to write but I don't know what language would let me do what I want to do.

My fiancee and I do a lot of cooking and we use a lot of recipes, I wanted to write a program that would let us enter recipes and then search for them by various criteria.

I could use PHP and MySQL to do this, but I'd rather have it be a program that ran in the OS instead so I could distribute it to our families who also do a lot of cooking.

So, what I'm looking for is a language that can use some kind of database...

Any ideas or pointers would be very much appreciated!  Thanks!

1) The only language that would let _me_ do what I want to do is C (nor Java either Python can do as fast and well as C, that's why I really wanna learn C)
2) You don't need a database. You are not going to store hundreds of thousands of recipes I guess, thus storing every recipe in a (text) file would be just good. Why? Because your friends won't need to install and configure a database! Besides you can just redistribute your folder with files, this is very handy and simple. There's practically no difference in speed.
How to search for a recipe? All your recipe-text-files should be stored into corresponding folders according to the most important criteria recipes might have, in folders with names like "sweet", "salty", "drinks" and alike. The name of the text file of the recipe might contain additional data, and finally the contents should describe the recipe itself.
You should consider:
1) nowadays computers can read very fast from the HDD.
2) programs of true quality should require from little to none setup, not to mention that databases are required only for apps that will use > 10000 items.
3) IMO the most important - your users will be happy to know that they can use your program without having to install (and configure) a database. I personally use a database for Desktop apps only in about 10% of my cases, and anyone is happy.

---

### Post by popch on 2008-01-13
As others have commented, you could implement your solution as a web application (provided one does not exist already).

What has not been mentioned so far: you can install the web server and database server on your PC and use the broswer to access your recipes just as they were on the web. 

Apache, mySQL and PHP are not very difficult to install both in Linux and Windows. If you want your solution to be really portable, you could even consider packaging your application in a virtual machine.

---

### Post by Rhubarb on 2008-01-13
Have you had a look at Gourmet Recipe Manager?
[http://grecipe-manager.sourceforge.net/](http://grecipe-manager.sourceforge.net/)
It's written in phython, and should be able to do everything you want (and if it doesn't, it'll give you a good incentive to learn python so you can tinker with it).

---

### Post by LaRoza on 2008-01-13
> **xlinuks said:**
> 1) The only language that would let _me_ do what I want to do is C (nor Java either Python can do as fast and well as C, that's why I really wanna learn C)
2) You don't need a database. You are not going to store hundreds of thousands of recipes I guess, thus storing every recipe in a (text) file would be just good. Why? Because your friends won't need to install and configure a database! Besides you can just redistribute your folder with files, this is very handy and simple. There's practically no difference in speed.
How to search for a recipe? All your recipe-text-files should be stored into corresponding folders according to the most important criteria recipes might have, in folders with names like "sweet", "salty", "drinks" and alike. The name of the text file of the recipe might contain additional data, and finally the contents should describe the recipe itself.
2) programs of true quality should require from little to none setup, not to mention that databases are required only for apps that will use > 10000 items.
3) IMO the most important - your users will be happy to know that they can use your program without having to install (and configure) a database. I personally use a database for Desktop apps only in about 10% of my cases, and anyone is happy.
1. That has nothing to do with the goals here...

2.SQLite doesn't require installations, and comes with Python.

3. Installing the ActivePython interpreter, and possible the GUI toolkit (single click installers for Windows) and making an installer for the script: [http://www.jrsoftware.org/isinfo.php](http://www.jrsoftware.org/isinfo.php) will make it very easy, even if the program is complicated.

4. SQLite doesn't need to be configured.

Programs of quality shouldn't be measured by how they are setup. If you do, Gentoo is the worst distro in the world, and Windows is the best. The quality of the software when it is running is what is important. Writing a little read me file isn't difficult.

---

### Post by Wybiral on 2008-01-13
> **xlinuks said:**
> 1) The only language that would let _me_ do what I want to do is C (nor Java either Python can do as fast and well as C, that's why I really wanna learn C)
2) You don't need a database. You are not going to store hundreds of thousands of recipes I guess, thus storing every recipe in a (text) file would be just good. Why? Because your friends won't need to install and configure a database! Besides you can just redistribute your folder with files, this is very handy and simple. There's practically no difference in speed.
How to search for a recipe? All your recipe-text-files should be stored into corresponding folders according to the most important criteria recipes might have, in folders with names like "sweet", "salty", "drinks" and alike. The name of the text file of the recipe might contain additional data, and finally the contents should describe the recipe itself.
You should consider:
1) nowadays computers can read very fast from the HDD.
2) programs of true quality should require from little to none setup, not to mention that databases are required only for apps that will use > 10000 items.
3) IMO the most important - your users will be happy to know that they can use your program without having to install (and configure) a database. I personally use a database for Desktop apps only in about 10% of my cases, and anyone is happy.

a-1. The database modules for Python are almost guaranteed to be written in C anyway (thus would be just as fast as using C itself for most cases)

a-2. That doesn't seem practical at all. What if something is sweet, salty, and is a snack (kettle corn, for instance)? Do you put it in each folder? Nope, you probably design a system of indexing them somehow. By the time you design a system that allows for easy searching / categorizing, you will probably have already designed a simple database. Don't reinvent the wheel!

b-1. True, but this doesn't scale well and would obviously be a problem for any multithreaded app.

b-2. Prove it!

b-3. As LaRoza said, SQLite doesn't require configuration.

---

### Post by Unterseeboot_234 on 2008-01-13
If you know SQL-lite you can have a DB application up and running in 20 minutes, with a GUI, using the NetBeans IDE 6.0. Which is the Apache Derby database. From there use GlassFish if you want it as a networked number of workstations.

Here a video:

**[Video demo NetBeans DB]("http://www.netbeans.tv/screencasts/CRUD-using-jMaki-and-JPA-243/")**

Here is an online tutorial for the DB connectivity:

**[NetBeans Tutorial  IDE 6.0 DB connectivity**]("http://www.netbeans.org/kb/60/java/gui-db.html")

---

### Post by xlinuks on 2008-01-13
> **Wybiral said:**
> a-1. The database modules for Python are almost guaranteed to be written in C anyway (thus would be just as fast as using C itself for most cases)

a-2. That doesn't seem practical at all. What if something is sweet, salty, and is a snack (kettle corn, for instance)? Do you put it in each folder? Nope, you probably design a system of indexing them somehow. By the time you design a system that allows for easy searching / categorizing, you will probably have already designed a simple database. Don't reinvent the wheel!

b-1. True, but this doesn't scale well and would obviously be a problem for any multithreaded app.

b-2. Prove it!

b-3. As LaRoza said, SQLite doesn't require configuration.

:))

---

### Post by pmasiar on 2008-01-13
> **xlinuks said:**
> 1) The only language that would let _me_ do what I want to do is C (nor Java either Python can do as fast and well as C, that's why I really wanna learn C)

so you don't know C, but you are so sure it is best for OP? Such app can be developed 10 times faster in Python than in C, from my experience in **both** languages. Additionally, most of the runtime would be spent accessing data, to I bet anything that Python+SQLite would beat your custom database wannabe engine in C.

Remember, premature optimization is root of all evil. :-)

> 2) You don't need a database. ...Besides you can just redistribute your folder with files, this is very handy and simple. There's practically no difference in speed.


I agree that full database server could be overkill - this is why I suggested SQLite. But unlike your proposal, program using SQLite can be later converted to using real DB server by just changing driver - SQLite is a library implementing SQL to access data in plain files (without a DB server).

One important difference in speed is **speed of development** - and in this, Python beats C every time, no questions.

---

