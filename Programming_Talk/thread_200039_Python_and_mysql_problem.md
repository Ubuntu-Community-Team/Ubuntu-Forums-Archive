---
title: "Python and mysql problem"
date: 2006-06-19
forum: Programming Talk
---

### Post by kthakore on 2006-06-19
I can't seem to use the mysqldb connection with python, I do have the python-mysqldb installed, but I still can't use the function to connect to databases.

this is the error I get
```
db= MySQLdb.connect(host='localhost', user='@#@#' , passwd='#$@#@', db='@#@@');
Traceback (most recent call last):
  File "<input>", line 1, in ?
NameError: name 'MySQLdb' is not defined
```

---

### Post by vasdee on 2006-06-19
have you imported the MySQLdb module?
put this somewhere before that line:

```
import MySQLdb
```

---

### Post by kthakore on 2006-06-19
I did try import but it made the cursor a plus sign, and i didn't know what to do. After that it still didn't work.

---

### Post by vasdee on 2006-06-20
i don't quite follow, lets just make sure we are on the same base here:
open a terminal and type 'python'
```
>>>import MySQLdb
```
if that doesn't throw an error then type:
```
>>>db= MySQLdb.connect(host='localhost', user='#@#@',passwd='@#@#@',db='#@#@')
```
That *should* be all you need to do to connect to mysql,  post any errors back here if not.

---

### Post by kthakore on 2006-06-20
Hey thanks a lot buddy, i love you!!!! YOU ARE THE MAN!!! ......:D ..... It worked, I don't know what I was doing before but it works. Thank you man!
........ can i ask two more questions? When I get results from a table and i print them by ```
>>>print Results
``` I have a field that is a ID feild that is auto incremented, and it is just numbers. Python returns these numbers with an L after it, how Do I fix this?

---

### Post by vasdee on 2006-06-20
glad i could help, its not often i can on these forums :) 

try the following, it should merely print out the all the autoincremented field values hopefully. If that gets rid of the mysterious L then maybe do it that way.

```
>>>import MySQLdb
>>>db= MySQLdb.connect(host='localhost', user='#@#@',passwd='@#@#@',db='#@#@')
>>>cursor = db.cursor()
>>>cursor.execute("SELECT <autoincremented field> FROM WHATEVER")
>>>result = cursor.fetchall()
>>>for record in result:
>>>    print record[0]
```

It may just be an issue with printing out the entire result set via  'print Result'

---

### Post by kthakore on 2006-06-21
thanks man that work perfect. and I am glad I could give u an oppurtuinity to answer on these forums

---

### Post by foxylad on 2006-06-21
The "L" denotes a long integer is returned, and only shows up in the python console. If you print it it will show as just a number.

---

