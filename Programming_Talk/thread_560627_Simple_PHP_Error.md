---
title: "*Simple* PHP Error"
date: 2007-09-26
forum: Programming Talk
---

### Post by dhtseany on 2007-09-26
Hi everyone,

I'm sure this is super easy but I'm still learning. What's wrong with this line?

```

$SQL = "delete from upload2 where ID = $_GET['sqlid']";

```

Like I said, it must be something simple but I just can't figure it out.

Thanks,

Sean

---

### Post by Occasionally Correct on 2007-09-26
The variable needs braces around it so that it can be parsed correctly:

[php]$SQL = "delete from upload2 where ID = {$_GET['sqlid']}";[/php]

In general, it's a good idea to always use surrounding braces with variable parsing in strings for consistency, clarity, and so things like this won't creep up on you. You can find more information about it [here](http://www.php.net/manual/en/language.types.string.php#language.types.string.parsing). Hope that helps. :)

---

### Post by aks44 on 2007-09-26
> **dhtseany said:**
> What's wrong with this line?

It allows SQL injection. As simple as calling page.php?sqlid=0%20OR%201 which will delete everything in your table.


You may want to use something along those lines:
[php]$SQL = "delete from upload2 where ID = '".mysql_real_escape_string($_GET['sqlid'])."'";[/php]ALWAYS quote & escape SQL arguments (and also escape variables that are output to HTML, using **htmlspecialchars**).

---

### Post by mssever on 2007-09-26
You also need a semicolon at the end of the SQL statement.

---

