---
title: "[PYTHON] Frustrated with string escaping, please help!"
date: 2007-06-15
forum: Programming Talk
---

### Post by Laterix on 2007-06-15
Ok, I've been fighting with this for a while now I find it impossible to add string with **'** to SQLite database.

I have a simple code that uses pysqlite:
```

db_conn = sqlite.connect("test.db")
db_cur = db_conn.cursor()
db_cur.execute("UPDATE test_table SET field_1='%s' WHERE field_2='%s'" % (data, condition))
db_conn.commit()
db_conn.close()

```

Now, if data is a string:
```

It's nice to program with python!

```
It fails to update it. It seems to be, because of **'** char. Without that everything works. Now I've tried to escape that char away with
```

data.replace('\'','\\\'')

```
But it stll fails...

Any ideas? Is there a better way to do escaping for SQL strings?

---

### Post by slightcrazed on 2007-06-15
Can you triple quote it? 

Usually if I have a string with multiple quotes or apostrophes in it I will triple quote it, like:

'''This is a ' test ' of triple apostrophes'''

""" this is a "test" of triple quotes"""

When python sees a triple quote it continues reading the string until it hits another triple quote. This may work.

---

### Post by Laterix on 2007-06-15
> **slightcrazed said:**
> Can you triple quote it? 

Thanks for reply,

I think I can't because I get this string as a return value of library method call.

---

### Post by pmasiar on 2007-06-15
library returns a string which contains single quotes? 

Can it contain also double quotes? or never?

---

### Post by slightcrazed on 2007-06-15
> **Laterix said:**
> Thanks for reply,

I think I can't because I get this string as a return value of library method call.


Actually, now that I look at the issue again, I think you need 2 modifications. It's actually the SQL that's getting messed up, and not python. Have you tried:


db_cur.execute('''UPDATE test_table SET field_1="%s" WHERE field_2="%s"''' % (data, condition))

I 'triple apostrophe' the UPDATE statement and then use quotes for the %s. This way, when you pass it a single quote it won't prematurely end the statement. 

Worth a shot.

---

### Post by Laterix on 2007-06-15
> **slightcrazed said:**
> 
I 'triple apostrophe' the UPDATE statement and then use quotes for the %s. This way, when you pass it a single quote it won't prematurely end the statement. 

Thank you! This seems to work just fine... Excellent!

---

### Post by steve.horsley on 2007-06-17
What you shouodl be doing is parsing the input string and escaping that. If you did so, the "It's" would be converted to "it\'s" which causes the SQL interpreter to correctly treat the \' as a single quote and not as the end of the SQL statement. You could of course do this by doing:
inputString.replace("'", "\'")
but there are other characters that should be escaped too, and I can't remember which now. The database library should provide you with an escape function that does this input string preparation for you.

---

### Post by Laterix on 2007-06-18
> **steve.horsley said:**
> What you shouodl be doing is parsing the input string and escaping that. If you did so, the "It's" would be converted to "it\'s" which causes the SQL interpreter to correctly treat the \' as a single quote and not as the end of the SQL statement. You could of course do this by doing:
inputString.replace("'", "\'")

I'm well aware of that. But the problem was how to do it, because the line you gave doesn't work. That was the first thing that I tried.

> 
but there are other characters that should be escaped too, and I can't remember which now. The database library should provide you with an escape function that does this input string preparation for you.
I'm in impression that **pysqlite** includes class **Cursor** whitch **execute()** method should do this kind of escapeing automatically when I query database. But for some reason, it didn't work for me. Maybe I missunderstood something there.

---

### Post by steve.horsley on 2007-06-18
In MySQL, MySQLdb.connect() returns a Connection object that has an excape_string() method that does the escaping for you. It seems that Cursor.execute(string) expects the string to be already escaped. My geuss is that they all work the same way but I'd have to check the python database docs to be sure. 

And I just realised that you need to esacpe the backspace in the command I gave you, so it should be:
inputString.replace("'", "\\'")
but of course you really should use the library function.

---

### Post by winch on 2007-06-18
> **Laterix said:**
> I'm in impression that **pysqlite** includes class **Cursor** whitch **execute()** method should do this kind of escapeing automatically when I query database. But for some reason, it didn't work for me. Maybe I missunderstood something there.

```
db_cur.execute("UPDATE test_table SET field_1='%s' WHERE field_2='%s'" % (data, condition))
```

It can't escape automatically because you are just passing it a query string. If you want it to escape automatically you need to pass it a parameterized SQL statement and the parameters.

Something like this.

```
db_cur.execute("UPDATE test_table SET field_1=? WHERE field_2=?", data, condition)
```

Since the sql and parameters are now separate it's possible for the library to take care of escaping.

---

### Post by Laterix on 2007-06-18
> **steve.horsley said:**
> In MySQL, MySQLdb.connect() returns a Connection object that has an excape_string() method that does the escaping for you.

And I just realised that you need to esacpe the backspace in the command I gave you, so it should be:
inputString.replace("'", "\\'")
but of course you really should use the library function.
in pysqlite library there is no escaping method in Connection class. And that codeline doesn't work either. Believe me, I have tested all possible and impossible lines. :) But you are right, I should do this with library functions...
```

>>> s = "It's nice to have an example"
>>> s.replace("'", "\\'")
"It\\'s nice to have an example"
>>> s.replace("'", "\'")
"It's nice to have an example"
>>> s.replace("'", "\\\'")
"It\\'s nice to have an example"

```

> 
Since the sql and parameters are now separate it's possible for the library to take care of escaping.

Ok thanks, I have to test this one.

---

### Post by arbinobjerg on 2010-02-05
Thanks for posting this. It really helped me solved my headaches. Just so simple. How I love Python. Thanks again.

---

