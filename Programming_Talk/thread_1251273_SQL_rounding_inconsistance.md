---
title: "SQL rounding inconsistance"
date: 2009-08-27
forum: Programming Talk
---

### Post by tc101 on 2009-08-27
In the code below, running on SQL server 2005, why does 1.125 get
rounded up to 1.13, but 1.775 gets rounded down to 1.77 ?

declare @ff float 
declare @mm money
set @ff = 1.125
select @mm=convert(numeric(10,2),@ff)
select @ff,@mm
set @ff = 1.775
select @mm=convert(numeric(10,2),@ff)
select @ff,@mm

---

### Post by oldfred on 2009-08-27
I once upon a time asked a similiar question since I was using MS Access and MS SQL server and VBA all with different results. 

Now this has a better summary of what I found, but I did not know that there were so many ways to round a number and Microsoft uses several depending on who/which group developed the software.

[http://en.wikipedia.org/wiki/Rounding](http://en.wikipedia.org/wiki/Rounding)

---

