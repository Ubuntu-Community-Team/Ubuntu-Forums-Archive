---
title: "[php] need help securing my script"
date: 2008-06-22
forum: Programming Talk
---

### Post by ELD on 2008-06-22
Hi all i am creating a simple forum software and have found an exploit, basically i need to stop people uploading a form on a website A that posts something to website B.

How can i make it so website B only accepts requests from website B.

If you see what i mean?

There is a post here: [http://www.waraxe.us/ftopicp-12283.html](http://www.waraxe.us/ftopicp-12283.html) of the exploit in question, how do i stop stuff like that?

---

### Post by Cappy on 2008-06-22
SQL Injection is where you pass input without validation to your SQL query. You should read [http://en.wikipedia.org/wiki/SQL_injection](http://en.wikipedia.org/wiki/SQL_injection)

The methods to prevent SQL Injection are pretty simple but you will need to change every call to SQL. Trust no input from the database or the user to be secure.

What version of php does this software run on?

---

### Post by ELD on 2008-06-22
I know all about sql injection, my question is how do i stop forms submitting information that are not with my software.

Since finding that i check the forum id, topic id and author id are all numbers, all text was secured by a function which calls in mysql_real_escape_string so i don't think any harm can be done.

---

### Post by LoneWolfJack on 2008-06-22
If your problem is that people post something like

```
<form action=...
```

you can stop this by using htmlentities() on the output, which will turn the above code into something like

```
&bla;form action=...
```

hence making it impossible to insert valid HTML or Javascript code.

Note that htmlentities is not UTF-8 safe by nature.

---

### Post by ELD on 2008-06-22
No that is not the problem, i think i have it all sorted now, thanks anyway.

---

