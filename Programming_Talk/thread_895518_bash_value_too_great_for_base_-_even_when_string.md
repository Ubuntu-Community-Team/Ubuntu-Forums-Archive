---
title: "bash value too great for base - even when string?"
date: 2008-08-20
forum: Programming Talk
---

### Post by many_miles on 2008-08-20
I've read the FAQs about posting and I've a fairly good handle on bash programming.

I am trying to get the numerical value of "last month".  Since this is August, the last month value I'm looking for is 7.

Obviously, I can just subtract one from "this month" as long as this month is not 1.  If this month is one, last month is 12.

As you can see, I am using the date +%m command for obtaining the two digit month number.

To do that, I have this code
[PHP]
#!/bin/bash

# First find out what this month is...
THIS_MONTH_NUM=`date +%m`

if [ $THIS_MONTH_NUM -eq 1 ]; then
        SRCH_MONTH_NUM=12
else
        SRCH_MONTH_NUM=$((THIS_MONTH_NUM-1))
fi
[/PHP]

But, on my Hardy Heron Ubuntu, because $THIS_MONTH_NUM contains 08, that produces:
[PHP]
./show_last_month: line 9: 08: value too great for base (error token is "08")
[/PHP]

So, I figured I could force a string comparison by replacing line 6 with
[PHP]
if [ "$THIS_MONTH_NUM" == "01" ]; then
[/PHP]
but, I still get the same error.

I've seen this other posting which I can use as a workaround
[http://ubuntuforums.org/showthread.php?p=4206419](http://ubuntuforums.org/showthread.php?p=4206419)

But, I am more curious as to why it's not a stringwise comparison...

---

### Post by ghostdog74 on 2008-08-20
use GNU date
```

# date +%m -d "1 month ago"
07


```

---

### Post by lswb on 2008-08-20
The reason for the error is that bash will try to interpret numbers with a leading 0 as octal (base 8 instead of base 10). Since "8" is not a valid numerical digit in base 8, it causes the error. You can force it to recognize "08" as a base 10 number by prefixing it with "10#", i.e. "10#08" (substitute X for "10" to change to base X IIRC you can use up to base36 arithmetic by using upper and lower case letters for digits)

So you could change line 4 to THIS_MONTH_NUM="10#`date +%m`"

---

### Post by many_miles on 2008-08-20
> **ghostdog74 said:**
> use GNU date


Wow, that's much simpler than my solution.  Thanks.

---

### Post by many_miles on 2008-08-20
> **lswb said:**
> The reason for the error is that bash will try to interpret numbers with a leading 0 as octal (base 8 instead of base 10). Since "8" is not a valid numerical digit in base 8, it causes the error. You can force it to recognize "08" as a base 10 number by prefixing it with "10#", i.e. "10#08" (substitute X for "10" to change to base X IIRC you can use up to base36 arithmetic by using upper and lower case letters for digits)

So you could change line 4 to THIS_MONTH_NUM="10#`date +%m`"

But, even when the number is within quotes?  I thought that quotes and the use of the == operator would force a string comparison.

---

### Post by lswb on 2008-08-20
> **many_miles said:**
> But, even when the number is within quotes?  I thought that quotes and the use of the == operator would force a string comparison.

It should and when I tested that code on my system, it does just that. Have you checked for any typos or misplaced "fi" and such?

---

