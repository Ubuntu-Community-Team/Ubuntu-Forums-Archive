---
title: "MySQL GUI"
date: 2006-03-16
forum: Programming Talk
---

### Post by Peturrr on 2006-03-16
I am starting with Ruby on Rails. I need a good GUI for MySQL. MySQL Administrator is not very useable on Linux, it crashes alot and somehow the software creates wrong queries. 
Anyway, I need a good alternative. Any suggestions?

---

### Post by David Marrs on 2006-03-16
I've got MySQL Query Browser installed, which came from the Ubuntu repository. It appears in Applications->Other. I still haven't used it though; I just work at the terminal.

---

### Post by bjweeks on 2006-03-16
phpmyadmin

---

### Post by mlind on 2006-03-16
Have you tried mysql-admin? you can install it using apt-get

I've used phpMyAdmin with mysql before, but downside is that it needs
web-server+php work.. It has lot of nice features tho.

---

### Post by Peturrr on 2006-03-16
Yes, I've tried mysql-admin. It keeps crashing on me plus it doesn't suggest anything while creating tables (the windows versions does it, linux seems not to). Maybe it's because of Dapper Drake, wich I am using.

---

### Post by Jova on 2006-04-01
:o 
I just have installed mysql-administrator-1.1.6-1 from mysql.com.
I downoad it and with alien make deb package.

alien mysql-administrator-1.1.6-1.i386.rpm

and  Install it:
dpkg -i mysql-administrator_1.1.6-2_i386.deb

Ther was a problem mising share  library libpcre.so.0
ok. I just link preinstaled ono with ubuntu to act as generic one with

 ln -s /usr/lib/libpcre.so.3 /usr/lib/libpcre.so.0

That's it. Now it works fine (form my activities)

---

### Post by adamkane on 2006-04-01
phpmyadmin only works on mysql4/php4. Otherwise you have to install phpmyadmin from source.

---

### Post by LordHunter317 on 2006-04-01
I'd get used to using the monitor; it's still of poor quality but it's better than all the GUI tools, which are all extremely defcient in one way or another.

---

### Post by rupert on 2006-04-02
you can also use openoffice to edit the data in the tables, best for mass editing,
but the structure has to be already finished.

---

### Post by aPello on 2006-04-26
[QUOTE=adamkane]phpmyadmin only works on mysql4/php4. Otherwise you have to install phpmyadmin from source.[/QUOTE]
All you  need to do to install PHP Myadmin from source is download and extract the archive to your web folder. edit the conf a little bit to work with your settings (Mostly just how you want phpmyadmin to verify you, via http or cookies or what.)

---

### Post by adamkane on 2006-04-26
> 
All you need to do to install PHP Myadmin from source is download and extract the archive to your web folder. edit the conf a little bit to work with your settings (Mostly just how you want phpmyadmin to verify you, via http or cookies or what.)
 
Any chance you could put a guide together, and share the info with the rest of us? This type of question gets asked constantly, and there is no info how to install phpmyadmin from source along with a custom Ubuntu LAMP installation.

---

### Post by menaar on 2006-06-21
I have a similar problem with mysql-query-browser that it crashes when you play with it too much.

And mysqladmin doesn't give you table queries, i think, correct me if i'm wrong.

I found a good program, called mysql-navigator.

It should be in your package manager, or check /usr/bin, it's probabaly there already.

By the way, do a ls /usr/bin/*sql* to see all the utilities you've got for mysql.

---

### Post by mdurham on 2006-06-21
have you tried SQLyog? [http://www.webyog.com/]("http://www.webyog.com/") I could only find a free Windows version, but it seems to work ok under Wine.

---

### Post by menaar on 2006-06-22
Thank you..

It's really nice.

Are you getting this error when you start it?

It doesn't seem to affect anything, I was just curious.

The error is:

Error in CreateFavFolder

and then

Error in AddMenu

---

### Post by menaar on 2006-06-22
Also when I try going into the data migration it tells me
Unable to set user enviroment.

Maybe I should take this to the sqlyog forums.

I don't know if it's a wine issue or a sqlyog issue.

---

### Post by mdurham on 2006-06-22
menaar, I don't see any errors when running sqlyog under Wine but I don't run from a terminal, do you see the error messages in a terminal or what?

---

### Post by menaar on 2006-06-23
I'll tell you, I had alot of problems with the wine install, because I installed it directly from the link. ( I had the option to install with wine when I clicked on the link. Funny that when I tried today to redownload it, I didn't get that option.)

I reinstalled it from the command line, and it wouldn't open at all, telling me I was missing the gdiplus.dll.

So I downloaded it from [http://www.dll-files.com/dllindex/download.php?gdiplusdownload0UHdXEbMhP](http://www.dll-files.com/dllindex/download.php?gdiplusdownload0UHdXEbMhP)
and now it works fine with no errors.

---

### Post by Dustismo on 2006-07-10
Navicat has a linux version which works well..  It is much better then all the others in terms of functionality and is pretty stable..  though it has the amazing ability to freeze my whole desktop on occasion (I thought user progs couldn't do that on linux, hehe)

---

### Post by menaar on 2006-07-11
It says it's only a 30 free trial, though.

And I like sqlyog with wine.

It works perfectly.

---

### Post by DouglasAWh on 2007-10-17
> **David Marrs said:**
> I've got MySQL Query Browser installed, which came from the Ubuntu repository. It appears in Applications->Other. I still haven't used it though; I just work at the terminal.

Mine shows up in Applications --> Programming.

---

### Post by pedrotuga on 2007-10-17
I use mysql-administrator and mysql-query-browser on a dailly basis. I don't see how these are limited. Sure they could have been put together in one aplication, but they will basically do everything you might need.

Simply install them from ubuntu repositories.

---

