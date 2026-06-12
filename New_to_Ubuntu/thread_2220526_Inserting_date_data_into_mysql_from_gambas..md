---
title: "Inserting date data into mysql from gambas."
date: 2014-04-28
forum: New to Ubuntu
---

### Post by Gurupad on 2014-04-28
I'm currently on ubuntu 11.10 and i'm working on my college mini-project using gambas 2 and mysql.

I've created a form where it accepts an employee's date of birth and his joining date to the organization.

Now i've used the date chooser ...(one that comes in container section) to accept date.

Now how should i use the mysql insert statement.

If there's any other simple way to accept date in the format dd-mm-yyyy and insert that into mysql database, please help me quick.


Thanks

---

### Post by TheFu on 2014-04-28
Never heard of gambas 2 before. Don't know anything about how it connects with mysql. Most frameworks have a safe way to perform parameter substitution, to avoid XSS attacks. This almost always avoids using SQL.  I'd be surprised if the mysql manual doesn't explain the approved formats for date input. With any language, converting whatever you have into whatever they need should be trivial. google found this [https://dev.mysql.com/doc/refman/5.5/en/date-and-time-functions.html](https://dev.mysql.com/doc/refman/5.5/en/date-and-time-functions.html) .

However, 11.10 was out of support in 2012, so it is running many out of support tools and is definitely non-secure and shouldn't be placed onto a network. /in short, it is time for a major update effort to get on the current LTS release 14.04 with 5 yrs of support. Learn more about LTS releases here;  [https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

---

### Post by Lars Noodén on 2014-04-28
> **TheFu said:**
> Most frameworks have a safe way to perform parameter substitution, to avoid XSS attacks. This almost always avoids using SQL.  

Yes, **always** treat data that has come from outside the program as corrupt until cleaned up.  Perl and some other languages have a taint mode, Gambas might too.  

For doing SELECT or INSERT, consider strongly to use [url=https://dev.mysql.com/d

Dates need to be in standard ISO 8601 which would be [yyyy-mm-dd](https://dev.mysql.com/doc/refman/5.5/en/date-and-time-types.html) when you work within in the database.  

If Gambas has modules or functions available to interact with MySQL, then use those.  Regardless of whether you use them or insert your own raw SQL, be sure to validate the incoming data.  For a date, that means rejecting any non-numerical characters in a purported date, and rejecting any months past 12 and any days past 31. 

For doing SELECT or INSERT, consider strongly to use [prepare](https://dev.mysql.com/doc/refman/5.5/en/sql-syntax-prepared-statements.html) and execute SQL statements with place holders.  (See the ? marks in the examples in the manual.)  Those will minimize the possibility of an injection attack should something get past your data validation.

---

### Post by TheFu on 2014-04-28
I should have included this link before. [https://www.owasp.org/](https://www.owasp.org/) - these guys have a good set of checklists and helpful documents to create more secure code.

---

### Post by squakie on 2014-04-28
Ok, this is coming from an OLD guy - so perhaps it doesn't even apply to todays world:  Can one not just use a julian date?

---

