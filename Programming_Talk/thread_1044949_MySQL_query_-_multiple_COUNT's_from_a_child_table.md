---
title: "MySQL query - multiple COUNT's from a child table"
date: 2009-01-19
forum: Programming Talk
---

### Post by osjak on 2009-01-19
Hi All,

I am trying to build an SQL statement that will pull data from a parent table and count rows in a child table.

Parent table - event:
```

eventid, title
1        'Metallica is coming'
2        'Elvis is in town'

```
Child table - eventattendance:
```

eventid,  userid,  response
1         24       Yes
1         5        Yes
2         7        Maybe
1         7        No
2         18       No
2         6        Yes

```
As a result of my query I am trying to have one line per event that would list attendance count for that event like this:
```

eventID, attendYes, attendMaybe, attendNo
1           2          0          1
2           1          1          1

```
So this is the query I am running:
```

SELECT 	eventTable.eventid AS eventID,
	COUNT(attendanceYes.response = 'Yes') AS attendYes,
	COUNT(attendanceNo.response = 'No') AS attendNo,
	COUNT(attendanceMaybe.response = 'Maybe') AS attendMaybe
FROM event AS eventTable
LEFT JOIN eventattendance AS attendanceYes
	ON ( attendanceYes.eventid = eventTable.eventid 
		AND attendanceYes.response = 'Yes' )
LEFT JOIN eventattendance AS attendanceNo
	ON ( attendanceNo.eventid = eventTable.eventid 
		AND attendanceNo.response = 'No' )
LEFT JOIN " . TABLE_PREFIX . "eventattendance AS attendanceMaybe
	ON ( attendanceMaybe.eventid = eventTable.eventid 
		AND attendanceMaybe.response = 'Maybe' )
WHERE date > $today
GROUP BY eventTable.eventid
LIMIT 10

```
This query does not give me the desired result. It looks like it counts the 'Yes' responses twice and places the number into both *attendYes* and *attendNo*. **Can anyone suggest the proper way to do it?**

I am running:
Ubuntu server: 8.04
MySQL Server version: 5.0.51a-3ubuntu5.4-log

---

### Post by slavik on 2009-01-20
not an SQL expert by any stretch of imagination, but does group by take more than field name? (I never tried this)

---

### Post by osjak on 2009-01-20
> **slavik said:**
> not an SQL expert by any stretch of imagination, but does group by take more than field name? (I never tried this)
Per MySQL docs a field name is all it takes:
[http://dev.mysql.com/doc/refman/5.0/en/group-by-functions.html#function_count](http://dev.mysql.com/doc/refman/5.0/en/group-by-functions.html#function_count)

---

### Post by slavik on 2009-01-20
I mean, have you tried something like:

select a, count(b), count(c) from table where something
group by b, c

---

### Post by osjak on 2009-01-20
> **slavik said:**
> I mean, have you tried something like:

select a, count(b), count(c) from table where something
group by b, c
I am counting data from the same child's column for all three counts, so this is what I just tried:

```

SELECT a, COUNT(b='yes') AS attendYes, COUNT(b='no') AS attendNo 
FROM table
WHERE something
GROUP BY attendYes, attendNo

```
This generates an error:
```
MySQL Error   : Can't group on 'attendYes'
```

If I do "GROUP BY b" then I have no error, but I also have incorrect results.

---

### Post by brentoboy on 2009-01-26
Use subqueries instead of grouping.

```

select eventID
,      (select count(*) 
        from eventattendance a
        where a.eventId = e.eventId
        and a.response = 'Yes'
       ) as attendYes
,      (select count(*) 
        from eventattendance a
        where a.eventId = e.eventId
        and a.response = 'No'
       ) as attendNo
,      (select count(*) 
        from eventattendance a
        where a.eventId = e.eventId
        and a.response = 'Maybe'
       ) as attendMaybe
from   event e

```

---

### Post by brentoboy on 2009-01-26
Use subqueries instead of grouping.

```

select eventID
,      (select count(*) 
        from eventattendance a
        where a.eventId = e.eventId
        and a.response = 'Yes'
       ) as attendYes
,      (select count(*) 
        from eventattendance a
        where a.eventId = e.eventId
        and a.response = 'No'
       ) as attendNo
,      (select count(*) 
        from eventattendance a
        where a.eventId = e.eventId
        and a.response = 'Maybe'
       ) as attendMaybe
from   event e
where  e.date > $today
limit 10

```


if you want to use grouping, try this
```

select 	  e.eventid as eventID
,         count(y.response) as attendYes
,	  count(n.response) as attendNo
,	  count(m.response) as attendMaybe
from      event e
left join eventattendance y
  on      e.eventid = y.eventid 
   and    y.response = 'Yes'
left join eventattendance n
  on      e.eventid = n.eventid 
   and    n.response = 'No'
left join eventattendance m
  on      e.eventid = m.eventid 
   and    m.response = 'Maybe'
where     e.date > $today
group by  e.eventid
limit 10

```

either of those should work, but I don't know which would offer the best performance.

---

### Post by osjak on 2009-01-27
Thank you guys for your responses. A friend of mine gave me a working solution for this problem. So here it is:

```
SELECT 	eventTable.eventid AS eventID,
	COUNT( distinct attendanceYes.userid ) AS attendYes ,
	COUNT( distinct attendanceNo.userid  ) AS attendNo,
	COUNT( distinct attendanceMaybe.userid ) AS attendMaybe
FROM event AS eventTable
LEFT JOIN eventattendance AS attendanceYes
	ON ( attendanceYes.eventid = eventTable.eventid 
		AND attendanceYes.response = 'Yes' )
LEFT JOIN eventattendance AS attendanceNo
	ON ( attendanceNo.eventid = eventTable.eventid 
		AND attendanceNo.response = 'No' )
LEFT JOIN " . TABLE_PREFIX . "eventattendance AS attendanceMaybe
	ON ( attendanceMaybe.eventid = eventTable.eventid 
		AND attendanceMaybe.response = 'Maybe' )
WHERE date > $today
GROUP BY eventTable.eventid
LIMIT 10
```

---

