---
title: "this is about mysql, don't know where else to post this"
date: 2009-10-27
forum: Programming Talk
---

### Post by filifunk on 2009-10-27
first off - I tried posting in the mysql forum and couldn't get it to work, or I don't know how to use it, so I'm trying here?  I guess!  


hey all I've been using mysql for about a week and I'm taking data from a csv file that has historical price data in columns date, open, high, low, close, volume, adj_close.

What I want in the date column are dates like: '2008-08-08' but what I'm getting instead are different years

mysql> SELECT * FROM ko;
+------+-------+-------+-------+-------+----------+-----------+
| date | open  | high  | low   | close | volume   | adj_close |
+------+-------+-------+-------+-------+----------+-----------+
| 1991 | 50.39 | 50.81 | 50.24 | 50.63 |  7906500 | 50.22     | 
| 1992 | 49.94 | 50.79 | 49.72 | 50.41 | 15641800 | 50.00     | 
| 1996 | 49.30 | 50.08 | 49.05 | 49.95 |  7558800 | 49.55     | 
| 1997 | 49.63 | 49.85 | 49.23 | 49.58 | 11289900 | 49.18     | 
| 1998 | 48.55 | 50.30 | 48.55 | 49.80 | 20412000 | 49.40     | 
| 1986 | 55.05 | 55.84 | 54.75 | 55.02 |  7705900 | 52.72     | 
| 1987 | 54.56 | 55.44 | 54.40 | 55.21 |  9518400 | 52.90     | 
| 1988 | 55.19 | 55.82 | 54.12 | 54.79 |  8345400 | 52.50     | 
| 1989 | 55.14 | 55.83 | 54.85 | 55.35 |  7091800 | 53.04     | 
| 1992 | 54.00 | 55.53 | 53.71 | 55.41 |  9829100 | 53.09     | 
+------+-------+-------+-------+-------+----------+-----------+


I tried changing the data type for date to DATE and this is what I get:

| 0000-00-00 | 25.71 | 25.83 | 25.08 | 25.34 | 10316400 | 25.06     | 
| 0000-00-00 | 25.57 | 25.76 | 25.40 | 25.58 |  6782400 | 25.30     | 
| 0000-00-00 | 25.73 | 25.77 | 25.26 | 25.56 | 11061500 | 25.28     | 
| 0000-00-00 | 25.81 | 26.20 | 25.50 | 25.97 | 11882700 | 25.40     | 
| 0000-00-00 | 25.82 | 26.00 | 25.65 | 25.74 | 10982100 | 25.17     | 
| 0000-00-00 | 25.34 | 25.72 | 25.20 | 25.63 | 11278800 | 25.07     | 
| 0000-00-00 | 25.30 | 25.51 | 25.17 | 25.25 | 10227700 | 24.70     | 
| 0000-00-00 | 26.09 | 26.09 | 25.29 | 25.41 | 12740300 | 24.85     | 
| 0000-00-00 | 24.95 | 25.98 | 24.87 | 25.85 | 11606000 | 25.28     | 
| 0000-00-00 | 24.88 | 25.34 | 24.80 | 24.88 | 13226000 | 24.33     | 
| 0000-00-00 | 25.39 | 25.39 | 24.81 | 24.81 | 11823300 | 24.26     | 
| 0000-00-00 | 25.85 | 25.85 | 25.23 | 25.26 |  9899900 | 24.70     | 
| 0000-00-00 | 32.98 | 33.10 | 32.58 | 32.67 | 15029300 | 30.93     | 
| 0000-00-00 | 32.69 | 33.04 | 32.40 | 32.96 | 28541700 | 31.21     | 
| 0000-00-00 | 32.65 | 32.95 | 32.35 | 32.69 | 18943100 | 30.95     | 
| 0000-00-00 | 32.65 | 32.86 | 32.40 | 32.86 | 27973200 | 31.11     | 
| 0000-00-00 | 32.40 | 32.98 | 32.38 | 32.67 | 19334400 | 30.93     | 
| 0000-00-00 | 32.68 | 32.92 | 32.45 | 32.81 | 15715500 | 31.07     | 
| 0000-00-00 | 31.65 | 32.84 | 31.65 | 32.80 | 17296400 | 31.06     | 
+------------+-------+-------+-------+-------+----------+-----------+


here's part of my source code, I'm using python:

```

cursor.execute('CREATE TABLE %s (date TEXT, open VARCHAR(12), high VARCHAR(12), low VARCHAR(12), close VARCHAR(12), volume INT, adj_close VARCHAR(12));' % tick)

for x in data:
    x = x.split(',')
    cursor.execute('INSERT INTO %s (date, open, high, low, close, volume, adj_close) VALUES(%s, %s, %s, %s, %s, %s, %s);' % (tick, x[0], x[1], x[2], x[3], x[4], x[5], x[6]))

```-----------------------------------

Anyone know how I can get the right dates in there?  I realize this might not be the right place to post this, but just winging it!

---

### Post by korvirlol on 2009-10-27
You can use the mysql date or datetime field types and use the built in mysql time() functions.

however, you should consider using the python mktime function and storing the data as an integer (representing the elapsed seconds from *i think* dec 31 1969 to the time generated). Saving it as in integer is very easy to manage.

---

### Post by falconindy on 2009-10-28
If you'd like to keep to the original query, you can use the MAKEDATE() function in sql and insert that as your first field. It accepts a year and a day (1-365).

[Source](http://dev.mysql.com/doc/refman/5.0/en/date-and-time-functions.html#function_makedate).

---

