---
title: "Python dabase api problem"
date: 2010-02-21
forum: Programming Talk
---

### Post by hoboy on 2010-02-21
I have download  MySQL-python-1.2.2.tar.gz, from 
[http://www.tutorialspoint.com/python/python_database_access.htm](http://www.tutorialspoint.com/python/python_database_access.htm)
there is an installation guide line.
My question is.
I am using Eclipse for python coding, specifically pydev pugging to eclipse,
when I follow the installation how can I access the api in my eclipse project. for example import MySQLdb.
In order to do this python has to be in project class path, this is my question.

---

### Post by jpkotta on 2010-02-21
This really sounds like an Eclipse question.  You should probably change the title.

The MySQL python binding is in the repos.  Once installed, it can be imported like any other module because it will be in the module path.
```
sudo apt-get install python-mysqldb
```

---

