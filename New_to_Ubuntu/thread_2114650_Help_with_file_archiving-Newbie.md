---
title: "Help with file archiving-Newbie"
date: 2013-02-10
forum: New to Ubuntu
---

### Post by gijs33 on 2013-02-10
Hi All-

I have a cron job that runs every morning at 1AM that goes out and picks up client data and redirects it to a file in my var/logs. 

This is a sample i moved to a test env. to play around so the time is obviously not the am i was playing around with date formatting on the output log file redirect but it wasn't working.

5,10,20,30,40,50,55 * * * * /home/jstewart/scripts/shippingdata.sh >> /var/log/shipping.log


This file is huge because it is continually being appended daily.

I am trying to figure out how to separate the files out by date so that when i have to go back and troubleshoot if a client has an issues I don't have to search one large file.

I don't know if the best approach is to try to rename my file extension in the redirect part of my cronjob or should i be changing the shell script. Sorry I'm very new and there is so much out there i have been reading for days that is really cool stuff I just need to start with the first logical step. Was wondering if any of you experts in file management had any suggestions.

I would like the output to be written as something like this:
shipping20130210.log
shipping 20130211.log
etc.

Then i would think the next step is figuring out the logrotate feature to eventually move these files elsewhere for archiving.

Any help is very much appreciated.

Thank you-

Jeanna

---

