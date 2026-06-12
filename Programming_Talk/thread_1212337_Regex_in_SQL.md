---
title: "Regex in SQL"
date: 2009-07-13
forum: Programming Talk
---

### Post by prem1er on 2009-07-13
I have been looking around on google for an example of this, but haven't found much or even know if it is possible. But I am trying to query some records for ids that end in non-numeric characters.  Is it possible to use regex for this?

---

### Post by Can+~ on 2009-07-13
[http://www.w3schools.com/SQl/sql_like.asp](http://www.w3schools.com/SQl/sql_like.asp)
[http://www.w3schools.com/SQl/sql_wildcards.asp](http://www.w3schools.com/SQl/sql_wildcards.asp)

It's not as feature complete as other regular expression implementation though. If you have any trouble, post what you want to match against.

---

### Post by jpkotta on 2009-07-13
I am most definitely not a database expert.  I wrote my first SQL query about a month ago.  But MySQL has regex queries - at least the installation I'm using does.  Much better than LIKE.
```
SELECT * FROM `table` WHERE field REGEXP "^foobar[0-9]*$"
```

---

### Post by prem1er on 2009-07-14
> **jpkotta said:**
> I am most definitely not a database expert.  I wrote my first SQL query about a month ago.  But MySQL has regex queries - at least the installation I'm using does.  Much better than LIKE.
```
SELECT * FROM `table` WHERE field REGEXP "^foobar[0-9]*$"
```

Thanks for the replies. I guess my version of SQL doesn't support the REGEXP operator, because it doesn't recognize it as a key word.  I am trying right now to use [this]("http://www.w3schools.com/SQl/sql_wildcards.asp") link to write what I want.  What I need is a query that returns results that the last three characters in the string contain non-numeric characters.

```
21903839027502PMM
23048023840823HTM
203840238408230

Would return 

21903839027502PMM
23048023840823HTM
```

---

### Post by prem1er on 2009-07-14
I guess my question would be, how do I define an entire character set to match?  Something like this doesn't seem to be working.

```
select CD_ACCT_NO_C, CD_SHORT_ACCT_C, CD_SRC_ACCT_C from data where CD_ACCT_NO_C like '%[A-Z][A-Z][A-Z]'
```

---

