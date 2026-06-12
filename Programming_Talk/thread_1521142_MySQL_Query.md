---
title: "MySQL Query"
date: 2010-06-30
forum: Programming Talk
---

### Post by lewisforlife on 2010-06-30
Didn't know where to post this, hopefully this is a good place.  I have 2 MySQL tables that look like the following.

Database: fax_contact

Table housemem:

ID	|	HM_Last
----------------------------------------
1	|	Lewis
2	|	Bob
3	|	Jean
4	|	Smith

Table h-dofc:

ID	|	HM_DistrictOfficeFax
---------------------------------------
1	|	
1	|	111-111-1111
2	|	222-222-2222
2	|	
2	|	333-333-3333
3	|	123-123-1234
4	|	555-555-5555
4	|	321-321-3210



Essentially what I want to output is housemem.HM_Last and then the first instance of h-dofc.HM_DistrictOfficeFax for each ID that is not NULL.  So the query should output the following for the above tables:

Lewis	111-111-1111
Bob	222-222-2222
Jean	123-123-1234
Smith	555-555-5555

In Microsoft Access, the SQL query looks like this:

```

SELECT housemem.HM_Last, 
FIRST (
h-dofc.HM_DistrictOfficeFax
) AS FirstOfFax
FROM housemem
INNER JOIN h-dofc ON ( housemem.ID = h-dofc.ID ) 
AND (
housemem.ID = h-dofc.ID
)

```

the FIRST () function is not supported in MySQL.  I am having trouble making this work in MySQL, does anyone have any ideas?  I have played around with LIMIT but cannot seem to get the same results as my Access Query.

---

### Post by Dragonbite on 2010-06-30
Not sure how to do this in MySQL, but could always add a column to [h-dofc] like [Active bit null] and filter for [Active]=1 for the entry you want associated.

---

### Post by robots.jpg on 2010-06-30
Is there anything wrong with doing it this way?

```
SELECT housemem.HM_Last, `h-dofc`.HM_DistrictOfficeFax 
FROM housemem 
INNER JOIN `h-dofc` ON housemem.ID=`h-dofc`.ID 
WHERE `h-dofc`.HM_DistrictOfficeFax IS NOT NULL 
GROUP BY housemem.ID;

```I'm a little rusty on SQL, so I might be forgetting something.

---

### Post by Some Penguin on 2010-06-30
Row ordering is ill-defined.  If you want to enforce some order so that 'first' actually is meaningful, add a column to impose that order -- e.g. an autoincrement column.  Then "SELECT blah WHERE blah is not null ORDER BY blah LIMIT 1" is the sort of thing you could use.

---

### Post by lewisforlife on 2010-07-01
> **robots.jpg said:**
> Is there anything wrong with doing it this way?

```
SELECT housemem.HM_Last, `h-dofc`.HM_DistrictOfficeFax 
FROM housemem 
INNER JOIN `h-dofc` ON housemem.ID=`h-dofc`.ID 
WHERE `h-dofc`.HM_DistrictOfficeFax IS NOT NULL 
GROUP BY housemem.ID;

```I'm a little rusty on SQL, so I might be forgetting something.

Thank you very much robots, this worked.  Well, I only made one small change, I changed "IS NOT NULL" to "!= ''" because it was not working, maybe my fields were not really NULL.

---

### Post by Dragonbite on 2010-07-01
(reply with quotes isn't working)

Won't that end up with two Smiths (555-555-5555 and 321-321-3210)?

If so, could try 
```

SELECT 
     t1.HM_Last, 
     t2.HM_DistrictOfficeFax 
FROM 
     housemem as t1
     INNER JOIN 
     (
          Select Top 1 ID, HM_DistrictOfficeFax
          From `h-dofc` 
          Where HM_DistrictOfficeFax IS NOT NULL 
     ) as t2 ON t1.ID=t2.ID 

```

Wait.. no, I don't think that is going to work. I think the "Top 1" will only return 1 record;

ID | HM_DistrictOfficeFax
---------------------------------------
1 | 111-111-1111

But if you can figure out how to do the "first" in the nested Select statement in the FROM section so you end up with one record per ID then you should be good.

---

### Post by Hellkeepa on 2010-07-11
HELLo!

"GROUP BY" ensures that each ID is only returned once.

Happy syncin'!

---

### Post by LoneWolfJack on 2010-07-11
I'm a bit reluctant to post this link again within just 5 minutes, but this is the same problem.

A simpler solution is to self-join your tables:
[http://www.thelampblog.com/2010/05/24/mysql-self-join-a-table/]("http://www.thelampblog.com/2010/05/24/mysql-self-join-a-table/")

---

