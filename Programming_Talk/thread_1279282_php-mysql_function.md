---
title: "php-mysql function"
date: 2009-09-30
forum: Programming Talk
---

### Post by akvino on 2009-09-30
Hello all!
I want to make remote call to MySQL database from the machine that does not run mysql. Is there a way to do this? This would be 3 tier environment, and it would help if MySQL installation was not needed on the middle tier where php lives. If I remove mysql - I get errors that mysql libraries are missing.

---

### Post by credobyte on 2009-09-30
```
sudo apt-get install php5-mysql

```

That's all you need. If you specify something else ( remote host ) than localhost ( 127.0.0.1 ), it'll not try to connect to your local MySQL server, which means, it's not a must to have it.

---

### Post by akvino on 2009-09-30
> **credobyte said:**
> ```
sudo apt-get install php5-mysql

```

That's all you need. If you specify something else ( remote host ) than localhost ( 127.0.0.1 ), it'll not try to connect to your local MySQL server, which means, it's not a must to have it.

THanks that helps but I am working on RH, getting php-mysql forces dependency for mysql server, since it is searching for libmysqlclient.so.15. Is it the same od Ubuntu distro?

---

### Post by CyberJack on 2009-10-01
Yes libmysqlclient.so.15 is a library which makes it possible for client software to talk to a mysql server. If your mysql server is local or on a remote machine does not make a difference.

---

### Post by akvino on 2009-10-06
> **CyberJack said:**
> Yes libmysqlclient.so.15 is a library which makes it possible for client software to talk to a mysql server. If your mysql server is local or on a remote machine does not make a difference.

So in essence if I don't want to run msyql-server locally (security standards) I have to copy the library and then remove the mysql package. Then PHP can make the call remotley?


Not fun.

---

### Post by CyberJack on 2009-10-07
On ubuntu the package "php5-mysql" (which installs the mysql library for php) depends on "libmysqlclient15off" so it's installed automatically.
The "libmysqlclient15off" package will install the mysql client libraries. (libmysqlclient.so.15 and libmysqlclient_r.so.15).

On ubuntu there is no dependency to mysql-server, so you don't need to install this.

According to your post on RH when you want to install php-mysql there is a dependency to mysql-server.
That sounds a bit strange because all rpm packages I found so far depend only on the client and never on the server.

---

### Post by jtdeloach10 on 2009-10-07
> **akvino said:**
> Hello all!
I want to make remote call to MySQL database from the machine that does not run mysql. Is there a way to do this?

[PHP]mysql_connect('SERVER:PORT', 'user', 'pass'[/PHP]

In case your wondering on the syntax.

---

