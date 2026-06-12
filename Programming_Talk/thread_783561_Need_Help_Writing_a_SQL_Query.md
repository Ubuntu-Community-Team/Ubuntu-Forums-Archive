---
title: "Need Help Writing a SQL Query"
date: 2008-05-05
forum: Programming Talk
---

### Post by gunksta on 2008-05-05
I need a helping hand from someone with more SQL experience than I. I am trying to write a couple of queries in OpenOffice.org Base and I've run into a problem.

I have two tables. Simplified, they look like this:

Sample
    General_ID  (this is a unique number)
    Date_Selected

Event
    General ID (this is not a unique number)
    Date_Event

I have a sample population of people, each with a unique General_ID. Each row in table Event describes . . . . an event. Each member of the sample has at least one event. Most have more than one.

I need to learn about the events, relevant to the date the population was selected. Most of these event happen after the Date_Selected. I would like to make a query where I look at the first event, the second event, etc. for each ID number.

I know how to count how many events happened after the Date_Selected:

```
SELECT "Event"."General_ID", COUNT( "Event"."Date" ) 

FROM "Sample", "Event" 

WHERE "Sample"."General_ID" = "Event"."General_ID" AND "Sample"."Date_Selected" <= "Event"."Date" 

GROUP BY "Event"."General_ID"
```

This gives me something that looks like

General ID       Number of Events
1                      11
2                      10
3                      16
4                       5
5                      10
etc. 


OK, so that tells me how many events happen to each member of my population, which is a good thing, but it's only part of what I need.

I'd like to be able to define a query to look at all of the first events, second events, etc. But, I don't know how. I appreciate any help on this. So, I'd like a query that returns something like:

General ID    Date     Stuff About My Event
1                  1/1/08       Stuff
2                  1/1/08       Stuff
3                  1/1/07        Stuff
4                  1/2/08       Stuff
5                  1/3/08       Stuff

Such that I have a query that looks like this for ALL of the first event, second event, third event, etc. If I can figure out how to do this once, I'm sure I can apply the logic and make it work more than once.


Once I can write this query, I can compare the first set of events to the second set of events and so on, to measure for change in "Stuff".

P.S.  - No, I can't reorganize the data, this is how we're pulling it out of the system. All I have are some nice big .csv files.

THANKS! THANKS! THANKS!

---

### Post by gunksta on 2008-05-05
One other note, the events do not all happen on the same date, since people entered the study at different times. Thus, I can't just look for all of the events that happen on date xx/xx/08 because there is no such date.

---

### Post by soaresnew on 2008-05-05
Why are you using GROUP  BY in the first place?

I think you're going to have to reorganize the data.  Otherwise you can just use UNION, they all share the same data type, unless I"m missing something here.

"One other note, the events do not all happen on the same date, since people entered the study at different times. Thus, I can't just look for all of the events that happen on date xx/xx/08 because there is no such date."

Yes, but they share the same ID.

---

### Post by gunksta on 2008-05-05
I think I may have thrown off a red-herring in my first post. I think I should concentrate on the one table, Event

Event
         .General_ID
         .Date  
         .Stuff_1


General_ID, is not unique. For example, General_ID = 1 has three entries, each with a different date. General_ID=2 has two entries, each with a different date.

I need to be able to group these by first date, second date, etc.

For starters I thought I should try to find the first event in the table. I came up with:
```
SELECT DISTINCT "General_ID", MIN( "Date" ) 
FROM "Event" 
GROUP BY "General_ID"
```This makes sense to me, but the output is kinda weird. It gives me:

General_ID    Date
1                    39203
2                    39405
etc.


I think I should concentrate on the first challenge that I have here and worry about the other stuff later, which may involve a union.

---

### Post by tardomatic on 2008-05-06
I assume that General_ID in Event is the Event Identifier, and the General_ID in Sample is the Sample Identifier (i.e. they aren't the same thing).

In your last post you said you want to focus on the Event table. And you want to count the number of events that occurred on a specific date?

This might work:

SELECT General_ID, Date, Count(Date)
FROM   Event
GROUP BY General_ID, Date
ORDER BY General_ID, Date

This, if my logic is correct, will show you, by General_ID and Date, the count (i used date for no specific reason... i guess you could use any column)...

So, lets say you had the following data: 

General_ID | Date
1          | 01/01/2008
1          | 01/02/2008
1          | 01/01/2008
2          | 01/01/2008
2          | 01/02/2008
2          | 01/02/2008

The results should look like:

1 | 01/01/2008 | 2
1 | 01/02/2008 | 1
2 | 01/01/2008 | 1
2 | 01/02/2008 | 2

is this what you're after?

---

### Post by gunksta on 2008-05-06
> **tardomatic said:**
> 
The results should look like:

1 | 01/01/2008 | 2
1 | 01/02/2008 | 1
2 | 01/01/2008 | 1
2 | 01/02/2008 | 2

is this what you're after?


Similar. I am beginning to suspect that I can't do what I want to do with SQL, and the project isn't big enough to make it worth writing an entire program for. I'd basically like to put each of these dates into a series of lists and then be able to compare the second set of dates to the first set of dates, etc. 

Oh well. I think I'll just find some way of reorganizing the data.

---

### Post by soaresnew on 2008-05-07
Perhaps you can use instead Xquery.

---

