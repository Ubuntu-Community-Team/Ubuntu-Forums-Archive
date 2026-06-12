---
title: "mysql syntax error..."
date: 2009-03-11
forum: Programming Talk
---

### Post by qmqmqm on 2009-03-11
Hi

Does anyone know what is wrong with this query:

INSERT INTO `ps` (`p_id` , `p_name` , `description`) VALUES ('' , "PA" , "") WHERE NOT EXISTS (SELECT * FROM ps WHERE `p_name` = "PA" AND `description` = "") 

Thanks.

Tom

---

### Post by kpatz on 2009-03-11
> **qmqmqm said:**
> Hi

Does anyone know what is wrong with this query:

INSERT INTO `ps` (`p_id` , `p_name` , `description`) VALUES ('' , "PA" , "") WHERE NOT EXISTS (SELECT * FROM ps WHERE `p_name` = "PA" AND `description` = "") 

Thanks.

Tom
You can't use a where clause on an INSERT statement.

What exactly are you trying to accomplish?  Insert a row if it doesn't already exist?

INSERT IGNORE INTO `ps` (`p_id` , `p_name` , `description`) VALUES ('' , 'PA' , '');

will insert the row if it doesn't already exist (do you have a primary key or unique index on the table?  This is important for this to work)

---

### Post by kpatz on 2009-03-11
Here's another way that does what I think you're after... which is to insert a row only if a row doesn't exist based on the where clause.

> 
insert into ps(p_id,p_name,description) select * from (select '' as p_id,'PA' as p_name,'' as description) as c where not exists(SELECT * FROM ps as b WHERE p_name = 'PA' AND description = '');


---

### Post by qmqmqm on 2009-03-11
> **kpatz said:**
> You can't use a where clause on an INSERT statement.

What exactly are you trying to accomplish?  Insert a row if it doesn't already exist?

INSERT IGNORE INTO `ps` (`p_id` , `p_name` , `description`) VALUES ('' , 'PA' , '');

will insert the row if it doesn't already exist (do you have a primary key or unique index on the table?  This is important for this to work)


Hi Kpatz

The p_id field is the primary key.

Thanks,

Tom

---

### Post by qmqmqm on 2009-03-11
> **kpatz said:**
> Here's another way that does what I think you're after... which is to insert a row only if a row doesn't exist based on the where clause.

Thank you very much Kpatz!

---

### Post by kpatz on 2009-03-11
> **qmqmqm said:**
> The p_id field is the primary key.If it's an autoincrement field, you don't need to specify it in your insert.

> insert into ps(p_name,description) select * from (select 'PA','') as c where not exists(SELECT * FROM ps as b WHERE p_name = 'PA' AND description = '');

---

### Post by qmqmqm on 2009-03-12
> **kpatz said:**
> If it's an autoincrement field, you don't need to specify it in your insert.

Great! Thanks Kpatz!

---

