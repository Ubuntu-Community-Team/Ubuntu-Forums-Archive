---
title: "How to I factor SQL code?  What's equiv of subroutine in SQL?"
date: 2007-06-16
forum: Programming Talk
---

### Post by SNYP40A1 on 2007-06-16
I tried creating a view like this:

CREATE VIEW view_name AS
SELECT columns
FROM table
WHERE predicates;

However, assuming that this works:

SELECT columns
FROM table
WHERE predicates

I get an error when I append the ';' to the end of the query and prepend the first line of CREATE VIEW...invalid character was the error.  So view does not seem to be working for me.  Is there another way to alias this part:

SELECT columns
FROM table
WHERE predicates

as a variable?  I effectively want to do something like this:

SELECT columns
FROM table
WHERE predicates
AS myQuery

and whenever I place "myQuery", the SQL interpreter just does a dumb macro-like substation.  This may sound trivial, but I reason that if I write the same code twice, then I have 2x the probability of messing something up.

---

