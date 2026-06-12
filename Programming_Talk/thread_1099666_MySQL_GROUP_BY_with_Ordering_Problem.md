---
title: "MySQL GROUP BY with Ordering Problem"
date: 2009-03-18
forum: Programming Talk
---

### Post by mike_g on 2009-03-18
I'm modifying a gallery component. This query gets a list of last commented pictures. It shows a duplicate image thumbails for each comment and I want to only display each image once with the most recent comment. 

So, I added the GROUP BY bit, but this does not always show the most recent comment, just one of the comments. The image ordering however is correct, as in it orders the pictures by when they were last commented, just the last comment for it shows up wrong. Can I fix this in SQL? If so how?

Cheers.

```
"SELECT a.*,cc.*, ca.*,u.username ".
"FROM #__joomgallery AS a, #__joomgallery_catg AS ca, #__joomgallery_comments AS cc ".
"LEFT JOIN #__users AS u on cc.userid = u.id ".
"WHERE a.id=cc.cmtpic AND a.catid=ca.cid AND a.published = '1' " . " AND a.approved='1' " . " AND cc.published = '1' " . " AND ca.published = '1' " . " AND cc.approved='1' " . " AND ca.access<=$gid ".
[COLOR=RED]"GROUP BY cc.cmtpic ".[/COLOR]
"ORDER BY cc.cmtdate DESC LIMIT $jg_toplist OFFSET $offset";
```

---

### Post by unutbu on 2009-03-18
If you must solve this problem with an SQL query, I believe the way to do so is to adapt this solution to your situation:

[http://dev.mysql.com/doc/refman/5.0/en/example-maximum-column-group-row.html](http://dev.mysql.com/doc/refman/5.0/en/example-maximum-column-group-row.html)

If you can store the latest comments in a data structure in program, you might be able to get much faster results than doing such a query.

---

