---
title: "newbie cron and anacron questions"
date: 2012-07-01
forum: New to Ubuntu
---

### Post by lance bermudez on 2012-07-01
Have labtop with 2 user one is for admin other for user. Admin user will not always be login most of time it will be the user.

Have crontab of admin user with
admin@acer:~$crontab -e
# m h  dom mon dow   command
30 * * * * /home/admin/bin/bdscanupdate

How do I set anacron to run the above when the computer has been shutdown.

also how do you set a cron job to run on the 2 tue of each mother? I did a google search and got the below post.

You can just add a control statement at the beginning of the script using the date command to check if the current day is Saturday and if it is the second of the month (it will be between the 8th and 14th of the month):
Code:
#!/bin/bash
if [ $(date +%w) -eq 6 -a $(date +%e) -gt 7 -a $(date +%e) -le 14 ]
then
  <code to be executed here>
else
  <do something>
  exit
fi

I do not know what this means.

---

### Post by Paqman on 2012-07-02
> **lance bermudez said:**
> 
How do I set anacron to run the above when the computer has been shutdown.


You wouldn't need to. Cron will run that command every 30mins when it's on, so the longest delay after startup would be 30 mins, just the same as a machine that was left on.

In short, it's not a job that needs anacron.

The shortest interval available in the default anacron setup is once a day. To run a job in anacron all you need to do is drop the executable script into the appropriate folder such as /etc/cron.daily

> also how do you set a cron job to run on the 2 tue of each mother? I did a google search and got the below post.

You can simply insert the code you quoted into a script than have cron run it.

---

### Post by lance bermudez on 2012-07-05
how do I edit the script for that? Also I was wondering how do I add a script to /etc/cron.daily do I just copy and past the script there?

I want 2 tue of each month so would it look like this?

%w     day of week (0..6); 0 is Sunday
%e     day of month, space padded; same as %_d

#!/bin/bash
if [ $(date +%w) -eq 2 -a $(date +%e) -gt 2 ]
then
/root/bin/update-script
else
/root/bin/backupscript
exit
fi

---

