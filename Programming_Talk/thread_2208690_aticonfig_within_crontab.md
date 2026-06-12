---
title: "aticonfig within crontab"
date: 2014-03-01
forum: Programming Talk
---

### Post by IanVaughan on 2014-03-01
Hiya,

I'm trying to read some values from my AMD GPU via aticonfig within a script started via a crontab.

Its running under the superuser's cron (i.e. "sudo crontab -e)
```

* * * * * /home/ian/monitor.sh

```

(I've also tried :
```

* * * * * DISPLAY=:0 /home/ian/monitor.sh

```

The file its running is a exec, owned by root :
```

4 -rwxrwxr-x 1 root root 2645 Mar  1 21:22 monitor.sh

```

And looks like this :
```

#!/bin/bash
# monitor.sh

temp=`DISPLAY=:0 /usr/bin/aticonfig --odgt`
echo "$temp" >> /tmp/temp

```

Every minute I get the following in the output file :
```

ERROR - X needs to be running to perform AMD Overdrive(TM) commands

```

But when I manually run the script, it works fine.
i.e.. running "sudo ./monitor.sh" appends this to the output file
```

Default Adapter - AMD Radeon R9 290 Series
                  Sensor 0: Temperature - 80.00 C

```

I can't see/find what I'm missing, can anyone help me on this?

Many thanks in advanced.

---

### Post by ian-weisser on 2014-03-01
I suspect you may be missing another environment variable that your X-based terminal has, but that the cron environment lacks.

---

### Post by IanVaughan on 2014-03-02
Thanks, I could not for the life of me find out what was missing, I even used my profile from the script!

But I solved it by using my user crontab and not superuser! :sigh:

---

