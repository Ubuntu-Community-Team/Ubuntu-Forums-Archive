---
title: "PHP cannot connect to MySQL DB because username uses the at sign (@)"
date: 2009-01-23
forum: Programming Talk
---

### Post by altonbr on 2009-01-23
Standard connection:

[PHP]	// create MySQL connection
	$mysql_link = mysql_connect('domain', 'username@domain', 'password');
	if (!$mysql_link)
	{
		die('Not connected: '.mysql_error());
	}

	// select MySQL DB
	$db_selected = mysql_select_db('database', $mysql_link);
	if (!$db_selected)
	{
		die ('Can not use '.$db_name.': '.mysql_error());
	}[/PHP]
returns
> Can not use : Access denied for user 'username'@'%' to database 'database'

Since, in this case, the username is 'username@domain' (don't ask my why free hosts insist on such stupid usernames), how can I insure the FQDN of username@domain@domain works? I can't seem to escape the '@' at sign in any way.

---

### Post by CodeBird on 2009-01-23
well it seems you got connected to mysql with the username, so the username has no issues the problem is as if you don't have privileges on the database you want... If the username was the issue you wouldn't have got connected at all

---

