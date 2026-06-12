---
title: "How to get the previous hour based on a date?"
date: 2013-10-17
forum: Programming Talk
---

### Post by OrangeMadness on 2013-10-17
The problem is that I have a given date, say 2013-10-17 05:10 and I want to get the previous hour: 2013-10-17 04:10

The closest I could find in forums is some awk date arithmetic, but I figured I will ask for an opinion also here. 

I am trying to get a calendar like behavior 
e.g. 
 2013-10-17 00:30 => 2013-10-16 23:30
       2013-10-01 00:30 => 2013-09-30 23:30

Can't get anywhere near that in linux environment. Figured I could compile a small Java program and use the Calendar class to do only this task but then... The whole project has been written in shell script so far, wouldn't be nice to spoil it in the end.

Any ideas?

---

### Post by steeldriver on 2013-10-17
You could convert to seconds, subtract 3600, then convert back to a date e.g.

```

$ dateval="2013-10-17 00:30"
$ datesec="$(date '+%s' --date="$dateval")"
$ date --date="@$((datesec - 3600))" '+%Y-%m-%d %H:%M'
2013-10-16 23:30

```

EDIT: or even easier

```

$ date --date='2013-10-17 00:30:00 1 hour ago' '+%Y-%m-%d %H:%M'
2013-10-16 23:30

```

or with a date variable *$dateval*

```

$ date --date="$dateval 1 hour ago" '+%Y-%m-%d %H:%M'
2013-10-16 23:30

```

---

### Post by OrangeMadness on 2013-10-17
So converting to seconds, do arithmetic, back to whatever format you like does the job
Works like a charm,
Thank you Sir

---

### Post by SeijiSensei on 2013-10-17
I'd just use the date command:

```
date --date='1 hour ago'
```

You can format the result however you like.  See "man date" for details.

To get the format you used above:

```

date '+%Y-%m-%d %H:%M' --date='1 hour ago'

2013-10-17 16:57
```

You need those single quotes around the date format string to enable you to have embedded spaces.

To convert an arbitrary date, I'd either use an environment variable or a positional parameter from the command line.  For instance,

```

DATE='October 12, 2013 3:44 PM'
date '+%Y-%m-%d %H:%M' --date="$DATE 1 hour ago"

2013-10-12 14:44

```

Note the use of double quotes so bash will replace $DATE with its value.

---

