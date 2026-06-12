---
title: "run script on a webserver"
date: 2008-09-04
forum: Programming Talk
---

### Post by monkeyking on 2008-09-04
Hi this might be a stupid question.

I want to be able to run a local bash script on a webserver,
That is I wan't  it to run at the server, as If I were sitting at the server.

Is this possible, or do i need to install perl og cgi support to the webserver.

thanks.
edit:
btw the webserver is an apache

---

### Post by Menschenfresser on 2008-09-04
You will need to install something on the server side. If you use PHP, take a look at the [System program execution]("http://de.php.net/manual/en/book.exec.php").

---

### Post by monkeyking on 2008-09-04
thanks, the webserver allready had php installed.

that saved me alot of trouble.


thanks again.

---

### Post by cszikszoy on 2008-09-04
Keep in mind that anything run from PHP's system functions get run as the "www-data" user.  IE, the Apache user.

It took me a lot of head scratching to figure out just what the heck was wrong with the scripts that I wrote to be controlled through a web server.

---

