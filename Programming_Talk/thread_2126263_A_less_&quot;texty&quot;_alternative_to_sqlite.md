---
title: "A less &quot;texty&quot; alternative to sqlite?"
date: 2013-03-16
forum: Programming Talk
---

### Post by TheHimself on 2013-03-16
I've been reading sqlite documentation and examples and two things caught my attention.

1-It seems that sqlite gives any entry in the database to you as a string, even if its a number. I say this because the callback function receives an array of strings. This looks a little bit inconvenient.

2-I would like it more if I had specific database functions at hand instead of having to express everything in a text based format (i.e. the SQL language). This for example makes debugging the program easier; if your SQL is wrong, you'd see that only at run time and not at compile time.

So, first, am I misunderstanding Sqlite? and if not, is there any alternative database library that may suite my taste better?

---

### Post by r-senior on 2013-03-16
You didn't mention a programming language but all the bindings for SQLite are similar. These are the functions from the C library for retrieving the value of a column after issuing a query. As you can see, many of them return values other than strings:

```
const [COLOR="#FF0000"]void *[/COLOR]sqlite3_column_blob(sqlite3_stmt*, int iCol);
[COLOR="#FF0000"]int[/COLOR] sqlite3_column_bytes(sqlite3_stmt*, int iCol);
[COLOR="#FF0000"]int[/COLOR] sqlite3_column_bytes16(sqlite3_stmt*, int iCol);
[COLOR="#FF0000"]double[/COLOR] sqlite3_column_double(sqlite3_stmt*, int iCol);
[COLOR="#FF0000"]int[/COLOR] sqlite3_column_int(sqlite3_stmt*, int iCol);
[COLOR="#FF0000"]sqlite3_int64[/COLOR] sqlite3_column_int64(sqlite3_stmt*, int iCol);
const unsigned char *sqlite3_column_text(sqlite3_stmt*, int iCol);
const void *sqlite3_column_text16(sqlite3_stmt*, int iCol);
[COLOR="#FF0000"]int[/COLOR] sqlite3_column_type(sqlite3_stmt*, int iCol);
sqlite3_value *sqlite3_column_value(sqlite3_stmt*, int iCol);
```

Why did you think the SQLite libraries could only return strings? Are you looking at a different API?

You are quite correct that when issuing SQL to a database via a library, you won't find out if your SQL is wrong until you run the code. That's true of most relational database access libraries in my experience. SQL is still the standard way of accessing relational databases. There are frameworks that allow you to work with objects rather than databases but the choice of those would depend on the programming language and target systems. Even then, although the SQL is generated, you don't always get complete validation against the database at compile time.

It would probably help to provide an idea of the amount and complexity of data you are thinking of, and also your programming language and expected target systems.

---

### Post by prodigy_ on 2013-03-16
1. SQLite has several datatypes and you can perform numeric comparisons for integer/real types: [http://www.sqlite.org/datatype3.html](http://www.sqlite.org/datatype3.html)

2. What's the point of working with a DB if you don't want to use SQL at all? Nobody forces you to use it for data processing though.

---

### Post by ofnuts on 2013-03-16
> **TheHimself said:**
>  if your SQL is wrong, you'd see that only at run time and not at compile time.

When you do DB development, you test your SQL queries (for correct results, but also for performance) against a DB outside of any code, so when they are added to the rest of the code (as hard-coded string constants or as some text file) they can be assumed to be correct. What you debug is how your code fills the parameters to these queries and what it does with the results.

And when you go beyond the basic SELECT or UPDATE, you find that API calls just wouldn't cut it... SQL has about the same status in application code as the notation for regular expressions...

---

### Post by TheHimself on 2013-03-17
Thank you guys and specially r-senior. I didn't know about those functions. The sqlite documentation on its website is pretty terse. 
I'm using C and want database support for storing and retrieving file data and metadata. So the columns would be file name and path, modification date, tags, rating, etc. 
Actually what I want to do is to write an open source alternative for Mendeley desktop (for organizing scientific papers). I have some experience with C and GTK but have not used databases before.

---

### Post by r-senior on 2013-03-17
As this is a Gnome/GTK application, you should make yourself aware of GDA: [https://developer.gnome.org/libgda/stable/index.html](https://developer.gnome.org/libgda/stable/index.html).

I've never tried it, but the main benefits I'm aware of are increased portability and some widgets for use with GTK:

[https://developer.gnome.org/libgda/stable/ch22.html](https://developer.gnome.org/libgda/stable/ch22.html)

It could be that the grid control in itself is worth the pain of learning GDA -- but if you thought the SQLite documentation was terse ... ;)

---

### Post by TheHimself on 2013-03-18
Thanks a lot. It has some useful features.

---

