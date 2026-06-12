---
title: "error when trying to access website"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by trod on 2008-10-24
I am trying to access a website and I keep getting this error . Can anyone help me out?



Warning: mysql_connect() [function.mysql-connect]: Lost connection to MySQL server at 'reading initial communication packet', system error: 111 in /home/erratic/public_html/db/mysql4.php on line 51

Warning: mysql_error(): supplied argument is not a valid MySQL-Link resource in /home/erratic/public_html/db/mysql4.php on line 518

Warning: mysql_errno(): supplied argument is not a valid MySQL-Link resource in /home/erratic/public_html/db/mysql4.php on line 519
phpBB : Critical Error

Could not connect to the database

---

### Post by ww711 on 2008-10-24
Looks like their database is broke.

---

### Post by Crandom on 2008-10-24
There is a problem with the website, not with your computer. The only thing you can do is contact the owners to tell them there are errors.

It seems they have taken down a MySQL database or are doing upgrading, or have had a crash.

---

### Post by trod on 2008-10-24
I have been told other people are able to access it.

---

### Post by Crandom on 2008-10-24
Well, it worked when they accessed it, now it is broken.

---

### Post by redseventyseven on 2008-10-24
> **trod said:**
> I have been told other people are able to access it.

When were these other people able to access the website? This might have been something that just happened with the server a few minutes ago, so your friends may have accessed it before it broke.

It's possible (though unlikely) that the website detects where you are and redirects you to a version of the website stored on a different server (more local to you for better access speeds or even just to spread the traffic around) and it could be that it's that particular server that's broken (which is why your friends can access the site and you can't).

Perhaps if you could tell us what website it is (provided it's not too rude of course!) then some of us could check to see if we have the same problem?

In any case, the first couple of respondents were right; the error message you received was spat out by the server providing the website, not your local computer. MySQL is something the server uses to turn a database into a web page that your computer can access, and so does its job entirely on the server before it sends anything to your computer.

---

### Post by trod on 2008-10-24
great thanks for you help

---

