---
title: "sorting criteria"
date: 2010-05-10
forum: Programming Talk
---

### Post by boondocks on 2010-05-10
I was trying to sort a large data file by doing:

**cat large_data_file.txt | sort > sorted_large_data_file.txt**

This was working because the data looked sorted:
[COLOR="Blue"]May  9 06:49:24 ...data...
May  9 06:50:22 ...data...
May  9 06:51:09 ...data...
May  9 06:51:53 ...data...
May  9 06:52:00 ...data...
[/COLOR]
But then May 10 came along and now the data is not sorted correctly:
[COLOR="Red"]May 10 11:58:33 ...data...
May 10 11:58:35 ...data...
May 10 11:58:38 ...data...
May 10 11:58:46 ...data...
May 10 11:59:00 ...data...
May 10 11:59:01 ...data...[/COLOR]
[COLOR="Blue"]May  9 06:49:24 ...data...
May  9 06:50:22 ...data...
May  9 06:51:09 ...data...
May  9 06:51:53 ...data...
May  9 06:52:00 ...data...[/COLOR]

It should be sorted like this:
[COLOR="Blue"]May  9 06:49:24 ...data...
May  9 06:50:22 ...data...
May  9 06:51:09 ...data...
May  9 06:51:53 ...data...
May  9 06:52:00 ...data...
May 10 11:58:33 ...data...
May 10 11:58:35 ...data...
May 10 11:58:38 ...data...
May 10 11:58:46 ...data...
May 10 11:59:00 ...data...
May 10 11:59:01 ...data...
[/COLOR]

The lack of a leading zero in the day-of-the-month is the issue.
If it was "May 09" this would not be a problem.
I cannot change the data file.
How should I change the sort criteria?

---

### Post by MadCow108 on 2010-05-10
cat test.txt | sed -e "s/^\(\w\+\) \([0-9]\) \(.*\)/\1 0\2 \3/" | sort | sed -e "s/^\(\w\+\) 0\([0-9]\) \(.*\)/\1 \2 \3/"
that adds leading zeros, sorts and removes them again

---

### Post by boondocks on 2010-05-10
> **MadCow108 said:**
> cat test.txt | sed -e "s/^\(\w\+\) \([0-9]\) \(.*\)/\1 0\2 \3/" | sort | sed -e "s/^\(\w\+\) 0\([0-9]\) \(.*\)/\1 \2 \3/"
that adds leading zeros, sorts and removes them again

That did not work.
Some of the recent data is now missing.
The last line is now:
May 10 00:00:18 ...
I should have more data after that.

---

### Post by boondocks on 2010-05-10
Wouldn't it be simpler to just convert

May 9
to
05 09

or

May 10
to
05 10

and leave it like that.

That would not only take care of the day 
but also the month because otherwise the
same problem would reappear at the end of
May where June would show before May.

---

### Post by stylishpants on 2010-05-10
This is pretty straightforward in ruby.  Just parse the dates and sort on them.

```
ruby -rtime -e 'puts ARGF.readlines.sort_by {|l| Time.parse(l)}' data.txt
```

Something similar would work in perl too if you prefer.

---

