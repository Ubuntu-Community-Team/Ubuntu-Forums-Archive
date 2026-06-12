---
title: "check statements in SQL"
date: 2007-09-20
forum: Programming Talk
---

### Post by DouglasAWh on 2007-09-20
I need to write a check statement in SQL that goes across two tables.

What I need in the check statement is something like:

```

CHECK (emp.eid = works.eid AND works.did=dept.did AND dept.managerid=emp.eid AND emp.age>30).

```

In English, I am trying to ensure that all managers are over 30 years old.  Now, the question is, can I pull in the other tables, assuming those tables have already been created?  There's no from statement in CREATE, so I don't know how it would know where to go.  Do I just need to use an ALTER instead?

It's probably obvious, but I'm a beginner.

---

### Post by smartbei on 2007-09-20
I don't believe you can. The CHECK statement is supposed to work on each column individually. Thus, your statement doesn't make sense. emp.eid, works.eid, works.did, etc. are all columns, and it doesn't make sense to compare them. If anything, you would be using a WHERE, but that isn't available in a CHECK statement. Therefore, I don't think what you are trying to do is possible. How do you plan on doing this with an ALTER?

---

### Post by DouglasAWh on 2007-09-20
well, there's not an age in the dept category where the managerid resides.  my understanding is that the CHECK can actually check multiple tables, but it can only *act* on one of those tables.

---

### Post by Matakoo on 2007-09-20
> **DouglasAWh said:**
> 
It's probably obvious, but I'm a beginner.

Well, at the risk of showing my sql ignorance (well, not ignorance but I'm certainly no expert either)...which SQL server are you using? It may not be supported in the server version you're using. MySQL does not, for example - at least if my understanding of it is correct.

Correct me if I've misunderstood you, but are you trying to make sure the software prohibits someone being hired as manager (or promoted to one) if they are less than 31 years old? If so, why not do that on the client? Some combination of stored procedures and triggers on the server might be an option too.

---

### Post by DouglasAWh on 2007-09-20
MySQL will not do this.  This is what we use for class, so there's no way to check the statement.  However, I think it can probably be done, since the book asks us to do it.  

You are right in what the query is trying to get at; no manager can be less than 31 years old.

---

### Post by Matakoo on 2007-09-21
> **DouglasAWh said:**
> MySQL will not do this.  This is what we use for class, so there's no way to check the statement.  However, I think it can probably be done, since the book asks us to do it.  

You are right in what the query is trying to get at; no manager can be less than 31 years old.

Well, I'm mostly familiar with MySQL now-a-days but the following is one approach if one just need to solve the problem. If you absolutely must use check, then I'm afraid I can't help.

Note though, that this is a simplified table-structure and the error-handling need to be extended but it should serve as a starting-point.

First, let's create the tables:

```

create database comp;
use comp;
create table employee (id INT NOT NULL AUTO_INCREMENT, PRIMARY KEY (id), name TEXT NOT NULL, dept SMALLINT NOT NULL, age SMALLINT NOT NULL);
create table dept (id INT NOT NULL AUTO_INCREMENT, PRIMARY KEY (id), name TEXT not null);

```Then, three example departments

```

insert into dept VALUES (null,'Sales');
insert into dept VALUES (null,'Marketing');
insert into dept VALUES (null,'Legal');

```Take a look at the definition for the employee table. The dept field works like this:
If it's zero, the employee in question is not a manager
If it's higher than zero, the number refers to the corresponding row in the dept table. I.e. a 1 means (s)he is the manager of the sales department.

Finally, let's create a trigger

```

delimiter //
CREATE TRIGGER age_check BEFORE INSERT ON employee
FOR EACH ROW
BEGIN
IF NEW.dept > 0 AND NEW.age <31 THEN
SET NEW.age = 192;
END IF;
END;//

```The if-section is the important bit. If the person is a manager (dept >0) AND younger than 31 (age<31) then we set a new value on that field. An impossibly high one, and that's the part that needs to be extended.
If the condition is not met, the value is accepted as-is.

Try these examples:

```

insert into employee VALUES (null,'John',1,35);
insert into employee VALUES (null,'Michael',2,25);
insert into employee VALUES (null,'Beverly',0,23);

```John should be accepted (manager of sales, older than 31 years)
Michael should not (manager of marketing, but too young so his age should be rewritten as 192)
Beverly should be accepted (not a manager so the age is irrelevant).

Hope this works as a starting point.

---

### Post by DouglasAWh on 2007-09-21
Well, in this case, we've had the tables defined for us

```

Emp (eid, ename, age, salary)
Works (eid, did, pct_time)
Dept (did, budget managerid)

```

so, that particular trigger won't work.  We're not really doing triggers and this specifically asks for a check.  I'll post when/if I get something reasonable.


I should note that in my book on page 167 of my book it says "Table constraints are associated with a single table, *although the conditional expression in the CHECK clause can refer to other tables*."  It is the second part that this question uses.

Oh, I just found an example of a CREATE TABLE with a CHECK that reference outside tables.  Now, the question is, do those outside tables have to have a foreign key in that table being created.  In the example both do, and there's no foreign key between Emp and Dept, unless managerid serves as one, and I'm not sure it does.  This, of course, ignores the fact that MySQL doesn't do foreign keys.

---

### Post by DouglasAWh on 2007-09-21
I think I've got it. 

```

CREATE TABLE emp (eid INTEGER,
ename CHAR(30),
salary REAL,
age REAL,
PRIMARY KEY (eid),
CONSTRAINT NoYoungManager
CHECK eid <> 
      (SELECT D.managerid 
       FROM dept D, emp E, works W 
       WHERE E.age <= 30 AND E.eid=W.eid AND W.did=D.did AND 
       E.eid=D.managerid);

```

---

