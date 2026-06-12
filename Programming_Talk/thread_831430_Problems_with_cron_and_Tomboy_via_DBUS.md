---
title: "Problems with cron and Tomboy via DBUS"
date: 2008-06-16
forum: Programming Talk
---

### Post by JHSaunders on 2008-06-16
Hi,

I'm trying to create a little application that automatically pops up a new tomboy note every hour so my girlfiernd can log her time at work more easily. The tomboy dbus scripting went fine, but when I tried to set a cron job to pop it up every hour it doesn't work.

I don't have my code here (its on my girlfriends machine) but I have attached some simpler code from arstechnica (with a few minor changes), test.py. 

All I want to do is set up a cron job that correctly runs this script every minute (Which would pop up a new tomboy note). If I can do that then I can set it up to work correctly. I have checked that the code is being executed, and it is (I pipe the output to a file and that file is being changed) but the new tomboy note is not popping up.

I have been reading about having to set the DISPLAY environment variable, which I think I am doing correctly, but still it does not work.

Anyone know what is going wrong? Would appreciate the help.

James.

---

