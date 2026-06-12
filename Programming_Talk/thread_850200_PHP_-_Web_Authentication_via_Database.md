---
title: "PHP - Web Authentication via Database"
date: 2008-07-05
forum: Programming Talk
---

### Post by wieman01 on 2008-07-05
OK, I am somewhat new to this, so please be nice. :-) Being an ex-programmer I don't need the basics.

I was able to establish database connection, read & write data, etc. Now I need secure & reliable PHP authentication so as to create a basic log-in & log-out function to protect my own website. 

What would I have to do? Would I use session cookies and if so, how do I create them? Is there any sound documentation available that would guide me through it step-by-step?

I know how to create database tables and all this, I just don't know how to create sessions & destroy upon user log-out or time-out.

Thank you, guys.

---

### Post by scragar on 2008-07-05
[sessions](http://php.net/sessions) are very simple, on any page you want to use them on you just make sure that before you send any content you [start sessions](http://php.net/session_start)(so before any echos, non-PHP content or buffer flushing), then you can just use the [$_SESSIONS](http://php.net/manual/en/reserved.variables.session.php) array as a persistant array between pages.

to clear sessions you can either use [session_destroy](http://php.net/session_destroy) or reset it to an empty array```
$_SESSION=array();
```
while the first will delete the assosiated file, the later will have an instant effect, so you may need to use both depending on desired effect.

---

### Post by henchman on 2008-07-05
[This]("http://phpeasystep.com/workshopview.php?id=6")  is a neat tutorial :)

You can either use the built in PHP session functions described here

[http://www.php.net/session](http://www.php.net/session)

or you can write your own session functions by [sending the user a cookie]("http://www.php.net/setcookie") as the session id and storing all the appropriate data in an own database table where the data is being matched to that session id.

the latter gives you more freedom, because you can design everything the way you want :)

---

### Post by wieman01 on 2008-07-05
Excellent, guys. Thank you very much! :-)

Found another excellent tutorial here, but wasn't sure if the authentication bit made sense:

[http://www.php-mysql-tutorial.com/]("http://www.php-mysql-tutorial.com/")

---

