---
title: "How to calculate weeknumber?"
date: 2007-01-18
forum: Programming Talk
---

### Post by cocteau on 2007-01-18
Hi

As a side project to learning c++ I'm trying to make a calendar, but I can't figure out any obvious way to calculate weeknumbers, from looking at other calenders. How is week 1 of the calendar year defined?

---

### Post by gpolo on 2007-01-18
ISO 8601 Week Numbers
ISO Definition & Consequences

ISO 8601 defines the Week as always starting with Monday being Day 1 and finishing with Sunday being Day 7. Therefore, the days of a single ISO Week can be in two different Calendar Years; and, because a Calendar Year has one or two more than 52×7 days, an ISO Year has either 52 or 53 Weeks.

The first Week of a Year is Number 01, which is :-

    * defined as being the week which contains the first Thursday of the Calendar year; which implies that it is also :-
    * the first week which is mostly within the Calendar year,
    * the week containing January 4th,
    * the week starting with the Monday nearest to January 1st. 

The last Week of a Year, Number 52 or 53, therefore is :-

    * the week which contains the last Thursday of the Calendar year;
    * the last week which is mostly within the Calendar year;
    * the week containing December 28th;
    * the week ending with the Sunday nearest to December 31st. 

Thus the ISO 8601 Week Numbers of a year are 01 to 52 or 53, which does not include zero. Part of Week 01 may be in the previous Calendar Year; part of Week 52 may be in the following Calendar Year; if a year has a Week 53, part of that week must be in the following Calendar Year. On average, six times out of seven, adjacent Dec 31st & Jan 1st are in the same Week.

There are 15 possible Week-numbering-year types. Clearly there are 14 possible Gregorian types corresponding to February having 28 or 29 days and the year starting of 7 possible days of the week. 13 of those have only one possible numbering, but a year starting on Saturday has Jan 1 & 2 in either Week 52 or 53 of the previous year, depending on whether it was a Leap Year.

The 15 possible ISO calendars 
[http://www.phys.uu.nl/~vgent/calendar/isocalendar.htm](http://www.phys.uu.nl/~vgent/calendar/isocalendar.htm)

---

### Post by cocteau on 2007-01-18
Wow. 

Let me just say thank you for giving such a good, concise answer. 

Now it's time to get cracking :)

See... now it's stuff like this that makes these forums so great. Knowledge and desire to share it :)

---

### Post by gummibaerchen on 2007-01-19
```
>>> import datetime
>>> datetime.date(2007, 1, 19)
datetime.date(2007, 1, 19)
>>> datetime.date(2007, 1, 19).strftime("%W")
'03'
>>> 
```

Is that ok?

---

