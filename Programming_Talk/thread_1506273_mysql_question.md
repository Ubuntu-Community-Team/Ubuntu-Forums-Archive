---
title: "mysql question"
date: 2010-06-10
forum: Programming Talk
---

### Post by Iuliux on 2010-06-10
I have a table with two columns. First is an id and the other is a user. How can I test from a php page that a line (id + user) exists in the table?

---

### Post by Bachstelze on 2010-06-10
There's a lot of ways to do that, here's one:

[PHP]$request = mysql_query("SELECT * FROM table WHERE id = 'foo' AND user = 'bar'");
if(!mysql_num_rows($request)) {
    print 'No results found!';
} else {
    // Do your stuff
}[/PHP]

---

### Post by Iuliux on 2010-06-10
Thanks, it's working beautifully.

---

