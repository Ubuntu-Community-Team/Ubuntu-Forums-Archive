---
title: "Learning Apache+PHP need help installing!"
date: 2007-04-21
forum: Programming Talk
---

### Post by jingo811 on 2007-04-21
I started taking a webdesigning night course.  Thus far we learned how to install Apache HTTP Server v.2.2.4 and PHP v.5 for Windows XP.  We started scripting some basic stuff for our html sites on the schools PCs.

Now I want to have Apache and PHP on my Dapper 6.06 Desktop so that I can practice at home.  The problem is I don't know how to install stuff properly for Ubuntu.
I managed to install an older Apache 1.3 something through Synaptic though and are currently configurating the httpd.conf file.  I think I'm OK so far.

**Question 1.) How do I restart Apache server?**
I just need to restart the Apache server now but how, I can't see any icon like in Windows XP?
I don't even know what folder Apache was installed on.
/etc/apache/httpd.conf file along with some other *.conf files was in this folder.  But it didn't look like any program file was installed in here.

Looking in the httpd.conf file:
ServerRoot  "/usr/local/apache"
I couldn't even browse to any such folder with Nautilus.

So how can I access the program Apache and its icon?

---

### Post by barmazal on 2007-04-21
seriously i would advice you to try out XAMPP, application which installs PHP mySQL Apache and few other things you may unselect at once. It works on Linux and Windows just read manual on their website

[http://www.apachefriends.org/en/xampp.html](http://www.apachefriends.org/en/xampp.html)    it's quite nice to know how to install all of those seperately but still XAMPP saves you lots of time

---

### Post by Mirrorball on 2007-04-21
There is no Apache icon. Look for Services in the menu and activate it (or desactivate it if you want to). But it's faster if you open a terminal and type:
```
sudo /etc/init.d/apache restart
```
Or apache2 for Apache 2. This is my PHP guide for Ubuntu:
[http://ubuntuforums.org/showpost.php?p=2327843&postcount=25](http://ubuntuforums.org/showpost.php?p=2327843&postcount=25)

---

### Post by jingo811 on 2007-04-21
Nice tut!  I'll dive into it if I get accepted to the Linux op. education.
But XAMPP is even nicer it saved me hours of endless reading.  Being lazy is my motto so I luv you barmazal.
XAMPP download & installation was even quicker than downloading & installing Apache and PHP for Windows :-)
I'm surprised for once there's something for Linux that's easier to download and setup than Windows.

---

### Post by jingo811 on 2007-04-22
**Question 2.) XAMPP related - DocumentRoot **
XAMPP install was great and all but support is too slow over there, maybe I've been spoiled by hanging too much in Ubuntuforums.  So I'm trying my luck in here instead with the problems.

Are you supposed to let XAMPP's index.html be untouched?
I tried changing the DocRoot somewhere on my Desktop but then [httP://localhost](httP://localhost) would give me errors and the http: adress bar would change to an adress pointing to some XAMPP catalog.

How do I add my own Website files to localhost?  Do I just copy n paste it into the
/opt/lampp/htdocs
catalog?  Which didn't work in Nautilus.  Is there a certain process to it or should I just use Terminal and force my way into XAMPP?

---

