---
title: "Php SQL INSERT INTO WHERE NOT EXISTS"
date: 2009-04-06
forum: Programming Talk
---

### Post by xRes on 2009-04-06
Please can someone help me with an issue I am having with the INSERT INTO WHERE NOT EXISTS Function. Here is my code so far:

```
$query = ("INSERT INTO document_association2 (name) VALUES ('$groupname') WHERE NOT EXISTS (document_association2.name = '$groupname'");
$result = mysql_query($query)
or die("error: ".
mysql_error());
```

I am wishing to insert a new row into document_association2 but only if if an item in the column 'name' is not already existing.

Thank you

---

### Post by Phristen on 2009-04-06
Make a unique index on clumn name, and

INSERT IGNORE INTO document_association2 (name) VALUES ('$groupname')

---

### Post by xRes on 2009-04-07
How do you mean unique index, that option only appears valid on the unique id (int) column I have set up within MySQL?

I have been given another possible option as shown below:

```
$query = ("INSERT INTO document_association2 (name) VALUES ('$groupname') WHERE NOT EXISTS (SELECT * FROM document_association2 WHERE document_association2.name = '$groupname'");
$result = mysql_query($query)
or die("error: ".
mysql_error());
```

I'm struggling with this part of my project so if there are there anyother means that I could use that will help me simply **search** the 'name' column, **determine** if the name has already been entered, then **add OR update** the row depending on the result, I would be most appreciative. Thanks in advance

---

### Post by Phristen on 2009-04-08
[s]$query = ("INSERT INTO document_association2 (name) VALUES ('$groupname') WHERE NOT EXISTS (SELECT * FROM document_association2 WHERE document_association2.name = '$groupname'");[/s]
NO

> here are there anyother means that I could use that will help me simply search the 'name' column, determine if the name has already been entered, then add OR update the row depending on the result, I would be most appreciative.
[ON DUPLICATE KEY UPDATE]("http://dev.mysql.com/doc/refman/5.0/en/insert-on-duplicate.html")
But you still need to add a unique index on the name column.
ALTER TABLE document_association2 ADD UNIQUE INDEX (`name`)

---

### Post by soltanis on 2009-04-08
> **xRes said:**
> 
I'm struggling with this part of my project so if there are there anyother means that I could use that will help me simply **search** the 'name' column, **determine** if the name has already been entered, then **add OR update** the row depending on the result, I would be most appreciative. Thanks in advance

```

UPDATE document_association2 SET name='$groupname' WHERE name = NULL;

```

? I think I misunderstand your intent, if you want to put a name in a row where the name wasn't defined, that would be how you do it.

---

