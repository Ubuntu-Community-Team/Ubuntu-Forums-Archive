---
title: "using a sting with \ in it"
date: 2011-02-11
forum: Programming Talk
---

### Post by Neezer on 2011-02-11
I am writing a python script to try to log into an sql DB....I'm having a problem with the connection due to a \ in a string...

here is my conneciton line...
```

db = MySQLdb.connect(host="INT5695391\ADVANTAGE2005",user = '', passwd = '', db = 'dbname', port = portnum)

```
the problem seems to be with the host string...

I get this for the error code

```

Traceback (most recent call last):
  File "<pyshell#27>", line 1, in <module>
    db = MySQLdb.connect(host="INT5695391\ADVANTAGE2005",user = '', passwd = '', db = 'advantage', port = )
  File "C:\Python27\lib\site-packages\MySQLdb\__init__.py", line 81, in Connect
    return Connection(*args, **kwargs)
  File "C:\Python27\lib\site-packages\MySQLdb\connections.py", line 187, in __init__
    super(Connection, self).__init__(*args, **kwargs2)
OperationalError: (2005, "Unknown MySQL server host 'INT5695391\\ADVANTAGE2005' (11004)")

```

I've removed the username and passwords from the code cause it is a work DB....

---

### Post by Zugzwang on 2011-02-11
You will need to "escape" the "\" character.

Read more on that here: [http://docs.python.org/release/2.7/reference/lexical_analysis.html#literals](http://docs.python.org/release/2.7/reference/lexical_analysis.html#literals)

---

### Post by Neezer on 2011-02-11
Does that mean I need to do:

```

db = MySQLdb.connect(host="INT5695391\\ADVANTAGE2005",user = '', passwd = '', db = 'advantage', port = 50000)

```

this also gives me an error message

```

Traceback (most recent call last):
  File "<pyshell#29>", line 1, in <module>
    db = MySQLdb.connect(host="INT5695391\\ADVANTAGE2005",user = '', passwd = '', db = 'advantage', port = 50000)
  File "C:\Python27\lib\site-packages\MySQLdb\__init__.py", line 81, in Connect
    return Connection(*args, **kwargs)
  File "C:\Python27\lib\site-packages\MySQLdb\connections.py", line 187, in __init__
    super(Connection, self).__init__(*args, **kwargs2)
OperationalError: (2005, "Unknown MySQL server host 'INT5695391\\ADVANTAGE2005' (11004)")


```

I've read all about the escape sequences, and I'm just not getting it....

I thought using \\ would result in just \ in the string, but it doesn't seem so in this case...

---

### Post by Zugzwang on 2011-02-11
Ah, I missed that escaping is probably not your problem here.

I'm not sure if the MySQL connector is able to resolve Windows network names. Try using a domain name that can be resolved by the DNS service or the IP address of the server you want to connect to instead.

---

### Post by LemursDontExist on 2011-02-12
Zugzwang's got it - MySQLdb wants an internet address, not a windows host name.  Assuming you're connecting to a DB on your local machine, you'll want to use
```
db = MySQLdb.connect(host="localhost", user = '', passwd = '', db = 'advantage', port = 50000)
```
Alternatively,
```
db = MySQLdb.connect(host="127.0.0.1", user = '', passwd = '', db = 'advantage', port = 50000)
```
ought to work.

If the DB is not on your local machine, you'll need to find the machine's IP address.

---

### Post by The Cog on 2011-02-13
Your escaping is correct - use two backslashes for every one backslashyou want in the string. But as Zugzwang says, that doesn't look like a proper hostname to me. It is probably worth using the ping command to see what names can be resolved to IP addresses. If the ping command works with the name, then I think the MySQL library should. But I doubt if
ping INT5695391\\ADVANTAGE2005
will succeed.

---

