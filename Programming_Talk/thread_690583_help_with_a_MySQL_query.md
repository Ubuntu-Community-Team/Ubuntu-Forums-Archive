---
title: "help with a MySQL query"
date: 2008-02-07
forum: Programming Talk
---

### Post by bmeyer on 2008-02-07
I'm trying to write a search function in PHP and can't get my SQL statements to work properly.  Here's the situation:

1 table contains posts and another contains comments made on a post.  When a search occurs, I'd like it to search posts.title and comments.text.  Obviously, a post can have more than one comment in the db.  When I do a query like:
```
SELECT posts.id FROM posts, comments WHERE post.title like '%TERM%' OR (comments.post=posts.id AND comments.text like '%TERM%')
```
the problem comes up.  Single posts are returned multiple times, since each has many comments.

Is there a way to return a post's id ONCE if the search term is in the post title or a comment's text?  Some sort of join function?

Thanks in advance for any help!

---

### Post by DrMega on 2008-02-07
Use the FIRST clause:

```

SELECT FIRST 1 field1, field2.... FROM table WHERE condition

```

Or, as you are only interested in the ID field, use DISTINCT

```

SELECT DISTINCT field1FROM table WHERE condition

```

---

### Post by bmeyer on 2008-02-07
Thanks -- I've tried DISTINCT and DISTINCTROW implementations and can't get that to work.  Not sure exactly how to implement the FIRST idea...
It's important to note that the result being returned multiple times isn't resulting from duplication within the database.  It's only because I'm trying to search the post OR the comments at the same time -- multiple successful matches on either cause the single post to be returned several times.

Here's an example query (sight is the "post"):
> SELECT sight.id, sight.title, sight.latitude, sight.longitude, sight.zoom, sight.parent, sight.views, sight.temp, sight.user, sight.date FROM sight, comments WHERE sight.title like '%kingsbury%' OR (comments.sight=sight.id AND comments.text like '%kingsbury%') ORDER BY title ASC LIMIT 0, 10

---

### Post by aks44 on 2008-02-07
Join your two tables together using an INNER JOIN...ON, or leave the FROM clause as it is and add another WHERE condition (AND'ed with your whole current clause).

Either way, both tables should be joined on posts.id and the corresponding field in the comments table.

---

