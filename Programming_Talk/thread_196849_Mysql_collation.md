---
title: "Mysql collation"
date: 2006-06-14
forum: Programming Talk
---

### Post by Isoss on 2006-06-14
Hey

I am having a collation problem in mysql. My problem has nothing to to with programming, but since Mysql is used by programmers so I thought you'd help me guys so please bare with me a little bit!

I have a christian arabic website and I've first developed it in windows using IIS and then apache servers. Everything went good with the collations and theser stuff, so I was able to view my retrieved data in correct arabic characters in my webpage with localhost, and was able to view them properly with phpmyadmin.

Now after I moved to linux, everything was ok and could continue developing my website and arabic characters are shown properly as they should in my webpage in localhost except for phpmyadmin!! They show like "ÝÑíÞ ÇáÑÄíÇ ÇáÌÏíÏÉ"

What I did actually is that I have copied the mysql DB data as they are to /var/lib/mysql and gave permission to them using sudo chmod 777.

I noticed that my DB took the default collation which is latin1_swedish_ci
Back in windows I didn't have to set the collation when creating a database, all I had to do is to choose the collation as "ar-win1256" first when login into phpmyadmin before I create or do anything with the data. But here, I found it as latin1_swedish_ci by default! As I mentioned, data are shown properly on the webpage but are shown like latin in the tables in phpmyadmin!

I exported the data into sql files, then dropped the database and re-created it with the collation cp1256_general_ci which is the collation for arabic. After that I imported the sql data and where all set as cp1256_general_ci and I could see them in correct arabic characters in phpmyadmin. But when I opened my webpage in localhost they appeared like "????? ???? ???????? ???"

What is wrong? How can I set the collation to get arabic shown correctly in phpmyadmin tables and on the webpage?

Hope someone knows the solution.

Thanks.

Isos

---

### Post by Isoss on 2006-06-15
Hello .. any1 there? it's easy come on programmers!

---

### Post by Isoss on 2006-06-15
Ok at least would somebody recommend somewhere were I'd post and get a better help? I'll appriciate that!

---

### Post by indytim on 2006-06-15
I'm really out of my league with this one (don't use collation actively in my db's)... but are the rev's in MySQL the same?  I know collation wasn't even an issue in 3.23... just a thought as you may have up'rvd with the LAMP build.

IndyTim

---

### Post by Isoss on 2006-06-15
Actually I couldn't understand what you are asking! What are "rev's"?

---

### Post by indytim on 2006-06-16
Sorry, been away... 

By rev's I mean revision level of the MySQL server. Things change as MySQL server is upgraded (otherwise why do a upgrade).  At any rate, what I'm alluding to is that MySQL did not do a real strong job of collation support on earlier revisions.  For the current stable release, collation is present and active (if you choose to use something other than the default settings).  

So, after a long "gassing" here, my point being check the support of collation on the two instances of MySQL that are in question.  As I said in my original posting, I don't do anything specific with collation on the 1-production server and 2 development servers I'm running.

Hope this is a starting point for you.  Good luck.

IndyTim

---

### Post by LordHunter317 on 2006-06-16
[QUOTE=Isoss]What I did actually is that I have copied the mysql DB data as they are to /var/lib/mysql and gave permission to them using sudo chmod 777.[/quote]Why did you do this?  This is bad.  Fix it.  It's a major security problem.

> What is wrong? How can I set the collation to get arabic shown correctly in phpmyadmin tables and on the webpage?Is the collation specified in the dump?  What collations are specificed in /etc/my.cnf.  Do the applications specify a collation when they connect?

MySQL has like 4 different collation settings, you obviously have one wrong.  Read the relevant docs carefully and post the above details.

---

### Post by Isoss on 2006-06-17
Actually I am totally confused!
[quote="LordHunter317"]Is the collation specified in the dump? What collations are specificed in /etc/my.cnf. Do the applications specify a collation when they connect?[/quote]
Excuse me but what do u mean by "is the collation specified in the dump?" What is the dump? 
I opened /etc/mysql/my.cnf and there is nothin has to do with collations. and what applications are u talking about? I am sorry I am not that much into web and db applications ... all I know is web programming that's it!

---

### Post by LordHunter317 on 2006-06-17
[QUOTE=Isoss]Excuse me but what do u mean by "is the collation specified in the dump?" What is the dump? [/quote]The backup of the database you took.


> I opened /etc/mysql/my.cnf and there is nothin has to do with collations.Then they are at the defaults.

>  and what applications are u talking about?The ones connecting to the database.

>  I am sorry I am not that much into web and db applications ... all I know is web programming that's it!You should be able to answer teh questions above if you're doing web programming that requires dealing with multiple languages.

---

### Post by Isoss on 2006-06-17
OK, the collation isn't specified in the dump ... I've done something: I opened gftp, I went to the folder that has the mysql db files of my website and downloaded them into /var/lib/mysql ... in the phpmyadmin of the webserver which hosts my website data appear in arabic characters but when I open the phpmyadmin of the localhost they show latin ... I tried to create another db with the collation cp1256_general_ci and then imported the dump they showed like ????? ??? ??????? ???

What is connecting to the DB is my website, in the header I have a meta tag to specifying the charset but that's no the issue! The issue is phpmyadmin!!

When I access mysql using terminal they appear in arabic so the issue is in phpmyadmin.

This is how phpmyadmin looks like; u can see the collation in the first image and how data appear in the second:
[IMG]http://nourelalam.org/Isos/phpmyadmin.jpg[/IMG]
[IMG]http://nourelalam.org/Isos/phpmyadmin2.png[/IMG]

---

