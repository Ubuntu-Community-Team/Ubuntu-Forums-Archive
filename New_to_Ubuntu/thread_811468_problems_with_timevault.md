---
title: "problems with timevault"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by benji.ijneb on 2008-05-29
i really love timevault, it's an excelent project and, in my opinion, far better than the likes of flyback.

however, every time i try to open the preferences dialogue, the 'opening administrative application' thing comes up on the menu thing (the.... start menu) and then disappears, and nothing happens.

when i try to run /usr/bin/timevault-config from the terminal, i get the following error message:

> Traceback (most recent call last):
  File "./timevault-config", line 31, in <module>
    configgui.MainDlg().Show()
  File "/usr/lib/python2.5/site-packages/TimeVault/configgui.py", line 241, in Show
    self.CheckDBVersion()
  File "/usr/lib/python2.5/site-packages/TimeVault/configgui.py", line 235, in CheckDBVersion
    if not db.Open():
  File "/usr/lib/python2.5/site-packages/TimeVault/database.py", line 107, in Open
    self.Create(0)
  File "/usr/lib/python2.5/site-packages/TimeVault/database.py", line 78, in Create
    result.Exec(sql)
  File "/usr/lib/python2.5/site-packages/TimeVault/database.py", line 42, in Exec
    self.cursor.execute(*args)
pysqlite2.dbapi2.OperationalError: database is locked

also, occasionally when i try to open the preferences dialogue, it gives me a message saying that the database neeeds to be upgraded from v0 to v5.

this is really annoying, and i need help! all help is appreciated, thans very much...

---

### Post by irrdev on 2008-05-29
I'm not a TimeVault user myself, but there are two things you can try. First try to run this command as root, since the sqlite database is probably locked due to insufficient file access permissions.
> sudo /usr/bin/timevault-config
If that doesn't work, then I would completely uninstall/reinstall TimeVault and its dependencies.

---

### Post by benji.ijneb on 2008-05-29
> **irrdev said:**
> I'm not a TimeVault user myself, but there are two things you can try. First try to run this command as root, since the sqlite database is probably locked due to insufficient file access permissions.

If that doesn't work, then I would completely uninstall/reinstall TimeVault and its dependencies.

thanks! that worked once, and the second time i tried, we were back to the same old bug.... damn.

also, i've tried reinstalling it many times, each time with the same result...

---

### Post by benji.ijneb on 2008-05-29
something new...

each time i close the snapshot browser, all my backed up files disappear. and it refuses to run a basic backup of everything. hurumph.

---

### Post by andraycho on 2008-06-19
I'm having same problem. I also have noticed that sbackup config is not opening as well. Could this be a Python problem?

---

