---
title: "Running CRON job on Ubuntu server for SugarCRM"
date: 2012-10-27
forum: New to Ubuntu
---

### Post by Logik_Beta on 2012-10-27
Hey guys,
The topic may sound advanced,but i am pretty inexperienced in Linux.So be descriptive on your answer. 

My environment :Local Linux server 12.04 hosting Sugar CRM 6.5.2.

There is area in sugar CRM called scheduler. I can configured some predefined jobs here. in my case i am trying to run email reminders (ever min/hour/day/month). For this scheduler to be effective, i read some where i need to setup CRON job. So i did some research & finally put following lines in CRONTAB for the root user, as per instructions given in sugarCRM.

> * * * * * cd /var/www/crm; php -f cron.php > /dev/null 2>&1

Well i am creating contracts in my sugarCRM (AOS module) & i want email reminders to be sent for these contracts to the concern person. Now my sugarCRM email is configured correctly & i can send test emails using it. But the CRON + scheduler not giving any result. I can't receive any emails.

Then i tried to read /var/log/syslog & it is showing entry for following line each minute.

> Oct 27 15:03:01 unicomm CRON[28182]: (root) CMD (cd /var/www/crm; php -f cron.php > /dev/null 2>&1) 

I've few questions:
1) what does the CRON job line i've added in crontab mean? cd /var/www/crm; php -f cron.php > /dev/null 2>&1 is not making any sense to me. 
2) How am i suppose to get this thing work? I've searched a lot (including SugarCRM forum), but no luck.

Logik

---

