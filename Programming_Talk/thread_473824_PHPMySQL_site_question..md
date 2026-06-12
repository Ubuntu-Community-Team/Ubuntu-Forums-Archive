---
title: "PHP/MySQL site question."
date: 2007-06-14
forum: Programming Talk
---

### Post by tipalm73 on 2007-06-14
I have managed, through tutorials, to get a skeleton website up using php and mysql.

You can add a new user, login to home page see links and log out. The problem is once you get to home page any link you click other then logout forces you to log in again. I want the initial login to carry over to the internal site. The URL is tipalm.mine.nu... please be gentle =]

I think the problem is auth.php doesnt check if you are allready logged in and it is called on each page. Here is a link to the tutorial [http://php.codenewbie.com/articles/p...ns-Page_1.html](http://php.codenewbie.com/articles/p...ns-Page_1.html)  and the auth.php code:

```
<?
// Login & Session example by sde
// auth.php

// start session
#session_start();

// convert username and password from _POST or _SESSION
if($_POST){
  $_SESSION['username']=$_POST["username"];
  $_SESSION['password']=$_POST["password"];
}

// query for a user/pass match
$result=mysql_query("select * from users
  where username='" . $_SESSION['username'] . "' and password='" . $_SESSION['p$

// retrieve number of rows resulted
$num=mysql_num_rows($result);

// print login form and exit if failed.
if($num < 1){

  echo "You are not authenticated.  Please login.<br><br>

  <form method=POST action=index.php>
  User name: <input type=text name=\"username\"><br><br>
  Password: <input type=password name=\"password\"><br><br>
  <a href=/adduser.php>New User</a><br>
  <br><input type=submit value='Log In' >
  </form>";

  exit;
}
?>

```

Thanks in advanced =]

---

### Post by aks44 on 2007-06-14
Although this login code is pretty insecure and easily abuseable (SQL injection), removing the # character in front of session_start() will solve your problem.

---

### Post by tipalm73 on 2007-06-14
> **aks44 said:**
> Although this login code is pretty insecure and easily abuseable (SQL injection), removing the # character in front of session_start() will solve your problem.

Thanks alot! I had actually commented that out because I got a strange error. What was happening is the index.php page called config.php 1st which caused problems when the session was started again in auth.php. I started the session in config and removed from the auth.php and everything works great.

Could you suggest newbie documentation on apache/php/mysql security? At this point, for me, it's getting the skeleton up and seeing how it works ...but at some point I'll want the password protection to be worth something hehe =] 

For example if you click on media you just get a link to tipalm.mine.nu:8888, which you could hit just by typing in the URL anyways =D....baby steps though hehe.


Thanks again.

---

### Post by LaRoza on 2007-06-14
[http://www.tizag.com](http://www.tizag.com) has tips for beginner PHP and MySQL programming, including basic security.

---

### Post by aks44 on 2007-06-14
> **tipalm73 said:**
> Could you suggest newbie documentation on apache/php/mysql security?
No documentation links, but a few advices (you can search for reference documentation on these topics by yourself)...

Very basic PHP configuration (read in PHP documentation what these configuration directives do) :

[B]register_globals=off
magic_quotes_gpc=off
magic_quotes_runtime=off
magic_quotes_sybase=off
[/B]
IMO these are mandatory to avoid a big mess. Any web host not allowing you to turn them off is just plain crap (also, check **phpinfo** to make sure they are indeed turned off).


Against **SQL injection** : ALWAYS (may I stress?... ****ALWAYS****) use **mysql(i)_real_escape_string** when building your SQL queries with variable data. The only exception to this is when you are 500% sure that the data is numeric. By "500% sure", I mean you generated it yourself, or you triple-checked it beforehand.


On the PHP side :
- against **Cross-Site-Scripting** : always echoing variables with **htmlspecialchars** using the **ENT_QUOTES** option should be enough in almost all cases.
- always (may I stress? :p) triple-check all incoming data (**$_GET**, **$_POST**, **$_COOKIE**). Check types, check ranges, check lengths, check everything you can think of. Be paranoid.


Following these advices will not make your site unhackable, but it *will* make things really harder for attackers.

Good googling / reading ;-)

---

### Post by tipalm73 on 2007-06-14
Thx so much! Now I have something to read at work.

---

