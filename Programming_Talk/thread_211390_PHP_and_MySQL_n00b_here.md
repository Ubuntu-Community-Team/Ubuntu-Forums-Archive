---
title: "PHP and MySQL n00b here"
date: 2006-07-08
forum: Programming Talk
---

### Post by KrisDwyer on 2006-07-08
Hey,

Just wondering if anyone out there was interested in teaching a n00b php and how to get it to talk to MySQL. If not could they link me to a site that can?

Thanks In Advance,
Kris

---

### Post by ifokkema on 2006-07-08
> **KrisDwyer said:**
> Hey,

Just wondering if anyone out there was interested in teaching a n00b php and how to get it to talk to MySQL. If not could they link me to a site that can?

Thanks In Advance,
Kris
Hi,

PHP has a great manual; [www.php.net/docs](www.php.net/docs)
The MySQL connection is well documented as well: [http://www.php.net/mysql](http://www.php.net/mysql)
Use mysql_connect() to connect to the database, mysql_select_db() to select the database you want to work with, mysql_query() to query the database, and mysql_fetch_row(), mysql_fetch_assoc() or mysql_fetch_array() to retreive the results of a SELECT query row by row.

Have fun!

---

### Post by indytim on 2006-07-10
A couple of other suggestions to get up to speed

- Check out the numerous scripting sites that specialize in PHP.  Find something simple and download and play with the script.

- There are also some really good discussion forums dedicated to PHP and MySQL.  Most of the lareger ones have boards for both.  It's like the Ubuntu community as far as having some really good expert help available for questions ranging from the noob user up to the expert level.

Best of luck and welcome to the PHP MySQL Community!


IndyTim

---

### Post by TFleck on 2006-07-10
Look at this tutorial to install everything correctly. It is very good.
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by LordHunter317 on 2006-07-10
Whatever you do, do not use the mysql_() functions. They're bad and shouldn't be used directly unless you absolutely must.  Use PEAR::DB, ADODB or any one of the other tools that wrap around them.

---

### Post by ifokkema on 2006-07-10
> **LordHunter317 said:**
> Whatever you do, do not use the mysql_() functions. They're bad and shouldn't be used directly unless you absolutely must.  Use PEAR::DB, ADODB or any one of the other tools that wrap around them.
'Bad'? Could you provide a little more information, please?

---

### Post by LordHunter317 on 2006-07-10
Lack of parameterized queries is really enough reason.

---

### Post by ifokkema on 2006-07-11
> **LordHunter317 said:**
> Lack of parameterized queries is really enough reason.
I still don't see the point. Would you mind elaborating any further?
Bad as in non-portable, bad as in insecure/unsafe or bad coding style?

---

### Post by LordHunter317 on 2006-07-11
If you don't understand why lack of parameterized queries are bad, read up on them on virtually any reputable security site.  It's a fairly major security issue not to have them.

The API has some other major braindamage too (quick, what's the difference between _escape_string() and _real_escape_string()?) but lack of parameterized queries should be a showstopper for anyone.

---

### Post by ifokkema on 2006-07-11
> **LordHunter317 said:**
> If you don't understand why lack of parameterized queries are bad, read up on them on virtually any reputable security site.  It's a fairly major security issue not to have them.

The API has some other major braindamage too (quick, what's the difference between _escape_string() and _real_escape_string()?) but lack of parameterized queries should be a showstopper for anyone.
Now I never read up on the packages you mention, but I believe your point is that these packages incorporate safeguards against SQL injection, and the mysql_query() function doesn't. Now I don't want to troll/flame or whatever, but I think rather than referring to the mysql_ functions as bad, a warning that you need to incorporate safeguards against SQL injection if you use mysql_query(), would be better.

---

### Post by LordHunter317 on 2006-07-11
> **ifokkema said:**
> Now I never read up on the packages you mention,Which do exactly what is needed, which is why I mentioend them.

> Now I don't want to troll/flame or whatever, but I think rather than referring to the mysql_ functions as bad, a warning that you need to incorporate safeguards against SQL injection if you use mysql_query(), would be better.Utter nonsense.  It's simply unacceptable paramterized queries were never included (and the PHP5 mysqli driver does include them).  Everyone else has them.  And I specifically mentioned those wrappers because they provide parameterized query support around the mysql driver.

I don't like telling people to take hand-rolled safeguards against SQL injection because they will likely get it wrong.  PHP makes it especially easy to get it wrong in a variety of ways.

---

### Post by ifokkema on 2006-07-11
> **LordHunter317 said:**
> Utter nonsense.
Ok :rolleyes:

---

### Post by LordHunter317 on 2006-07-11
Well, if you don't want a response like that, please act in good faith and do the research necessary.  You didn't do it, you admitted you didn't do it, so what did you expect?

It's a big deal.  It makes working with MySQL safely and securely much more work for everyone than it needs to be (ignoring potential missed performance opportunities as well).

---

