---
title: "programming books"
date: 2008-03-12
forum: Programming Talk
---

### Post by duuchung on 2008-03-12
Dear pals,
I am not a programmer. I have special interest in database and accounting systems. I have used more than enough downtime or waiting time to pursue my interest in I.T. All these years, I have bought the following books in my home library.

  Learning Perl  	Perl  	R Schwartz and others  	                         O'Reilly
  Advanced Perl Programming 	Perl 	S Cozens 	                         O'Reilly
  Perl Best Practices 	Perl 	D Conway 	                                      O'Reilly

  Python in a nutshell 	Python 	A Martelli 	                                   O'Reil ly
  Professional PHP4 	PHP 	various 	                                        wrox 
  Professional PHP5 	PHP 	various 	                                        wrox 	

  Teach yourself PHP 	PHP 	M Zandstra 	                                     Sams 	

  Teach yourself SQL 	SQL 	R Plew and other                                  Sams 	

  Core MYSQL The Serious Developer's Guide 	MYSQL 	L Atkinson    Pearson

  Learning MySQL 	MYSQL 	S Tabagbogbi and others 	           O'Reilly      
  Beginning PHP5 and MySQL E-Commerce from novice to fessionalPHP+MYSQl
                          	C Darie and other                                                Apress 

  AJAX & PHP Web2.0 	PHP+AJAX 	C Darie and other                    packt                               
  CSS Instant Results 	CSS 	R York 	                                                wrox 	

  Teach yourself TCl/Tk 	TCL 	V Sastry and other 	              Sams 	

  SQL: A beginner's guide 	SQL 	F Houlette 	                             Osborne
  HTML: A beginner's guide 	HTML 	W Willard 	                           Osborne
  Using TCP/IP 		 J Ray 	                                                               Que

I have read all these books. I still cannot write big programmes. I can follow the logic and codes of all these books. These books do not teach you how to chain up the small programmes to become big  programmes. What is the use of books? Could  anyone enlighten me?
regsards,                                                                                           duuchung

---

### Post by pmasiar on 2008-03-12
You missed one important book: "Learning Python". :-)

You cannot learn programming by reading many beginner's books in many different languages. The only way is to pick a language, stick with it, and write programs with it. By opinion of many, Python is best choice (see poll in sticky FAQ). Programming is not science, it is a skill - a craft. You learn by doing it.

There are many books about process of creating bigger programs, like "Code Complete", "Pragmatic Programmer", "Mythical man-month", "Head first object design" and hundreds of others (sticky FAQ links to discussion about them), but many things written there will not make much sense until you write and debug your own programs.

You need to pick a simple training task and solve it, and then another. Wiki in my sig links many tasks, but even better will be your own "itch".

---

### Post by bmeyer on 2008-03-12
Try picking up a book about Object Orientation, or maybe design patterns.

---

### Post by themusicwave on 2008-03-12
I have 2 questions for you:

1) What do you want to make?

  A game, some websites, utilities, what is it you are aiming to make.  You should choose a language based on this need/desire.

2) Have you ever tried?

It seems daunting, but sometimes you just have to get in there and do it.  I usually learn by doing, so I tend to think up projects to try to learn new things.  Try and make a big program, learn as you go, make mistakes and then fix them.

Also keep in mind some programs have dozens, hundreds or even thousands of people working on them.  You need to have realistic goals.  Don't go thinking you are going to code an amazing browser better than firefox in a week or anything like that.

Also, I cannot stress enough how much good planning is important in large applications.  Before you write any code flush out what exactly the program needs to do.  Then look into what modules you need to build to do it and how they interact.  Then build them, testing as you go.

The truth is that the code is just one part of a project.  Equally important are some specs, design documents and a testing strategy.  They aren't as fun to make as the code, but they will save you massive headaches. 

These things fall more into the Software Engineering domain than simply just programming.  Try picking up a Software Engineering book.

---

### Post by duuchung on 2008-03-13
Tks for you advice.

I thought of supporting or developing accounting systems as my part-time job. I know that big projects take man-years to complete. At least, I could develop small projects as add-ons. 

I followed the tutorials on PHP and MySQL from the websites of Dev Shed, OnLam.com and W3Schools. I spotted Three-Tier Development with PHP 5 from OnLam.com back in 2005 and developed several similar models for purchases, sales and inventory. However I lost my hard work in a disc crash. 

As I learned programmimg all on my own except attending short courses or learning Basic at college, I failed to learn how to write up links between the small programmes or package a project. I 'll read the books as recommended by pmasiar. I'll try to write some small programmes.

---

### Post by elithrar on 2008-03-13
> **pmasiar said:**
> You missed one important book: "Learning Python".


Seconded! I think the OP has spread his knowledge/focus too thinly and without dedicating himself to a particular language or two, he's not been able to consolidate knowledge. 

If you want to develop web-applications, look towards Python (+ Django/Turbogears/web.py), PHP or .NET with a mySQL/postgreSQL backend. Frameworks will go a long way into abstracting your DB queries and letting you focus on the Python/PHP/.NET side of things.

Python & Django are my preference, but that doesn't mean they have to be yours. I'd highly recommend investing your time into a language you **enjoy** writing and that is relevant to current (and future) demands.

---

### Post by pmasiar on 2008-03-13
For part-time jobs on the side, Python seems like best choice (C is too demanding and too slow to develop in). SQLite (and pySQLite) is very decent SQL database which is just library (single user, no server running).

PHP might be good choice if all you do are web apps, but with TurboGears (and Python) you can make them as easy, and in much more flexible and maintainable way. SQLAlchemy is excellent object-relational mapper, comes with TG v2.

---

### Post by Can+~ on 2008-03-13
> **pmasiar said:**
> For part-time jobs on the side, Python seems like best choice (C is too demanding and too slow to develop in). SQLite (and pySQLite) is very decent SQL database which is just library (single user, no server running).

I second that, the python sqlite3 is an awesome way to both practice SQL commands in a safe enviroment if you're starting, or to develop small storages, like Amarok which uses sqlite to store the playlist.

---

### Post by LaRoza on 2008-03-13
> **Can+~ said:**
> I second that, the python sqlite3 is an awesome way to both practice SQL commands in a safe enviroment if you're starting, or to develop small storages, like Amarok which uses sqlite to store the playlist.

I believe that Amarok can also use MySQL (which makes it faster, I hear)

---

