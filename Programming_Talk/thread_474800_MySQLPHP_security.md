---
title: "MySQL/PHP security"
date: 2007-06-15
forum: Programming Talk
---

### Post by tipalm73 on 2007-06-15
Hi,

I am pretty new to php/mysql web developement. Currently I put up a little site where you can make users, login, browse some php pages, and log out.

Before I make it pretty I am interested in security. Got some great leads into magic_quotes and real_escape_string,  and have 2 topics of discussion:

1) Any leads on security documentation relating to Ubuntu/PHP5/MySql would be greatly appreciated =].

2) Is more of a question, im reading alot about removing rogue characters but was curious if there is a method for adding bunk characters to secure data? Example all entries are followed by y5@G. So if a rogue site tried to insert something that wasn't followed by the "key" it would return a false. Sorry if this is a noob question, but at least my wheels are turnin!

Thanks in advance!

---

### Post by lingnoi on 2007-06-15
In my experience the most important things are:

1) If you use GET variables don't name them the same as the variable in your MySQL database. It allows someone to build up in their mind what your database looks like.
2) You should escape ALL data going into the database. A good class you can use is called EzSQL for this.
3) Don't store important data in cookies.
4) Don't store passwords as plain text. MD5 them and make your dog eat them and run them through another hashing algorithm. When the user logs in do the same to the password they give you and compare the results.
5) Make your script silently fails. There should never be a debug error otherwise you could be giving away information about your MySQL database to the public which would allow someone to build up a better picture of how to break in.

bad example
```
index.php?uid=2
<?php 
$sql = 'SELECT * FROM users WHERE uid='.$_GET['uid'];
$data = $database->get_row($sql);
$_COOKIE['data'] = $data->password;
?>

```

good example
```
index.php?id=2
$sql = 'SELECT * FROM users WHERE uid='.$database->escape($_GET['id']);
$data = $database->get_row($sql);
$_SESSION['data'] = $data->password;
$_COOKIE['data'] = get_session_id(); /* you could store the session id in case the user closes the browser. */

```

When you do your login script beware of cross site scripting.

Bad example
```
<?php 
/* login form */
$sql = 'SELECT * FROM users WHERE username='.$database->escape($_GET['username']).' AND password=MD5('.$_GET['password'].')';

```

No need to escape the password because its being put through MD5 right? Using the password
```
') or ('x'='x
```

Would break your security.

Hope this helps you a little. :D

---

### Post by vexorian on 2007-06-15
> **tipalm73 said:**
> Hi,

I am pretty new to php/mysql web developement. Currently I put up a little site where you can make users, login, browse some php pages, and log out.

Before I make it pretty I am interested in security. Got some great leads into magic_quotes and real_escape_string,  and have 2 topics of discussion:

1) Any leads on security documentation relating to Ubuntu/PHP5/MySql would be greatly appreciated =].

2) Is more of a question, im reading alot about removing rogue characters but was curious if there is a method for adding bunk characters to secure data? Example all entries are followed by y5@G. So if a rogue site tried to insert something that wasn't followed by the "key" it would return a false. Sorry if this is a noob question, but at least my wheels are turnin!

Thanks in advance!

- Escape EVERY variable that will be used inside a mysql query.
- Escape EVERY variable that will be outputted to html

---

### Post by aks44 on 2007-06-15
> **tipalm73 said:**
> Before I make it pretty I am interested in security.Glad to see you take it seriously, as security is probably the most important matter for any network application, especially web sites.

> **tipalm73 said:**
> im reading alot about removing rogue characters but was curious if there is a method for adding bunk characters to secure data? Example all entries are followed by y5@G. So if a rogue site tried to insert something that wasn't followed by the "key" it would return a false.I'm not sure to get you right on this one. The thing is, the database can't check that by itself.
However, such stuff can be useful to prevent dictionnary attacks on hashed secrets (mainly passwords), if you are ever unlucky enough to get your DB dumped by an attacker. This is called a **salt**.
Your scripts could also use this kind of method to check data integrity, and detect if your DB has been tampered with. Unfortunately, by itself this can't *prevent* the tampering.



Also, a good way to obfuscate your site structure is to use Apache's excellent **mod_rewrite**, if your web host allows you to use it (see **.htaccess** files). However this is a bit more advanced topic, I'm not sure you should focus on that yet.


Good luck on your journey ;)

---

### Post by tipalm73 on 2007-06-15
Thanks for the tips.

I am hosting it in my closet and comcast doesnt block anything... so..I allow this!

=D

---

