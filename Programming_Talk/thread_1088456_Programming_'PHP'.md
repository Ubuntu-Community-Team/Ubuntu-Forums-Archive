---
title: "Programming 'PHP'"
date: 2009-03-06
forum: Programming Talk
---

### Post by old_dope on 2009-03-06
I have always wanted to learn a programming language and being able to use HTML. XHTML and CSS for building my web page(s) and getting them validated i thought it time to move on and learn a programming language 'PHP'. So is there anyone out there who would be willing to help me get started? Getting and installing the PHP engine? Thanks

---

### Post by dzark on 2009-03-06
sooooo much php resources on the web its not funny....

w3schools.com is very comprehensive. great to reference
try track down a copy of a php book at the local used book store 
[http://devzone.zend.com/node/view/id/627](http://devzone.zend.com/node/view/id/627) 101 lesson from the makes of php

to install just install the package ```
libapache2-mod-php5
``` 
(i find that one makes sure i get all dependencies with it)

---

### Post by old_dope on 2009-03-06
Have been Googling for PHP and have just come across Xampp for Linux at:
[http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)
What do you think?

By the way...thanks for the reply!

---

### Post by dzark on 2009-03-06
i use portable xampp for windows on my usb stick, nice and easy to carry around, but i find it easier to have the ubuntu-package 'apache2' and all needed extras installed, updates automatically no hassles.. sooner or later you'll probably install a program that will need it anyway - phpMyAdmin or zoneminder or such..

---

### Post by old_dope on 2009-03-06
Thanks dzark

---

### Post by bapoumba on 2009-03-06
Moved to PT.

---

### Post by jackmcslay on 2009-03-06
this command should get you all you need to start developing on PHP
```
sudo apt-get install apache2 php5 php5-mysql php5-gd phpmyadmin mysql-server
```

---

### Post by old_dope on 2009-03-06
Thanks for all the help and advice guys but i just want to learn PHP on my computer or in other words make my computer the server. I think that's right.

---

### Post by stevescripts on 2009-03-06
> **old_dope said:**
> Thanks for all the help and advice guys but i just want to learn PHP on my computer or in other words make my computer the server. I think that's right.

XAMPP should be just fine to start with then, and IMHO a bit easier to setup than Apache....

Steve

---

### Post by drubin on 2009-03-06
> **stevescripts said:**
> XAMPP should be just fine to start with then, and IMHO a bit easier to setup than Apache....

Steve

Xampp is a great packaged version for windows. But absolutly shocking for linux since Ubuntu and most other *nix's have a package manager any way so they will handle the install dependances and every thing.

I would very highly suggest not using xampp on linux, but rather as a quick fix for is you have to use windows :)

---

### Post by stevescripts on 2009-03-06
This made it really easy for me to get XAMPP going on Ubuntu:

[http://ubuntuforums.org/showthread.php?t=223410](http://ubuntuforums.org/showthread.php?t=223410)

Steve
(drubin - not nit-picking at you here, I have great respect for your contributions to this forum - this just happened to work great for me...)

---

### Post by drubin on 2009-03-06
> **stevescripts said:**
> This made it really easy for me to get XAMPP going on Ubuntu:

[http://ubuntuforums.org/showthread.php?t=223410](http://ubuntuforums.org/showthread.php?t=223410)

Steve
(drubin - not nit-picking at you here, I have great respect for your contributions to this forum - this just happened to work great for me...)

@stevescripts Each to his own :) Thanks never knew people even knew who I was around here :)

But with out starting a whole long debate (I really don't think that is needed) but could you please from your point of view explain how that guide is easier then copy/pasting the 4/5 commands listed [here]("https://help.ubuntu.com/community/ApacheMySQLPHP") or was it just a case of I tried out xampp first and it work?

---

### Post by stevescripts on 2009-03-06
drubin - hmm ... that link didnt work for me ...

FWIW, regarding XAMPP, it was more of a "I tried it out, and it worked for me" ;)

Over the years, I have configured Apache only a few times, and I always found it to be a PITA (for me...)
(especially on 'doze)

Steve

---

### Post by drubin on 2009-03-06
Fixed the link. it was [http://https://](http://https://) that clearly not valid 

Point taken. I am not going to carry on since it would just turn into a long debate that never ends. Thanks for your point of view.

---

### Post by CptPicard on 2009-03-06
> **old_dope said:**
> i thought it time to move on and learn a programming language 'PHP'.

Please don't.

PHP needs to die.

Please learn a real programming language (such as Python perhaps) and the associated MVC pattern. You will learn to program for real and in addition learn to do web apps properly.

---

### Post by Reiger on 2009-03-06
> **CptPicard said:**
> Please don't.

PHP needs to die.

Please learn a real programming language (such as Python perhaps) and the associated MVC pattern. You will learn to program for real and in addition learn to do web apps properly.

Nah, PHP is a very useful language for what it does best: preprocessing/generating documents. You may consider it ugly, but it is far easier, cleaner, and I-would-say-better to code the glue that keeps your webpages together in PHP than it is in Python. Not in the least precisely because Python enforces a design pattern [here] (or rather the interface between Apache and Python interpreter does). The argument is comparable to why Java is a PITA to code small apps in: the design patterns enforced may be a good thing in 'big' apps, they only add dead weight in small scale applications.

---

### Post by hessiess on 2009-03-07
PHP is good for smaller applications and persoonal websites, as a lot of the cheep hoasting avalable only supports PHP. Also  I find Python hard to read, and a PITA to code in due to the lack of '{}' and becouse it is verry fussy about indenting.

---

### Post by stevescripts on 2009-03-07
While I tend to (mostly) agree with Cpt Picard, it remains an (unfortunate) fact of life, that there are times and places where PHP is the only tool available.  Such a situation a few years back lead me into my one and only foray into PHP.  It's there, and it does work - but it is incumbent on the programmer to never, NEVER, overlook security issues. (Always important, but to me, it seems even more important when using PHP).

Just another $.02 from an old hacker ;)

Steve

---

### Post by drubin on 2009-03-07
> **stevescripts said:**
> While I tend to (mostly) agree with Cpt Picard, it remains an (unfortunate) fact of life, that there are times and places where PHP is the only tool available.  Such a situation a few years back lead me into my one and only foray into PHP.  It's there, and it does work - but it is incumbent on the programmer to never, NEVER, overlook security issues. (Always important, but to me, it seems even more important when using PHP).
+1

Programmers need to take every thing into account to decide the best tool for the job.

Things that should be included (In no particular order)
1) Tools that are avalible.
2) Programmers skill set
3) Time frame.
4) Environment

A good programmer works with what they have. If the constraints are that the costs need to be kept down finding hosting for Java/Python can be combersome.

While I agree there are tones and tones and tones of bad PHP programmers and programming in PHP does lead to bad code since it's in its design. Not all programmers write bad php code!!

Something to take note of as well. For small websites  that aren't intended of running NASA php is very well suited because of it's native integration with web servers and back end DB.

All these points taken into account some times php is the best and only option.

---

