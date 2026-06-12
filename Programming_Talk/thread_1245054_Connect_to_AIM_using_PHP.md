---
title: "Connect to AIM using PHP"
date: 2009-08-20
forum: Programming Talk
---

### Post by Mirge on 2009-08-20
Anybody aware of a PHP library that can be used to create an AIM bot?

I tried using [http://sourceforge.net/projects/phptoclib/](http://sourceforge.net/projects/phptoclib/) but it fails to connect, keeps timing out.

Thanks!

---

### Post by Mirge on 2009-08-20
Still using the above library, I can't get it to work. I got farther, by supplying the same server Pidgin uses to connect, which is: $b->myServer="login.messaging.aol.com";

Now it just connects, then disconnects... waits 60 seconds, and repeats.

---

### Post by Mirge on 2009-08-24
bump... how about using Python?

---

### Post by SOULRiDER on 2009-08-24
If there are libpurple wrappers for python you could connect to AIM (libpurple is that pidgin uses).

---

### Post by SOULRiDER on 2009-08-24
Apparently AIM uses the OSCAR protocol, [http://dev.aol.com/aim/oscar/](http://dev.aol.com/aim/oscar/)

Also, check out this stack overflow thread: [http://stackoverflow.com/questions/599218/authentication-required-problems-establishing-aim-oscar-session-using-python](http://stackoverflow.com/questions/599218/authentication-required-problems-establishing-aim-oscar-session-using-python)
And python bindings for libpurple: [http://briglia.net/wiki/tiki-index.php?page=Python-purple+Howto](http://briglia.net/wiki/tiki-index.php?page=Python-purple+Howto)

---

### Post by Mirge on 2009-08-24
Hey thanks a lot :)

Found a PHP binding for libpurple as well: [https://sourceforge.net/projects/phpurple/](https://sourceforge.net/projects/phpurple/)

I'm much much more familiar with PHP than Python, so I'm gonna give that a shot first. I'm just now learning Python.

EDIT: Actually, I'm gonna take a peek at Python's version... give me something to actually look forward to with Python.. as of right now, I have no "goals" with Python.

---

