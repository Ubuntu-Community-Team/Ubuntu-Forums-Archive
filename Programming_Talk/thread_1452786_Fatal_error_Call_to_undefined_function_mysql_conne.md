---
title: "Fatal error: Call to undefined function mysql_connect() in /var/www/welcome.php on li"
date: 2010-04-12
forum: Programming Talk
---

### Post by piyush.neo on 2010-04-12
i am using ubuntu 9.10 with apache2, php5 and mysql.
On opening this file in browser its showing the error
[PHP]
<?php
//phpinfo();
$con=mysql_connect("localhost","root","sql");
if (!$con)
  {
  die('Could not connect: ' . mysql_error());
  }
?>
[/PHP]**Fatal error**:  Call to undefined function mysql_connect() in **/var/www/welcome.php** on line [B]2
[/B]How to rectify it..?

---

### Post by zoff_ita on 2010-04-12
> **piyush.neo said:**
> i am using ubuntu 9.10 with apache2, php5 and mysql.
On opening this file in browser its showing the error
[PHP]
<?php
//phpinfo();
$con=mysql_connect("localhost","root","sql");
if (!$con)
  {
  die('Could not connect: ' . mysql_error());
  }
?>
[/PHP]**Fatal error**:  Call to undefined function mysql_connect() in **/var/www/welcome.php** on line [B]2
[/B]How to rectify it..?

Are you sure to have php5-mysql package installed on your system?

---

### Post by piyush.neo on 2010-04-12
Thanks a lot..i installed it and problem solved...:guitar:

---

### Post by MattPhillips on 2011-03-25
zoff_ita, I had the same problem and you solved it for me as well.  Thank you!!

---

### Post by sushy on 2012-08-27
Thank you that solved my problem..:)

---

### Post by overdrank on 2012-08-27
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

