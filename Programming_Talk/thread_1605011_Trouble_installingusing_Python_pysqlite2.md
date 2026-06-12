---
title: "Trouble installing/using Python pysqlite2"
date: 2010-10-24
forum: Programming Talk
---

### Post by cheetaux on 2010-10-24
Hi,
I am having trouble installing/using Python psyqlite2.

I installed as follows:

```
$ sudo apt-get install python-psyqlite2 libsqlite3-dev
```

But when I try testing as follows:

```
$ python -c "from pysqlite2 import test;test.test()"

```

I get the following error:

```
Traceback (most recent call last):
  File "<string>", line 1, in <module>
ImportError: No module named psqylite2
```

I have Python 2.6.6 installed.

---

### Post by oldfred on 2010-10-24
I use this:

import sqlite3

Is there some reason to use sqlite2, not sure what it was back then?

---

### Post by cheetaux on 2010-10-25
I am trying to get rdiffWeb (a web interface for browsing and restoring from rdiff-backup repositories).  rdiffWeb is written in Python and the instructions I was listing came directly from their installation instructions ([www.rdiffweb.org](www.rdiffweb.org)).

---

### Post by oldfred on 2010-10-25
It shows rdiffweb was last updated in 2008, so you will have some issues.

---

### Post by cheetaux on 2010-10-25
Hmmm.  I just read about rdiff-backup and rdiffWeb in a article in the October 2010 issue of LinuxJournal and thought I would give it a try.

rdiffWeb should work just fine with Python 2.6.6.  Just because rdiffWeb has not been updated since 2008, why should that be a problem?

---

