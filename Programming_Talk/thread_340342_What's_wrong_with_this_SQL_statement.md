---
title: "What's wrong with this SQL statement?"
date: 2007-01-17
forum: Programming Talk
---

### Post by hagen00 on 2007-01-17
Hi

The following SQL statement is taking a long time to execute. If one of the tables that it queries has around 30 or so records in it, it takes up to 30 seconds to execute. 


> SELECT DISTINCT(jobseeker.JobSeekerID) FROM jobseeker,relocatecountryselected, relocateregionselected, jobseekerlanguage,workpermitscountryselected,educationselected WHERE jobseeker.JobSeekerID = relocatecountryselected.JobSeekerID AND jobseeker.JobSeekerID = relocateregionselected.JobSeekerID AND jobseeker.JobSeekerID = jobseekerlanguage.JobSeekerID AND jobseeker.JobSeekerID = workpermitscountryselected.JobSeekerID AND jobseeker.JobSeekerID = educationselected.JobSeekerID  

All that is happening here is that tables are being joined by the JobSeekerID. Each of the tables (except table jobseeker) might have the JobSeekerID more than once. e.g. a jobseeker may want to relocate to more than one country, and therefore the relocatecountryselected table will have the same JobSeekerID in it more than once. That's also why I use DISTINCT, since I just want the Distinct JobSeekerID returned, even if they are relocating to more than one country. 

Any ideas why it's taking so long to execute? It eventually gets there, just takes forever. 

Do you need more info? Should I use different SQL?

Many thanks

H

(This is just a part of the query. I append stuff to it, but that isn't causing any problems. )

---

### Post by phossal on 2007-01-17
What kind of database? MySQL?

---

### Post by theslut on 2007-01-17
that is an awful long time. is the query being ran remotely from a local machine to a remote machine or ran locally?  There's defintely a problem there.

What version of mysql are you using?

---

### Post by hagen00 on 2007-01-17
Hey slut...haha, that sounds funny. 

Anyway. Someone helped me out and this works great!

SELECT 
    j.JobSeekerID 
FROM jobseeker j 
LEFT JOIN relocatecountryselected r ON j.JobSeekerID = r.JobSeekerID 
LEFT JOIN relocateregionselected r1 ON j.JobSeekerID = r1.JobSeekerID 
LEFT JOIN jobseekerlanguage j1 ON  j.JobSeekerID = j1.JobSeekerID 
LEFT JOIN workpermitscountryselected w ON j.JobSeekerID = w.JobSeekerID 
LEFT JOIN educationselected e ON j.JobSeekerID = e.JobSeekerID 
GROUP BY j.JobSeekerID 

Nothing to do with MySQL or the version. I should just write proper SQL

---

### Post by jblebrun on 2007-01-17
> **hagen00 said:**
> Hey slut...haha, that sounds funny. 

Anyway. Someone helped me out and this works great!

SELECT 
    j.JobSeekerID 
FROM jobseeker j 
LEFT JOIN relocatecountryselected r ON j.JobSeekerID = r.JobSeekerID 
LEFT JOIN relocateregionselected r1 ON j.JobSeekerID = r1.JobSeekerID 
LEFT JOIN jobseekerlanguage j1 ON  j.JobSeekerID = j1.JobSeekerID 
LEFT JOIN workpermitscountryselected w ON j.JobSeekerID = w.JobSeekerID 
LEFT JOIN educationselected e ON j.JobSeekerID = e.JobSeekerID 
GROUP BY j.JobSeekerID 

Nothing to do with MySQL or the version. I should just write proper SQL

In the future, you may want to check out a query analyzer. They can help you see exactly what your SQL statement is asking the database to do, and figure out where problems are.

---

### Post by Null Reference Exception on 2007-01-27
> **hagen00 said:**
> 
Nothing to do with MySQL or the version. I should just write proper SQL

Are JOIN operators supported by all DBMS? 

I only ask because I remember a few years ago asking a developer why he didn't use INNER JOINs in his code to which he replied they are not supported by all DBMS. Since the application targeted several  DBMS and he did not want to rewrite the data access code for each database he stuck to using WHERE PK = FK.

---

### Post by phossal on 2007-01-27
> **Null Reference Exception said:**
> Are JOIN operators supported by all DBMS?

No. There are commercial software packages in use that use legacy databases that don't support all of the features of modern SQL

---

