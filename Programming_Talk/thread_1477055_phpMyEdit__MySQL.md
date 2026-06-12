---
title: "phpMyEdit / MySQL"
date: 2010-05-08
forum: Programming Talk
---

### Post by ugm6hr on 2010-05-08
I've set up a database with phpMyAdmin on MySQL to store clinical data.

I want a browser-based user frontend, and tried VFront [http://vfront.org/](http://vfront.org/)

This works reasonably well, but dosn't appear able to allow you to search for linked entries in other tables, or create new entries in linked tables with pre-filled data from fields in the existing table.

Hence, I was going to have a go with phpMyEdit [http://www.phpmyedit.org/](http://www.phpmyedit.org/) to try and create something that will achieve this.

Is this a realistic goal for someone who has no background in programming / php use?  Vfront took me about 8 hours to set up in a basic fashion that works - how long would I need to commit for this approach?

Apologies for the beginner question, but I don't want to invest time with no result unless this is something that might actually work...

---

### Post by Majorix on 2010-05-08
I don't get what you are trying to achieve here.

PHPMyAdmin IS a browser-based front-end for MySQL databases, and a pretty good one at that. Are you getting any problems with it? Maybe post the errors/logs here so someone can check?

---

### Post by ugm6hr on 2010-05-08
Apologies for notbeing clear.

phpMyAdmin works flawlessly.

However, I want an end-user frontend. i.e. one that is designed for data entry with "Forms" - like MS Access / OO.org Base etc - but web-based.  phpMyAdmin does allow data entry, but not in a simple way for non-expert users.

VFront does allow this.  But it does not appear to have the facility to do what I want (in an ideal world).

Perhaps a simple demo of phpMyEdit might help to illustrate the kind of interface I would like to create: [http://www.phpmyedit.org/demo/](http://www.phpmyedit.org/demo/)

But I want to be able to link between multiple tables - essentially create "subforms"

---

### Post by tturrisi on 2010-05-09
What you want is what programmers get paid to do.  You want a Web application.  This is simply HTML that queries your database using HTML forms and PHP.  It's not hard to do yourself if you know some basic PHP and HTML.  Have a look at these examples:
[http://www.itc.virginia.edu/desktop/web/database/inventory/display/home.html](http://www.itc.virginia.edu/desktop/web/database/inventory/display/home.html)
[http://www.php.happycodings.com/Database_Related/index.html](http://www.php.happycodings.com/Database_Related/index.html)

---

### Post by Line on 2011-10-13
Hi ugm6hr!
I am just working on the same thing. In the phpMyEdit documentation there is a chapter named "Advanced joining". It seems like a second table can be joined.

---

