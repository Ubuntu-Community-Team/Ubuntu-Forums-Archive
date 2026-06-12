---
title: "find file older than one month not by x days olds"
date: 2011-12-03
forum: Programming Talk
---

### Post by jao_madn on 2011-12-03
Hi,

I would like to ask about some question on the -mtime option in the find command. I want to move a log files older than one month and planning to used the find -mtime +30 but i have some clarrification does -mtime +30 or -30 refer to x days beyond or between so how about the month. suppose the month with 31 or 28 days. Does the -mtime +30 will include the 1 of the current month if its 31. What i mean is like -mtime +X ; which X refer to number of months not days beyond or between. Im not sure i really understand the find -mtime command how the days been counted. Hope someone can give some better input.. How about other ways to achieve what i had in mind if someone knows something hope they can share it.

Thanks in advance for any input.

---

### Post by ofnuts on 2011-12-03
> **jao_madn said:**
> Hi,

I would like to ask about some question on the -mtime option in the find command. I want to move a log files older than one month and planning to used the find -mtime +30 but i have some clarrification does -mtime +30 or -30 refer to x days beyond or between so how about the month. suppose the month with 31 or 28 days. Does the -mtime +30 will include the 1 of the current month if its 31. What i mean is like -mtime +X ; which X refer to number of months not days beyond or between. Im not sure i really understand the find -mtime command how the days been counted. Hope someone can give some better input.. How about other ways to achieve what i had in mind if someone knows something hope they can share it.

Thanks in advance for any input.mtime is in days (actually in 24-hours periods, so you won't get the same results if you issue it at 8am and 8pm on the same day).

"Older than one month" doesn't completely make sense. If you are in February, is "older than one month" 31, 29, or 28 days old?

if you want to work with dates, use the "-newerXY" paramater (ie, -newermt to check  modification time against an absolute date).

---

### Post by Vaphell on 2011-12-04
```
$ LANG=C date
Sun Dec  4 13:38:08 CET 2011
$ LANG=C date -d "now 1 month ago"
Fri Nov  4 13:38:21 CET 2011
$ LANG=C date -d "now 1 month ago + 1 day"
Sat Nov  5 13:40:36 CET 2011

```
as you see you can go 1 month back (though it sucks big time in cases ofnuts mentioned, it pretty much works reliably only in 1st-28th range). Format the date to suit your needs and use with -newermt
LANG=C is not important, it merely forces date to spit the result out in default english

---

### Post by stylishpants on 2011-12-04
Consider letting logrotate handle this for you instead of rolling your own solution to this common problem.  It should be installed by default on Ubuntu systems.

You can create a congiguratino file in /etc/logrotate.d/ that specifies the names of your logfiles and the rotation handling you want.  There should already be other files there describing the logfile handling for some system utilities, you could use these as a starting point.

See the logrotate man page for more details.

---

