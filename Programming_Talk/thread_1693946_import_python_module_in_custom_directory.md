---
title: "import python module in custom directory"
date: 2011-02-23
forum: Programming Talk
---

### Post by tgm4883 on 2011-02-23
I've created a little python application that uses sqlite3. I need this to run a variety of systems, so I've got to have compatibility with Python 2.3. From the looks of it, I need to have pysqlite2 compiled for 32-bit and 64-bit as well as python 2.3 and 2.4, so I'll need a total of 4 builds.

I've already compiled it for each of those scenarios and I've placed it in my applications dir. It appears that dashes aren't allowed in the import statement for python, so I had to get a little creative with my folder naming.

```
program.py
modules/__init__.py
modules/pysqlite2i686p24/__init__.py
modules/pysqlite2i686p24/dbapi2.py
modules/pysqlite2i686p24/dump.py
modules/pysqlite2i686p24/_sqlite.so
```

In my program.py, I have 

```
import modules.pysqlite2i686p24.dbapi2 as sqlite3
```

The issue appears to be that in dbapi2.py it has

```
from pysqlite2._sqlite import *
```

so every time I run I get the error

```
ImportError: No module named pysqlite2._sqlite
```


I can fix this as long as the folder containing pysqlite2 is named pysqlite2, but thats going to create (IMO) somewhat of an overengineered tree of directories. Is there an easier way to resolve this issue?

---

### Post by LemursDontExist on 2011-02-23
You could force a mapping between 'pysqlite2' and 'modules.pysqlite2i686p24':
```

import sys
import modules.pysqlite2i686p24
sys.modules['pysqlite2'] = sys.modules[modules.pysqlite2i686p24.__name__]
import pysqlite2.dbapi2 as sqlite3

```

The sys.modules dictionary maintains a mapping between names and loaded modules, so this might be a way to do what you want.  I suspect there might be an even more elegant solution based on restructuring things a little but this ought to work if you want to keep the directory structure flat.

---

### Post by MadCow108 on 2011-02-23
you could also change the PYTHONPATH depending on the version:
```

import sys
if sys.version_info[1] == 3:
  sys.path.append("somepath")
else:
  sys.path.append("someotherpath")

```

---

### Post by tgm4883 on 2011-02-23
> **LemursDontExist said:**
> You could force a mapping between 'pysqlite2' and 'modules.pysqlite2i686p24':
```

import sys
import modules.pysqlite2i686p24
sys.modules['pysqlite2'] = sys.modules[modules.pysqlite2i686p24.__name__]
import pysqlite2.dbapi2 as sqlite3

```

The sys.modules dictionary maintains a mapping between names and loaded modules, so this might be a way to do what you want.  I suspect there might be an even more elegant solution based on restructuring things a little but this ought to work if you want to keep the directory structure flat.

That works great. Thanks!

---

