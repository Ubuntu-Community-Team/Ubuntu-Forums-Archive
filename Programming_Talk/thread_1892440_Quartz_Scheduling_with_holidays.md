---
title: "Quartz Scheduling with holidays"
date: 2011-12-08
forum: Programming Talk
---

### Post by jmwalloh on 2011-12-08
Hi, i need to run a job whose description is as follows:
1. I have 8 members to send message to after 24hrs (3600 seconds)
2. 1st member to get it on the first day, second member on the second day and so on till the eighth member gets it
3. FRI and SUN are not working days so no message will be sent on these days to the remaining members
4. If the job starts on MON say 9:00 am, how can implement this either using simpletriggers or crontriggers. Code sample will be highly appreciated

---

### Post by McNils on 2011-12-08
I would create one cron job. Schedule it to trigger on every day (1-4, 6) and leave the logic to figure out correct receiver up to the job. For example store a message counter and use modulo to find correct receiver from an array.

---

