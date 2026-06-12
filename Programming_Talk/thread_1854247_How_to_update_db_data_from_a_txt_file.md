---
title: "How to update db data from a txt file"
date: 2011-10-04
forum: Programming Talk
---

### Post by caja0710 on 2011-10-04
I am trying to update one of the fields of a db table.  Since there are hundreds of records, I am thinking of using a txt or cvs file to store the new name.  Then use script to read the value from the file and logon to the db and perform an update query.  I read from some post of using do while but not sure how to achieve as I am very junior on scripting.

Sample input:
object_id,name
1234,primary
1235,secondary
1236,third

SQL:
update table_level
set name='<input from the txt file>'
where object_id='<input from the txt file>';

---

### Post by karlson on 2011-10-04
> **caja0710 said:**
> I am trying to update one of the fields of a db table.  Since there are hundreds of records, I am thinking of using a txt or cvs file to store the new name.  Then use script to read the value from the file and logon to the db and perform an update query.  I read from some post of using do while but not sure how to achieve as I am very junior on scripting.

Sample input:
object_id,name
1234,primary
1235,secondary
1236,third

SQL:
update table_level
set name='<input from the txt file>'
where object_id='<input from the txt file>';

You need to read the database SQL documentation on how to do this.

in MySQL it's "LOAD DATA INFILE"
in PostgreSQL it's something else you can find it in [http://www.postgresql.org/docs/manuals/](http://www.postgresql.org/docs/manuals/)
in Oracle there is a program called sqlldr if I recall correctly

etc, etc.

And if you are doing your own processing the SQL syntax would be
```

insert into table(<fieldnames>) values (<values>);

```

---

