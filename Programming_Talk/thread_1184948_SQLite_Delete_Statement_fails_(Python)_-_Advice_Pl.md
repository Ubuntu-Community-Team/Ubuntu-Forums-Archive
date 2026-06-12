---
title: "SQLite Delete Statement fails (Python) - Advice Please"
date: 2009-06-11
forum: Programming Talk
---

### Post by greyfox1 on 2009-06-11
Hi All,

I can't figure out what the problem with a delete statement I've written is.  I am working on a simple database manager (it actually started as a response to [LaRoza's BPC #7]("http://ubuntuforums.org/showthread.php?p=5926632") and turned into a bit of a monster as I added more and more functionality once I satisfied the initial requirements).

The program is written in Python and uses a sqlite database.  Nearly everything works as intended (including all the sqlite-related pieces) except a portion where I try to delete a record from the database.

I have a sqlite table called 'main' with an integer primary key called 'id' as well as fields for first name last name, and age.  There is a variable edOrDel which determines whether to update an existing record or delete it.  The update portion of things works as intended (when edOrDel is 'E') but the delete statement fails (when edOrDel is 'D').

Here is the code in question:

```
        if edOrDel=='E':
            cursor.execute('UPDATE main SET FName=?, LName=?, age=? WHERE id=?', (dataFName, dataLName, dataAge, record))
        elif edOrDel=='D':
            cursor.execute('DELETE FROM main WHERE id=?', (record))
        connection.commit()
```

dataFName, dataLName, and dataAge are strings of data entered by the user, and 
 the 'record' variable is an integer that corresponds to the primary key for the database row that I want to delete.

When edOrDel is 'D' and the second bit of code runs, I get this error from the interpreter:

```
  File "BPC7DBOperations.py", line 96, in DBWrite
    cursor.execute('DELETE FROM main WHERE id=?', (record))
**ValueError: parameters are of unsupported type**
```

I can't figure out what I'm doing wrong.  The statement works when I hard-code the record number (WHERE id=1 for example) but I need it to work for any record number needed.  The program checks that the number indicated by the 'record' variable is valid before this piece of code is written.

Any help would be much appreciated!

---

### Post by Can+~ on 2009-06-11
```
cursor.execute('DELETE FROM main WHERE id=?', (record**[COLOR="Red"],[/COLOR]**))
```

If I remember correctly, that forces python to make a tuple out of record.

---

### Post by greyfox1 on 2009-06-11
That did the trick! Thanks for the tip. I've been trying to figure this out for a few days now.

What I'm wondering now is why I didn't need to make a tuple out of record in the first scenario.

---

### Post by Can+~ on 2009-06-11
> **greyfox1 said:**
> That did the trick! Thanks for the tip. I've been trying to figure this out for a few days now.

What I'm wondering now is why I didn't need to make a tuple out of record in the first scenario.

How would python guess that you want to create a tuple?

I mean, if you do "x = (2 + 3)", most people would expect a numeric result (5), having a tuple returned could break everything.

This could get out of control if there were multiple sentences like ((2 + 3) - 5*(7 - 9)), etc..

---

### Post by greyfox1 on 2009-06-11
> **Can+~ said:**
> How would python guess that you want to create a tuple?

Oh come on now, you must know that's not what I meant.  I didn't know *I* needed a tuple.  In both places where I executed a sqlite statement, I was basically saying "perform operation where id is [record]".  

What I was asking was: why doesn't record need to be a tuple in my first statement-- the "update" statement?

*EDIT* I get it: what I didn't realize was that the string of variables in the update statement *is* a tuple.  This was completely by accident on my part.  I was not aware that a tuple was even needed in this case but just happened to be creating one without realizing it.

---

### Post by soltanis on 2009-06-11
> **Can+~ said:**
> How would python guess that you want to create a tuple?

Probably the same way that Perl guesses you want to do anything: heuristics.

---

