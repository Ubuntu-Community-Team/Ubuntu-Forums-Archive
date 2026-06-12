---
title: "mysql not working at all"
date: 2009-02-22
forum: Programming Talk
---

### Post by gingerj on 2009-02-22
I have installed Mysql on one of my other laptops - the first time around was perfect, everything ran first time of asking. I have installed it on a second machine and after being told it has successfully installed - at the terminal screen I see this error message.

[ginge@ginge ~]$ mysql
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/lib/mysql/mysql.sock' (2)

After doing some research lots of people have come across this problem - but I cannot locate a definitive answer as to how this should be fixed.

Can anyone help?

---

### Post by unutbu on 2009-02-22
If I turn off mysqld with the command
```
sudo invoke-rc.d mysql stop
```

and then run
```

mysql
```

I get (almost?) the same error:```


ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysql[COLOR="Red"]d[/COLOR].sock' (2)

```

So it appears the mysqld server is not running. To start it, try typing
```

sudo invoke-rc.d mysql start
```
Is there any error output?

---

### Post by gingerj on 2009-02-23
hi - it worked many thanks :)

---

