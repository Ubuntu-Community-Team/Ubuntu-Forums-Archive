---
title: "[SOLVED] exaile not running"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by danmeetswood on 2008-09-24
Hey, exaile's not running.
```
dan@dennis:~$ exaile
Traceback (most recent call last):
  File "exaile.py", line 2634, in <module>
    main()
  File "exaile.py", line 2626, in main
    exaile = ExaileWindow(options, fr)
  File "exaile.py", line 125, in __init__
    self.database_connect()
  File "exaile.py", line 1091, in database_connect
    self.db = self.get_database()
  File "exaile.py", line 1078, in get_database
    database = db.DBManager(loc)
  File "/usr/share/exaile/xl/db.py", line 75, in __init__
    cur.execute("PRAGMA auto_vacuum=1")
OperationalError: database is locked

```
The only thing I can think of is running the program as root a few minutes ago, but all I did was play some music. Is there anything I can do to fix this short of reinstalling and losing my playlists?

---

### Post by lazyart on 2008-09-24
Delete the .exaile folder from your home directory.
Use Control-H in Nautilus so that you can see the folder (the . in front means it's hidden).

This I found by googling "exaile locked database".  If you ran as root you might have to take ownership first:```
sudo chown danmeestwood /home/danmeetswood/.exaile -R
```changing both instances of danmeetswood to your actual user name.

---

### Post by danmeetswood on 2008-09-24
Well, that did unlock it for sure. But now all the settings and playlists are gone. Oh well, spilled milk. Thanks for the reply, dog.

---

### Post by johnvile on 2010-01-31
you only need to delete "music.db" and "music.db-journal" although I'm not sure what "music.db-journal" is or if it realy needs to go.
Deleating "music.db" may be all thats required.
Delaete "music.db" first and see if that works.

---

