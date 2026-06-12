---
title: "PHP help"
date: 2008-12-22
forum: Programming Talk
---

### Post by davidcaiazzo on 2008-12-22
[I want to make something like this.]("http://ati.amd.com/support/driver.html")

I know how to connect to a mysql database, I know how to query it. For the love of god though I have no idea how to make a dynamic drop down box, or more preferably a dynamic table in php. I am still learning. Can anyone give me a shove in the right direction please?

---

### Post by ufis on 2008-12-22
See the examples on [http://www.php.net/manual/en/function.mysql-fetch-array.php](http://www.php.net/manual/en/function.mysql-fetch-array.php)

Bookmark [http://www.php.net/](http://www.php.net/) Do it now. (<-- This is the shove in the right direction)

---

### Post by Reiger on 2008-12-22
Yep. Another shove could be [http://eriksdiary.blogspot.com/2007/07/xml-output-from-mysql.html](http://eriksdiary.blogspot.com/2007/07/xml-output-from-mysql.html)

It's really easy to turn basic XML into all kinds of XHTML using simple XSLT. A drop down box can be as easy as (scroll this page down to the section on drop down boxes) : [http://csshtmltutorial.com/csshtmltutorial-htmlformcodetutorial.php](http://csshtmltutorial.com/csshtmltutorial-htmlformcodetutorial.php).

---

### Post by davidcaiazzo on 2008-12-22
Thanks already have that book marked. And thank you both for the responses. =D

---

### Post by slavik on 2008-12-23
there are two ways to do this.

1. preload all values and spit the correct ones out which increases page size.
2. use AJAX to dynamically request the new information. I have done this and it isn't very difficult.

---

