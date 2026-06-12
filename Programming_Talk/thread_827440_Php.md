---
title: "Php"
date: 2008-06-12
forum: Programming Talk
---

### Post by psychofish25 on 2008-06-12
I am making a simple username and password login in php for a site. It is not attached to a database, just a simple If statement. I was wondering what the problem is.

First: Index HTML appears, asking for the username and password
```
<html>
<head>
<title>Login</title>
</head>
<body>
<div align="center">
<h1>Welcome!</h1>
<h3>Please Log In</h3>
<form name="myform" action="login.php">
Username: <input type="input" name="username" /><br><br>
Password: <input type="password" name="password" /><br><br>
<input type="submit" value="Login" />
<input type="reset" value="Clear Fields" />
</form>
</div>
</body>
</html>
```

Then: Login.php opens
```
<?php
$username=$_POST['username'];
$password=$_POST['password'];
if($username=="user")&&($password=="pass"){
echo "lol!";
header("Location: login_success.html");
}
else {
echo "Wrong Username or Password";
}
?>
```

However, even when I type in user and pass in the form under index.html, my browser does not go to login_success.html, but instead goes blank. Remember, I am using geocities to do this.

Thanks,
Jordan

---

### Post by mike_g on 2008-06-12
Apparently geocities dosent do php unless its paid for:
[http://www.webmasterworld.com/forum88/8731.htm](http://www.webmasterworld.com/forum88/8731.htm)

You will need webhosting which offers php service (and sql if you want a db).

---

### Post by psychofish25 on 2008-06-12
> **mike_g said:**
> Apparently geocities dosent do php unless its paid for:
[http://www.webmasterworld.com/forum88/8731.htm](http://www.webmasterworld.com/forum88/8731.htm)

You will need webhosting which offers php service (and sql if you want a db).

Ah okay, I figured that'd be the problem. I made a little one with just a JS if statement. It's not secure, but it's good enough.

---

