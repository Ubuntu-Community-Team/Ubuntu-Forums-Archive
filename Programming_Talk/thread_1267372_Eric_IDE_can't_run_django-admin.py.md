---
title: "Eric IDE can't run django-admin.py"
date: 2009-09-15
forum: Programming Talk
---

### Post by Ivar Ragnarsson on 2009-09-15
Hi 
I just installed Kubuntu and wanted to use Eric IDE to work with Django.
Every time I try to start a Django project (through the Django plugin)  in Eric I get the error:
"The process django-admin.py could not be started. Ensure, that it is in the search path."

I've tried adding "/var/lib/python-support/python2.6/django/bin" to PATH and PYTHONPATH  but that did not change anything.

Can anyone tell me what I'm missing here?

Thanks, 
          Ivar

---

### Post by durand on 2009-09-15
Your best option is to post on the django mailing list.

[http://groups.google.com/group/django-users?pli=1](http://groups.google.com/group/django-users?pli=1)

You could also try the programming forum on ubuntu forums. I'll ask a mod to move this thread.

---

### Post by Michael.Godawski on 2009-09-15
Moved to PT.

---

### Post by Ivar Ragnarsson on 2009-10-25
Problem solved.
Name of "django-admin.py" was changed to "django-admin" in /usr/bin directory in the python-django package.
To get around this I just created a symbolic link to django-admin named django-admin.py.
ln -s /usr/bin/django-admin /usr/bin/django-admin.py    (as root)

---

### Post by vhenry on 2009-12-15
Thanks, I was having the same problem. Simlink worked.

---

