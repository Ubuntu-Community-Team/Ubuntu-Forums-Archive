---
title: "I/O error"
date: 2013-08-21
forum: Programming Talk
---

### Post by wingnut2626 on 2013-08-21
here is my code :

```
dbfilename = 'people-file'
ENDDB = 'enddb.'
ENDREC = 'endrec.'
RECSEP = '=>'

def storeDbase(db, dbfilename=dbfilename):
    [B]dbfile = open(dbfilename, 'w')
    for key in db:
        print(key, file=dbfile)[/B]
        for(name,value) in db[key].items():
            print(name + RECSEP + repr(value), file=dbfile)
        print(ENDREC, file=dbfile)
        dbfile.close()
```

When I try to run this snippet of code I get the traceback that there is an I/O error : Trying to write to closed file????!?!?!?!  The lines in bold show where the file is opened, and the last line of bold is where the exception is generated.  Any ideas?

---

### Post by spjackson on 2013-08-21
dbfile.close() is inside the outer for loop. You want it outside that loop. Decrease the indentation on that line so that it matches the open statement.

---

### Post by r-senior on 2013-08-21
In addition, you might also want to look at the "with" statement in Python, which automatically closes a file after a block ends.

---

