---
title: "SQL relationship tables, foriegn and primary keys"
date: 2011-06-12
forum: Programming Talk
---

### Post by psycho5 on 2011-06-12
Hi, I am very new to SQL, I am using MSSQL management studio. Can anyone explain to me how to establish relationships? 

Here's the basic outline, 

I have 3 Faculties, each faculty has one or more cluster (departments), underneath each cluster is one or more module (courses) offered, each module has a module descriptor, and 2 moderation forms.

So the Faculty has a one to many relationship with clusters

Each cluster has a one to many relationship to modules

Each module has a one to one relationship to the module descriptor, and the 2 moderation forms per module.

How can I link them? If each module is defined by the Module Name and Module Code, then these two (or maybe just the module code) is the key that links the module to the descriptor and the 2 moderation forms... how do I form the relationships? MSSQL is quite confusing to me in that regard, and I could really use some guidance, thanks!

Much appreciated

---

### Post by psycho5 on 2011-06-12
OK I made some progress, I assigned primary keys to all my tables... now I have a question.

suppose table A has 10 columns and table B has 4 Columns

how do I link column 2 of A to column 2 of B, columns 3,4,5 of A to column 3 of B, and columns 6,7,8,9,10 of A to column 4 of B?

---

### Post by Petrolea on 2011-06-13
First of all, it's MS SQL. You're at Ubuntu Forums.

And to kind of answer your question, you could use Case studio to establish relationships. It's very easy, check it out.

---

### Post by r-senior on 2011-06-13
> **Petrolea said:**
> First of all, it's MS SQL. You're at Ubuntu Forums.
Anything goes in this Programming Talk forum. Any language, any platform.

---

### Post by Petrolea on 2011-06-13
> **r-senior said:**
> Anything goes in this Programming Talk forum. Any language, any platform.

I was trying to say that people might not know MS SQL since these are linux forums.

---

### Post by psycho5 on 2011-06-13
> **Petrolea said:**
> I was trying to say that people might not know MS SQL since these are linux forums.

Well, to be perfectly blunt, that's for the people to decide isn't it? if they don't know, they will probably won't answer. So, that comment was unnecessary.

---

### Post by simeon87 on 2011-06-13
Design the tables first, then create everything in MySQL. It seems to me there are three tables:

[LIST]
[*]Faculties
[*]Clusters
[*]Modules
[/LIST]

Each of these should have a unique identifier (primary key) so you can refer to them in the other tables. Effectively those are foreign keys in those other tables.

---

### Post by simeon87 on 2011-06-13
> **psycho5 said:**
> OK I made some progress, I assigned primary keys to all my tables... now I have a question.

suppose table A has 10 columns and table B has 4 Columns

how do I link column 2 of A to column 2 of B, columns 3,4,5 of A to column 3 of B, and columns 6,7,8,9,10 of A to column 4 of B?

You don't wanna do that, it's a mess. Table A should have a primary key and table B should have a primary key as well. Then in table B you can refer in a column to a column in A.

So you can have a students table (A) and each student has a student number (primary key). In table B you can then have the student's enrollments that refer to the primary key in table A. For example:

```
// table A
123456 John
234567 Jack
```

```
// table B
123456 Introduction to Computer Programming
123456 Databases
234567 Computer graphics
```

---

### Post by PaulM1985 on 2011-06-13
To start you off

It sounds like your Module table should include a column which would contain the cluster_id (primary key from the Cluster table) of the cluster that it has a relationship with.

Your Cluster table would include a column which would contain the faculty_id (primary key from the Faculty table) of the faculty that is has a relationship with.

These two columns that I have described are called foreign keys.

Paul

---

### Post by SeijiSensei on 2011-06-13
Create three tables for the main information and give each of them a primary key.

```
Table     Pri Key
Faculty   FacID
Cluster   ClusID
Module    ModID
```

To create the relationship between Faculties and Clusters, you need another "relational" table.  It should contain pairs of IDs, so you can create a many-to-one relationship. Suppose FacID 1 belongs to two clusters with ClusID=1 and ClusID=2.  Then you'd have two records in this linking table, call it FacClus:

```
FacID     ClusID
1         1
1         2
```

To select all the faculty in a cluster you'd run a command like:

```
select * from FacClus left join Faculty using (FacID) left join Cluster using (ClusID) where ClusID=1;
```

Follow the same procedure for Clusters and Modules.

---

### Post by psycho5 on 2011-06-14
Thanks all for the help.

I have created the tables as such

faculty table : faculty_id (int) and faculty_name

cluster table : cluster_id (int) and cluster_name

insert into faculty (faculty_id, faculty_name) VALUES ('','a');
insert into faculty (faculty_id, faculty_name) VALUES ('','b');

in mysql

then I can make a relationship table, name it cluster_faculty and in it add values like ('','1','1'); and ('','2','1'); and so on to indicate the relationships. Then I can use the select command to filter.

My question is, does anyone know how to identify the syntax or the method MSSQL 2008 uses to assign the keys? so that I could create the same type of relationship table in MSSQL?

Also, suppose I have a value in the table as such

alter table table1 add choices set('1','2','3','4'); 

How do I make it so that each choice in the set also asks for a "percentage" value once you select them? As in, I select 1 and 2, then the user must be able to enter the percentage of people who got 1 and the percentage of people who got 2.

---

