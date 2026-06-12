---
title: "SQL Help - Left Join?"
date: 2010-07-07
forum: Programming Talk
---

### Post by cartisdm on 2010-07-07
I have three tables:

OPT - contains OPT_IDs and the Description
OPT_CV - contains OPT_IDs and PLAN_IDs
PLAN_DFN - contains the PLAN_IDs

I want to show all the Plans available, their corresponding Options, and the option's Description.  This wouldn't be so hard except there are two PLAN_IDs that don't have matching OPT_IDs; thus, they don't show up in my query results.

This is what I did have, but then realized it's missing two PLAN_IDs and I need to include them:

```
SELECT  
	 A.PLAN_ID
	,A.OPT_ID
	,B.PLAN_LDSC_TX
	,B.PLAN_TYPE_CD
	,B.PLAN_BRND_CD
	,C.OPT_LDSC_TX

FROM     
         &DATABASE..OPT_CV    A
        ,&DATABASE..PLAN_DFN  B
        ,&DATABASE..OPT         C

WHERE    
	A.PLAN_ID = B.PLAN_ID
      AND A.OPT_ID  = C.OPT_ID

WITH UR

```

---

### Post by LoneWolfJack on 2010-07-11
You're providing too few details to be sure, but I think I know what you're trying to do.

You need to self-join some of your tables.

Check this out:
[http://www.thelampblog.com/2010/05/24/mysql-self-join-a-table/]("http://www.thelampblog.com/2010/05/24/mysql-self-join-a-table/")

---

### Post by Tony Flury on 2010-07-11
> **LoneWolfJack said:**
> You're providing too few details to be sure, but I think I know what you're trying to do.

You need to self-join some of your tables.

Check this out:
[http://www.thelampblog.com/2010/05/24/mysql-self-join-a-table/]("http://www.thelampblog.com/2010/05/24/mysql-self-join-a-table/")

In normal SQL speak what you need is called an "outer join" - which includes entries for a table (as NULL) values, when a matching row does not exist.

I think that MS Access (and maybe some others) call them left and right joins, Oracle SQL uses the (+) modifier to signify the table that is lacking entries - it all depends on what dialect your database uses.

---

### Post by jflaker on 2010-07-11
I attached a pdf.  I use this frequently.....hope it helps you too

I believe that some of the references may be DB2 related as they may not be standard key words...but the rules still apply, especially on joins

---

### Post by LoneWolfJack on 2010-07-11
> In normal SQL speak what you need is called an "outer join" - which includes entries for a table (as NULL) values, when a matching row does not exist.

Your description of outer joins is correct, but self-joins are not (necessarily) outer joins. 

You're right if you mean that self-joins can be used to simplify queries that would otherwise be a complex mixture of inner and outer joins, but self joins make it possible to reference the same column multiple times, which is extremely helpful if you're trying to retrieve a row from table A that is referenced by two or more rows (same column) in table B, just as Craig correctly describes in his blog.

---

### Post by crush304 on 2010-07-11
```

SELECT  
	 A.PLAN_ID
	,A.OPT_ID
	,B.PLAN_LDSC_TX
	,B.PLAN_TYPE_CD
	,B.PLAN_BRND_CD
	,C.OPT_LDSC_TX

FROM     
         
        &DATABASE..PLAN_DFN  B 
        left join &DATABASE..OPT_CV A on A.PLAN_ID = B.PLAN_ID
        left join &DATABASE..OPT C on AND A.OPT_ID  = C.OPT_ID

```

that should get all rows in B

---

### Post by cartisdm on 2010-07-12
Thanks everyone for the replies.  I got stuck working on a different task at the moment but I promise to return to this issue since I need to get it completed!

---

### Post by cartisdm on 2010-07-12
With a little bit more tweaking I got it, you guys rock! No way I could have gotten it without everyone's help.  I'm slowing trying to get back into this whole SQL thing now that my job requires it! :D:D:D

Final Version:
```

SELECT  
	 B.PLAN_ID
	,A.OPT_ID
	,B.PLAN_LDSC_TX
	,B.PLAN_TYPE_CD
	,B.PLAN_BRND_CD
	,C.OPT_LDSC_TX

FROM     
         
        &DATABASE..PLAN_DFN  B 
        left join &DATABASE..OPT_CV A on A.PLAN_ID = B.PLAN_ID
        left join &DATABASE..OPT C on A.OPT_ID  = C.OPT_ID
WHERE
	B.PLAN_ID IN(1000,3500,5000,5010,5020,5030,5200,5300
		    ,5700,5800,6100,7500,8600,8874,8894,9000
		    ,90919,90929)
WITH UR

```

---

