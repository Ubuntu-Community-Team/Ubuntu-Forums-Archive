---
title: "Howto download part of a mysql DB?"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by kramer65 on 2008-05-06
Hello,

This is maybe not the right place to ask but I though I'll just give it a try.

I rented some (shared) hosting somewhere and now I want to give a part of my mysql db to somebody as kind of a sample. The database is quite large (400+ mb) so I want to export the DB including *some* data, say the first 1000 records.

Is this possible in any way?

---

### Post by Monicker on 2008-05-06
How many tables are you talking about in the database? For a single table, you could export the schema, and then use "select into outfile" for a portion of the records.

---

### Post by JudasReanimated on 2008-05-06
You should be able to export your database, but as for splitting it I'm not sure exactly, you may want to just look through the exporting options on that one.

---

### Post by kramer65 on 2008-05-06
I'm talking about some 10 tables. So that is not really possible.

How can you do this "select into outfile" for a portion of the records? Is this possible in phpmyadmin?

---

### Post by Monicker on 2008-05-06
I haven't used phpmyadmin in a while, but it should be doable there.  I usally use the mysql query browser or the cli.

```

SELECT * INTO OUTFILE '/dir/file.txt'
  FIELDS TERMINATED BY ','
  LINES TERMINATED BY '\n'
  FROM mytable LIMIT 1000;
```


That will give you a comma delimited file containing 1000 records from a table.

---

