---
title: "PHP Profile Script"
date: 2008-08-21
forum: Programming Talk
---

### Post by eliastk on 2008-08-21
In php, how do I make a profile page like this: [www.example.com/profile.php?&id=1](www.example.com/profile.php?&id=1)     I have a database and login script etc.

---

### Post by mike_g on 2008-08-21
I take it you were showing the url as an example of how to pass data as the link is not to a valid site.

You can obtain the profile id using GET. IE:
```
$profile_id = $_GET['id'];
```
Generally you would then connect to your database ad query the table containing the profile data with the id. For example, in mysql:
```
$result = mysql_query("SELECT * FROM users WHERE id=$profile_id");
```
Thats assuminng that you have already connected to your database. Then you would fill in your page with the content obtained from the db.

---

