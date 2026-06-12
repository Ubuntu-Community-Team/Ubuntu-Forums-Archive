---
title: "increment a day"
date: 2008-10-27
forum: Programming Talk
---

### Post by davidtuti on 2008-10-27
Hi,

First of all sorry for my english, I hope that you can understand me



What I would know if there is a command that I could increment one day to the date and the program gives me the correct date, for instance, when I increment one day to the 30th semptembre, it doesn't gives me 31th, it must  gives me octuber 1th.

Many thanks!!

---

### Post by Tony Flury on 2008-10-27
it depends on the programming language you are using :

if you are using C you can use the time libraries to add days etc to given dates (convert date to a timestamp, add the right interval to the timestamp and then convert the new timestamp back to a date), and I would assume that many other programming languages have a similar process, or even have special date types that you can add together, subtract (SQL and Visual Basic spring to mind here).

If you don't want to use libraries (and you have the date stored as 3 integers - Day, Month, Year) it is relatively simple to write a function that will add a day to a given date, and cope with changing months, years, leap years etc - having had to code something like this before I used an array to store the number of days in each month, so I could detect when the month needed to change. 

If you do go down the manual code route then a year is a leap year if : 
```

if (Year Mod 4 == 0)
{
    if (Year Mod 100 == 0)
    {
        if (Year Mod 400 == 0)
            leap_year = True
        else 
            leap_year = False
     }
     else
            leap_year = True
}
else
{
    leap_year = False
}

```


Some more information about the language that you are using would be useful

---

### Post by pp. on 2008-10-27
> **Tony Flury said:**
> a year is a leap year if : 

Year Mod 4 = 0 

That is not true.

---

### Post by Tony Flury on 2008-10-27
I know - i hit the submit button by mistake :( - now corrected.

---

### Post by stylishpants on 2008-10-27
The command is "date -d tomorrow".

For more info, read the "date" command's man page, or (even more useful) the "date" command's info page.

---

### Post by ghostdog74 on 2008-10-27
date -d "tomorrow" is relative to today.
```

# date +%Y-%m-%d -d "1 day 2008-09-30"
2008-10-01

```

---

### Post by jespdj on 2008-10-28
In Java:
[php]// Get a Calendar which is set to today
Calendar cal = Calendar.getInstance();

// Add one day
cal.add(Calendar.DATE, 1);[/php]

---

### Post by davidtuti on 2008-10-28
Many thanks to all.

I must use ksh

Any help?

Thanks!

**************

Any help? Please

---

### Post by davidtuti on 2008-10-31
It's in ksh

Any help???

Many thanks

---

### Post by Zugzwang on 2008-10-31
> **davidtuti said:**
> It's in ksh

Any help???

Many thanks

ghostdog74 has already given you the solution. It works in ksh as well (just try it).

---

### Post by davidtuti on 2008-10-31
> **Zugzwang said:**
> ghostdog74 has already given you the solution. It works in ksh as well (just try it).

Yes, but I would like to do dinamically.
Thanks

---

### Post by Zugzwang on 2008-10-31
> **davidtuti said:**
> Yes, but I would like to do dinamically.
Thanks

What do you mean by that? Please give an example.

---

### Post by davidtuti on 2008-11-03
> **Zugzwang said:**
> What do you mean by that? Please give an example.

For example:

command parm1 parm2 parm3  20080817 parm5
command parm1 parm2 parm3  20080818 parm5
...............
..............
..............
..............
command parm1 parm2 parm3  20081023 parm5

---

