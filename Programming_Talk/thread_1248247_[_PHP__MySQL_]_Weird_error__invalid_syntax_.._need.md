---
title: "[ PHP / MySQL ] Weird error / invalid syntax .. need assistance !"
date: 2009-08-23
forum: Programming Talk
---

### Post by credobyte on 2009-08-23
Does anybody have an idea, why I keep getting this error ? I can't seem to find a single reason why it should fail :-k


MySQL table:
```
options
-------------------------
id (int)
from (varchar)
to (varchar)
rate (int)
```

PHP code:
[PHP]<?php

$from = $_GET['from'];
$to = $_GET['to'];

$connection = mysql_connect("localhost", "username", "password") or die(mysql_error());
$database = mysql_select_db("database") or die(mysql_error());

$query = mysql_query("SELECT * FROM options WHERE from='$from' AND to='$to'") or die(mysql_error());

?>
[/PHP]

[COLOR=Red]**Error:**[/COLOR]
```
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'from='wmz' AND to='wmr'' at line 1
```

---

### Post by Wim Sturkenboom on 2009-08-24
*from* is a reserved keyword (select * **from**); put it between back-ticks like *WHERE `from`='$from'*

Some say it's a bad habit to use reserved keywords for variables.

---

### Post by credobyte on 2009-08-24
> **Wim Sturkenboom said:**
> *from* is a reserved keyword (select * **from**); put it between back-ticks like *WHERE `from`='$from'*

Some say it's a bad habit to use reserved keywords for variables.

