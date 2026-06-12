---
title: "Shell script to schedule and run a C program"
date: 2011-05-17
forum: Programming Talk
---

### Post by IEOR on 2011-05-17
Hi people, 

I am new to shell programming so I may need some help. I have a C program that can run from the command line like this:

$ checkfiles filelist.txt

checkfiles is a program that can monitor certain files in filelist.txt

Now I want to write a shell script that can run this program at a specified time or frequency. Can somebody show me how to do it? Thanks :)

---

### Post by Some Penguin on 2011-05-17
Read the 'cron' manual page.  cron is all about running specified commands according to a schedule.

---

### Post by IEOR on 2011-05-17
Hi Penguin, can we do something without having to resort to 'cron'. I am a shell scripting novice so I just want to use some basic tools. Thanks.

---

### Post by r-senior on 2011-05-17
Cron *is* a basic tool. Try this quick start:

[http://adminschoice.com/crontab-quick-reference](http://adminschoice.com/crontab-quick-reference)

There used to be a GUI tool in the repositories for setting up cron jobs but I don't remember what it was called.

---

### Post by IEOR on 2011-05-18
Hi Mr. Senior! I got you, man. My script is working now. Thank you all for your help! :)

---

