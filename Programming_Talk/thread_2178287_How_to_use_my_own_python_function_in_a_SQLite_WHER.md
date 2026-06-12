---
title: "How to use my own python function in a SQLite WHERE clause?"
date: 2013-10-02
forum: Programming Talk
---

### Post by Bao_Niu on 2013-10-02
I've been struggling to get this to work yet not successful, would highly appreciate some advice:
I have my own python module to represent some Chinese calendar dates. I use sqlite3 to persist data. All the dates are converted to string before being stored by sqlite3. Now, I want to query the database with a WHERE caluse, for example:
[COLOR=#0000ff]SELECT * FROM table1 WHERE dates > MyOwnModule.ChineseDate('&#20820;&#24180;&#20843;&#26376;&#21313;&#20116;')[/COLOR]
I got a sqlite operation error.:confused:


How can I ever use my own functions in a SQLite query? If I can't do queries, what's the point of using a database to persist??? Please give me some advice, many many thanks!

---

### Post by oldfred on 2013-10-02
Does SQLite support the Chinese character set, or do you have to turn that on. And it may not be a date function where you can use > ?

This works in one of my queries.
where hist_date = '2011-12-31' and (basis_date > '2011-12-31' or not NULL)

and in another I convert a date 
where  ((strftime('%m', ty.hist_date) = '12' and  strftime('%Y',ty.hist_date) = '2012' )

But I think my queries work as that is the supported date functions.

---

### Post by Bao_Niu on 2013-10-02
> **oldfred said:**
> Does SQLite support the Chinese character set, or do you have to turn that on. And it may not be a date function where you can use > ?

This works in one of my queries.
where hist_date = '2011-12-31' and (basis_date > '2011-12-31' or not NULL)

and in another I convert a date 
where  ((strftime('%m', ty.hist_date) = '12' and  strftime('%Y',ty.hist_date) = '2012' )

But I think my queries work as that is the supported date functions.


Thanks for your reply. I believe it is not Chinese character's problem. I've just ran the program with the Chinese characters replaced by ascii date, and the result was the same. 

No my function is not a date function, it is my own python function written by me. Does it mean I cannot directly use it in a WHERE clause?

---

### Post by Kevin_Arnold on 2013-10-02
> **Bao_Niu said:**
> 
No my function is not a date function, it is my own python function written by me. Does it mean I cannot directly use it in a WHERE clause?

Are you running this inside of a python program/script or trying to query directly?

Running it in python, I'd do something like that:

```

chinese_date = MyOwnModule.ChineseDate('&#20820;&#24180;&#20843;&#26376;&#21313;&#20116;')
your_cursor.execute('SELECT * FROM table1 WHERE dates > ?', chinese_date)

```

---

### Post by oldfred on 2013-10-02
SQLite is not as full featured as some of the full SQL implementations that make it easy to create functions.

I have never tried functions:
[http://webpy.org/cookbook/sqlite-udf](http://webpy.org/cookbook/sqlite-udf)
[http://php.net/manual/en/function.sqlite-create-function.php](http://php.net/manual/en/function.sqlite-create-function.php)

---

### Post by Bao_Niu on 2013-10-02
> **Kevin_Arnold said:**
> Are you running this inside of a python program/script or trying to query directly?

Running it in python, I'd do something like that:

```

chinese_date = MyOwnModule.ChineseDate('&#20820;&#24180;&#20843;&#26376;&#21313;&#20116;')
your_cursor.execute('SELECT * FROM table1 WHERE dates > ?', chinese_date)

```



Thanks Kevin, this is a good thought, however, my situation is a bit stranger here.
"&#20820;&#24180;&#20843;&#26376;&#21313;&#20116;" is actually a recurring date, so I can't just assign its result to a variable like what you did in your example. I have to pass the whole object into the query and let the sql query trigger the comparison between two objects, not two strings or two dates.

Maybe I simply can't do this in sqlite3?

---

### Post by Vaphell on 2013-10-02
SQL is simple and doesn't know the concept of objects.
Could you elaborate what exactly you want to achieve? What do you mean by recurring and what that has to do with dates in db?

---

### Post by Bao_Niu on 2013-10-02
> **Vaphell said:**
> SQL is simple and doesn't know the concept of objects.
Could you elaborate what exactly you want to achieve? What do you mean by recurring and what that has to do with dates in db?


Yes, here is what I'm doing and what I wanted to achieve.
I coded a module that has a ChineseDate class, which automatically parse Chinese dates characters into a python-dateutil object(which actually is a datetime.datetime object as well).
I used [COLOR=#333333][FONT=monospace]detect_types[/FONT][/COLOR][COLOR=#666666][FONT=monospace]=[/FONT][/COLOR][COLOR=#333333][FONT=monospace]sqlite3[/FONT][/COLOR][COLOR=#666666][FONT=monospace].[/FONT][/COLOR][COLOR=#333333][FONT=monospace]PARSE_DECLTYPES [FONT=century gothic][SIZE=2]to tell the connection object to store this ChineseDate type directly into one column in my schema. When inserted into that column, the python ChineseDate object will be automatically adapted into a complex string, containing the first occuring date and the interval, etc. Now I want to select all the records with their MyDate column later than a certain &#20820;&#24180;&#20843;&#26376;&#21313;&#20116;, so I built this query:
[/SIZE][/FONT][/FONT][/COLOR][COLOR=#0000ff][FONT=monospace][FONT=century gothic][SIZE=2]SELECT * FROM myTable WHERE MyDate > MyModule.ChineseDate("&#20820;&#24180;&#20843;&#26376;&#21313;&#20116;")[/SIZE][/FONT][/FONT][/COLOR][COLOR=#333333][FONT=monospace][FONT=century gothic][SIZE=2]
This comparison is legal in the pure Python context because both sides are a ChineseDate instance. But for some reason I got an sqlite3.operationalError from running it.
Am I in the wrong path to achieve my goal? Thank you very much.[/SIZE][/FONT][/FONT][/COLOR]

---

### Post by oldfred on 2013-10-02
I am sure it is against Codd's rules, but could you not have another column with SQLite date as well as Chinese date? It seems your function is converting back & forth already?

---

### Post by Bao_Niu on 2013-10-02
> **oldfred said:**
> I am sure it is against Codd's rules, but could you not have another column with SQLite date as well as Chinese date? It seems your function is converting back & forth already?

Yes I can, it is only the start of my project so I can easily refactor my code base at this phase. But I'm more interested in the question of "**is this kind of in-place comparison of two native python objects supported in sqlite3 WHERE clause**"?
Or it is not supported at all. WHERE A >= B, A and B must be BOTH dates or integers or strings ONLY and no other custom types?

I'm really eager to hear some pro's advice on this. Thanks a lot!

---

### Post by Vaphell on 2013-10-02
no pro but being curious i searched in the internet and i haven't seen a simple example of such a thing.

i'd look into registering a function via sqlite3.Connection.create_function()

[http://docs.python.org/2/library/sqlite3.html#connection-objects](http://docs.python.org/2/library/sqlite3.html#connection-objects)
> create_function(name, num_params, func)

    Creates a user-defined function that you can later use from within SQL statements under the function name name. num_params is the number of parameters the function accepts, and func is a Python callable that is called as the SQL function.

    The function can return any of the types supported by SQLite: unicode, str, int, long, float, buffer and None.

    Example:
```

    import sqlite3
    import md5

    def md5sum(t):
        return md5.md5(t).hexdigest()

    con = sqlite3.connect(":memory:")
    con.create_function("md5", 1, md5sum)
    cur = con.cursor()
    cur.execute("select md5(?)", ("foo",))
    print cur.fetchone()[0]
```

---

### Post by ofnuts on 2013-10-03
Your design hardly makes sense. A date is a date (some instant in time) whether it's Chinese or French or Sudanese. DB systems all have a built-in date/time type (where date/time is typically represented internally as seconds from the epoch (1970-01-01, 00:00 UTC)), and a good design uses these,  while application-level functions converts between the external representation(*) and the DB ones where necessary. DB systems typically provide convenient date/time related functions that can be used in queries. 

You can decide to shun these principles but then you have to deal with the consequences, such as wondering if SQLite can be coerced into executing some Python code (or Perl or Haskell or Scheme or, $deity forbids, Visual Basic).

Unless your "Chinese date" is just a random character string and store as such in the DB, but then you cannot expect the DB system to do anything special with it.


(*) and in a good design this external representation only occurs when humans have to be taken in account: display in web page, print out, entry fields (when you cannot afford calendar.clock widget).

---

### Post by theDaveTheRave on 2013-10-03
hi,

I agree with ofnuts on this.

SQLite probably doens't have a 'chinese' representation of dates as a native type, from memory they are numeric.

You should deal with the conversion of dates between chinese / numeric on your user interface (most likely)

However, if you have created a 'python object' you probably want to implement a 'dateComparison' method so as python can determine if  2 'date' values are equal or different.
dateComparison(object1, object2)
return 0 : if dates are the same
return -1: is object1 value is less than object2 (ie is before)
return 1: if obect1 value is greater than object2 (ie object one is after)

Then your code would be able to function by calling the 'dateComparison' function of each python object stored in the DB column (you would also then be able to sort ascending / descending as a by product of the same method.

May be a little more complex to set up, but should work out.

David

---

### Post by Bao_Niu on 2013-10-03
> **ofnuts said:**
> Your design hardly makes sense. A date is a date (some instant in time) whether it's Chinese or French or Sudanese. DB systems all have a built-in date/time type (where date/time is typically represented internally as seconds from the epoch (1970-01-01, 00:00 UTC)), and a good design uses these,  while application-level functions converts between the external representation(*) and the DB ones where necessary. DB systems typically provide convenient date/time related functions that can be used in queries. 

You can decide to shun these principles but then you have to deal with the consequences, such as wondering if SQLite can be coerced into executing some Python code (or Perl or Haskell or Scheme or, $deity forbids, Visual Basic).

Unless your "Chinese date" is just a random character string and store as such in the DB, but then you cannot expect the DB system to do anything special with it.


(*) and in a good design this external representation only occurs when humans have to be taken in account: display in web page, print out, entry fields (when you cannot afford calendar.clock widget).

Hi ofnuts thank you for this detailed explanation. It is this kind of post that benefits our beginners the most. I appreciate the time you put into it.
I totally agree that SQLite is already more than enough for storing internal representation of any date(time), as float. And the philosophy of separating internal representation and external representation also makes perfect sense to me. I've got a follow-up question here: how can I conveniently store time points with **different granularity** (e.g. 2011, 2011-11, 2011-11-21 11:21:31, etcs) into one single column? There is no way to do this without using my own custom type design. Chinese character is just a superficial obstacle. I think this different granularity is the core of the problem(and there is more, such as recurring time point and timezones). Don't you agree?
I really thank you for going this deep with my topic, ofnuts.

---

### Post by Bao_Niu on 2013-10-03
> **theDaveTheRave said:**
> hi,

I agree with ofnuts on this.

SQLite probably doens't have a 'chinese' representation of dates as a native type, from memory they are numeric.

You should deal with the conversion of dates between chinese / numeric on your user interface (most likely)

However, if you have created a 'python object' you probably want to implement a 'dateComparison' method so as python can determine if  2 'date' values are equal or different.
dateComparison(object1, object2)
return 0 : if dates are the same
return -1: is object1 value is less than object2 (ie is before)
return 1: if obect1 value is greater than object2 (ie object one is after)

Then your code would be able to function by calling the 'dateComparison' function of each python object stored in the DB column (you would also then be able to sort ascending / descending as a by product of the same method.

May be a little more complex to set up, but should work out.

David

Hi David, thank you too. I've already written python special methods for my class, those for comparisons, such as __gt__, __lt__, etc. But I can't invoke them in my SQL query. So their use is very very limited. As far as I know after a good research, you can only compare values that are of SQLite native types, such as string, integers. For your own objects stored in a column, you cannot compare their values in a SELECT...WHERE query, even when you defined your own comparison functions.

---

### Post by Vaphell on 2013-10-03
what do you need these different date formats for exactly? Why do you store them all in a single column? what is your query supposed to return and why? I know you mentioned it briefly but you didn't explain exactly what is the supposed interaction between the input and dates in all these formats. Some example showcasing the problem would be nice.

---

### Post by ofnuts on 2013-10-03
> **Bao_Niu said:**
> Hi ofnuts thank you for this detailed explanation. It is this kind of post that benefits our beginners the most. I appreciate the time you put into it.
I totally agree that SQLite is already more than enough for storing internal representation of any date(time), as float. And the philosophy of separating internal representation and external representation also makes perfect sense to me. I've got a follow-up question here: how can I conveniently store time points with **different granularity** (e.g. 2011, 2011-11, 2011-11-21 11:21:31, etc (*)) into one single column? There is no way to do this without using my own custom type design. Chinese character is just a superficial obstacle. I think this different granularity is the core of the problem(and there is more, such as recurring time point and timezones). Don't you agree?
I really thank you for going this deep with my topic, ofnuts.
2011 or 2011-11 or 2011-11-11 aren't time ***points*** but time ***spans*** (between two time ***points***: 2011-01-01 00:00:00 inclusive to 2012-01-01 00:00:00 exclusive for the first), and you'll need two columns to store that (either as two time points or as a start point and a duration). Of course nothing prevents you from storing a strange string that combines both in one column, but before you do so, read [this book]("http://www.amazon.com/SQL-Anti-Patterns-Chinese-Edition-Mei/dp/711526127X/") and then reconsider :)

(*) The convention to store things with "start inclusive; end exclusive" is pervasive in the IT industry because it has plenty of nice properties. Your users may want a different representation (end inclusive, often) but this is  a matter of input and display (like human-readable dates).

---

### Post by Bao_Niu on 2013-10-04
> **ofnuts said:**
> 2011 or 2011-11 or 2011-11-11 aren't time ***points*** but time ***spans*** (between two time ***points***: 2011-01-01 00:00:00 inclusive to 2012-01-01 00:00:00 exclusive for the first), and you'll need two columns to store that (either as two time points or as a start point and a duration). Of course nothing prevents you from storing a strange string that combines both in one column, but before you do so, read [this book]("http://www.amazon.com/SQL-Anti-Patterns-Chinese-Edition-Mei/dp/711526127X/") and then reconsider :)

(*) The convention to store things with "start inclusive; end exclusive" is pervasive in the IT industry because it has plenty of nice properties. Your users may want a different representation (end inclusive, often) but this is  a matter of input and display (like human-readable dates).


Thanks for the explanation, and the books. I learn very much from your post. I really love Ubuntu Forums, it's so newbie-friendly!:D

---

### Post by theDaveTheRave on 2013-10-08
just another link that may be of interest from the python site

[custom python types]("http://docs.python.org/2/library/sqlite3.html#converting-sqlite-values-to-custom-python-types") .

A quick read suggests you could store your complete python [COLOR="#DAA520"]chinese date object[/COLOR], this object could contain the required function to convert to / from a numeric value.

Your user interface will still need to catch this object, but at least you will have the conversion in the object that you store in the DB, so it should be a little easier.

The alternative is you could store a key and value (again the same object with with 2 interdependent members) in the field, the key being the chinese characters, and the value being the actual numeric value, then the extraction of the object can give you both values, and the sorting can be one on the numeric one only.

Of course you will still have to handle the conversion of the chinese characters into numerics within the interface, or have a customised SQLite function to do the conversion.

Anyway just another thought into the mix.

David

---

### Post by theDaveTheRave on 2013-10-24
> **Bao_Niu said:**
>  store time points with **different granularity** (e.g. 2011, 2011-11, 2011-11-21 11:21:31, etcs) into one single column?

Just re-read this comment... and my thought is that you don't store different granularity, you store at the finest you require (probably down to hours and minutes).

Then in your interface you extract only the portion that the user demands, give them the option of extraction to year / month / date ... etc.

I've not looked at the python API, but I'm sure that there is a fairly generic timestamp API that will allow you to extract only the portion that you need such as 
```

getYear()

```
or similar.

Then depending on the user option for the granularity to collect the time with the required API calls.

Of course you are going to need to convert to chinese characters. Not knowing chinese, I don't know if there are 'constant' characters for each month / year (knowing that there are 13 years in the chinese 'animal' year chart this could be quite complex ???)

Maybe it is an interestingly complex problem and you could write it into a howto ? I personally would be interested in how you perform the conversion.

Maybe you could attach a code sample (or full API for python)?

David

---

