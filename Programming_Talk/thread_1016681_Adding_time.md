---
title: "Adding time"
date: 2008-12-20
forum: Programming Talk
---

### Post by dtommy79 on 2008-12-20
Hi,

I have this code:

[PHP]$userid=$CURUSER["id"];
$username=$CURUSER["username"];
$date=time();
$text=trim($_GET["shbox_text"]);[/PHP]

I'd like to increase the time by 6 hours. How can i do that?

Any help is appreciated.

---

### Post by Sprut1 on 2008-12-20
[PHP]
$userid=$CURUSER["id"];
$username=$CURUSER["username"];
$date=time() + (60 * 6);
$text=trim($_GET["shbox_text"]);
[/PHP]

Changed it for you, php.net explains all php functions for you.

---

