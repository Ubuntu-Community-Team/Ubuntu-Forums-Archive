---
title: "PHP LDAP and SQL connection help"
date: 2008-06-10
forum: Programming Talk
---

### Post by obievil on 2008-06-10
My employer is creating a user portal that to begin with will be internal only. They want it to connect and authenticate against LDAP, then MYSQL on a slackware box, Eventually this is going external for our clients. 

They elected me to do the scripting in between to make the connections, and the stupid reason is, because I'm learning C#. 

However, they want it done in Ajax and PHP. The Ajax part I've scrapped already, I'm not going to over complicate a process because it's "New". 

The kicker is, I have no knowledge of PHP or how it works. Basic HTML, Sure, but PHP is another animal to me. 

I've got some basic scripts that I've figured out and altered but I can't get them to work. 
Here is the HTML side

```
<html>
<body>
<form action="index.php" method="post">
Username:<input type="text" name="username"/><br />
Password:<input type="password" name="userpass"/><br />
<input type="submit" name="submit" value="Submit" />
</form>
</body>
</html>

```

And the PHP 
```
<? 
$user = mysql_real_escape_string($_POST['username']);
$pass = mysql_real_escape_string($_POST['userpass']);

mysql_query("SELECT * FROM user WHERE Username = '$user'
         AND userpass = '$pass'");
$pass = mysql_real_escape_string(sha1($_POST['userpass']));

session_start();
$_SESSION['userName'] = $user;
?>
```

can anyone give me any idea of what I'm doing wrong here. At this point I'm just trying to make it connect to SQL. I do not have a CLUE of how to do it with LDAP.

---

### Post by LoneWolfJack on 2008-06-10
oops..... double post, sorry

---

### Post by LoneWolfJack on 2008-06-10
Besides that you don't need to escape hashes, you don't have a mysql connection handler.

---

### Post by obievil on 2008-06-10
> **LoneWolfJack said:**
> Besides that you don't need to escape hashes, you don't have a mysql connection handler.

as I stated I haven't a clue what i'm doing her. can you point me in the right direction?

---

### Post by LoneWolfJack on 2008-06-10
[http://de2.php.net/manual/en/function.mysql-connect.php]("http://de2.php.net/manual/en/function.mysql-connect.php")

```

$connection_handler = mysql_connect('host','user','pass');
mysql_query('use mydb',$connection_handler);
$foo = mysql_query('SELECT 1',$connection_handler);
$bar = mysql_fetch_assoc($foo);
print_r($bar);

```

---

### Post by obievil on 2008-06-19
Thanks, I'll give this a  try this afternoon.

---

