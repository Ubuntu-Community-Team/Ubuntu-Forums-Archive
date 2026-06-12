---
title: "Database question"
date: 2009-10-13
forum: Programming Talk
---

### Post by nmccrina on 2009-10-13
This is for a school-planning application I'm writing. I'll try to make it understandable :P I'm pretty much a n00b when it comes to databases, though I think today something finally clicked and I made some progress. :)

I have a database table of students. I would like to keep track of which courses a student is currently taking, but cannot figure out how to store this information in the database. The best idea I've had is adding columns to the table like 'course_one', 'course_two' etc., but this isn't optimal as it imposes a limit on the number of courses a student can take at once and also makes queries awkwarder (more awkward?) like:

```
SELECT student.last_name, student.first_name, course.name 
FROM student, course 
WHERE course.name = 'science' AND (course.name = student.course_one OR course.name = student.course_two OR course.name = student.course_three OR course.name = student.course_four
```

This to list the students that are taking science at the moment. Any suggestions on the best database design to go with here? Is a database even the best way to go? My dad (a programmer, but by his own admission with little experience in databases) suggested XML, which is tempting because I at least understand it halfway decently (you cant't really get any more basic than XML!).

---

### Post by Can+~ on 2009-10-13
What you're suggesting is known as an 1:n relation

1 student can have n courses. Therefore, this problem is solved with 2 tables:

```
           takes
Student 1 ------- * Course
```

But now, we got a problem, a course can be taken by m students too,  so it becomes a m:n relation

```
           takes
Student * ------- * Course
```

But m:n relations can't exist on a relational database, so a third table is added to normalize (If someone can think a better name for the middle table, go ahead)

```

            has                with
Student 1 ------ * Schedule * ------ 1 Course
```

This is how you should solve this, if you're working with Relational Databases.

On the other hand, a "database" doesn't imply a "relational database" with SQL commands and stuff, a database could be a plain unsorted text file, a bitmap, etc. XML could be easier, since it doesn't require much knowledge about [Relational Algebra]("http://en.wikipedia.org/wiki/Relational_algebra").

---

### Post by nmccrina on 2009-10-13
Ok, so if the student table has

name
--------
Linus Torvalds
Eric Raymond
Richard Stallman

and the courses table has

course
----------
Computer Science
Math
Physics
English

then the schedule table might look like

name             course
----------       -----------------
Linus Torvalds    Math
Eric Raymond    Physics
Linus Torvalds    English
Richard Stallman  Computer Science
Eric Raymond    Math
Eric Raymond    Computer Science

and to find all students taking math you would do

```
SELECT name FROM schedule WHERE course = 'math';
```

and to find all the courses Linus Torvalds is taking you would do

```
SELECT course FROM schedule where name = 'linus torvalds';
```

Is this right? 

Mentioning the phrase 'many-to-many relationship' helped, a quick google and I had a ton of information!

This actually doesn't seem very complicated. :P Thanks!

---

### Post by Can+~ on 2009-10-13
You usually store a unique id for each value, so you can have random access to the values (either hashing, indexing or sorting). Then, with keys, you can do foreign keys:

student
id_student (Primary Key)
name

course
id_course (Primary Key)
name

schedule
id_student (Foreign Key)
id_course (Foreign Key)

Foreign keys store a relation with the other table, finally, you can obtain all by:

1. Cartesian Product (Expensive)
```
SELECT student.name, course.name FROM student st, course cr, schedule sch WHERE st.id_student = sch.id_student AND sch.id_course = cr.id_course;
```

2. Joining (This one depends on the DB engine, and I totally forgot the syntax for each one of them)

The difference between the two, lies in the fact that Cartesian Product joins both tables with all attributes, and then filters them by the WHERE statement.

Whereas, Joining filters, then joins tables, so if you choose the center table and INNER/OUTER LEFT/RIGHT JOIN ON a certain condition, you can get a more efficient result.

---

