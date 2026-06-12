---
title: "pysqlite &quot;unsupported file format&quot;"
date: 2006-11-23
forum: Programming Talk
---

### Post by pedrotuga on 2006-11-23
Can anybody tell me why da heck does this code throws this error?

```
from pysqlite2 import dbapi2 as sqlite

con = sqlite.connect("news")

# Get a Cursor object that operates in the context of Connection con:
cur = con.cursor()

# Execute the SELECT statement:
cur.execute("select * from feed")

# Retrieve all rows as a sequence and print that sequence:
print cur.fetchall() 
```

i have a sqlite database in the** news** file with is in the same directory of the script.
What is the damn problem?

---

