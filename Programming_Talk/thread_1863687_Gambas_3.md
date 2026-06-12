---
title: "Gambas 3"
date: 2011-10-18
forum: Programming Talk
---

### Post by kalaharix on 2011-10-18
Gambas 3 is on release candidate 5. Final release cannot be far away. It has not made it to repositories so you will have to compile from source.

It is a BASIC style programming language which can be made to behave like VB but is in fact much more. A lot of the Object Orientation in Gambas has the smell of Java.

I have said before on this forum that Gambas is a superb database frontend and have stolen this recent post by 'bbb888' from the Gambas forum:

" I have just finished a little ETL exercise of a reasonable sized database (7.5million rows over 28 tables, heavily "foreign-keyed", postgresql 8.3 backends on both sides).  It took me a few days longer than I thought it 
would because I tried some "major" linux ETL tools first. 

Of the three I tried, all were java based, two were free and open source and one was commercial licence linux (30day non-crippled trial).  One could not cope with any datatype stronger than an integer and insisted 
that all floating point numeric types have a scale of 1245678????? (Guess which one).  Of the two free ones, one just gave up and pointed it toes toward the sky on the first occurrence of more than 1000 rows in 
the transform set, the other is still going on a test machine (6 days now?). 

So. I gave up. 

And did it myself. 

I would have done it in gb2 but I thought I'd just see how gb3 went. The job took 6 projects, 4 to build nice clean base tables (including one of 1.1M rows) and two to clean, transform, recode and load the 
dependent tables.  If we "excuse" the mistakes that I made in the DDL for the new database, which meant two re-runs, the whole development time was 14 hours and the elapsed time for the final run was 3hours and 
12minutes. 

Net result, 7.43million rows in new database in 16 tables.  (How can 5 users create 70,000 junk records in a year? ) 

I have now run the 60 odd test queries to prove the data is correct (26 hours) with zero errors. "

---

