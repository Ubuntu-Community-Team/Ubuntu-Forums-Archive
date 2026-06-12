---
title: "Mysql and media wiki"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by jbailey22 on 2008-07-28
I just set up an Ubuntu 8.04 Server for my wiki. I got everything going and when I do the mediawiki install via the webpage interface it always hangs out the database config. I dont have any databases on this server, will be moving a database from an exsisting wiki to the new one soon tho. Do I need to set up a database first, move mine over, or what? Thanks

---

### Post by Potatoj316 on 2008-07-28
well you need a database server.  You can move the old files over from the old server but you will still have to install the database server (probably mysql)

Try ```
sudo aptitude install mysql-server
```

---

### Post by compiledkernel on 2008-07-28
Actually reference these three pages. 

[https://help.ubuntu.com/8.04/serverguide/C/httpd.html](https://help.ubuntu.com/8.04/serverguide/C/httpd.html)
[https://help.ubuntu.com/8.04/serverguide/C/php5.html](https://help.ubuntu.com/8.04/serverguide/C/php5.html)
[https://help.ubuntu.com/8.04/serverguide/C/mysql.html](https://help.ubuntu.com/8.04/serverguide/C/mysql.html)

---

### Post by jbailey22 on 2008-07-28
Thanks for the guides, seemed that all i needed to do was to restart mysql. Thanks a ton, i was starting to pull out my hair over something so simple.

---

