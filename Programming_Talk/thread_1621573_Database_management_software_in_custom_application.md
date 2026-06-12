---
title: "Database management software in custom applications"
date: 2010-11-14
forum: Programming Talk
---

### Post by nair on 2010-11-14
I was wondering exactly how database management software could be useful in designing an application.  I am not very familiar with what database management software is.  I have never used MySQL, PostgreSQL, or SQL Server.  I have never been a database administrator.  I am not familiar with a lot of the terms and concepts used in describing databases, but I think of a simple database as being something like a huge table--like a spreadsheet of records.  Again, I have never done anything involving databases.

If I ever wanted to design an application on my own just writing code, and I wanted to deal with (create, manage, retrieve) a very large number of records of a certain type that I define within that application, should I be using a database management system to store all of these records?  It seems to me that just using structures, arrays, and other standard programming techniques, I can make records and organize them very easily--and potentially obtain the same or better performance.  It is possible to do pretty much anything I want or need to just using conventional programming techniques.

I do not have any idea what the benefits are of using a database management system to store records.  Does database management software offer some sort of speed/performance benefit in retrieving records in a custom application?  Does it make the process of creating backups easier?  What would you use if you were going to program your own application, and it were going to deal with thousands and tens of thousands of the same types of records?

---

### Post by nair on 2010-11-15
Also, is one of the main reasons for using a database management system to be able to compartmentalize different parts of the database (the records stored on the database) within different physical and virtual servers?  In my particular case, I was not looking to store tens of thousands of records elsewhere--I just wanted them stored locally on the machine running the application.

---

### Post by elenzo on 2010-11-15
Hi Nair,

From your own words, you never used a DBMS before. Probably, the main fact here is that a DBMS doesn't just "store records". Among other things, a DBMS can control who access to your stored records, it also indexes them (following specifications) for faster retrieval, and runs code to ensure data integrity (again, following specifications). If you are thinking of a data base as a big spreadsheet, you clearly need to read some DBMS literature about DB design and operation. 
If you plan to work with a small number of records, you will probably be well by creating your own application. But if you plan to grow the amount of stored information, you will probably experience slowdowns in performance as the searches for data will take more time. Keep in mind that there are several hundred programmers working in each company to write, test and obtain quality db software. But, if anyway you want to reinvent the wheel...

---

### Post by Some Penguin on 2010-11-15
Do a search for 'RDBMS'.

And think about *how you'd implement* 

> 
It seems to me that just using structures, arrays, and other standard programming techniques, I can make records and organize them very easily--and potentially obtain the same or better performance. It is possible to do pretty much anything I want or need to just using conventional programming techniques.


---

