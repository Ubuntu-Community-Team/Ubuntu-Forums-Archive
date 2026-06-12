---
title: "How to get date of tomorrow in console?"
date: 2006-04-02
forum: Programming Talk
---

### Post by cro.smiley on 2006-04-02
Is there a way to get tomorrow date in console, using "date" command or something else?

I need that so i can put new date in /proc/acpi/alarm to wake my computer every day at 7:00.

Date should be in format: yyyy-mm-dd
Thank you.

---

### Post by sphinx on 2006-04-02
I was about to suggest obtaining the day field seperately and incrementing it yourself in the bash script, like this $((`date +%d`+1)) but then I realised that wouldn't work if today was the last day of the month. Otherwise you might end up with a date of 2006-03-32. 

You could program around this problem but I'm sure someone somewhere has already solved this problem in one language or another. As I only really know Java I'll list the code to do it in that, but I'm sure other languages has this abillity too. I realise this code is useless to you if you dont have java installed and if this is the case then hopefully someone else will reply with another solution.

```

import java.util.Calendar;
import java.text.SimpleDateFormat;

public class PrintTomorrow {
    public static void main(String[] args) {
        Calendar cal = Calendar.getInstance();
        cal.setTimeInMillis(System.currentTimeMillis());
        cal.add(Calendar.DAY_OF_MONTH,1);
        SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd");
        System.out.print(sdf.format(cal.getTime()));
    }
}

```

---

### Post by Moobert on 2006-04-02
or in python which comes preinstalled

```
#!/usr/bin/env python

import time
import datetime

day = (24*60)*60
tomorrow = datetime.datetime.fromtimestamp(time.time() + day)
print tomorrow.strftime("%Y-%m-%d")
```

your just need to put it in a text file (ending in .py), then ```
chmod +x <file name>
```the file, then run it from the terminal, with a ```
./<file name>
``` As for alarms i'd look into crontab:

[http://www.adminschoice.com/docs/crontab.htm](http://www.adminschoice.com/docs/crontab.htm)

---

### Post by wmcbrine on 2006-04-02
I found out a while back that "date" is a remarkably powerful and flexible command. Check it out:

 date -d tomorrow

However, I agree that this really sounds like a job for cron.

---

### Post by sphinx on 2006-04-02
[QUOTE=wmcbrine]
 date -d tomorrow
[/QUOTE]

Bah! Foiled by a ridiculously simple command line argument yet again!

---

### Post by thumper on 2006-04-03
If we ignore the date command and go back to python... 

```
#!/usr/bin/env python
# don't need time module
from datetime import datetime, timedelta
tomorrow = datetime.today() + timedelta(1)
# default string representation is extended ISO
date_str = str(tomorrow)[:10]
print date_str

```
:)

---

### Post by cro.smiley on 2006-04-03
Thank you all for help. I think I'll use python to solve this.

btw I think I can't use cron for this cause I need to wake my computer from suspend to RAM, and I can do it only by putting date and time in /proc/acpi/alarm file.
So if I need to wake it up every day I need to refresh file with the date of tomorrow every day.

But nevermind, you all helped a lot.

---

### Post by thumper on 2006-04-03
You could run a cron job everyday that updates the contents of the alarm file to be tomorrows date.  No reason why that would be a problem.

---

