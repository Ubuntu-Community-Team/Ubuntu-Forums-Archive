---
title: "Command to check if your Ubuntu 20.O4 laptop has been &quot;enslaved&quot;?"
date: 2022-02-01
forum: New to Ubuntu
---

### Post by bhubunt on 2022-02-01
Hi All,
I wonder if there are any "quick" commands to check if one is still in control of one's laptop or if the OS might be compromised?

Although I only use LibreOffice on my laptop, I noticed a lot of the following entries in my system logs, which to me seem strange, as they happen while I am typing essays on my laptop. In other words, I never opened the terminal to give these commands as root: 

pam_unix(cron:session): session opened for user root by (uid=0)
(root) CMD (  cd / && run-parts  --report   /etc/cron.hourly)

I have no special additional software or anything else on this laptop.  I never entered any of these commands for actions running in the background, no cron jobs.

On an Ubuntu platform I read that cron jobs should be checked as such hourly commands etc are signs of having been hacked. How do I check the files for malicious cron jobs?

Thanks for your time!

---

### Post by Holger_Gehrke on 2022-02-01
There are quite a few cron jobs running by default. By default you can drop scripts into /etc/cron/hourly, /etc/cron/daily, /etc/cron/weekly, and /etc/cron/monthly and they will be executed after the given interval. Examples would be the daily rotation of log files and the recreation of the database used by locate. Even if you have no personal crontabs and have removed the scripts from these directories the system wide /etc/crontab will start a session for root and start run-parts to run scripts in the directories. The best way to be certain is to actually read the scripts. Shell scripts are not that hard to understand and most official scripts are fully commented to tell the reader what they are doing and how they go about achieving that goal. 

Beyond that the standard commands for task management (ps, the variants of top), for finding ongoing network communications (netstat), and perhaps lsof for finding open files are useful tools for finding out what your machine is doing. Sadly there's no simple one-command-solution to discovering a hack.

Holger

---

### Post by bhubunt on 2022-02-02
> **Holger_Gehrke said:**
>  The best way to be certain is to actually read the scripts. Shell scripts are not that hard to understand and most official scripts are fully commented to tell the reader what they are doing and how they go about achieving that goal.

Holger

Follow-up question: how do I read the scripts? How do I check the cron jobs being executed?

---

### Post by SeijiSensei on 2022-02-02
Look in /etc/cron.d and the /etc/cron.daily, etc., directories for the scripts that are run routinely. You can view scripts with "less script_name".

On a vanilla installation, you don't need to worry about any of this stuff.

---

