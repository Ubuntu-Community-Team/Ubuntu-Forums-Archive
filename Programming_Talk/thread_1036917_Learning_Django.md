---
title: "Learning Django"
date: 2009-01-11
forum: Programming Talk
---

### Post by robtotheb on 2009-01-11
Been having fun playing around with Django and I'm a little stuck and would love some help:

My model:
```

from django.db import models
from django.contrib.auth.models import User

class Profile(models.Model):
	title = models.CharField(max_length=20)
	user = models.ForeignKey(User)
	detail = models.ForeignKey('Detail')

class Detail(models.Model):
	subject = models.CharField(max_length=20)

```

Shell:
```
>>> from django.contrib.auth.models import User
>>> from social_pages.models import *
>>> user = User.objects.get(id=1)
>>> detail = Detail.objects.get(id=1)
>>> user.profile_set.all()
Traceback (most recent call last):
  File "<console>", line 1, in <module>
  File "/usr/lib/python2.5/site-packages/django/db/models/query.py", line 147, in __repr__
    data = list(self[:REPR_OUTPUT_SIZE + 1])
  File "/usr/lib/python2.5/site-packages/django/db/models/query.py", line 162, in __len__
    self._result_cache.extend(list(self._iter))
  File "/usr/lib/python2.5/site-packages/django/db/models/query.py", line 275, in iterator
    for row in self.query.results_iter():
  File "/usr/lib/python2.5/site-packages/django/db/models/sql/query.py", line 206, in results_iter
    for rows in self.execute_sql(MULTI):
  File "/usr/lib/python2.5/site-packages/django/db/models/sql/query.py", line 1734, in execute_sql
    cursor.execute(sql, params)
  File "/usr/lib/python2.5/site-packages/django/db/backends/util.py", line 19, in execute
    return self.cursor.execute(sql, params)
  File "/usr/lib/python2.5/site-packages/django/db/backends/sqlite3/base.py", line 168, in execute
    return Database.Cursor.execute(self, query, params)
OperationalError: no such column: social_pages_profile.detail_id
>>> profile = Profile.objects.get(id=1)
Traceback (most recent call last):
  File "<console>", line 1, in <module>
  File "/usr/lib/python2.5/site-packages/django/db/models/manager.py", line 93, in get
    return self.get_query_set().get(*args, **kwargs)
  File "/usr/lib/python2.5/site-packages/django/db/models/query.py", line 304, in get
    num = len(clone)
  File "/usr/lib/python2.5/site-packages/django/db/models/query.py", line 160, in __len__
    self._result_cache = list(self.iterator())
  File "/usr/lib/python2.5/site-packages/django/db/models/query.py", line 275, in iterator
    for row in self.query.results_iter():
  File "/usr/lib/python2.5/site-packages/django/db/models/sql/query.py", line 206, in results_iter
    for rows in self.execute_sql(MULTI):
  File "/usr/lib/python2.5/site-packages/django/db/models/sql/query.py", line 1734, in execute_sql
    cursor.execute(sql, params)
  File "/usr/lib/python2.5/site-packages/django/db/backends/util.py", line 19, in execute
    return self.cursor.execute(sql, params)
  File "/usr/lib/python2.5/site-packages/django/db/backends/sqlite3/base.py", line 168, in execute
    return Database.Cursor.execute(self, query, params)
OperationalError: no such column: social_pages_profile.detail_id

```

So its telling me I don't have a column called 'social_pages_profile.detail_id' but when I check my sql I do?!  I'm very confused.  What am I doing wrong?

SQL
```
rob@rob-desktop:~/django_code/social$ python manage.py sql social_pages
BEGIN;
CREATE TABLE "social_pages_profile" (
    "id" integer NOT NULL PRIMARY KEY,
    "title" varchar(20) NOT NULL,
    "user_id" integer NOT NULL REFERENCES "auth_user" ("id"),
    "detail_id" integer NOT NULL
)
;
CREATE TABLE "social_pages_detail" (
    "id" integer NOT NULL PRIMARY KEY,
    "subject" varchar(20) NOT NULL
)
;
COMMIT;

```

---

### Post by mike_g on 2009-01-11
Have you checked your database to see if the tables exist?

In standard SQL you dont put double quotes around your table and column names. (Not sure how django works with SQL tho)

in MySQL I'm also pretty sure that you have to define your primary key and indexes after everything else. 

You might also want to add auto increment to your id field.

IE:
```
CREATE TABLE social_pages_detail (
    id integer AUTO_INCREMENT,
    subject varchar(20) NOT NULL,
    PRIMARY KEY(id)
);
```

Edit: Also, AFAIK you cant use references with a MyIASM storage engine, which is the MySQL default.

---

### Post by ankursethi on 2009-01-11
I'm not a Django expert, but I do know a little of it. Take my word with a grain of salt.

Did you run syncdb after creating your model?

```
./manage.py syncdb
```

The *sql* command merely prints the SQL statements. It doesn't commit anything to the database.

---

### Post by robtotheb on 2009-01-11
> **ankursethi said:**
> I'm not a Django expert, but I do know a little of it. Take my word with a grain of salt.

Did you run syncdb after creating your model?

```
./manage.py syncdb
```

The *sql* command merely prints the SQL statements. It doesn't commit anything to the database.

Yes but I've just been told I should try a manage.py <app name> reset too... giving that ago now.

---

### Post by mike_g on 2009-01-11
Does Django not have an installer system? In Joomla (the main CMS I work with) you can have an SQL file with your module. Then, when installing the module through the backend it will execute your queries.

---

### Post by robtotheb on 2009-01-11
the manage.py reset did the trick

/solved.

---

