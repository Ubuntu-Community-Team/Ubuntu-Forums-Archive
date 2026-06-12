---
title: "Crystal Reports v10 code question"
date: 2010-01-18
forum: Programming Talk
---

### Post by Cyked on 2010-01-18
Figured I'd give this a shot here.  Thanks in advance. :)

I found some Ken Hamady formulas and am trying to work with them to calculate the duration between start and end date/time taking into consideration for business hours.  Which are M-F 8am-5pm as a starting example. 

I'm using Formula 1 and Formula 13 from his site as a starting point for what I am trying to do.  In forumla 13 he points out that anything outside of the set business hours you will get weird data (which I am) andyou have to run the data through another forumla to correct for it.  I have no idea what this is though.

I've set my business hours in one piece of code to be from 08:00 to 17:00 and anything that falls outside of that for start or end time I get a negative value once I run the report.  Anything within business hours works fine.

So if I have a ticket opened at 8:50am and closed at 3:30pm (regardless of the day) I have no issues.  If I have a ticket opened at 3:30am for example I get a negative value for duration.

I'm running another formula before all of this that converts GMT to PST.

First I'm running this to get # of days between open/closed (minus weekends).

```

WhileReadingRecords;
Local DateVar Start := {@Begin Date};   // place your Starting Date here
Local DateVar End := {@Closed Date};  // place your Ending Date here
Local NumberVar Weeks;
Local NumberVar Days;
//Local Numbervar Hol;
//DateVar Array Holidays;

Weeks:= (Truncate (End - dayofWeek(End) + 1
- (Start - dayofWeek(Start) + 1)) /7 ) * 5;
Days := DayOfWeek(End) - DayOfWeek(Start) + 1 +
(if DayOfWeek(Start) = 1 then -1 else 0)  +
(if DayOfWeek(End) = 7 then -1 else 0);   

//Local NumberVar i;
//For i := 1 to Count (Holidays)
//do (if DayOfWeek ( Holidays ) in 2 to 6 and
//     Holidays in start to end then Hol:=Hol+2 );

Weeks + Days
```


----------------------------------------------------------

Then I'm running this to get specifically the data providing business hours are 8-5.

    ```
WhileReadingRecords;

    NumberVar Days := {@#daysbetween};  // The field that calculates your business days
    TimeVar SetStart := TimeValue( "08:00:00");      // The start your work day
    TimeVar SetEnd   := TimeValue("17:00:00");      // The end your work day
    TimeVar StartTime := TimeValue({@PST_Opentime});// The data field that holds your Start Time
    TimeVar EndTime   := TimeValue({@PST_Closetime});  // The data field that holds your End Time

    //These lines are only needed if your times are strings that do not indicate AM or PM, like "3:30"
    //They will convert afternoon times to PM.  Of course, this won't work if your workday is over 12 hours.
   // If StartTime < (SetEnd - 43200) then StartTime := StartTime + 43200;
   // If EndTime   < (SetEnd - 43200) then EndTime   := EndTime   + 43200;

    Days * ((SetEnd - SetStart) / 3600)
    -  ((SetEnd     - EndTime)  / 3600)
    -  ((StartTime - SetStart)  / 3600)
```


As I said, if open time or close time is outside of the set bus hours I get a negative value as my output.  Any thoughts.

---

