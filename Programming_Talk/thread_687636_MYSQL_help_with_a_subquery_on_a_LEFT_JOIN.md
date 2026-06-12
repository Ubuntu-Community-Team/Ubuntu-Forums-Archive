---
title: "MYSQL: help with a subquery on a LEFT JOIN"
date: 2008-02-04
forum: Programming Talk
---

### Post by lefen on 2008-02-04
Hi all,

I hope someone will be able to help with this. I'm trying to LIMIT a LEFT JOIN in MYSQL, but it's all gone horribly wrong.

I have two tables, one called 'links' and the other called 'linktags'. 

'linktags' stores tags for URLs in table 'links' and also, the id in table 'links' of said URL.

So the object is to output the URL, with all its associated tags. Here's what I'm using (wrapped in some PHP):

$query = "
SELECT linktags.*, links.* FROM linktags
LEFT JOIN links ON linktags.linkid = links.id
WHERE (links.public='y')
ORDER BY links.id DESC LIMIT 4";
$result = mysql_query($query) or die(mysql_error());

Here, the intent is to limit the output of the query to 4 URLS, but it actually limits the output to 4 tags, like so:

[http://www.ubuntuforums.org](http://www.ubuntuforums.org)
tag: linux
tag: ubuntu
tag: forum

[http://www.linux.com](http://www.linux.com)
tag: linux

I'm sure I'm doing something really stupid, but just can't see it. Also, I have a horrible feeling that I should be doing something clever with subqueries, but I've not had any experience with them and the internet fails to help.

Any ideas? Thanks very much, I know it's a big ask!

---

### Post by aks44 on 2008-02-04
Does this solve your problem?

```
SELECT linktags.*, links.*
FROM linktags
LEFT JOIN (SELECT * FROM links LIMIT 4)
ON linktags.linkid = links.id
WHERE (links.public='y')
ORDER BY links.id
```

---

### Post by lefen on 2008-02-04
Not quite, MYSQL says: "Every derived table must have its own alias" in response to this?

---

### Post by DrMega on 2008-02-04
> **lefen said:**
> Not quite, MYSQL says: "Every derived table must have its own alias" in response to this?

As far as I can see, all aks44 has missed is an alias for the cursor formed by the subquery in the join. Where you have the form:

```

LEFT JOIN (SELECT Something FROM SomethingElse)

```

you need to give it an alias, like this:

```

LEFT JOIN (SELECT Something FROM SomethingElse) SomeAlias

```

---

### Post by lefen on 2008-02-04
Right, I'm not entirely sure that I follow, so you mean the query should be altered to something like this?

```

SELECT linktags.*, links.*
FROM linktags
LEFT JOIN (SELECT * FROM links LIMIT 4) AS selectedLinks
ON linktags.linkid = selectedLinks.id
WHERE (links.public='y')
ORDER BY selectedLinks.id

```

I'm not sure how to go about using the aliases or why they are important?

(also, thanks to both you so for this!)

---

### Post by aks44 on 2008-02-04
> **DrMega said:**
> As far as I can see, all aks44 has missed is an alias for the cursor formed by the subquery in the join. Where you have the form:

Looks like it, thanks for pointing this out.

The new alias name should also be used in the outer query instead of the table name:

```
SELECT linktags.*, lnk.*
FROM linktags
LEFT JOIN (SELECT * FROM links LIMIT 4) AS lnk
ON linktags.linkid = lnk.id
WHERE (lnk.public='y')
ORDER BY lnk.id
```


I hope this is OK now... :)


EDIT: lefen you beat me to it, but I believe the alias name should really replace all occurrences of the table name.
To answer your question, aliasing is needed because without it, the outer query has no way to reference records from the (otherwise anonymous) subquery.

---

### Post by lefen on 2008-02-04
Thank you both, this is just what I needed! :D

---

### Post by bcg30506 on 2009-08-21
What if the subquery select statement in the left join has a condition that compares one of its fields to a field from the "parent" table?  For example:

```

SELECT linktags.*, lnk.*
FROM linktags
LEFT JOIN (SELECT * FROM links WHERE lnk.datefld<=linktags.datefld ORDER BY lnk.datefld DESC LIMIT 1) AS lnk
ON linktags.linkid = lnk.id;

```

When I try something like this MySQL tells me:

```
Unknown column 'linktags.datefld' in 'where clause'
```

The only solution I've been able to find thus far is to use a nested select for each field I want from lnk instead of a left join, like:

```

SELECT linktags.*,
      (SELECT fld1 FROM table2lnk WHERE table2lnk.id=linktags.id AND table2lnk.datefld<=linktags.datefld ORDER BY table2lnk.datefld desc LIMIT 1) as linkedFld
FROM linktags;

```

This appears to work but is highly inefficient the more fields I start needing from the table2lnk table.  Is there a better way using a join or is this just how to do it in MySQL?

---

