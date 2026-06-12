---
title: "Getting the last saturday of the month"
date: 2009-06-07
forum: Programming Talk
---

### Post by Scormen on 2009-06-07
Hi,

I would like to get the date of the last saturday of the month in Bash.
If we look to this month (june 2009) it would be "27".

I have this (week is starting on monday):

```
saveFullMonthOn='6'
lastXDay=`cal | awk {'print $saveFullMonthOn'} | xargs | /usr/bin/cut -d" " -f5`
```

But that is printing "We" instead "27".
Whats going wrong?

Thanks.

---

### Post by Scormen on 2009-06-07
Problem [solved]("http://forum.ubuntu-nl.org/programmeren/print-de-laatste-zaterdag-van-de-maand"):

> saveFullMonthOn='6'
lastXDay=`cal | awk {"print "'$'"$saveFullMonthOn"} | xargs | /usr/bin/cut -d" " -f5`

---

### Post by ghostdog74 on 2009-06-07
> **Scormen said:**
> Problem [solved]("http://forum.ubuntu-nl.org/programmeren/print-de-laatste-zaterdag-van-de-maand"):

that will print 26 instead of 27.

here's another way, with only gawk
```

awk 'BEGIN{
 for(i=1;i<=31;i++){
    day=sprintf("%02d",i)    
    d="2009 06 "day" 00 00 00"
    if ( strftime("%a",mktime(d)) == "Sat"){
     lastsat=day
    }
 }
 print "Last sat is: " lastsat
}'

```

---

### Post by Scormen on 2009-06-07
Is your week starting on sunday mabye?

---

### Post by ghostdog74 on 2009-06-07
> **Scormen said:**
> Is your week starting on sunday mabye?

does it matter?

---

### Post by unutbu on 2009-06-07
Scormen, the command
```
lastXDay=`cal | awk {"print "'$'"$saveFullMonthOn"} | xargs | /usr/bin/cut -d" " -f5` 

``` only works on certain months because

```
cut -d" " -f5
```

will only work when the last saturday happens to be the fourth saturday of the month.
Some months like May 2009 had five saturdays.

An alternative to ghostdog74's solution would be

to save this as ~/bin/last_sat
[PHP]
#!/usr/bin/env python
import sys
import datetime
from dateutil.relativedelta import relativedelta,SA
print (datetime.date(int(sys.argv[1]),int(sys.argv[2]),1)+relativedelta(day=31,weekday=SA(-1))).day
[/PHP]
make it executable (of course)
[PHP]
chmod 755 ~/bin/last_sat[/PHP]

and use it in your script like this:
[PHP]
lastXDay=$(last_sat 2009 $saveFullMonthOn)
echo $lastXDay[/PHP]

In general, "last_sat YEAR MONTH" will return the day of the last saturday in year YEAR and month MONTH.

Or, as a one-liner:

[PHP]lastXDay=$(python -c 'import sys;import datetime;from dateutil.relativedelta import relativedelta,SA;print (datetime.date(int(sys.argv[1]),int(sys.argv[2]),1)+relativedelta(day=31,weekday=SA(-1))).day' 2009 6)
[/PHP]

---

### Post by Scormen on 2009-06-07
Sometimes?

My output is realy:
> root@test:/home/kris# ./test.sh 
27

Edit: unutbu was first. :)

@unutbu:
Thank, but I don't know anything about python, but I understand what you mean.

What do you think about this one?
```
cal | awk "{ if(\$6!=\"\") x=\$6; } END { print x }"
```

---

### Post by unutbu on 2009-06-07
ghostdog74 knows much more about awk than I do, so I would listen to his opinion.
That said, 
```

cal -m | awk "{ if(\$6!=\"\") x=\$6; } END { print x }"
```

looks like a good solution to me. (I added the -m flag so cal will make Monday the first day of the week. That way your script will work independent of locale.)

---

### Post by ghostdog74 on 2009-06-07
> **Scormen said:**
> Sometimes?

My output is realy:


Edit: unutbu was first. :)

@unutbu:
Thank, but I don't know anything about python, but I understand what you mean.

What do you think about this one?
```
cal | awk "{ if(\$6!=\"\") x=\$6; } END { print x }"
```
don't have to put slashes
```

cal -m | awk '$6!=""{x=$6;} END { print x }'

```
also, no need the if statement.

---

