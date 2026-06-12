---
title: "Deleting files should include verification, and, what script do you adopt for batch?"
date: 2015-11-13
forum: Programming Talk
---

### Post by jon80 on 2015-11-13
I tend to make errors sometimes, and, I am not sure whether it is prudent to use verification in scripting when deleting or whether one should adopt archiving scripts rather than removal scripts.  It is possible that data consists of databases and also of large volumes of text or other data, so the scripting problem becomes a relevant administrative task to script.

What is your opinion on this with respect to systems administrations tasks you might have and any scripts you might want to share for reference?

See % rm -i foo

Sourced from [https://en.wikipedia.org/wiki/Rm_(Unix)](https://en.wikipedia.org/wiki/Rm_(Unix)).

---

### Post by Habitual on 2015-11-13
Non-interactive shell scripts would ignore "rm -i" environment settings in say ~/.bashrc. so you can't verify.
and if you wrote the script using rm -i *, your script would stop until the prompt was satisfied.
This would break scheduled scripts (via cron)
I archive every day, and then only keep the first of the month for months past.
Except for the current month, I keep every day.

---

### Post by leclerc65 on 2015-11-13
I usually do a Find first, then Remove after verification, for example.
```

sudo find /media/Data -iname '*.appledouble*' 
sudo find /media/Data -iname '*.appledouble*' -exec rm -rf {} \; 

```

---

### Post by Bucky Ball on 2015-11-13
*Thread moved to **Programming Talk**.*

---

