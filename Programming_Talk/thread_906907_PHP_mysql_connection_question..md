---
title: "PHP mysql_connection question."
date: 2008-08-31
forum: Programming Talk
---

### Post by Griff on 2008-08-31
Quick synopsis.  I have a home page that takes user information in an html form and sends it to the user page.  The user page attempts to log them in to the mysql database.  What I want to be able to do is if they are unable to log in (wrong pass, bad username whatever) is to halt the loading of the rest of the page or at least the php part.  I've tried this:
```

$connection = mysql_connection($db_host, $db_username, $userpass);
if (!$connection) {
  die("Unable to connect:<BR>".mysql_error());
}

```
but it doesn't work.  I assume login errors must be handled differently but I haven't been successful in finding out how.  Any help greatly appreciated.

Thanks,
Griff

---

### Post by mdawg414 on 2008-08-31
You could try this:

```

$connection = mysql_connection($db_host, $db_username, $userpass);

$error = mysql_error();
if (strlen($error) > 0) {
  die("Unable to connect:<BR>".$error);
}

```

It basically just checks if the length of the error string is > 0, then dies.

---

