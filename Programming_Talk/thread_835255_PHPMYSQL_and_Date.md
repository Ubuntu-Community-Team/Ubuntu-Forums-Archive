---
title: "PHP/MYSQL and Date"
date: 2008-06-20
forum: Programming Talk
---

### Post by Squizz on 2008-06-20
Hi there

I'm looking for some information regarding php/mysql and dates.

I'm creating a website where a user has to input a specific date;  Firstly, I'd like to know if there's an alternative way to input/store the date other than forcing them to input '2008-01-31' .

With this date, I'd like to display all records where this date is due to arrive in the next 30 days.

I've been trying to look through the manuals, and googling around but to no avail.  Can anyone provide me with a tutorial link or some sample code?

Thanks in advance

---

### Post by smartbei on 2008-06-20
There are javascript calenders that you can use to help users select dates. See [http://www.thefreecountry.com/javascript/calendar-date-picker.shtml](http://www.thefreecountry.com/javascript/calendar-date-picker.shtml) for some free ones.

As for displaying all records: Wouldn't something like:
> 
"SELECT * from `table_name` WHERE DATEDIFF(date, CURDATE()) < 31;"

work?

Note - I haven't tried the sql statement, it just seems fine.

---

### Post by LoneWolfJack on 2008-06-20
> I'm creating a website where a user has to input a specific date; Firstly, I'd like to know if there's an alternative way to input/store the date other than forcing them to input '2008-01-31' .

You can have them write it any way you want, yet you will have to parse it.
If you let them enter mm/dd/yyyy you can parse it to a timestamp with strtotime(). Note, however, that outside of the US, dates are for the very most part written in the forms dd/mm/yyyy or dd.mm.yyyy, which forces you to rearange the string before using strtotime().

Assuming the SQL column you are performing the check on is a valid date format, you can use the acquired timestamp in a pretty simple way by adding the 30 day equivalent in seconds (60*60*24*30) to it and then do

```
SELECT * FROM table WHERE mydate<=mytimestamp
```

You will probably also have to limit the results backwards so you don't get dates from the past returned.

---

