---
title: "graphite on 11.10"
date: 2012-03-29
forum: Programming Talk
---

### Post by mohanradhakrishnan on 2012-03-29
Hi,
          I have tried to install graphite based on [http://geek.michaelgrace.org/2011/09/how-to-install-graphite-on-ubuntu/](http://geek.michaelgrace.org/2011/09/how-to-install-graphite-on-ubuntu/).
 
[COLOR=#000000][LEFT][FONT=Bitstream Vera Sans Mono]Completed everything before 'sudo python manage.py syncdb' when I got this error.[/FONT][/LEFT][/COLOR]
[COLOR=#000000][LEFT][FONT=Bitstream Vera Sans Mono]Can anyone advice ? [/FONT][/LEFT][/COLOR]
[COLOR=#000000][LEFT][FONT=Bitstream Vera Sans Mono][/FONT][/LEFT][/COLOR] 
[COLOR=#000000][LEFT][FONT=Bitstream Vera Sans Mono]One think I noticed was the multiple versions of python but typing 'python' brings up only 2.7[/FONT][/LEFT][/COLOR]
[COLOR=#000000][LEFT][FONT=Bitstream Vera Sans Mono][/FONT][/LEFT][/COLOR] 
 
Thanks,
Mohan
 
----------------------------------------------------------------------------------------
Traceback (most recent call last):
  File "manage.py", line 11, in <module>
    execute_manager(settings)
  File "/usr/lib/pymodules/python2.7/django/core/management/__init__.py", line 438, in execute_manager
    utility.execute()
  File "/usr/lib/pymodules/python2.7/django/core/management/__init__.py", line 379, in execute
    self.fetch_command(subcommand).run_from_argv(self.argv)
  File "/usr/lib/pymodules/python2.7/django/core/management/base.py", line 191, in run_from_argv
    self.execute(*args, **options.__dict__)
  File "/usr/lib/pymodules/python2.7/django/core/management/base.py", line 220, in execute
    output = self.handle(*args, **options)
  File "/usr/lib/pymodules/python2.7/django/core/management/base.py", line 351, in handle
    return self.handle_noargs(**options)
  File "/usr/lib/pymodules/python2.7/django/core/management/commands/syncdb.py", line 56, in handle_noargs
    cursor = connection.cursor()
  File "/usr/lib/pymodules/python2.7/django/db/backends/__init__.py", line 252, in cursor
    cursor = util.CursorWrapper(self._cursor(), self)
  File "/usr/lib/pymodules/python2.7/django/db/backends/sqlite3/base.py", line 207, in _cursor
    self.connection = Database.connect(**kwargs)
pysqlite2.dbapi2.OperationalError: unable to open database file
 
----------------------------------------------------------------------------------------

---

### Post by CynicRus on 2012-03-29
similar problem with a lack of permission.

---

### Post by mohanradhakrishnan on 2012-03-30
> **CynicRus said:**
> similar problem with a lack of permission.
 
Folder permissions ? I have tried to allow full permissions in many graphite folders.
 
I don't work with python. Just wanted to use graphite.
 
Which sqllite db file is it ?
>  OperationalError:unabletoopendatabasefile>OperationalError: unable to open database file
 
Besides the obvious reason of missing **read** permissions on the file, it can also happen when the server process has already opened too many files and is unable to open new ones due to O/S limitations. 


---

