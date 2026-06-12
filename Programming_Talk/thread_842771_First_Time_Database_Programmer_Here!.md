---
title: "First Time Database Programmer Here!"
date: 2008-06-27
forum: Programming Talk
---

### Post by tablebreaker on 2008-06-27
Hey everyone! I just got involved in a project, and I don't know where else to go for help right now. I've got no experience with MySQL, but I do have web design experience. What it's going to be is a setup where bands can enter in their info (like what kind of music they play, a checkbox if they can play acoustic, etc) and then the ability for people to go to the site and find bands that match based on what they're looking for. 

I'm thinking about using Joomla, as I like the way it looks, and from what I understand, it uses MySQL as well, so maybe it will be easier? 

Any help or ebook suggestions or anything would be great!

thanks a lot!

---

### Post by LoneWolfJack on 2008-06-27
As far as I know, Joomla is written in PHP, so you will have to learn PHP and then program a new module that will provide the desired functionality.

There are like a zillion books for learning PHP out there, just pick one. O'Reilley are usually quite good.

---

### Post by doorman on 2008-06-27
For what you described, you'll need to know only the basic MySQL syntax ( how to insert, edit or delete a row in a database ) - the [MySQL HQ]("http://www.mysql.com") has a lot of documentation, but it will probably be easier by reading a tutorial ( google is your friend for that ).
For creating the database / tables I suggest you use [phpMyAdmin]("http://www.phpmyadmin.net/") - a great visual web-based MySQL manager.
As LoneWolfJack said, if you use Joomla, you'll need some php knowledge too. There are a lot of PHP / MySQL books out there that usually walk you through all the important phases of building a database-enabled web site

good luck!

---

### Post by pmasiar on 2008-06-27
If you use decent ORM (object-relational mapper), you may get by without knowing any SQL at all. I personally know a guy who cannot write INSERT statement, but hacked together Python/Turbogears website which was for a while on first page of google search in their category. Django (another framework for Python) generates all DB table maintenance screens   automagically.

---

### Post by tablebreaker on 2008-06-28
> **pmasiar said:**
> If you use decent ORM (object-relational mapper), you may get by without knowing any SQL at all. I personally know a guy who cannot write INSERT statement, but hacked together Python/Turbogears website which was for a while on first page of google search in their category. Django (another framework for Python) generates all DB table maintenance screens   automagically.

Thanks for the replies, guys! I've emailed the project director to find out if there will be any "fill in the blank" sections. I like the idea of "automagically" doing something, so it's possible I'll pm you guys when I get more info! :)

---

