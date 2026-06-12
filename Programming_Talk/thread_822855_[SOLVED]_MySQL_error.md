---
title: "[SOLVED] MySQL error"
date: 2008-06-08
forum: Programming Talk
---

### Post by mike_g on 2008-06-08
I have a table using an email address as the key. I need to check if an entry exists before inserting a new one, but I'm getting this error:
```
Warning: mysql_num_rows(): supplied argument is not a valid MySQL result resource on line 16
```
And heres the code I'm using:
```
	$link = mysql_connect($localhost, $username, $password);
	mysql_select_db($database);
	$result = mysql_query("SELECT * FROM customer WHERE email = $email");

	// If customer is not registered then add to the database 
	if(mysql_num_rows($result) == 0) [COLOR="RED"]// <- doesent like this[/COLOR]
	{
		mysql_query(" INSERT INTO 
		customer (email, firstname, lastname, house, street, town, country, postcode) 
		VALUES ('$email','".$_POST['first_name']."','".$_POST['last_name']."','".$_POST['address_1']
		."','".$_POST['address_2']."','".$_POST['city']."','".$_POST['country']."','".$_POST['zip']."')")
		or die( mysql_error ().":".mysql_errno ());
	}
	else	
		mysql_free_result($result); 
	
	mysql_close($link);
```
Anyone know how I can get the number of rows returned even when none exist?

---

### Post by Matt Mc on 2008-06-08
Where you have this:
```
mysql_query("SELECT * FROM customer WHERE email = $email")
```

Try this:
```
mysql_query("SELECT * FROM customer WHERE email = '$email'")
```
(there are single quotes around $email here)

I can't guarantee it will work. Also, I hope you're sanitising your queries (mysql_real_escape_string will help you here)

---

### Post by mike_g on 2008-06-08
Yep, that works. And no I'm not sanitising it at the moment. I'll look into it. Thanks.

---

### Post by Can+~ on 2008-06-08
[http://xkcd.com/327/](http://xkcd.com/327/)

---

