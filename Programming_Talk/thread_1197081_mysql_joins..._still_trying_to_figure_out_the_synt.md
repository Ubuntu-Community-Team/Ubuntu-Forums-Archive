---
title: "mysql joins... still trying to figure out the syntax"
date: 2009-06-25
forum: Programming Talk
---

### Post by lapubell on 2009-06-25
hello rad developers.

I'm having trouble working with three tables in a mysql database.  working with a smarter programmer than me, I set up my tables so that they work really well, when I can get it figured out.  He's not around today, and he usually helps he set up the joins.  After googleing and reading the mysql docs and the tiztag tutorials (usually pretty good) I can't get this thing to work right.

Three tables:
table 1 - instructors (truncated to show good data)
id - first - last  - ...
1  - Joe   - Smith - ...
2  - John  - whatever...

table 2 - students (almost identical to instructors)
id - first - last  - ...
1  - Sally - ASDF  - ...
2  - Billy - whatever...

table 3 - lessons (looks something like this):
id - student_id - instructor_id - ...
1  - 1          - 2 - ...
2  - 1          - 1 - ...

so i'm trying to get the students and instructors first and last names replacing the student_id and instructor_id when i query the lessons table.  do i use a left join?  if so, which table is the far left?  anyone want to help me out?  if there is a rad tutorial that is super dumbed down, I would love that link too.

Thanks in advance!

---

### Post by Can+~ on 2009-06-25
Seems more an issue about Relational Algebra on Joins

[http://en.wikipedia.org/wiki/Relational_algebra#Outer_joins](http://en.wikipedia.org/wiki/Relational_algebra#Outer_joins)

---

### Post by lapubell on 2009-06-25
i'm reading through it, but without some syntax, the aha! moment will be lost.  still reading through it though... maybe some help with something mysql specific?

---

### Post by Can+~ on 2009-06-25
> **lapubell said:**
> i'm reading through it, but without some syntax, the aha! moment will be lost.  still reading through it though... maybe some help with something mysql specific?

"**Relational** Databases" work around "**Relational** Algebra", at first glance you have troubles recognizing which attribute does what, that's why I handed you info on Relational Algebra. To be fair, [MySql JOIN's Syntax]("http://dev.mysql.com/doc/refman/6.0/en/join.html") is the exact same thing.

---

### Post by lapubell on 2009-06-25
good point.  thanks for the info.
still trying to get this thing to work...

---

### Post by jimv on 2009-06-25
```
SELECT

LessonID,
StudentName,
InstructorName

FROM Lessons
JOIN Students ON Lessons.StudentID = Students.StudentID
JOIN Instructors ON Lessons.InstructorID = Instructors.InstructorID
```

This is just one way...you could also do it like this:

```
SELECT

LessonID,
StudentName,
InstructorName

FROM Lessons, Students, Instructors
WHERE Lessons.StudentID = Students.StudentID
AND Lessons.InstructorID = Instructors.InstructorID
```

Also, remember to put indexes on your ID fields (if you haven't already), and if you have the same field name in more than one table, you have to prefix the field name with the table name.

---

