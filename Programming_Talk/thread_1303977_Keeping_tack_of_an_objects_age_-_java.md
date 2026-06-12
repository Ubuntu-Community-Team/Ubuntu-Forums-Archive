---
title: "Keeping tack of an objects age - java"
date: 2009-10-28
forum: Programming Talk
---

### Post by MCBTunes on 2009-10-28
Hi,

I was wondering if there was anyway too keep track of how old an object was? I want objects on my server program to be deleted if they remain unchanged for 3 days. the Date class has been deprecated, looks like it has been replaced by the Calendar class but I dont know how to set a time/day in an object and comeback and check it later with that.

If an item is added to the list within the object I want to reset the field so the counter starts over.

Ideas?

---

### Post by PaulM1985 on 2009-10-28
After having a quick look at the API, I think you can create a new Calendar object using:

Calendar anObjectsTime = Calendar.getInstance();

then for the current time when you want to test, you could use:

Calendar thisTime = Calendar.getInstance();

and then test if anObjectsTime is greater than 3 days away from thisTime by creating a function to compare the DAY_OF_WEEK value of each Calendar object.

Or look at using the time attribute of the Calendar classes which is the number of milliseconds from the start of the year till now. (so difference greater than 1000 x 60 x 60 x 24 x 3.

Hope this helps.

Paul

---

### Post by MCBTunes on 2009-10-29
That worked, thanks Paul.

I assumed Calendar would post the current date only(eg whenever accessed it would update it's variable.... I don't know why :roll: anywho, thanks again for the help.

---

