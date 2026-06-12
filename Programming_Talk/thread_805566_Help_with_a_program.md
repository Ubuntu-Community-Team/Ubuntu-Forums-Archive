---
title: "Help with a program"
date: 2008-05-24
forum: Programming Talk
---

### Post by aquavitae on 2008-05-24
I've been writing a program for preparing bills of quantities, although it could really be used as a kind of spreadsheet, but with more control over the contents. Th reason behind it is that we do a lot of them at work using a spreadsheet, but the formatting is a nightmare and inconsistencies almost always slip in. So I though I'd write a program to do it.  It GPLv3 and is hosted at [http://code.google.com/p/boq/]("http://code.google.com/p/boq/"). There's one [wiki page]("//http://code.google.com/p/boq/wiki/ProgramDesign") there describing a bit about it.

So my questions are:
[LIST=1]
[*]Is there anything existing which will do this easily? I know it is possible to write macros in a spreadsheet to do it, but if I'm going to write a lot of code I'd rather write it into a program that does exactly what I want.
[*]Is there a better way of implementing it - e.g. using a database?  I have a feeling that a database might be better, but I don't know very much about them.
[*]Is anyone interested in helping with it: writing code, managing the webpage, etc
[/LIST]

---

### Post by Lau_of_DK on 2008-05-24
> **aquavitae said:**
> 
[LIST=1]
[*]Is there anything existing which will do this easily? I know it is possible to write macros in a spreadsheet to do it, but if I'm going to write a lot of code I'd rather write it into a program that does exactly what I want.
[*]Is there a better way of implementing it - e.g. using a database?  I have a feeling that a database might be better, but I don't know very much about them.
[*]Is anyone interested in helping with it: writing code, managing the webpage, etc
[/LIST]

Hey,

To answer #2, then in a way it depends a bit on the scale of your application, but I would absolutly base this on Sql/MySql and then apply some relational-databasing: [Link]("http://php.about.com/od/learnmysql/ss/mysql_3.htm")

Good luck with it
/Lau

---

### Post by aquavitae on 2008-05-24
Thanks for the reply. I'll have a look.

---

### Post by pmasiar on 2008-05-24
Don't waste time on MySQL. MySQL etc is way too complicated database for such simple case. Look at SQLite: simple single-user SQL data repository without hassle of administering like 'real' database, as MySQL etc. 

Database is exactly best fit if you do not want to have formulas and formatting all over  the cells. 

You may need to learn up some SQL, or for simplicity, get object-relational mapper (ORM), like SQLObject or SQLAlchemy: it will create objects according to your schema, make them accessible to program, and find and store them. Easier than plain SQL, especially for SQL beginners.

---

### Post by aquavitae on 2008-05-25
After a bit of gooling I'd come to that decision - sqlite is what I want. 

All this database stuff is going over my head a bit! I don't really know the limitations or possibilities of databases. Is it possible to give columns properties, or would that be done by creating a separate table? How would they link then? Is it possible to use the records in one table as fields in another? 

ORM does look like it would simplify things a bit, but which one? Since I'm using PyQt, I'd like to be able to use the QSqlTableModel to display the data, does that mean I can't use an ORM? Or is QSqlTableModel basically an ORM by itself?

I'll google around for answers, but if anyone can give guidance I'd be grateful!

---

### Post by pmasiar on 2008-05-25
> **aquavitae said:**
> I don't really know the limitations or possibilities of databases.

there are no limits! :-) only your imagination and programming skills.

> Is it possible to give columns properties, or would that be done by creating a separate table? How would they link then? Is it possible to use the records in one table as fields in another? 

You JOIN tables using FOREIGN KEY - a value  in first table will be record ID in the second.

---

### Post by aquavitae on 2008-05-26
Ok, here's an idea for the database layout. I've listed the fields I'm going to use under each table:

```

Table 1: Global document variables
    Name
    Value

Table 2: A list of properties that apply to rows columns or cells
    Name
    Applies_To    (i.e. 'row', 'column' or 'cell')
    Help_String
    Default_Value

Table 3: A list of all the columns
    ID
     <Properties as
    described in Table 2
    ...>

Table 4: A list of all the schedules
    Table_ID

Table 5: Master schedule (i.e. list of rows used in other schedules)
    Row_ID
    <Properties as
    described in Table 2
    ...>

Table 6: Properties unique to a cell
    Schedule_ID
    Row_ID
    Column_ID
    Property_Name
    Property_Value

Table Table_ID: A schedule based on Table 5 and contained in Table 4:
    Row_ID (must be contained in Table 4)
    <A selection of the 
    columns listed in Table 3
    ...>



```
Any comments on this? I don't know if all of this is possible, and I'm certain someone who knows more about databases will see a better way of doing this!

---

