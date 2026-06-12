---
title: "MySQL frontends (PHP?)"
date: 2008-06-10
forum: Programming Talk
---

### Post by wutti on 2008-06-10
I am trying to come up with a "thin" client for the MySQL database for update data and generating reports. It will be running in an office environment with Linux/Windows users.

I've searched around but the only thing I can think of is a custom PHP application. Any other suggestions?

Is there a ubuntu equivalent of a MySQL PHP generator like [http://www.sqlmaestro.com/products/mysql/phpgenerator](http://www.sqlmaestro.com/products/mysql/phpgenerator)


Thanks!

---

### Post by pmasiar on 2008-06-10
Python with Django will generate update screens for you to maintain databases, all you need to do are reports - and ORM will map tables to objects, so that is easy too. you don't even need to understand any SQL.

Not mentioning that Python is cleaner and more universal language (use it laso as bash replacement), and Django follows much cleaner Model-view-controller design pattern (see wikipedia for why is it good)

---

