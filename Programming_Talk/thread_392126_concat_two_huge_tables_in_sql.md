---
title: "concat two huge tables in sql"
date: 2007-03-24
forum: Programming Talk
---

### Post by monkeyking on 2007-03-24
I have two gigantic tables in mysql.

They share the first column, it's like the identifier, and it is primary.

So I want to take all the columns from one of the tables(except the first), and then extend the other table with these columns.

btw the are hundres of column, so it wouldn't be feasible to write each column name.

---

### Post by lloyd mcclendon on 2007-03-24
this might be pretty naive but it is how i would do it.  before you start make a backup of the database.  

copy both tables to temp tables using SELECT INTO (this may take a long time so grab a beer).  drop the identifier columns on both temp tables.  use SELECT INTO again to copy the second table to the bottom of the first, add your identifier column.  drop the second table, the two original tables, and rename the full table.

---

