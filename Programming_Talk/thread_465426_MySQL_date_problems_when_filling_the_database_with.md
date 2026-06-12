---
title: "MySQL: date problems when filling the database with data."
date: 2007-06-05
forum: Programming Talk
---

### Post by jingo811 on 2007-06-05
I have problems with the datatype DATE how should I break down the steps for troubleshooting things logically?  (By the way I'm the opposite of logical so.....any Vulcan help would be appreciated.)

> Script line: 345	**Incorrect date value: 'NULL' for column 'written' at row 1**      -   ErrorNr. 1292

```
# --------------------------------------------------
#          ***  Link tables  ***
# --------------------------------------------------
# --------------------------------------------------
#  Fill the table "clothes_org" with values.  (4)
# --------------------------------------------------

#  Empty table of old values:
#
#
DELETE FROM clothes_org;

#  Fill with all values:
#
#
**INSERT INTO clothes_org**    -    (line 345)
  (
    article_id,
    org_id,
    opinion,
    comments,
**    written,**
    updated
      )
VALUES
  (
    '1',
    '2',
    '0',
    '',
**    'NULL',**
    'NULL'
      ),
  (
    '2',
    '3',
    '1',
    'Good good.',
**    '2007-05-11',**
    '2017-12-11'
      ),
  (
    '3',
    '',
    '0',
    '',
**    'NULL',**
    'NULL'
      );
```

I tried these values instead of **'NULL'** but I still get the same error:
**' '**    -   (without space)
**'0'**

---

### Post by jingo811 on 2007-06-05
Also in case it helps you Vulcan people this is how I created that table.

```
# --------------------------------------------------
#          ***  Link tables  ***
# --------------------------------------------------
# --------------------------------------------------
#  Create table "clothes_org"  (4)
# --------------------------------------------------

#  Delete table if it already exists:
#
#
DROP TABLE IF EXISTS clothes_org;

#  Create table:
#
#
CREATE TABLE clothes_org (
  article_id SMALLINT UNSIGNED NOT NULL, # FK
  org_id SMALLINT UNSIGNED, # FK  ,  blir det rätt om artiklar inte fått nån bedömning?
  opinion  TINYINT UNSIGNED NOT NULL, # Vilken datatyp ska vara här?
  comments  TEXT,
**  written  DATE,**
  updated DATE,
  PRIMARY KEY (article_id, org_id)
);
```

---

### Post by primski on 2007-06-06
If you want NULL, you need to enter it without quotes as NULL and not 'NULL', to enter a date, then u need quotes as in '2007-06-06'.

Also to enter NULL, field must have NULL, otherwise it wont let you insert null values as its required.

CREATE TABLE clothes_org (
.
.
.
written date null
);

---

### Post by tturrisi on 2007-06-06
Also, it appears you are running 2 consecutive operations, deleting the valuse in the table and then inserting new values, whereas you could do it in one operation with UPDATE SET.

UPDATE clothes_org SET 
article_id = X,
org_id =X,
opinion =X,
comments =X,
written =X,
updated =X;

[http://dev.mysql.com/doc/refman/5.0/en/update.html](http://dev.mysql.com/doc/refman/5.0/en/update.html)

---

### Post by jingo811 on 2007-06-06
tnx for the tips everyone!

> Also, it appears you are running 2 consecutive operations, 
Yeah it might not look so good from the parts I've taken out.  But the parts are part of 2 different script files that's intended to be run only once.
I haven't learnt the update part yet in my nightcourse but I think I know what you're insinuating.

---

### Post by jingo811 on 2007-06-07
I have another question!
So the solution worked for my FIELD "**written**" but when I try to do the same for a FOREIGN KEY - FIELD it doesn't want to allow NULL.
I've tried doing it to my **org_id** by following the same procedure but things doesn't take?
Is there a special rule for setting NULL to foreign keys?

[COLOR="Red"]Script line: 345	Column was set to data type implicit default; NULL supplied for NOT NULL column 'org_id' at row 1[/COLOR]



Script 1 - table
> CREATE TABLE Organization (
 ** org_id SMALLINT UNSIGNED NULL AUTO_INCREMENT, # PK**
  name VARCHAR(100) NOT NULL,
  PRIMARY KEY (org_id)
);


Script 1 - link table
> CREATE TABLE clothes_org (
  article_id SMALLINT UNSIGNED NOT NULL, # FK
**  org_id SMALLINT UNSIGNED NULL, # FK**
  opinion  TINYINT UNSIGNED NOT NULL, # Vilken datatyp ska vara här?
  comments  TEXT,
  written  DATE NULL,
  updated DATE NULL,
  PRIMARY KEY (article_id, org_id)
);


Script 2 - insert data
```
INSERT INTO clothes_org
  (
    article_id,
    org_id,
    opinion,
    comments,
    written,
    updated
      )
VALUES
  (
    '1',
   [COLOR="Red"] NULL[/COLOR],
    '0',
    '',
    NULL,
    NULL
      ),
  (
    '2',
    '3',
    '1',
    'Good good.',
    '2007-05-11',
    '2017-12-11'
      ),
  (
    '3',
    '3',
    '0',
    '',
    NULL,
    NULL
      );
```

---

### Post by tturrisi on 2007-06-07
AFAIK, auto increment keys cannot be null because they HAVE to automatically get a value as each new row is created, these keys are NOT NULL.

---

### Post by jingo811 on 2007-06-07
hmm....so can I just insert **'unknown'** instead of NULL to simulate the same effect with my outside org_id like tables?
So that when I want to search for NULL posts when doing it on **xxx_id like tables** I just search for 'unknown'.  Would that be a water proof solution or would it create problems later on when the database grows bigger?

---

### Post by winch on 2007-06-07
> A PRIMARY KEY is a unique index where all key columns must be defined as NOT NULL. If they are not explicitly declared as NOT NULL, MySQL declares them so implicitly (and silently). A table can have only one PRIMARY KEY. If you do not have a PRIMARY KEY and an application asks for the PRIMARY KEY in your tables, MySQL returns the first UNIQUE index that has no NULL columns as the PRIMARY KEY.
From [http://dev.mysql.com/doc/refman/5.0/en/create-table.html](http://dev.mysql.com/doc/refman/5.0/en/create-table.html)

Why can't you just use article_id as the primary key for table clothes_org?

---

### Post by jingo811 on 2007-06-07
> Why can't you just use article_id as the primary key for table clothes_org?
Because my table drawings look like this

([COLOR="Sienna"]Article[/COLOR] - **article_id** [COLOR="Olive"]PK[/COLOR]) [COLOR="Sienna"]>--<[/COLOR] ([COLOR="Sienna"]Org[/COLOR] - **org_id** [COLOR="Olive"]PK[/COLOR])      # Crows notation ([COLOR="Sienna"]>--<[/COLOR] or many to many)

Which means tables [COLOR="Sienna"]Article[/COLOR] and [COLOR="Sienna"]Org[/COLOR] each have their own respective primary key fields, article_id and org_id.
To connect those 2 "many to many" relations I use each respective [COLOR="Olive"]PK[/COLOR].
Which in the [COLOR="Sienna"]clothes_org[/COLOR] Link table both becomes Foreign Keys, but [COLOR="Olive"]2 FK's[/COLOR] in one table makes a unique id so I won't have to appoint a PK in clothes_org.

([COLOR="Sienna"]clothes_org[/COLOR] - **article_id**/**org_id**) [COLOR="Olive"]fk+fk = PK[/COLOR]


**Script 1 - link table**

> CREATE TABLE clothes_org (
[COLOR="Olive"]article_id SMALLINT UNSIGNED NOT NULL, # FK
org_id SMALLINT UNSIGNED NULL, # FK[/COLOR]
opinion TINYINT UNSIGNED NOT NULL, # Vilken datatyp ska vara här?
comments TEXT,
written DATE NULL,
updated DATE NULL,
PRIMARY KEY (article_id, org_id)
); 

---

