---
title: "[Python] &quot;_mysql was already imported&quot; error"
date: 2008-12-03
forum: Programming Talk
---

### Post by unutbu on 2008-12-03
Can you explain what is causing this error?

[PHP]% cat test.py
#!/usr/bin/env python
import MySQLdb
import matplotlib
% test.py
/usr/lib/python2.5/site-packages/pytz/__init__.py:29: UserWarning: Module _mysql was already imported from /var/lib/python-support/python2.5/_mysql.so, but /var/lib/python-support/python2.5 is being added to sys.path
  from pkg_resources import resource_stream
[/PHP]
But if I switch the order of the imports, the error goes away:
[PHP]% cat test.py
#!/usr/bin/env python
import matplotlib
import MySQLdb
% test.py
%
[/PHP]
This is occurring on a fresh Intrepid install. I tried googling
"_mysql was already imported" for an answer, but came up empty.

[PHP]
% apt-cache policy python-matplotlib
python-matplotlib:
  Installed: 0.98.3-4ubuntu1

% apt-cache policy python-mysqldb
python-mysqldb:
  Installed: 1.2.2-7[/PHP]

---

### Post by pp. on 2008-12-04
It would appear that matplotlib imports mySQLdb and that it does it in a manner that a message is issued if mySQLdb already is imported.

If it's an issue, I'd have a look into the initialization of matplotlib, particularly into the method __init__ of the class pytz which is named in the warning message.

---

### Post by unutbu on 2008-12-04
Thanks, pp., but I'm still confused. 

If you have python-mysqldb and python-matplotlib installed,
can you reproduce the same error?

[list]
[*]As far as I can tell, matplotlib does not import _mysql.
For one thing, python-matplotlib does not list mysql as a dependency.
[*]Isn't it true that packages can be imported repeatedly with no adverse consequence? If so, why should pytz throw a UserWarning about this?
[*]/usr/lib/python2.5/site-packages/pytz has to do with timezones.
Is matplotlib or mysqldb importing pytz? I haven't been able to track down where this is happening.
[/list]

Thank you for your time and thought. I'd greatly appreciate any additional help you can give.

---

### Post by pp. on 2008-12-04
Perhaps it would be useful to study this file, particularly line 29:

/usr/lib/python2.5/site-packages/pytz/__init__.py:29

---

### Post by unutbu on 2008-12-04
I managed to make the warning go away by editing /usr/lib/python2.5/site-packages/pkg_resources.py:

I changed line 2272: 

From:[PHP]
            if fn and normalize_path(fn).startswith(loc):[/PHP]

To:[PHP]
            if fn and (fn.startswith(loc) or normalize_path(fn).startswith(loc)):[/PHP]

Thanks for your help, pp.!

---

### Post by pp. on 2008-12-05
> **unutbu said:**
> Thanks for your help, pp.!

You're welcome, but I suggest to read this thread again: All I did was to selectively quote the error message to you which you included in your first post. There's a lesson somewhere hidden.

---

