---
title: "[PHP] Warning: mysql_fetch_object():"
date: 2010-05-12
forum: Programming Talk
---

### Post by subman on 2010-05-12
Hello!

I keep getting this error: Warning: mysql_fetch_object(): supplied argument is not a valid MySQL result resource in /opt/lampp/htdocs/functions.php on line 6

and it wont show results.

the code -> [http://pastebin.com/nH7pAWs2](http://pastebin.com/nH7pAWs2)

Any help?

---

### Post by roccivic on 2010-05-12
Well, you need to connect to the database first...
[http://php.net/manual/en/function.mysql-connect.php](http://php.net/manual/en/function.mysql-connect.php)

---

### Post by subman on 2010-05-12
No i don't thats already done. this is just a snippet of the whole 500 line functions page.

---

### Post by subman on 2010-05-12
Solved- SQL Table was misspelled.

---

### Post by roccivic on 2010-05-12
Maybe the query is failing... Typo in the field name or something?
Did you try to run the query in phpMyAdmin or mysql client?
Do you get any results there?

---

### Post by Seal Daemon on 2010-05-12
Catch your mistakes before you move on ;)

[PHP]mysql_query($querry) or die(mysql_error());
[/PHP]

---

