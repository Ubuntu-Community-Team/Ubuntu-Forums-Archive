---
title: "only run it x times in crontab"
date: 2018-01-09
forum: Programming Talk
---

### Post by cazz on 2018-01-09
Hi I going to have a bash script that I was going to run every hour with crontab.
But in the script I just want it to run x times so if I just want it to run 8 times it just going to do that and no more.
I guess I need some kind of textfile to remind the script how many times it have running??

---

### Post by 1clue on 2018-01-09
Easiest way is to have a countdown timer in a file somewhere, but you could also tell the script not to run after a certain date/time. I would do that from inside the script, figuring out a cron expression to match is likely to be difficult.

---

### Post by cazz on 2018-01-09
hmm yes that is a idea too

I just want to make it script to work anytime I going to do use it

---

### Post by SeijiSensei on 2018-01-09
You could run the script eight times per day with a crontab entry like

```
*/3 * * * * /path/to/some/script
```

That will run the script at hours divisible by three.

---

### Post by cazz on 2018-01-09
hmm yes I can do that.
Now I have something to think about.

---

### Post by 1clue on 2018-01-10
> **SeijiSensei said:**
> You could run the script eight times per day with a crontab entry like

```
*/3 * * * * /path/to/some/script
```

That will run the script at hours divisible by three.

No, that will run it every 3 seconds.

[https://docs.oracle.com/cd/E12058_01/doc/doc.1014/e12030/cron_expressions.htm](https://docs.oracle.com/cd/E12058_01/doc/doc.1014/e12030/cron_expressions.htm)

```
0 0 */3 * * * * /path/to/some/script
```

At any rate, cron may not be your service of choice here if you want it to run X times and then stop, but do it every time you want to start the process.

Maybe look at 'at' jobs? **sudo apt install at **Here you would have shell scripts (/bin/sh, not /bin/bash) which are executed when you want them to be. You could pass a parameter N to your script, which would be responsible for scheduling the next job some fixed time later, with N-1 as a parameter, or not schedule anything if N==0.

---

### Post by cazz on 2018-01-10
ahh ok thanks for the info

But I did make it easy for me

use cat to read a textfile that have a number inside and use echo to write a new number.

---

