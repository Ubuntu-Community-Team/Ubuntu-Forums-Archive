---
title: "Django sqlite database not working"
date: 2010-11-09
forum: Programming Talk
---

### Post by Crazedpsyc on 2010-11-09
I just started trying to use django with the tutorial on their website. everything was fine until I came to the "python manage.py syncdb" command and got ```
Traceback (most recent call last):
  File "manage.py", line 11, in <module>
    execute_manager(settings)
  File "/usr/lib/pymodules/python2.6/django/core/management/__init__.py", line 438, in execute_manager
    utility.execute()
  File "/usr/lib/pymodules/python2.6/django/core/management/__init__.py", line 379, in execute
    self.fetch_command(subcommand).run_from_argv(self.argv)
  File "/usr/lib/pymodules/python2.6/django/core/management/base.py", line 191, in run_from_argv
    self.execute(*args, **options.__dict__)
  File "/usr/lib/pymodules/python2.6/django/core/management/base.py", line 220, in execute
    output = self.handle(*args, **options)
  File "/usr/lib/pymodules/python2.6/django/core/management/base.py", line 351, in handle
    return self.handle_noargs(**options)
  File "/usr/lib/pymodules/python2.6/django/core/management/commands/syncdb.py", line 52, in handle_noargs
    cursor = connection.cursor()
  File "/usr/lib/pymodules/python2.6/django/db/backends/__init__.py", line 75, in cursor
    cursor = self._cursor()
  File "/usr/lib/pymodules/python2.6/django/db/backends/sqlite3/base.py", line 174, in _cursor
    self.connection = Database.connect(**kwargs)
pysqlite2.dbapi2.OperationalError: unable to open database file

```
I got the same thing when trying to add the "polls" app to the database and when I ran "Poll.objects.all()" in the interactive interpreter. Why am I getting all this? I have python-sqlite installed.

---

### Post by naoyamakino on 2010-11-10
I am having the exact same issue when I am going through the tutorial on django's website. 
would very appreciate for any suggestions!

---

### Post by naoyamakino on 2010-11-10
solved it! my settings.py's database path was wrong..
make sure yours is all good too.


> **Crazedpsyc said:**
> I just started trying to use django with the tutorial on their website. everything was fine until I came to the "python manage.py syncdb" command and got ```
Traceback (most recent call last):
  File "manage.py", line 11, in <module>
    execute_manager(settings)
  File "/usr/lib/pymodules/python2.6/django/core/management/__init__.py", line 438, in execute_manager
    utility.execute()
  File "/usr/lib/pymodules/python2.6/django/core/management/__init__.py", line 379, in execute
    self.fetch_command(subcommand).run_from_argv(self.argv)
  File "/usr/lib/pymodules/python2.6/django/core/management/base.py", line 191, in run_from_argv
    self.execute(*args, **options.__dict__)
  File "/usr/lib/pymodules/python2.6/django/core/management/base.py", line 220, in execute
    output = self.handle(*args, **options)
  File "/usr/lib/pymodules/python2.6/django/core/management/base.py", line 351, in handle
    return self.handle_noargs(**options)
  File "/usr/lib/pymodules/python2.6/django/core/management/commands/syncdb.py", line 52, in handle_noargs
    cursor = connection.cursor()
  File "/usr/lib/pymodules/python2.6/django/db/backends/__init__.py", line 75, in cursor
    cursor = self._cursor()
  File "/usr/lib/pymodules/python2.6/django/db/backends/sqlite3/base.py", line 174, in _cursor
    self.connection = Database.connect(**kwargs)
pysqlite2.dbapi2.OperationalError: unable to open database file

```
I got the same thing when trying to add the "polls" app to the database and when I ran "Poll.objects.all()" in the interactive interpreter. Why am I getting all this? I have python-sqlite installed.

---

### Post by Crazedpsyc on 2010-11-10
Thanks! I had pybin instead of pysrv in the database path

---

### Post by JMatlack on 2011-02-20
Can you help me by explaining where the database file should go and why? I dont know what path to put in settings.py for ubuntu. On windows I can use 
]import os
 PROJECT_ROOT = os.path.abspath(os.path.dirname(__file__))
 
 
 
my settings.py database name= os.path.join(PROJECT_ROOT, 'cms.db')
 
 
for saome reason it tells me that file is undefined
    This is the traceback I get
> josh@optimus-prime:~/django-projects/mysite$ python manage.py syncdb
Traceback (most recent call last):
  File "manage.py", line 11, in <module>
    execute_manager(settings)
  File "/usr/local/lib/python2.5/site-packages/django/core/management/__init__.py", line 362, in execute_manager
    utility.execute()
  File "/usr/local/lib/python2.5/site-packages/django/core/management/__init__.py", line 303, in execute
    self.fetch_command(subcommand).run_from_argv(self.argv)
  File "/usr/local/lib/python2.5/site-packages/django/core/management/base.py", line 195, in run_from_argv
    self.execute(*args, **options.__dict__)
  File "/usr/local/lib/python2.5/site-packages/django/core/management/base.py", line 221, in execute
    self.validate()
  File "/usr/local/lib/python2.5/site-packages/django/core/management/base.py", line 249, in validate
    num_errors = get_validation_errors(s, app)
  File "/usr/local/lib/python2.5/site-packages/django/core/management/validation.py", line 22, in get_validation_errors
    from django.db import models, connection
  File "/usr/local/lib/python2.5/site-packages/django/db/__init__.py", line 41, in <module>
    backend = load_backend(settings.DATABASE_ENGINE)
  File "/usr/local/lib/python2.5/site-packages/django/db/__init__.py", line 17, in load_backend
    return import_module('.base', 'django.db.backends.%s' % backend_name)
  File "/usr/local/lib/python2.5/site-packages/django/utils/importlib.py", line 35, in import_module
    __import__(name)
  File "/usr/local/lib/python2.5/site-packages/django/db/backends/sqlite3/base.py", line 32, in <module>
    raise ImproperlyConfigured, "Error loading %s: %s" % (module, exc)
django.core.exceptions.ImproperlyConfigured: Error loading either pysqlite2 or sqlite3 modules (tried in that order): No module named _sqlite3
josh@optimus-prime:~/django-projects/mysite$ 
 
grateful for any help thanks

---

### Post by Crazedpsyc on 2011-03-04
The database path can be anything. Mine is /home/me/django/db.sqlite.  Just put the path in the settings.py file and run "python manage.py  syncdb". Then it will automatically create the database and set up the  admin superuser (if admin is installed) and you're ready to go.
Perhaps you should try a static path? Maybe /home/you/project/cms.db?
EDIT: Oh, see at the bottom of the error message it says "No module  named _sqlite3"? open up the python shell and try importing sqlite3. If  it gives you a similar importerror you may need to install  python-sqlite3. If there is no error, it could be a problem with that  underscore, I'm not sure. Here is the DB part of my settings file for  reference:
```
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3', # Add 'postgresql_psycopg2', 'postgresql', 'mysql', 'sqlite3' or 'oracle'.
        'NAME': '/home/me/django/db.sqlite',                      # Or path to database file if using sqlite3.
        'USER': '',                      # Not used with sqlite3.
        'PASSWORD': '',                  # Not used with sqlite3.
        'HOST': '',                      # Set to empty string for localhost. Not used with sqlite3.
        'PORT': '',                      # Set to empty string for default. Not used with sqlite3.
    }
}

```
You would get answers quicker if you created your own thread vs. posting on a solved one :wink:

---

