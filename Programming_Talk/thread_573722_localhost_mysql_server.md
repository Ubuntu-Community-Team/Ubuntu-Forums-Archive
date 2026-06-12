---
title: "localhost mysql server"
date: 2007-10-11
forum: Programming Talk
---

### Post by rekahsoft on 2007-10-11
hi all, i need to set up a mysql server so i can start testing my J2EE app..i have very little experiance with J2EE, mysql and web services so it would be great if someone could give me a little help :P..thanks :D

---

### Post by LaRoza on 2007-10-12
To install lampp in Feisty, use "sudo tasksel" and select "lampp". If you don't need the whole setup, install "mysql-server".

---

### Post by thomasaaron on 2007-10-12
You can also use phpMyAdmin:

sudo apt-get install phpmyadmin

This will load a mysql management tool right into your lamp server. You can then open a browser, type "localhost" and then select "phpmyadmin" for all of the SQL management junk you'll ever need.

---

### Post by aks44 on 2007-10-12
I guess what the OP wants is something like Apache+Tomcat+Mysql.

However to be honest, I don't have a clue how to integrate them. Apache & Mysql both are very easy to install from the repos, but when it comes to Tomcat I can't help much since I avoid anything Java-related like the pest...

Anyway maybe mentionning the "Tomcat" name can give a hint to the OP...

---

### Post by Xenaco on 2007-10-12
The process for setting up LAMPP on Ubuntu is really a bit more complicated and detailed than has been detailed here, especially for a new user.

I suggest visiting [[COLOR="Blue"]http://www.howtoforge.com[/COLOR]]("http://www.howtoforge.com")  
for instructions on setting up most applications.  It is a step by step how to site which allows you to cut and paste very complicated commands from the site to your terminal screen without retyping.

Here is the article on [[COLOR="Blue"]Installing LAMP On Ubuntu For Newbies[/COLOR]]("http://www.howtoforge.com/ubuntu_lamp_for_newbies")

Good luck.

---

### Post by mousepad on 2007-10-12
Thanks for posting that link Xaneco, that's exactly what I needed.  The problem I'm having is that trying to run a test php script, firefox just shows a popup requesting me to open the file (as if php extension is not recognized).  Terminal shows that I have the latest php5 installed...

This works if anyone was having my problem:
> **gertmul said:**
> And if you don't have the php5.xxxx files in the mods-available folder the following should put them there:

```
apt-get --purge remove php5-common
apt-get install php5 phpmyadmin
```

---

### Post by rekahsoft on 2007-10-13
thanks all...i got phpmyadmin and mysql working but i cannot for somereason create databeses...in phpmyadmin it says i have "no privledges"...i am loging in as root so i don;t know what is going on..how do i get the permision to create databases?...note that i am running it on a home computer (localhost) so i have 100% access..

---

### Post by pmasiar on 2007-10-14
> **aks44 said:**
> I guess what the OP wants is something like Apache+Tomcat+Mysql.

This is rather confusing indeed, because project name is "Apache Tomcat", but Tomcat, the Java web application server ("servlet container" in javaspeak) does not require or use the "Apache web server" used by  other (so called "scripting") languages, like Perl/Python/PHP/Ruby from LAMP stack. 

Confused? Get used to it, Java's marketoids like to place java sticker all over too. Power to give a name is obviously too much for some people :-)

---

### Post by aks44 on 2007-10-14
> **pmasiar said:**
> project name is "Apache Tomcat", but Tomcat, the Java web application server ("servlet container" in javaspeak) does not require or use the "Apache web server"

Heh, I learnt something today. :)

I never had to deal with it, and indeed I thought that it ran on top of httpd... Thanks for the correction.

---

### Post by pmasiar on 2007-10-14
Well sometimes they do run http server aside, for serving static files.

As most things in Java, Tomcat is designed for enterprise-level apps: thousands and tens of thousands of pages, gazilion users. And as most things in java, it does not scale down. If you don't believe me, try to create simple "hello world" webpage in popular Java web app framework like Struts. I never worked that hard in my life for stupid "hello world" as I did with Struts. And part of problem is, they (Java enterprise web apps) have own lingo and own incompatible tools for everything.

---

### Post by rekahsoft on 2007-10-14
why can i not create a database using phpmyadmin...it says i have no privledges :S

---

