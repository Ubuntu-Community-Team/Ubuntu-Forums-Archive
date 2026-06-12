---
title: "Need help with from textfile to a SQL database"
date: 2014-01-23
forum: Programming Talk
---

### Post by cazz on 2014-01-23
Hi
I have two question I hope someone can help me with

Question 1)
I have now a script that look like this

```
echo "scale=2; `curl  --progress-bar -w "%{speed_download}" http://addresssomething.com -o /dev/null` / 131072" | bc | xargs -I {} echo {} >> loggen.txt
```

It save a value to a textfile name "loggen.txt"

But now I like to have that in a variable so I can put that inside a SQL database but I don't know what to do to make it work?
I did try to remove echo and add > variabel = before but that was not right.


Question 2)
What is the best SQL database for me to use.
It is going to save two variabel every 15 min for sometime and I don't know if MySQL is a little overkill for that?
I also going to have a PHP page that can read the SQL database and show the result.

---

### Post by justleen on 2014-01-23
The output of that command is send to a text file.. You can't just replace the echo and expect it to end up in your DB.

You can either run a sql interface from that script and send it to the database, or have log to the loggen.txt in a SQL understandable format.

something like this..
```

var=$("scale=2; `curl  --progress-bar -w "%{speed_download}" http://addresssomething.com -o /dev/null` / 131072" | bc | xargs -I {} echo {})
echo "INSERT INTO db  VALUES ${var}" |  mysql -uUSER -pPASSWORD DBNAME;

```
Basicly, I get the value into a variable "var", then use echo to send it as a query to the db (pipe it to mysql)

What DB to use is little harder to answer.. You might want to try SQLlite if you think MySQL is over kill..

---

### Post by justleen on 2014-01-23
The output of that command is send to a text file.. You can't just replace the echo and expect it to end up in your DB.

You can either run a sql interface from that script and send it to the database, or have log to the loggen.txt in a SQL understandable format.

something like this..
```

var=$("scale=2; `curl  --progress-bar -w "%{speed_download}" http://addresssomething.com -o /dev/null` / 131072" | bc | xargs -I {} echo {})
echo "INSERT INTO db  VALUES ${var}" |  mysql -uUSER -pPASSWORD DBNAME;

```
Basicly, I get the value into a variable "var", then use echo to send it as a query to the db (pipe it to mysql)

What DB to use is little harder to answer.. You might want to try SQLlite if you think MySQL is over kill..

---

