---
title: "SQL View input parameters?"
date: 2009-03-16
forum: Programming Talk
---

### Post by Joe88 on 2009-03-16
Does anyone know the syntax for getting input from a user in mySQL?, I'm guessing the syntax would be like this:

CREATE VIEW patientGP AS
SELECT GP
FROM patient
WHERE PName = ['Please input patient name: '];

---

### Post by CptPicard on 2009-03-16
You need to write some sort of script/external application to do that sort of stuff... you accept user input there, and then manipulate the database accordingly. And no, you would not use "create view" like that at all.

---

### Post by Joe88 on 2009-03-16
Thanks for the helpful reply, I am an SQL beginner and I was stuck on the last question of a practice university assignment, because I thought it was asking me to make a view with user input.

---

### Post by CptPicard on 2009-03-16
Well, you *can* run a "create view" from a script like that, but I have this strong feeling that they are just after a select...

---

