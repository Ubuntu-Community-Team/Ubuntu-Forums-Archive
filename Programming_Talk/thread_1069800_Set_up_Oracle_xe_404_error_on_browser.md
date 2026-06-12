---
title: "Set up Oracle xe: 404 error on browser"
date: 2009-02-14
forum: Programming Talk
---

### Post by andrew222 on 2009-02-14
Hello,

I set up Oracle xe on Ubuntu 8.10 following instructions from this web page

[http://www.cyberciti.biz/faq/howto-install-linux-oracle-database-xe-server/](http://www.cyberciti.biz/faq/howto-install-linux-oracle-database-xe-server/)

After the installation is done, it instructs to go to this url for a log on screen

[http://127.0.0.1:8080/apex](http://127.0.0.1:8080/apex)

I am getting a 404 status code from Apache.  Would anyone one know why I am getting this error.

---

### Post by asifkhursheed on 2009-09-17
configure your oracle DB using
 [B]$ sudo /etc/init.d/oracle-xe configure
change the port number 8080. this port number is used by tomcat and thats y u r getting 404 message.


[/B]

---

### Post by retiefdv on 2009-09-19
I have exactly the same problem, but when attempting to use the

sudo /etc/init.d/oracle-xe configure

command I get the message "Oracle Database 10g Express Edition is already configured". How do I "unconfigure" Orace XE?

---

### Post by Waappu on 2009-09-21
Hi,

You do not need re-configure.

Check listener status```
lsnrctl status
```if it is not up start it ```
lsnrctl start
```

Also make sure your database is running

Edit:
See also this post, if it help you
[http://ubuntuforums.org/showpost.php?p=7838671&postcount=4](http://ubuntuforums.org/showpost.php?p=7838671&postcount=4)

---

### Post by retiefdv on 2009-09-21
Hi Waapu

Thanks, I got my problem sorted out by visiting the post that you cross-referenced in your reply ([http://ubuntuforums.org/showpost.php?p=7838671&postcount=4](http://ubuntuforums.org/showpost.php?p=7838671&postcount=4)).

Much appreciated.

Retief

---

