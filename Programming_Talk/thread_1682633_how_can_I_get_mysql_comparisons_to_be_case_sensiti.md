---
title: "how can I get mysql comparisons to be case sensitive?"
date: 2011-02-06
forum: Programming Talk
---

### Post by guest_user on 2011-02-06
Using the C API,
I have a VARCHAR column as my primary key in 2 of my tables and when I try to insert "TEST" and subsequently "Test", the second insertion fails. How can I programmatically make it such that same text with differing cases are treated uniquely?

I'm using prepared statements for the insertion, deletion and update if that means anything...

---

### Post by gmargo on 2011-02-06
From the MySQL reference manual, on "Identifier Case Sensitivity"
[http://dev.mysql.com/doc/refman/5.0/en/identifier-case-sensitivity.html](http://dev.mysql.com/doc/refman/5.0/en/identifier-case-sensitivity.html)
> 
Column, index, and stored routine names are not case sensitive         on any platform, nor are column aliases. 


Ahh... now that I read it again, you're talking about the data itself, not column names, are you not?

---

### Post by [Snc] on 2011-02-06
HM ... try to fetch results as lowercase or cast them as lowercase, then lowercase the thing you want to check against and check ...

---

### Post by gmargo on 2011-02-06
Googling about, I found this is a common problem.  All the solutions I've seen give a method to retrieve the data (using BINARY in the WHERE clause); no one seems to address the insertion problem.

I did find one bit in the MySQL manual, that says you can force binary comparison by changing the column data type delcaration to include BINARY, which presumably would fix the primary key issue:
[http://dev.mysql.com/doc/refman/5.0/en/charset-binary-op.html](http://dev.mysql.com/doc/refman/5.0/en/charset-binary-op.html)

---

### Post by [Snc] on 2011-02-06
> **gmargo said:**
> Googling about, I found this is a common problem.  All the solutions I've seen give a method to retrieve the data (using BINARY in the WHERE clause); no one seems to address the insertion problem.

I did find one bit in the MySQL manual, that says you can force binary comparison by changing the column data type delcaration to include BINARY, which presumably would fix the primary key issue:
[http://dev.mysql.com/doc/refman/5.0/en/charset-binary-op.html](http://dev.mysql.com/doc/refman/5.0/en/charset-binary-op.html)

If the colation is set to utf8_bin (that would translate into UTF8 binary ... doh :)), then the data is binary

Test != TEST
TEST = TEST

---

