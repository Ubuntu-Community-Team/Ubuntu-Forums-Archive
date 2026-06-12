---
title: "sql aggregate functions"
date: 2013-06-29
forum: Programming Talk
---

### Post by Xender1 on 2013-06-29
I am having trouble when it comes to writing queries that involve aggregate functions (such as Count and also when using Having). I have two tables of People (id and name) and Books (bookid, author_id, title) (here author_id is a foreign key to People id). 
I currently have a query that returns to me all the People who have written a book (not all the people have written a book).
```
SELECT People.name, Books.title FROM People, Books WHERE Books.author_id = People.id;
```
Now I am trying to find only People who have written more than 2 books and have it select the same info (people.name and books.title), but I am confused as to how I would go about this. I have been trying to use a HAVING count(People.name) > 1 but the selection I get is definitely not correct. 

Sort of new to using sql especially when it comes to putting these extra parameters on my queries and was just wondering if anyone could help me out. I have not really seen any examples of queries with these conditions.

---

### Post by Bodsda on 2013-06-30
The trick to SQL is knowing what it actually returns before writing a 2 or more part query. Try running SELECT COUNT(*) against your tables with certain where clauses and see how it changes, then look at using the GROUP BY clause to filter your results.

This site has some really nice examples with some decent explanations
[http://www.techonthenet.com/sql/count.php](http://www.techonthenet.com/sql/count.php)

HTH,
Bodsda

---

### Post by r-senior on 2013-06-30
> **Xender1 said:**
> Now I am trying to find only People who have written more than 2 books and have it select the same info (people.name and books.title)
There are two steps here, as your sentence implies:

1. Find people who have written more than two books
2. Show the books written by those people

You'll find it easier to do the first part on its own, then learn to do the second part using the first.

Hints:

1. This is a group by and having query. Just aim to list the names of authors with more than two books.
2. Correlated subquery

---

### Post by Xender1 on 2013-06-30
Ahh yes thank you for the tips and that link as well.
```

SELECT Books.author_id
FROM Books
GROUP BY Books.author_id
HAVING COUNT(*)>=2

```
This got me the people who have written 2 or more books and then to get all the data out I used an inner join with a where and put this select in the where area.

---

### Post by Xender1 on 2013-06-30
Another quick question that might have an answer. In my Book table I also have a Date field (yyyy-dd-mm), is there anyway to return that in years it has been published? So for example one may be 2000-6-30, it would return 13.0? Trying to keep 1 decimal point in there.

Solved. Used Round with Datediff.

---

