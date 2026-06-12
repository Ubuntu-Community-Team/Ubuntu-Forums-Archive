---
title: "Oracle Help"
date: 2009-04-18
forum: Programming Talk
---

### Post by Squizz on 2009-04-18
Hi all - I'm trying to go through some Oracle examples, but seem to have a problem that I can't fathom.  Essentially, I'm just playing with an example but get an error.

Here is the original code, that works fully.

```

create type salesman_t;
create type car_t;


create type car_t as object (
reg# char(7),
make varchar2(10),
model varchar2(10),
is_sold_by ref salesman_t
);

create type car_list_t  as table of ref car_t;

create type salesman_t as object (
salesman# char(4), salesname varchar2(10), sells car_list_t);


create table salesman_tab of salesman_t (
primary key (salesman#))
nested table sells store as sells_car_table;


create table car_tab of car_t (
primary key (reg#),
scope for (is_sold_by) is salesman_tab) ;


```

Here is mine with very slight changes.

```

create type programme_t;
create type student_t;

create type student_t as object (
person_id char(4),
person_name varchar2(10),
person_dob varchar2(10),
person_address varchar2(50),
is_enrolled_on ref programme_t
);

create type student_list_t  as table of ref student_t;

create type programme_t as object (
programme_id char(4), programme_name varchar2(30), dept_id char(4), contains student_list_t);

create table programme_tab of programme_t (
primary key (programme_id))
nested table contains store as contains_student_table;

create table programme_tab of programme_t (
primary key (programme_id),
scope for (is_enrolled_on) is programme_tab);

```

The problem comes when I try to run the final statement, and receive the error;

```
ORA-00904: "IS_ENROLLED_ON": invalid identifier
```

Can somebody please explain to me why I'm getting this error?

Also, on a similar topic, if I were to use DATE for student_dob, will the format '01 JAN 2009' work properly?

Thanks very much in advance.

---

### Post by Squizz on 2009-04-18
Simple oversight.  I tried to create programme_tab twice for some reason instead of creating the student_tab....

---

