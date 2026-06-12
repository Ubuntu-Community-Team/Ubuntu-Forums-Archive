---
title: "Mysql Query Help"
date: 2013-05-06
forum: Programming Talk
---

### Post by dazman19 on 2013-05-06
Hi,

Just tried to run this query on mysql 5.6. It was previously working on 5.1.

Anyone have any Idea why it wont let me set this column to null?

```

mysql> describe diagnostic;
+--------------------------------+-------------+------+-----+---------+----------------+
| Field                          | Type        | Null | Key | Default | Extra          |
+--------------------------------+-------------+------+-----+---------+----------------+
| diagnostic_id                  | int(11)     | NO   | PRI | NULL    | auto_increment |
| diagnostic_time                | int(15)     | NO   |     | NULL    |                |
| diagnostic_user                | int(15)     | NO   |     | NULL    |                |
| diagnosticdata_time            | int(15)     | NO   |     | NULL    |                |
| diagnosticdata_user            | int(15)     | NO   |     | NULL    |                |
| diagnosticdata_name            | varchar(50) | NO   |     | NULL    |                |
| diagnosticdata_suppliercontact | int(11)     | YES  | MUL | NULL    |                |
+--------------------------------+-------------+------+-----+---------+----------------+
7 rows in set (0.00 sec)

mysql> UPDATE diagnostic 
    ->                 LEFT JOIN contact ON diagnosticdata_suppliercontact = contact_id
    ->                 SET diagnosticdata_suppliercontact = NULL
    ->                 WHERE (!contactdata_issupplier) OR (contact.contact_id IS NULL);
ERROR 1048 (23000): Column 'diagnosticdata_suppliercontact' cannot be null
mysql> 



```

---

### Post by lisati on 2013-05-06
A quick response before I go help Mrs Lisati with the shopping: It's possible that it can't be NULL because it's a KEY field.

---

### Post by slickymaster on 2013-05-07
If you want, it is possible to allow NULL values in a foreign key, this property has a relation with another property "ON UPDATE/DELETE SET NULL".

See [this]("http://dev.mysql.com/doc/refman/4.1/en/innodb-foreign-key-constraints.html") (scroll down until you reach the part about **"Deviation from SQL standards"**).

---

