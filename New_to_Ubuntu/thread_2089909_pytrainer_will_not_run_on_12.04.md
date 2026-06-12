---
title: "pytrainer will not run on 12.04"
date: 2012-11-30
forum: New to Ubuntu
---

### Post by digitography on 2012-11-30
I have recently upgraded from 11.04 to 12.04 (via 11.10).
Now pytrainer will not run.
I have tried uninstalling, with a command line purge, and then reinstalling from the sourceforge download.

Still no joy.

any ideas please

---

### Post by digitography on 2012-12-02
If I run from terminal this is what I get
----------------------
running pytrainer from egg installation
data_path: /usr/local/share/pytrainer/
gettext_path: /usr/local/share/locale
site_path: /usr/local/lib/python2.7/site-packages
Traceback (most recent call last):
  File "/usr/local/bin/pytrainer", line 96, in <module>
    from pytrainer.main import pyTrainer
  File "/usr/local/lib/python2.7/dist-packages/pytrainer/main.py", line 36, in <module>
    from upgrade.data import initialize_data
  File "/usr/local/lib/python2.7/dist-packages/pytrainer/upgrade/data.py", line 23, in <module>
    from pytrainer.upgrade.migratedb import MigratableDb
  File "/usr/local/lib/python2.7/dist-packages/pytrainer/upgrade/migratedb.py", line 19, in <module>
    from migrate.versioning.api import db_version, upgrade, version, version_control
ImportError: No module named migrate.versioning.api
--------------------------

Thanks

---

### Post by Bashing-om on 2012-12-02
digitography; Hi !

Version 1.9.1-2 of pytrainer is available in the ubuntu software repositories (12.04 version).
If That works for you, purge the current install and (re)install from the system package manager.

[INDENT][INDENT]just try'n to help <== BDQ

[/INDENT][/INDENT]

---

### Post by digitography on 2012-12-02
Thanks for the information, I tried uninstalling via a purge and then reinstalling.

It is definitely version 1.9.1-2, but it still fails to start correctly.

---

### Post by Bashing-om on 2012-12-02
Isn't the sourceforge install via a ppa? ..if so will have to be (un)installed via a ppa-purge; then I suggest you (re)install via USC.

[INDENT][INDENT]hth <== BDQ

[/INDENT][/INDENT]

---

### Post by digitography on 2012-12-03
Sorry to sound dumb, but what is USC?

---

### Post by BlinkinCat on 2012-12-03
> **digitography said:**
> Sorry to sound dumb, but what is USC?
  
Hi,

Ubuntu Software Center  -  :P

---

### Post by digitography on 2012-12-03
Thanks, I was thinking too deep, University of Southern California is what came to my mind DOH! :-)

I think I may have got the syntax for purge wrong, I'll try it again when I get home later.

---

