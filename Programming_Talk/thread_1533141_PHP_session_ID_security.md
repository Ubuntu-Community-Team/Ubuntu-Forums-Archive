---
title: "PHP session ID security"
date: 2010-07-17
forum: Programming Talk
---

### Post by V for Vincent on 2010-07-17
Hi there, I'm working on a small web app that requires users to login. I'm pretty new to PHP, but I've learnt that session handling  using a cookie should be the way to go. I got my hands on a PHP book (beginning PHP and MySQL 5, apress) which does explain the basic idea, but which doesn't really say anything on session security. That is, it explains how a SID is stored in a cookie and how that can be used to identify a user, but... well, here's an example:

```

if(!isset($_SESSION['name'])){
...
}
else{
$name=$_SESSION['name']; 
echo "Welcome back, $name!";
}

```

No check to see whether the cookie hasn't been manipulated by the client. Seems to me that, given that cookies are stored on the client machine, you would have to include something like a hash of the user's password as an additional session variable and then check that against a login table, rather than just accept what's in the cookie. Would that make for a secure login mechanism?

---

### Post by Barrucadu on 2010-07-17
I typically include a hash of the users username and password, possibly along with part of their IP or user agent if I'm feeling particularly secure.

---

### Post by regreth on 2010-07-17
A session can be "hijacked" by getting the SESID as it's the client-side reference to it.You could avoid Session-Hijacking by including some of the user information at the session (like his ip and browser for example) and checking it among accessing the session data.

---

### Post by V for Vincent on 2010-07-17
Okay, good to hear there's a simple solution. Thanks!

---

### Post by DanielWaterworth on 2010-07-17
php session ids are at least 128bits long afaik. In this case the chances of a collision of slim to none, 1 in 340282366920938463463374607431768211456 provided they're generated randomly enough.

---

### Post by Hellkeepa on 2010-07-21
HELLo!

I'd also recommend you to read the following post, as it's basicly the same issue. ;-)
[http://ubuntuforums.org/showpost.php?p=9616860&postcount=8](http://ubuntuforums.org/showpost.php?p=9616860&postcount=8)

Happy syncin'!

---

