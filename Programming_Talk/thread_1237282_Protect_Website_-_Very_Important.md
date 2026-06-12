---
title: "Protect Website - Very Important"
date: 2009-08-11
forum: Programming Talk
---

### Post by mthalis on 2009-08-11
I created website using php and deploy it, now I want to protect that web site from **HACKERS**, so how can I do it, Any tutorials very helpful.

note - some hackers change index page picture, how  to stop this sort of attack

---

### Post by credobyte on 2009-08-11
[http://en.wikipedia.org/wiki/Cross-site_scripting](http://en.wikipedia.org/wiki/Cross-site_scripting)
[http://en.wikipedia.org/wiki/SQL_injection](http://en.wikipedia.org/wiki/SQL_injection)
[http://en.wikipedia.org/wiki/Botnet](http://en.wikipedia.org/wiki/Botnet)

These 3 pages might be a good starting point ;)

---

### Post by hessiess on 2009-08-11
if you are on a shared server, make sure PHP is *NOT* running as the same user as Apache, store everything in the database and make sure you run any data from an external source through "mysql_real_escape_string" before using it in a SQL query. Then chmod the file containing the MySql info to 600 to prevent other users on the server from messing with it.

Your whole application should have a single entry point as it makes keeping track of what data is filtered/unfiltered substantially easier and also helps to keep the code base clean. If you are not already doing so, using a framework like cakephp will handle most of the above automatically.

---

### Post by mthalis on 2009-08-11
Please I need more comments....

---

### Post by slavik on 2009-08-12
> **hessiess said:**
> if you are on a shared server, make sure PHP is *NOT* running as the same user as Apache, store everything in the database and make sure you run any data from an external source through "mysql_real_escape_string" before using it in a SQL query. Then chmod the file containing the MySql info to 600 to prevent other users on the server from messing with it.

Your whole application should have a single entry point as it makes keeping track of what data is filtered/unfiltered substantially easier and also helps to keep the code base clean. If you are not already doing so, using a framework like cakephp will handle most of the above automatically.
and use prepared statements.

Also an idea is to have a cron script that will scrub logs and look for too many connections from a single IP ... because something like 2000 connections from 1 IP address in 1 hour is not kosher. (Believe it or not, this is a common problem for "adult content" providers).

---

### Post by mthalis on 2009-08-12
I very new to Protect website subject, I upload my website remote host(popular provider) then How can I protect my website from malicious attack's

In my website only one page contain **form**,  all other pages are descriptions(text, image)

How should I grantee hackers not change my descriptions. 

I have much more to ask please help me...

---

### Post by mthalis on 2009-08-12
Any suggestion?

---

### Post by Mirge on 2009-08-12
Maybe provide an example or the specific website of interest? I'm having a hard time actually understanding what you're wanting from us.

---

### Post by mthalis on 2009-08-12
I saw some websites, hackers change website frontage(images, text), some time they changed other pages text,picture so how can I prevent this sort of attack?

---

### Post by myrtle1908 on 2009-08-12
> **mthalis said:**
> I saw some websites, hackers change website frontage(images, text), some time they changed other pages text,picture so how can I prevent this sort of attack?

See credobyte's post above.  They are most likely using one of those techniques. However due to the limited information you have provided it is impossible to tell.

Finally, you could post a link to your site and someone may offer further suggestions.

---

### Post by mthalis on 2009-08-12
Thank you for your reply but I can't give my website name sorry for that(because website not officially launch). what kind of information should I post here?

I want description of web site attack and how to prevent them( web site like or documentation) like my above post example.

---

### Post by Mirge on 2009-08-12
Well then look at the advice you were already given if you can't supply the site you're trying to protect.

> **credobyte said:**
> [http://en.wikipedia.org/wiki/Cross-site_scripting](http://en.wikipedia.org/wiki/Cross-site_scripting)
[http://en.wikipedia.org/wiki/SQL_injection](http://en.wikipedia.org/wiki/SQL_injection)
[http://en.wikipedia.org/wiki/Botnet](http://en.wikipedia.org/wiki/Botnet)

These 3 pages might be a good starting point ;)

---

### Post by jeffathehutt on 2009-08-12
Also, keep in mind that your site is only as secure as the weakest link.  Some people spend days reading their code, making sure that every possible security flaw is fixed.  Then, they use ftp with a four character password to upload their site and a hacker has destroyed it before they can even refresh the page.

There is no absolute security in web sites.  The only option available to developers is to try to minimize the chances they can be hacked.

---

