---
title: "sqlite3 “OperationalError: unable to open database file” in python only when I deploy"
date: 2015-02-17
forum: Programming Talk
---

### Post by shaansweb on 2015-02-17
Please help. I've been stuck on this issue for three days nw and I think I'm about to go mad.

I made an app in flask that uses an sqlite3 database. **The app works flawlessly when I run it using Flask's internal testing server.** However, when I attempt to deploy my app, either using apache2 or gunicorn+nginx, and the logs of whatever server I'm using shows the python exception "OperationalError: unable to open database file".


Here is the full file that's causing the error:


    import sqlite3
    
    __all__ = ['Database']
    
    class Database(object):
    
        def __init__(self, name):
            self._name = name
        
        def _execute(self, command, args=None):
            connection = sqlite3.connect(self._name)
            cursor = connection.cursor()
    
            if args is None:
                out = cursor.execute(command).fetchall()
            else:
                out = cursor.execute(command, args).fetchall()
            
            connection.commit()
            connection.close()
            return out


The `connection = sqlite3.connect(self._name)` is the line that is actually triggering the error and I have no clue why. I have tried replacing `self._name` with a hard coded string to the path of the database to no avail. I have also made sure the database file has proper read write permissions.


Does anyone know how I can figure out what's going on?

---

### Post by ofnuts on 2015-02-18
I would look for strange characters in filenames (dump the name used to file, open with hex editor and check that all characters have plain ASCII codes); Also are you using a relative or absolute path?

---

### Post by The Cog on 2015-02-18
Permissions: 
Make sure that the file is accessible to the user account that flask is running under. This is probably not the account that you used during manual testing.

Filename: 
Use an absolute path (not relative) to eliminate the possibility that you are running in an unexpected current working director. 
Check for odd characters and correct upper/lower case.

---

### Post by anant4 on 2015-08-28
Hi, I'm stuck with the same problem.
Did you find a solution for this?

---

