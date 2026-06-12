---
title: "MySQL Design Tool"
date: 2008-07-11
forum: Programming Talk
---

### Post by wieman01 on 2008-07-11
Is there any free (open source) design tool available for MySQL? I want to create a database design using a graphical tool that allows me to export SQL code... Anything you would know of? For Linux please.

---

### Post by mike_g on 2008-07-11
I use phpMyAdmin for creating MySQL databases but AFAIK it does not export SQL code tho. 

If theres better tools around I would be interested to hear about them.

---

### Post by wieman01 on 2008-07-11
One I found is Navicat, but it is free for trial on (30 days) and comes with Wine, so it's basically a Windows program. It's pretty nice, but only for 30 days I guess.

---

### Post by cpetercarter on 2008-07-11
phpMyAdmin allows you to export your database in a number of different formats, including SQL. I back up my website database (when I remember!) in this format. phpMyAdmin is available in the repositories (though you can equally easily download it direct from the website and install it where you wish on your computer.)

---

### Post by wieman01 on 2008-07-11
> **cpetercarter said:**
> phpMyAdmin allows you to export your database in a number of different formats, including SQL. I back up my website database (when I remember!) in this format. phpMyAdmin is available in the repositories (though you can equally easily download it direct from the website and install it where you wish on your computer.)
But you still have to generate the SQL code by hand when you create your database design, right? I don't want that because it consumes to much time and is prone to error.

---

### Post by bruce89 on 2008-07-11
> **wieman01 said:**
> But you still have to generate the SQL code by hand when you create your database design, right? I don't want that because it consumes to much time and is prone to error.

No, everything is GUI.

---

### Post by cpetercarter on 2008-07-11
No - you can create new databases, new tables, new columns, amend or drop any of these, edit data etc all from the GUI. You don't much if any SQL to set up the database.

---

### Post by wieman01 on 2008-07-11
Mmm... That sounds tempting then. Thanks, cpetercarter & bruce89. I will give it a go and report back.

---

### Post by bruce89 on 2008-07-11
Only snag with phpMyAdmin is that it needs the whole LAMP stack as it's Web-based.

---

### Post by essexboyracer on 2008-07-11
something like this...

[http://www.fabforce.net/dbdesigner4/screenshots.php](http://www.fabforce.net/dbdesigner4/screenshots.php)

On the flip side, if you already have something in another DB language, try [http://kettle.pentaho.org/](http://kettle.pentaho.org/) to convert the data to mysql

---

### Post by tinny on 2008-07-11
Ive used [DBDesigner4]("http://www.fabforce.net/dbdesigner4/") with great success in the past.

Also there is [MySQL Workbench]("http://dev.mysql.com/downloads/workbench/5.0.html"). (A fork of DBDesigner4) I briefly tried the alpha of MySQL Workbench and it looked nice. Unfortunately its currently only available for Windows

---

### Post by wieman01 on 2008-07-12
> **essexboyracer said:**
> something like this...

[http://www.fabforce.net/dbdesigner4/screenshots.php](http://www.fabforce.net/dbdesigner4/screenshots.php)

On the flip side, if you already have something in another DB language, try [http://kettle.pentaho.org/](http://kettle.pentaho.org/) to convert the data to mysql
Yes, exactly. But DBDesigner is Windows only. I don't use Windows so it's not an option at the moment.

---

### Post by tinny on 2008-07-12
> **wieman01 said:**
> Yes, exactly. But DBDesigner is Windows only. I don't use Windows so it's not an option at the moment.

You can install DBDesigner on Linux as well. (ive used it on Ubuntu and it was good)

[http://www.fabforce.net/dbdesigner4/downloads.php]("http://www.fabforce.net/dbdesigner4/downloads.php")

MySQL Workbench is only available for Windows.

---

### Post by wieman01 on 2008-07-13
Thank you, Tinny. That was a great tip. I could get it to run on Ubuntu following this tutorial:

[http://knightlust.blogspot.com/search?q=dbdesigner]("http://knightlust.blogspot.com/search?q=dbdesigner")

I'll check out DBDesigner and let you guys know.

_**EDIT:**_
Works great. You might also need to do this:

> cd /usr/lib
> sudo ln -s libsqlmda.so.4.20 libsqlmy.so

---

### Post by wieman01 on 2008-07-13
DBDesigner4 rocks... it's exactly what I was looking for. After some tweaking and following the guides above it works great. Thank you!

---

### Post by Tony Flury on 2008-07-13
i just install phpMyAdmin - and i can't get it to work - in fact i can't even find it 

I have apache installed yet the URL 

```

http://localhost/phpMyAdmin/

```

returns a 404 error - 

so i have no idea where it installed itself - or how to acccess it - as all the tutorials point to a URL like above.

EDIT : I cannot remember what i did now - but it works now.

---

