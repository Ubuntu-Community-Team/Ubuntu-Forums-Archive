---
title: "Can't connect to MySQL DB from python"
date: 2009-04-16
forum: Programming Talk
---

### Post by aaronp on 2009-04-16
Hi,

Running some python tests from the interactive mode, trying to use MySQLdb to connect to my MySQL database at my hosting site.

I am getting the following error after trying to use MySQLdb.connect() and specifying the host, user, passwd and db names as arguments to it.

```

Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/var/lib/python-support/python2.5/MySQLdb/__init__.py", line 74, in Connect
    return Connection(*args, **kwargs)
  File "/var/lib/python-support/python2.5/MySQLdb/connections.py", line 170, in __init__
    super(Connection, self).__init__(*args, **kwargs2)
_mysql_exceptions.OperationalError: (2003, "Can't connect to MySQL server on 'fdb1.awardspace.com' (4)")
```

My searches on this error so far indicate that MySQL isn't running to enable the connection. But I have checked this MySQL server and it is definitely running, as my existing php scripts can connect to it no problems. 

Note, the python interpreter just hangs after I issue this line until i Ctrl-C, then it spits out the above exception.

Any ideas?

thanks
Aaron

---

### Post by elCabron on 2009-04-16
Are those PHP scrips running on the same system as from which you're doing these Python tests ?
And if not, do you get a response from the MySql server when trying e.g. telnet fdb1.awardspace.com 3306 (or another port, depending on the server's configuration)

---

### Post by aaronp on 2009-04-16
Thanks for the response. 

I went to the hosting FAQ and saw that remote connections to the MySQL database are not allowed.

Then I started to think about how I have previously been connecting by php - I always upload my php files to the server which is obviously why they successfully connect to the database!

I have a 'replica' of my databases on my local MySQL server which I connect to when I am testing php scripts from the local apache/php environment. This is why my php scripts were connecting successfully!!

So, the question now...
I was going to use my local python script and run it on a regular nightly cron job to connect to the server, and extract data from the database for backup purposes.
Given the fact that I can't connect remotely to MySQL are there any other options which will allow me to dump the database (or changes to it) on a nightly basis?

I guess I could run a cron job on the server and then run my own local script to pick up the file via SSH or FTP?? Any other ideas? That might be more reliable/efficient?

thanks
Aaron

---

### Post by pmasiar on 2009-04-17
> **aaronp said:**
> I was going to use my local python script and run it on a regular nightly cron job to connect to the server, and extract data from the database for backup purposes.
Given the fact that I can't connect remotely to MySQL are there any other options which will allow me to dump the database (or changes to it) on a nightly basis?

I guess I could run a cron job on the server and then run my own local script to pick up the file via SSH or FTP?? Any other ideas? That might be more reliable/efficient?

Don't waste time on writing dump script - your database has dump/load command which runs faster and without your handcrafted bugs. Read up about DBA (database admin) tools, there are more you will find handy.

---

### Post by aaronp on 2009-04-17
thanks pmasiar, I'll look into that.

However, I'll have you know that the most featured part of my programming are my hand-crafted bugs!! lol

---

### Post by slavik on 2009-04-17
can you telnet to the IP:port on which the database runs?

---

### Post by ajackson on 2009-04-17
> **aaronp said:**
> So, the question now...
I was going to use my local python script and run it on a regular nightly cron job to connect to the server, and extract data from the database for backup purposes.
You might be able to set up the cron job on your web server, the option might be buried somewhere on the control panel but a lot of hosting companies allow you to do cron jobs. If you then wish to store that data away from your web server you could place it somewhere where you could download it using a cron job on your local machine.

---

