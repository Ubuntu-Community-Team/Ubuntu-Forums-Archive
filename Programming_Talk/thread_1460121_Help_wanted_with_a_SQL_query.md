---
title: "Help wanted with a SQL query"
date: 2010-04-22
forum: Programming Talk
---

### Post by bkann on 2010-04-22
I'm trying to write a SQL query that is giving me some trouble.  Seems like it should be easier than I'm making it.  Here's the deal, simplified just a bit from my table structure in real life:

```

events		        event_activities
======			================
id			id
event_name		event_id
			dtetme
			activity
```

These two tables are in a one-to-many relationship such that each event can have multiple activities.  I need to query a list of events (grouped by event) with their minimum activity dates where some subset of minimum activity dates is >= now().  For example:

Today is 4/22.  If the activities table has an event that has dates 4/20, 421, 4/22, and 4/23, I want the minimum date to be reported as 4/22, so the resultset would read:

```

e.id	e.event_name	min(ea.dtetme)
=====   =============   ==============
1	Event One	4/22

```

If the minimum date is greater than 4/22, then it reports it.  If there is no date >= 4/22 it does not get reported at all.

I'm not sure I explained that well.  If you think you can help, please feel free to ask for clarification.  I'm not a SQL novice, but it's also not my specialty, so I thank you very much in advance for any help you can provide.

---

### Post by ajlee on 2010-04-22
Try something like this:

SELECT e.id, e.event_name, MIN( ea.dtetime ) AS min_date
FROM  `event_activities` ea, 
EVENTS e
WHERE e.id = ea.event_id
GROUP BY e.id
HAVING min_date > CURDATE();

Edit:  This assumes MySQL.  CURDATE() may not be the way to get the current date in your DBMS.  Or if you want to be able to specify a date instead of using today's date you could put some other date function in there.

---

### Post by bkann on 2010-04-22
Thanks for the input.  This is about as far as I was able to get, but there's a problem.

The query you provided first returns the minimum date for the event.  Even if there are dates later than today, if the min date is prior to today, it will be excluded from the results.  In my example, it sees the event as having a min date of 4/20 and is therefore excluded, where I want it to return a min "applicable" date of 4/22 (ie., now).

I think I need to have a subquery or a query alias or something like that where it *first* finds:

SELECT event_id, min(dtetme)
FROM event_activities
WHERE dtetme >= CURDATE()
GROUP BY event_id
ORDER BY min_date

... and then those results will be joined with the events table in order to get event_name.  I don't know how to do that.


Additionally, thanks for introducing me to CURDATE().  I am using MySQL, but I had been using NOW().  I'll have to read up on these.  I was not aware of CURDATE before.

Thanks!

---

### Post by doas777 on 2010-04-22
when comparing a datetime field to check only date elements, be sure to use >= and <= rather than just < and >, as the time component will cause problems in the matching.

also if your db supports it, I really like the EXISTS subquery for testing to see if a record exists to match a set of criteria but i don't need any results from that query itself (when I want parents that have a specific type of children, but I don't need details on the children.

'Select * from Event Where Exists(Select EventActivityID From EventActivity Where ...)'

another handy onliner for subqueries is the IN() statement. 
'Event.EventID IN(Select EventID From EventActivities where ...)'

no idea if that helps, but felt like sharing.//

---

### Post by ajlee on 2010-04-22
Sorry - I misunderstood.  So if I understand correctly, as long as the event has at least one activity >= today you want it listed, but you still want the min_date displayed in the report.   I would use a subquery on the event_activities table... I haven't tested this.

SELECT e.id, e.event_name, ea.dtetime AS min_date
FROM `event_activities` ea, 
EVENTS e
WHERE e.id = ea.event_id
GROUP BY e.id
AND e.id IN (SELECT DISTINCT event_id FROM event_activities WHERE dtetime > CURDATE());

Edit:  Fixed stupid errors in my query. ;)
Edit2: This doesn't work - see below (post #6)

---

### Post by ajlee on 2010-04-22
Ignore my last query - it won't work, you can use your subquery as if it were a table and join to it.  Try this one:

SELECT e.id, e.event_name, MIN(ea.dtetime) AS min_date
FROM `event_activities` ea, 
EVENTS e,
(SELECT DISTINCT event_id FROM event_activities WHERE dtetime > CURDATE()) a
WHERE e.id = ea.event_id
AND a.event_id = e.id
GROUP BY e.id

---

