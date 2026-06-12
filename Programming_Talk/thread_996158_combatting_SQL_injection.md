---
title: "combatting SQL injection?"
date: 2008-11-28
forum: Programming Talk
---

### Post by slavik on 2008-11-28
This is something I brought up that has been kicked around in the IRC channel.

So now, I am giving this idead a wider audience.

What about using urlencode() before inserting a string to combat SQL injection? (then using urldecode() before printing it)

---

### Post by kknd on 2008-11-28
May work with the most popular database, but seems like an ugly hack.

A good way to do it is by using the DBMS native functions to it. PostgreSQL, by example, have a function to escape strings and have also parametrized queries that do this automatically.

P.S: Also, urlencode can handle other codifications than ASCII?

---

### Post by slavik on 2008-11-28
I believe so.

The idea is to use some encoding that has a limited character set.

---

### Post by happysmileman on 2008-11-28
I imagine there would probably be relatively easy ways around this? Best just to use the escaping functions provided (such as mysql_real_escape_string() I think in PHP) AND cast any GET variables to the correct types?.

A very common error on sites is that they just mysql_real_escape_string($_GET[whatever]) and assume it's safe, but when the value given by POST or GET is an integer this provides no safety at all (unless perhaps the integer is surrounded by quotes in the SQL query anyway).

---

### Post by mike_g on 2008-11-28
I'm creating joomla mods atm and I just mysql_real_escape_string my queries. I can understand people shoving in modified IDs, but how would casting help? Just curious.

---

### Post by happysmileman on 2008-11-28
> **mike_g said:**
> I'm creating joomla mods atm and I just mysql_real_escape_string my queries. I can understand people shoving in modified IDs, but how would casting help? Just curious.

If you have "news.php?id=2" and the SQL function was ```
"SELECT title, whatever, blah FROM news WHERE id="+mysql_real_escape_string($GET[id])
```

Then someone could send ```
news.php?id=2 UNION ALL SELECT concat(username, char(58,58,58), password) FROM users
```

NONE of that would get escaped because it contains no apostrophes, special characters or quotation marks, it would execute ```
SELECT title, whatever, blah FROM news WHERE id=2 UNION ALL SELECT concat(username, char(58,58,58), password) FROM users
```

Whereas since "id" will always be an integer in database you could cast it before executing statement, if you did "$id = (int)$_GET[id]" then the above example of injection would not work because when casting you an int you're ignoring everything but the "2" at the start.

Not sure if I'm explaining clearly.

---

### Post by mike_g on 2008-11-28
> Not sure if I'm explaining clearly.
Yeah, dunno. I'm too drunk tom pay attention so I'll thank you anyway; although I'm sure you're right on this :)

But its going to mean more work for me tho :(

---

### Post by happysmileman on 2008-11-28
> **mike_g said:**
> But its going to mean more work for me tho :(

Only really affects integers, for strings it's fine to just use mysql_real_escape_string() AFAIK.

---

### Post by doas777 on 2008-11-28
personally, I avoid inline SQL in my source. everything runs through parameterized stored procedures. between that and sanitation of all input, it gives me several levels of protection. 

good luck,
franklin

---

### Post by michaelzap on 2008-11-28
[http://www.php.net/manual/en/security.database.sql-injection.php](http://www.php.net/manual/en/security.database.sql-injection.php)

---

### Post by tinny on 2008-11-29
I use ORM alot so this problem is largely taken care of for me (E.g Hibernate uses parametrized queries). However even if you are using ORM you need to be aware of a few things.

FYI:
[http://www.owasp.org/index.php/Interpreter_Injection#ORM_Injection](http://www.owasp.org/index.php/Interpreter_Injection#ORM_Injection)

(Even if you are not directly using SQL this can be a problem)

---

### Post by drubin on 2008-11-29
> **slavik said:**
> This is something I brought up that has been kicked around in the IRC channel.

So now, I am giving this idead a wider audience.

What about using urlencode() before inserting a string to combat SQL injection? (then using urldecode() before printing it)



LOL  I finally found the post :) Can is paste the 10k of logs files for the discussion :) 

But here is the just of it. sql escaping should only change the syntax *not* the data that is actually stored. Your method actually changes the data set(It also increases it makes more data to store).

Seems like taking a jack hammer to open a peanut. 

Also this approach is not valid for mysql uses the '%' sign for wild card comparison. url encoding stuff will all wile cards when they are not supposed to be there.
```

SELECT * FROM a WHERE d LIKE '%drubin'
```

In your way this would be 
```

SELECT * FROM a WHERE d LIKE '%25drubin'
```

but the "d" column only contains  drubin,asdf_drubin but none of those would be found with your method. (as there was not "escaping" on insert because % was not inserted. )

---

