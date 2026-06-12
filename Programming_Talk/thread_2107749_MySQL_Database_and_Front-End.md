---
title: "MySQL Database and Front-End"
date: 2013-01-22
forum: Programming Talk
---

### Post by muddpup64 on 2013-01-22
I was recently asked by one of my administrators to create an online accessible database to which they, knowing nothing about anything, can easily access and understand enough to update themselves. I have made a functioning MySQL database that I would like to give two (windows friendly) front-ends; one for data entry, the other for online queries.
  
 I have never done anything like this before and am not sure what to do, any suggestions?

---

### Post by tgalati4 on 2013-01-22
Depending on what kind of data that you are storing, I would set up a content management system such as [http://drupal.org](http://drupal.org).  Install tasksel then run it and select the LAMP server, then follow the tutorial to install drupal.  Instant mysql database with accounts to add data, available through any browser on any device.

---

### Post by Some Penguin on 2013-01-22
[https://www.djangoproject.com/]("https://www.djangoproject.com/") might be quite useful for your purposes.

---

### Post by trent.josephsen on 2013-01-22
It is also not difficult to write this kind of thing yourself, if you know some Perl or Python. For Perl you'd probably use the Perl DBI to access the database and one of the many CGI modules to create the actual pages the user sees. I've done it before, many times over. I'm not 100% sure what the Python analogues would be. (Of course, you can technically do CGI in any language you want.)

Depending on your needs, a homegrown solution may be simpler to implement and more future-proof than an entire CMS. CMSes are designed for more general, more flexible (and more complex) applications than just a few tables with a data entry webapp. On the other hand, you could also code yourself into a corner, or find yourself reimplementing an entire CMS from scratch, if you roll your own; that's a design decision you have to make, but I wanted to make sure you have some idea what your options are.

---

### Post by dazman19 on 2013-01-27
Python is pretty good to use if you want to run CGI's. 

PHP is very easy to use as well with mysql you can find loads of resources on the internet. Run it on LAMP and the windows machines can connect to it.

If you want to use windows forms, and know graphical programming you could try your luck at Java. The benefits of java is it is portable, so if you do have other unix or mac users later you dont need to re-write all the code.

---

