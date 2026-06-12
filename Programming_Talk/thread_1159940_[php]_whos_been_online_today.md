---
title: "[php] whos been online today?"
date: 2009-05-15
forum: Programming Talk
---

### Post by ELD on 2009-05-15
On my online system i wish to find a way to display who has been online in the current day.

I currently have a field in sql for the last active time which has a stored string of the last time the member was active. I am wondering how i can compare that string to a whole day and if it is within the day then show them as having been online?

---

### Post by simeon87 on 2009-05-15
It's easier to use a DATETIME instead of a string because then you can select all users from a particular time interval. If you only want the date, you could also use a DATE and then select all users that have been active on that date. A DATETIME would be convenient in the future when you only want the users of the last few hours.

If the string is in a convenient format, it would work too (i.e., year month day hour minutes seconds because then it first compares the year, then the month, then days, etc which is exactly the order in which you will want to perform the comparison between two "date-strings").

So basically it would be:

- log each user's last active time
- select all users from that table with an active time that's within the current date
- gather the usernames as well and display them as having been online today

Selecting all values from a particular day can be done with:

```

WHERE DATE(active_time) = DATE(NOW())

```

where active_time is a DATE/DATETIME field. See also [http://dev.mysql.com/doc/refman/5.1/en/date-and-time-functions.html](http://dev.mysql.com/doc/refman/5.1/en/date-and-time-functions.html)

---

### Post by ELD on 2009-05-15
When i said string i mean a formatted date into a string like this:
```

strtotime(gmdate("d-m-Y H:i:s"));

```It is real easy to work with that.

Well what you posted is interesting but that won't work with my current setup since that will need me to re-format my field into a "date" field (although that would be easy to do come to think of it, but i also want the time as well).

---

### Post by simeon87 on 2009-05-15
> **ELD said:**
> When i said string i mean a formatted date into a string like this:
```

strtotime(gmdate("d-m-Y H:i:s"));

```It is real easy to work with that.

Well, perhaps, but now we can see that a string and a date aren't the same type of data (which is why MySQL provides DATE and DATETIME).

> **ELD said:**
> Well what you posted is interesting but that won't work with my current setup since that will need me to re-format my field into a "date" field (although that would be easy to do come to think of it, but i also want the time as well).

In case you do convert, storing the date and time is easy, because that's done by inserting/updating:

```

INSERT INTO activity (user_id, active_time) VALUES (1, NOW())

```

If you want to work with strings, you'll probably need to some inefficient comparisons: take the value of gmdate("d-m-Y") and then compare that with all the date-strings to see if they begin with that date; if so, those users have been active on the current day.

---

### Post by ELD on 2009-05-15
I pinched this from a mod on a forum software which doesn't look half bad to learn from:
```

// Load the users online during last period.
if ($site_config['online_period'] == 'current_day')
{
    $date = @getdate(forum_time(false));
    $midnight = mktime(0, 0, 0, $date['mon'], $date['mday'], $date['year']) - ($modSettings['time_offset'] * 3600);
}

else
{
    if ($membersOnlineTodayOptions['period'] == 'last_24_hours') 
    {
        $midnight = time() - 86400;
    }
    else if ($membersOnlineTodayOptions['period'] == 'last_7_days')
    {
        $midnight = time() - 604800; 
    }
}

```
Then just compare the $midnight in the sql, easy peasy by the looks of it :D

---

### Post by Reiger on 2009-05-15
Altough simeon87 has a very good point in using a DATETIME over anything else: what if you later decided that the really neat thing was to have the comparison being performed _against the local time of the user_? That is someone looking at your web page if she/he lives in the CDT region would see a different page from someone looking at your web page if she/he lives in the GMT region when "17 hours ago" some 3rd other person visited your site.

---

### Post by ELD on 2009-05-17
I have a system that changes the times based on what region you are in, no biggy.

---

