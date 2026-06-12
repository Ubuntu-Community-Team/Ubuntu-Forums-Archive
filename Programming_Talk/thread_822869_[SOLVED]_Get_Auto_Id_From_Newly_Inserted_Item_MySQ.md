---
title: "[SOLVED] Get Auto Id From Newly Inserted Item MySQL"
date: 2008-06-08
forum: Programming Talk
---

### Post by mike_g on 2008-06-08
I have an 'order' table in a mysql database which links to an 'item' table via an auto increment field in the 'order' table.

When I create a new order I want to be able to get the auto id assigned to it so that I can add items that link to it. Heres the code I have so far:
```
	$date = date("F j, Y, g:i a"); 
	$link = mysql_connect($localhost, $username, $password);
	mysql_select_db($database);
	mysql_query(" INSERT INTO order(email, date) VALUES($email, $date)");
```
Can anyone tell me how I would be able to get it? Cheers.

---

### Post by geirha on 2008-06-08
[mysql_insert_id](php.net/mysql_insert_id)

---

