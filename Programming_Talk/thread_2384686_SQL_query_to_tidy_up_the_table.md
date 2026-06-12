---
title: "SQL query to tidy up the table"
date: 2018-02-10
forum: Programming Talk
---

### Post by dam034 on 2018-02-10
Dear users,

I have a sql table with a primary key auto_increment.

Over time I deleted some rows and inserted others, and now when I type:
```
SELECT * FROM table
```
I get the rows not in key order. I know I have to type this:
```
SELECT * FROM table ORDER BY key ASC
```
But I saw in phpmyadmin a function which tidy up the keys for me. Now I can't see its query.

Can you tell me what query is?

Thanks

---

### Post by SeijiSensei on 2018-02-10
You could [create a "view:"]("https://dev.mysql.com/doc/refman/5.7/en/create-view.html")

```
CREATE VIEW ordered AS SELECT * FROM table ORDER BY key ASC;
```

Now a "select * from ordered" will give you the results in the order you want.

---

### Post by dam034 on 2018-02-17
Sorry for the delay,

I went in the phpmyadmin online demo and I did a screenshot:
[ATTACH=CONFIG]278572[/ATTACH]
What I want to do is indicated by the red arrow, but phpmyadmin doesn't show the query it does.

That are a primary key, and the command will ordinate the table.


Please help!

---

### Post by spjackson on 2018-02-17
What I believe that option does is:
```

ALTER TABLE fraction ORDER BY id

```

---

### Post by QIII on 2018-02-17
I've been at this for many, many years.  SeijiSensei has the best accepted practice in post #2.

Views also allow you to avoid creating ad hoc SQL statements in code -- a dangerous, dangerous practice.  You can also (carefully) use parameterized stored procedures.

Changing your keys will destroy any relationships between tables based on the key and it will produce unpredictable and most certainly useless results.

---

### Post by banceu_sergiu_ione on 2018-02-17
What SeijiSensei said and confirmed by QIII.

I also add:

Is  "alter table 'table' order by id" of any good?

And quote from here [https://dev.mysql.com/doc/refman/5.7/en/alter-table.html](https://dev.mysql.com/doc/refman/5.7/en/alter-table.html)

> [h=4]Row Order for MyISAM Tables[/h]       ORDER BY enables you to create the new table       with the rows in a specific order. This option is useful primarily       when you know that you query the rows in a certain order most of       the time. By using this option after major changes to the table,       you might be able to get higher performance. In some cases, it       might make sorting easier for MySQL if the table is in order by       the column that you want to order it by later. 


   [B] Note :
[/B]
**         The table does not remain in the specified order after inserts         and deletes.** 


 
        ORDER BY syntax permits one or more column       names to be specified for sorting, each of which optionally can be       followed by ASC or DESC to       indicate ascending or descending sort order, respectively. The       default is ascending order. Only column names are permitted as       sort criteria; arbitrary expressions are not permitted. This       clause should be given last after any other clauses.     
       ORDER BY does not make sense for       InnoDB tables because InnoDB       always orders table rows according to the       [clustered index]("https://dev.mysql.com/doc/refman/5.7/en/glossary.html#glos_clustered_index").     

       When used on a partitioned table, ALTER TABLE ... ORDER       BY orders rows within each partition only. 



---

### Post by dam034 on 2018-02-21
So, I understood the query is:
```
ALTER TABLE table ORDER BY key ASC
```
Is it right?

I want to order the table as PHP does to an array with ksort() function.


Thanks

---

