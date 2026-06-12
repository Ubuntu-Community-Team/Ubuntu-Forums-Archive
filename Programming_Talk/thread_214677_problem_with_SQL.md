---
title: "problem with SQL"
date: 2006-07-12
forum: Programming Talk
---

### Post by 008325 on 2006-07-12
hi all , i have a problem with SQL

i have two table , one table reference with other table ( FK )

sth like that 

table 1
xxx pk + fk + auto increasment
xxx Varchar

table 2
XXX PK
XXX FK reference to table 1 FK 

=======

however ,while i insert the value to the table 2 and table 1 

i must need to know the table 1 PK value that inserted before 

i am going to insert table 2 ...you know ..the FK 

so how can i do that ?

i dont want to insert table 1 then use select command to find out the result , then insert to the table 2

i hope all of you can understand my question , thxxxxx

Gordon

---

### Post by fluffington on 2006-07-13
Depends on the tools. What language are you developing in, and what database product are you using?

---

### Post by 008325 on 2006-07-13
> **fluffington said:**
> Depends on the tools. What language are you developing in, and what database product are you using?


i am using mysql + vb.net 2005

thx a lot

---

### Post by Ozitraveller on 2006-07-13
I would have thought that you would be able to do something like this:

Insert into Table1 (Fieldname) Values('ZZZZZ')
set @k = @@IDENTITY 

Sorry I'm sql server guy I don't know mysql, but there should be some function to retrieve the ID from the last insert.


Insert into Table2 (Fieldname, fk) Values('ZZZZZ', @k)

Hope that helps :)

---

### Post by 008325 on 2006-07-13
thx a lot , i will try it 

but i am afraid that there are too many people to retrive the 
mysql , the last record might no is the last record after 1 sec 
so...what can i do now ...
i have too many problem on mysql

---

### Post by 008325 on 2006-07-13
sorry , i still have one more question 

is that any SQL command to check the value exist or not ?

i dont want select the data then fill it in to the dataset to search ....

i hope that there are some sql can return the true or false value while checking exist or not ....

---

### Post by fluffington on 2006-07-13
I don't know if MySQL supports @@IDENTITY (never tried it), but I know it has LAST_INSERT_ID(), which does the same thing (See [here](http://dev.mysql.com/doc/refman/4.1/en/getting-unique-id.html) for details).

> **008325 said:**
> but i am afraid that there are too many people to retrive the mysql , the last record might no is the last record after 1 sec 
so...what can i do now ...

From the page I linked:

> For LAST_INSERT_ID(), the most recently generated ID is maintained in the server on a per-connection basis. It is not changed by another client.

---

### Post by LordHunter317 on 2006-07-13
FWIW, using GUIDs and generating them in client code solves this problem.

At either rate, use InnoDB and transactions to retain referential integrity.

---

### Post by 008325 on 2006-07-13
thx a lot @@"

but any suggestion on the existing value problem ?

---

### Post by LordHunter317 on 2006-07-13
> **008325 said:**
> but any suggestion on the existing value problem ?I'm not sure I understand.  Auto-incrementing PKEYs always yield unique values, so there's no need to check for a value beforehand.

If you're asking how to query, you need to read a SQL tutorial or book.

---

### Post by 008325 on 2006-07-13
um....actually , i am doing a program and there are many combo box , such as education , qualification , company , etc

main point : the item list of the combo box saved into Mysql

to provide a better user-friendly GUI . so i need to check that

the combo box value is existing in sql or not , while it is 

exist then  it use the existing value , while it is not exist

it need to create the new combo box list item , and create the 

new record reference by new list item.

so here is the structure
```


[B]Table Education 
Edu_No ( PK + Auto increase)
Edu_Name [/B]

[B]Table Personal_Information
Personal_No ( PK + Auto increase )
Name
Phone
Edu_No ( reference to Education table Edu_No)[/B]


```

so , you know while i create the new person 
i need to check the education combobox is new value or not in the Education table

if yes , just create the personal and set the Edu_No reference to Education table 

if not, create the new education record , and then create the new person and and set the Edu_No reference to Education table 

thx all , quite **urgent** ...thxxxxxx

---

### Post by LordHunter317 on 2006-07-13
Well first off, if that's your education table, then I would drop the surrogate key and just make edu_name the primary key.  It's senseless to have a surrogate key in this case.

You'll have to do a SELECT query first.  There is no way around if.  If you're using MySQL 5.0, then you can write a UDF that does a select first and returns the existing row, otherwise inserts the new row.  But, you won't have any way around this.

---

