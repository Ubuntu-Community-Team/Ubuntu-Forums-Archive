---
title: "Neeb mysql help"
date: 2008-12-01
forum: Programming Talk
---

### Post by rtoot3 on 2008-12-01
im learning mysql and i wanted to try to make a simple registration form so i made 2 files

registration1.php ```

<form action="register2.php" method="post" name="register">
choose a username:<br />
<input type="text" name="registeru"/>
choose a password:<br />
<input type="text" name="registerp"/>
<input type="submit"/>
</form>
```

registration1.php ```

<?php
$user = $_POST['registeru'];
$pass = $_POST['registerp'];
mysql_connect('classified','classified','classified') or die(mysql_error());
mysql_select_db('classified') or die(mysql_error());
mysql_query("INSERT INTO users(username,password) VALUES($user,$pass) ") or die(mysql_error());
echo 'Registered Successfully';
?>
```

when you try to enter something it says
Unknown column 'whatever you put for username' in 'field list'
what happened?

---

### Post by wilbbe01 on 2008-12-01
You did create the table first correct?  If you did it does indeed have a username column and a password column right?

---

### Post by mike_g on 2008-12-01
Also, when entering text into a database you want to put apostrophes around the variable IE:
```
"INSERT INTO users(username,password) VALUES(**'$user','$pass'**)"
```
Otherwise things will screw up. It would also be a good idea to escape stuff you shove in your db with [mysql_real_escape_string](http://uk2.php.net/mysql_real_escape_string)

---

### Post by rtoot3 on 2008-12-01
> **wilbbe01 said:**
> You did create the table first correct?  If you did it does indeed have a username column and a password column right?

correct, i have already successfully conected to the database and made tables and put values in it with out using $_POST, it just wont work for me with the form

> **mike_g said:**
> Also, when entering text into a database you want to put apostrophes around the variable IE:
```
"INSERT INTO users(username,password) VALUES(**'$user','$pass'**)"
```
Otherwise things will screw up. It would also be a good idea to escape stuff you shove in your db with [mysql_real_escape_string](http://uk2.php.net/mysql_real_escape_string)

i did put appostraphies, the code box just makes it look like periods.

---

### Post by mike_g on 2008-12-01
Apostrophes are these things: '
Commas are these things: ,
Commas sometimes look like a full stop, but apostrophes generally dont ;)

---

### Post by rtoot3 on 2008-12-01
> **mike_g said:**
> Apostrophes are these things: '
Commas are these things: ,
Commas sometimes look like a full stop, but apostrophes generally dont ;)

oops, lol. thanks! it worked!

---

### Post by rtoot3 on 2008-12-01
by the way, i already know about mysql real escape, im not using it here though because its just a test website.

---

### Post by rtoot3 on 2008-12-01
oh, one more thing,
whats the diff between primary key, and unique key?

---

### Post by drubin on 2008-12-01
Also remember to escape the users input so that if their name is drubin's it wont break your query.

Read [this]("http://www.php.net/function.mysql-real-escape-string")

---

