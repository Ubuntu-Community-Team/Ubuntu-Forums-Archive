---
title: "External mysql database problem"
date: 2008-07-29
forum: Programming Talk
---

### Post by Sitix on 2008-07-29
I have a strange problem.. I want to seperate my webserver from my database server, but for some reason it just doesn't want to connect.

I have a webserver ip that is 192.168.0.104 and a databaseserver ip of 192.168.0.106. So, I used 192.168.0.106 instead of localhost, and I have followed [this]("http://www.vbulletin.com/forum/showthread.php?t=185705") topic to give the right permissions to the webserver. Yet still it refuses to work.

The exact error is "Can't connect to MySQL server on '192.168.0.106' in [dir] on line [x]"

So, I have the right IP's, the right permissions, but somehow it doesn't connect.

Thanks in advance!

---

### Post by hal10000 on 2008-07-29
you have to grant a remote connection on your mysql server, there is a table (i guess it's called hosts) in your mysql database, where you have to make an entry to allow the remote host to log in.

---

### Post by Sitix on 2008-07-29
If you mean the USER_PRIVILEGES table.. I have already done that. But if that wasn't correct I suppose I would've had a permission error, some sort of access denied. The problem more lies in the fact that it can't find my computer on the network, even though it's there...

It might be useful to say that the webserver is (sadly) windows with a WAMP server, and the databaseserver runs on Ubuntu. Both have the packages installed and working, so that can't be the problem...

Any other suggestions?

---

### Post by unutbu on 2008-07-29
Try commenting out the "bind-address" in /etc/mysql/my.cnf by putting a # sign at the beginning of the line:
```
#bind-address		= 127.0.0.1
```

Then restart the mysqld server with
```

sudo /etc/init.d/mysql restart
```

If that does not work, perhaps try the suggestions here: [http://dev.mysql.com/doc/refman/5.0/en/can-not-connect-to-server.html](http://dev.mysql.com/doc/refman/5.0/en/can-not-connect-to-server.html)

---

### Post by Sitix on 2008-07-29
Thanks a LOT!! It works perfectly, I'll remember this one ;-)

Again, thanks!

---

