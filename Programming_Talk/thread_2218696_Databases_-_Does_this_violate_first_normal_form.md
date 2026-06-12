---
title: "Databases - Does this violate first normal form?"
date: 2014-04-21
forum: Programming Talk
---

### Post by cp43tcW on 2014-04-21
Hello, I was wondering if there would be absolutely any chance of someone telling me: If I have DATE and Time in the same column is that a violation of first normal form?  For example: 
Table Appointments
 --------------------------------------------- 
|FirstName | LastName   | Date&Time           |
 --------------------------------------------- 
|Bob         |Bolderstein   | 04/04/2016 10:00 | 
|Bill          |Strongstein  | 03/04/2016  11:00 | 
|Samantha|Weakstein    | 05/05/2016  04:00 | 
|Enrico     |Averagestein| 09/03/2016  02:00 | 
----------------------------------------------

---

### Post by SeijiSensei on 2014-04-21
I store dates as [Unix timestamps]("http://en.wikipedia.org/wiki/Unix_time") and format them as required in the application.  They will pose a problem in 2038, but I doubt it will matter to me as I will be nearly ninety then and probably not maintaining any more databases!

---

### Post by bkline on 2014-04-21
The language of the spec is ambiguous, but common usage considers this conformant to first normal form.

---

### Post by cp43tcW on 2014-04-21
The language I am using is Sql. Can date and time be in the same column in first normal form?

---

### Post by ofnuts on 2014-04-22
No it doesn't, and it's closer to 1NF than storing date and time in separate columns. However as SeijiSensei said above storing these data as time stamps instead of strings is a more open way(*). With your format, answering questions such as "which customers have an appointment next Thursday between 2pm and 6pm" is difficult. With time stamps you just select the lines where the appointment timestamps is between two values.

(*) the second best is to store them as a directly sortable string: "2016-04-28 19:00". Btw your format above is ambiguous, I doubt you customers have appointment at 2am...

---

### Post by llanitedave on 2014-04-23
It depends on how you're using it.  If you have events that can happen several times during a day, then it makes sense to keep dates and times as separate entities.  Even then, though, you can still use the Unix timestamps.

---

