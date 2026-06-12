---
title: "PL/SQL loop to update values"
date: 2009-12-05
forum: Programming Talk
---

### Post by andrew222 on 2009-12-05
Hello,

I would like to ask for some help on writing a PL/SQL script.

I have a table called PROJECT and have added a new column called POSITIONINDEX which is the index position row in which a hibernate list collection mapping uses as the column to sort by.  Also,a GRANT_APPLICATION class can have 0 to 4 PROJECTS.  The foreign key for PROJECT table is GRANT_APPLICATION_ID 

I have older data that does not have this column and will add the column.  Hence, I will have to write a SQL script to write index values to the POSITIONINDEX column in these rows.

I am in the process of learning PL/SQL and I know that I will have to use a cursor, and loops to accomplish this task.

Right now I am thinking about using a nested numeric for loop.  As mentioned earlier, the foreign key for PROJECT table is GRANT_APPLICATION_ID .  So, I think the outter loop will loop through all PROJECT rows and the inner row will loop through projects with the same GRANT_APPLICATION foreign key and use the count variable to set the value for POSITIONINDEX. 

I think I will have to use the aggregate count(*) function to get the number PROJECTS per GRANT_APPLICATION to set the conditional value of iterations for inner loop.

I have read a couple of books and am getting an idea of how to write this.

I would like to ask if there is anyone who has done a script like what recommendations, advice or examples could be shared.


Regards,

Andrew

---