Bad habit .. Currency exchange/pairs - why would I add something else than from/to ? :( Ehh, anyway - thnx for the info .. it really went online after replacing my column names.

---

### Post by v8YKxgHe on 2009-08-24
It's very kind of you to let your users edit that SQL query them selves as well. I like being able to write my own SQL in an application I don't control :P

What I'm getting at is, you're open to SQL injection attacks there - since you're taking raw user data and simply constructing a SQL query from it. If you want to keep MySQL extension, use [http://php.net/mysql_real_escape_string](http://php.net/mysql_real_escape_string) - or, switch to [http://php.net/pdo](http://php.net/pdo) and use prepared statements.

---

### Post by credobyte on 2009-08-24
> **AlexC_ said:**
> It's very kind of you to let your users edit that SQL query them selves as well. I like being able to write my own SQL in an application I don't control :P

What I'm getting at is, you're open to SQL injection attacks there - since you're taking raw user data and simply constructing a SQL query from it. If you want to keep MySQL extension, use [http://php.net/mysql_real_escape_string](http://php.net/mysql_real_escape_string) - or, switch to [http://php.net/pdo](http://php.net/pdo) and use prepared statements.

I don't do complicated scripts without verifying it's parts separately ( in this case, I don't make classes, input validation, etc., without being sure that my queries/functions are +/- valid ) ;)

---

### Post by v8YKxgHe on 2009-08-24
That is not a complicated script, and even if you make the SQL query valid - **I** can make it invalid. You never ever, ever, trust user input - all users are out there to crack into and exploit your website.

---

### Post by Mirge on 2009-08-24
> **AlexC_ said:**
> That is not a complicated script, and even if you make the SQL query valid - **I** can make it invalid. You never ever, ever, trust user input - all users are out there to crack into and exploit your website.

I have to agree. It would be a good habit to have to validate all of your user input as you fetch it, as you code, IMO. Going back over your code again, especially on larger projects, will become tedious and easier to overlook an occurrence or two that remain exploitable.

---

### Post by v8YKxgHe on 2009-08-24
Indeed, security is not something you bolt on as an afterthought. The entire architecture of your software needs to be built around security from the start, implementing ways of avoiding most common issues, and those not so common.

---

### Post by credobyte on 2009-08-24
> **AlexC_ said:**
> That is not a complicated script, and even if you make the SQL query valid - **I** can make it invalid. You never ever, ever, trust user input - all users are out there to crack into and exploit your website.

This is not a script - it's a snippet. Anyway, good luck with that .. 4 years and not a single hacked website.

---

### Post by Mirge on 2009-08-24
> **credobyte said:**
> This is not a script - it's a snippet. Anyway, good luck with that .. 4 years and not a single hacked website.

Heh, he was just offering advice... not issuing a threat. Relax.

And he was referring to this snippet:

```

[COLOR=#000000] [COLOR=#0000bb]<?php

$from [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]$_GET[/COLOR][COLOR=#007700][[/COLOR][COLOR=#dd0000]'from'[/COLOR][COLOR=#007700]];
[/COLOR][COLOR=#0000bb]$to [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]$_GET[/COLOR][COLOR=#007700][[/COLOR][COLOR=#dd0000]'to'[/COLOR][COLOR=#007700]];

[/COLOR][COLOR=#0000bb]$connection [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]mysql_connect[/COLOR][COLOR=#007700]([/COLOR][COLOR=#dd0000]"localhost"[/COLOR][COLOR=#007700], [/COLOR][COLOR=#dd0000]"username"[/COLOR][COLOR=#007700], [/COLOR][COLOR=#dd0000]"password"[/COLOR][COLOR=#007700]) or die([/COLOR][COLOR=#0000bb]mysql_error[/COLOR][COLOR=#007700]());
[/COLOR][COLOR=#0000bb]$database [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]mysql_select_db[/COLOR][COLOR=#007700]([/COLOR][COLOR=#dd0000]"database"[/COLOR][COLOR=#007700]) or die([/COLOR][COLOR=#0000bb]mysql_error[/COLOR][COLOR=#007700]());

[/COLOR][COLOR=#0000bb]$query [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]mysql_query[/COLOR][COLOR=#007700]([/COLOR][COLOR=#dd0000]"SELECT * FROM options WHERE from='$from' AND to='$to'"[/COLOR][COLOR=#007700]) or die([/COLOR][COLOR=#0000bb]mysql_error[/COLOR][COLOR=#007700]());

[/COLOR][COLOR=#0000bb]?>[/COLOR] [/COLOR] 

```

Which as it stands right now... valid query or not, remains exploitable.

---

### Post by v8YKxgHe on 2009-08-24
> **credobyte said:**
> This is not a script - it's a snippet. Anyway, good luck with that .. 4 years and not a single hacked website.

Haha, sorry - but that is just stupid. I really would hate to see the rest of your code if you think like that.

SQL injection in PHP applications account for the greatest percentage of security exploits across the 'net, and you're adding to it. Do you really think that doing:

```
mysql_query('SELECT * FROM foo WHERE bar = "'.$_GET['bar'].'"');
```
Is wise and clever? You're letting your users edit that SQL query to do *what ever* they want. Now, granted the PHP MySQL extension doesn't let you run multiple queries at once via mysql_query, however you should not rest your ignorance to security issues on an extension someone else wrote.

I've given you the links to secure your code, I advise you read them and Internet security in general.

---

### Post by Mirge on 2009-08-24
Damn, flame war incoming....... well, I think credo got his answer (backticks--or rename the fields).... I'm out.

---

### Post by credobyte on 2009-08-24
> **AlexC_ said:**
> Haha, sorry - but that is just stupid. I really would hate to see the rest of your code if you think like that.

SQL injection in PHP applications account for the greatest percentage of security exploits across the 'net, and you're adding to it. Do you really think that doing:

```
mysql_query('SELECT * FROM foo WHERE bar = "'.$_GET['bar'].'"');
```Is wise and clever? You're letting your users edit that SQL query to do *what ever* they want. Now, granted the PHP MySQL extension doesn't let you run multiple queries at once via mysql_query, however you should not rest your ignorance to security issues on an extension someone else wrote.

I've given you the links to secure your code, I advise you read them and Internet security in general.

:lolflag: 


Sorry, you sound like all these small script kiddies. How can you judge me from a line of code without knowing, what I'm going to do further and if it really is a part of my application ? Have you thought about suggesting something, not being some kind of "I CAN" geeks ?

I know what encapsulation means, I know what input validation means, I know what PHP means .. Yes, sometimes even I make mistakes ( as you see in this thread .. was too tired to see the problem ).

Anyway, thread reported - I'm not going to fight for what I'm not interested in.

[SIZE=4][COLOR=DarkGreen]**Problem Solved**[/COLOR][/SIZE]

---

### Post by Elfy on 2009-08-24
Closed at OP request.

---

