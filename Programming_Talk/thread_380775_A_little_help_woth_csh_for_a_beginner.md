---
title: "A little help woth csh for a beginner"
date: 2007-03-10
forum: Programming Talk
---

### Post by Irvius on 2007-03-10
):P Hello Ubuntu users!
I'm a happy italian Ubuntu 6.10 user, pushing the edge of this O/S for scientific purposes in the field of meteorology and it suits me well.
I've a question for you great scripters.
Actually, my weather forecasts of MM5 model lie on a mega script that every morning puts fresh maps on my site. But this mega script has an issue.

I need to create a text file in which the first lines have the today date and the lasts show the current date + 3 days. For now, my csh script just get the date in format YY MM DD and I defined a variable ENDDAY= $STARTDAY + 3.
Obviously, this approach is useless when the end of the month is near. In fact, if the current date is March 29 (e.g.), with that syntax, the final day will be March 32...  
I'm a bit confused about the solution of that... can you please suggest me some hints?

Thank you very much, your efforts will be helpful serving my local community weather safeguard.

---

### Post by Irvius on 2007-03-10
):P Hello Ubuntu users!
I'm a happy italian Ubuntu 6.10 user, pushing the edge of this O/S for scientific purposes in the field of meteorology and it suits me well.
I've a question for you great scripters.
Actually, my weather forecasts of MM5 model lie on a mega script that every morning puts fresh maps on my site. But this mega script has an issue.

I need to create a text file in which the first lines have the today date and the lasts show the current date + 3 days. For now, my csh script just get the date in format YY MM DD and I defined a variable ENDDAY= $STARTDAY + 3.
Obviously, this approach is useless when the end of the month is near. In fact, if the current date is March 29 (e.g.), with that syntax, the final day will be March 32...  
I'm a bit confused about the solution of that... can you please suggest me some hints?

Thank you very much, your efforts will be helpful serving my local community weather safeguard.

---

### Post by bapoumba on 2007-03-10
@ Irvius: merged your duplicate thread in here.

---

### Post by LotsOfPhil on 2007-03-10
Today is March 10, 2007 so you get 070310, right?

If you use a different format for the date (date +%Y%j) you'll get 2007069. Would that work?

You'll still have a jump when you get to 2008 (2007365 -> 2008001).

---

### Post by WW on 2007-03-10
Irvius,

In the next minute or so, I bet someone will come up with a one line method for doing what you want.  In the meantime, here is a short python script that you could try.  The command **dateplus** takes two arguments. The first is the amount of time to add to the current time, and the second is the format with which to print the resulting new date. For example:
> $ ./dateplus 3
14:45:27 03/13/07
$ ./dateplus 3 "%F"
2007-03-13
$ ./dateplus 0
13:46:16 03/10/07
$ ./dateplus 12h
01:46:19 03/11/07

See 'man strftime' for valid formats.

The code is here, and I have also attached the python file.  If you use the attached file, rename 'dateplus.py' to 'dateplus' and make it executable to use it like I did above.

```

#!/usr/bin/python

#
# dateplus
# ... by WW
#

import sys
import time

if  len(sys.argv) < 2 or len(sys.argv) > 3:
    sys.stderr.write("use: dateplus addtime fmt\n")
    sys.stderr.write("where addtime is the time to add to the current time, and fmt is the format\n")
    sys.stderr.write("with which to print the date.  See 'man strftime' for documentation of the\n")
    sys.stderr.write("valid formats.  addtime must be a number, followed optionally by either an\n")
    sys.stderr.write("'s', 'm', 'h' or 'd' meaning seconds, minutes, hours, and days, respectively.\n")
    sys.stderr.write("If the last character in addtime is not one of those four, 'd' is assumed.\n")
    sys.stderr.write("The default fmt is '%X %x'.\n")
    sys.exit(1)

multipliers = {'s':1, 'm':60, 'h':60*60, 'd':24*60*60}

lastchar = sys.argv[1][-1]
if lastchar in ('s','m','h','d'):
    numstr = sys.argv[1][0:-1]
    mult = multipliers[lastchar]
else:
    numstr = sys.argv[1]
    mult = multipliers['d']

try:
    addtime = float(numstr)
except ValueError:
    sys.stderr.write("Invalid number given in the first argument.\n")
    sys.exit(2)

if len(sys.argv) == 2:
    fmt = "%X %x"
else:
    fmt  = sys.argv[2]

now = time.time()
then = now + addtime*mult;
thenstr = time.strftime(fmt,time.localtime(then))
print thenstr

```

---

### Post by Mr. C. on 2007-03-10
So much code!

Here's your solution:
```

date
date -d '+3 days'  
```

---

### Post by WW on 2007-03-10
Hey Mr.C., I figure someone would come up with a one-liner.  I have to remember to look at documentation with **info**, not just **man**.

---

### Post by Irvius on 2007-03-13
Men, you're great!
Thank you very much to all of you and see you soon on Ubuntu!:popcorn:

---

