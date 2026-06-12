---
title: "Help with shell script"
date: 2009-11-27
forum: Programming Talk
---

### Post by Spikerok on 2009-11-27
Target to make script which will create mysql user.
I have mysql commands
[PHP]
mysql -u userName -p

insert into db (host, db, user, select_priv) values ('localhost', 'customers', 'kayon', 'Y');
[/PHP]

Im not sure how to combine it in to shell script. 
Please help..

---

### Post by korvirlol on 2009-11-27
you could put it into a .sql file and do something like:

```
mysql -u username -ppassword databasename < script.sql
```

note the spacing on the password switch

---

### Post by carl.davis on 2009-11-27
You should also be able to do the following:

```
mysql -u userName -ppassword -e 'insert into tablename (host, db, user, select_priv) values ('localhost', 'customers', 'kayon', 'Y')' databasename
```

---

### Post by Spikerok on 2009-11-27
can't believe that it's so simple...
Is their any thing alse I should include?

---

### Post by korvirlol on 2009-11-27
It would be better to handle database scripts with a python or php script... but that way works fine too

---

### Post by Spikerok on 2009-11-27
I will be using PHP to give values to shell script.
User will enter data in browser which will transferred to script.
Script will start and complete given task.

---

### Post by carl.davis on 2009-11-28
> **Spikerok said:**
> I will be using PHP to give values to shell script.
User will enter data in browser which will transferred to script.
Script will start and complete given task.

There is no reason to do it that way. PHP can do those things directly without having to call a shell script. Just search for "PHP MySQL" and you will find lots of great tutorials with simple examples.

---

