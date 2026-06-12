---
title: "MySQLdb and Python - problem with adding values to table"
date: 2012-12-18
forum: Programming Talk
---

### Post by kpuz on 2012-12-18
I have a scraper that I need to configure to push data into a mysql database table. I have already created a table and a non-root user that has access to it. Here is the test script:
```
import MySQLdb

db=MySQLdb.connect(host="localhost",user="scraper",passwd="getrich",db="mlsto")
cur=db.cursor()
date="2055-01-19"
listings=66
cur.execute("INSERT INTO housedates (date,listings) VALUES(%s,%s)", (date,listings))
sql="SELECT * FROM housedates"
cur.execute(sql)
results=cur.fetchall()
cur.close()
print results
```

the output of this script is:
```
((datetime.date(2012, 12, 12), 23), (datetime.date(2012, 12, 12), 23), (datetime.date(2055, 1, 19), 66))
```

The first two rows were placed in the table by me using the mysql command line, the third row is added by python. 

When I list out all the rows of this table using command-line, I don't see the row added by python. What gives? I'm not sure how to go about troubleshooting this. Any tips?

---

### Post by spjackson on 2012-12-18
It looks like your transaction is being rolled back by the DBMS. Add an explicit commit and/or disconnect from the database cleanly before exiting your program.

---

### Post by kpuz on 2012-12-18
> **spjackson said:**
> It looks like your transaction is being rolled back by the DBMS. Add an explicit commit and/or disconnect from the database cleanly before exiting your program.

Thanks. Adding db.commit() fixed the problem.

---

