---
title: "get top 10 cronjobs for last week"
date: 2014-11-18
forum: New to Ubuntu
---

### Post by marchello_lippi2 on 2014-11-18
Hi all, 

How do I get top 10 cronjobs for last week? 
Thanks ahead.

---

### Post by ian-weisser on 2014-11-18
What do you mean by 'Top 10'?
Most frequent? Favorite? Most characters?

You can check your /etc/cron.d/ and /etc/cron.hourly . The jobs are predictable, and root cron jobs are already sorted by frequency....
You can sift through /var/log/syslog .

---

### Post by marchello_lippi2 on 2014-11-18
[ 						 							]("http://ubuntuforums.org/member.php?u=1841707")[**[COLOR=#000000]ian-weisser[/COLOR]**]("http://ubuntuforums.org/member.php?u=1841707"),
thanks for your answer. Speaking of top 10 cron jobs I mean 
1) top 10 time consuming
2) top 10 cpu consuming. 
Also I'd like to compare how jobs worked last time and month ago (if possible). 
Any help?

---

### Post by Impavidus on 2014-11-18
You could time the cronjob using **time** (prepend it to the command) and send the output to a log file.

---

### Post by ian-weisser on 2014-11-18
Your system does not collect nor store those statistics. You can build a collection mechanism if you really want to.
 
If you look in /var/log/syslog, you can see what is collected. That's what your system collects.

Here is an example:
```
ian@rashaverak:~$ cat /var/log/syslog | grep cron | less
Nov 18 06:46:12 rashaverak anacron[14584]: Job `cron.daily' terminated
Nov 18 06:46:12 rashaverak anacron[14584]: Job `cron.weekly' started
Nov 18 06:46:13 rashaverak anacron[15585]: Updated timestamp for job `cron.weekly' to 2014-11-18
Nov 18 06:46:24 rashaverak anacron[14584]: Job `cron.weekly' terminated
Nov 18 06:46:24 rashaverak anacron[14584]: Normal exit (2 jobs run)
Nov 18 07:17:01 rashaverak CRON[15762]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
```

You can see that all the weekly jobs together took 12 seconds.
Daily jobs began at 6:32:33 (look in yesterdays syslog for that, logrotate is a daily job), so daily tasks took a bit under 14 minutes.
Hourly jobs took 0 seconds - no jobs at all (my /etc/cron.hourly is empty).

I suppose if you really need to know the runtime of each cron job, you can wrap the job in a script that records time and CPU usage, and outputs them to the log...or to your own data collector. Do you know how to script a wrapper like that? 

Is there a problem you are trying to solve? Or is this curiosity?

---

