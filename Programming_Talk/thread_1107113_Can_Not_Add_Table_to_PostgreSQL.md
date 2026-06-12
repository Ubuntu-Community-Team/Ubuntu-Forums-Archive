---
title: "Can Not Add Table to PostgreSQL"
date: 2009-03-26
forum: Programming Talk
---

### Post by rmtatum on 2009-03-26
I attempted to add a table to postgresql, but it doesn't do anything.

```
CREATE TABLE Course_Taken (
	Student_Id INTEGER,
	Course_Id INTEGER,  

	Num_Grade DOUBLE(1,1),

	Letter_Grade CHAR(1) NOT NULL,

	CONSTRAINT Chk_Course_Taken CHECK(Letter_Grade in ('A','B','C','D','F'),

	CONSTRAINT Pk_Course_Taken PRIMARY KEY (Student_Id, Course_Id)

);
```

I then attempted to add some data to the table, 

```
INSERT INTO Course_Taken(Student_Id, Course_Id, Num_Grade, Letter_Grade) VALUES (1, 001, 3.0, 'B');

```

I then executed the following query and only a blank line was displayed:

```
SELECT * FROM Course_Taken;
```

I am running postgresql-8.3 on Ubuntu Jaunty.

---

### Post by dwhitney67 on 2009-03-26
I presume that you have created a database and are using it.

I am not that familiar with PostgreSQL, but you should be able to follow these steps:

1.  Create database  (e.g. createdb mydb)
2.  Use database     (e.g. psql mydb)
3.  Create table     (e.g. CREATE TABLE mytable ...)
4.  Show all         (e.g. SHOW ALL or SHOW mytable)

Try all these before attempting to add a row to the table just to make sure the database and the table are indeed present.

---

