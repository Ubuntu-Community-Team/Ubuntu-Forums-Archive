---
title: "cron ends jobs early?"
date: 2007-01-02
forum: Programming Talk
---

### Post by Mateo on 2007-01-02
i am trying to get cron to record an internet radio show daily. I created a script which runs streamripper and then gets rid of unnecessary files after it's done.  I set up crontab to run the script every day at a specific time, and it does so, but it cuts off after only downloading about 1megabyte (about 15 minutes, I think), while I have the script set up to record for 3 hours.  When I run the script on my own, it doesn't stop after 1megabyte is downloaded.  Only in crontab.

Does crontab stop jobs?  what could be my possible mistake here?

---

### Post by Mateo on 2007-01-03
i'm going to go ahead and bump this, just in case someone knows of something about how long crontab waits on jobs.

i'll do some testing later to see if I can pin down for sure that the problem is with crontab (by making sure the file size is consistently more or less the same, by timing the jobs, and testing the script both myself and with crontab).  then we can see where we should go from there, to pinpoint where the problem is.

---

### Post by Mateo on 2007-01-03
ok, testing complete.

When running the script on my own, it works fine.

When running the script with crontab, the file is always 1008kb in size.  Always.  I even changed the length to download with streamripper, but still 1008kb. 

So it's obviously something with crontab.  It's stopping streamripper after 1008kb.  Why could that be?

---

### Post by Mateo on 2007-01-04
here's the cron command I am using:

00 10 * * 1-5 /home/user/.script


I also tried 

00 10-13 * * 1-5 /home/user/.script

with no luck.  still 1008kb.

---

### Post by Mateo on 2007-01-06
bump

---

### Post by Mateo on 2007-01-09
bump

---

### Post by eteran on 2007-01-09
Thats not enough information. Please tell us the language the script is written in and if possible you could post the whole script/relevant parts.

Some scripting languages have limited runtime for a single script. PHP for example is limited to 15 minutes by default iirc. Anyways, I think the script you're using is causing the malfunction, not the crontab.

---

### Post by Mateo on 2007-01-09
Thanks for responding eteran.  It is a bash script.  I know that the problem is cron related because I have tested the script by itself and it works 100% as wanted.  only the problem occurs when using cron..

**But** it appears to have fixed itself.  I don't know what, I haven't touched the script or basic commands of cron (only adjusted the times a bit for testing).  One of the weird things about Linux.  Something might not be working one minute, but working fine the next.

---

### Post by LotsOfPhil on 2007-01-11
Just a thought, you could run it in the background:

00 10 * * 1-5 /home/user/.script &

---

### Post by grahams on 2007-01-19
I believe streamripper outputs too much to stdout and this screws up cron. 

Try adding ">/dev/null 2>&1" to the end of the command in crontab. This directs streamrippers text and error text  to /dev/null. This works for me

My crontab looks like this 
# crontab -l 
# m h  dom mon dow   command
00 11 * * 5 tsocks streamripper [http://205.234.249.144:80](http://205.234.249.144:80) -d ~/Music/ -l 7200 >/dev/null 2>&1
00 16 * * 1-5 tsocks streamripper [http://205.234.249.144:80](http://205.234.249.144:80) -d ~/Music/ -l 3600 >/dev/null 2>&1

---

### Post by devilbush on 2007-03-02
> **grahams said:**
> I believe streamripper outputs too much to stdout and this screws up cron. 

Try adding ">/dev/null 2>&1" to the end of the command in crontab. This directs streamrippers text and error text  to /dev/null. This works for me

My crontab looks like this 
# crontab -l 
# m h  dom mon dow   command
00 11 * * 5 tsocks streamripper [http://205.234.249.144:80](http://205.234.249.144:80) -d ~/Music/ -l 7200 >/dev/null 2>&1
00 16 * * 1-5 tsocks streamripper [http://205.234.249.144:80](http://205.234.249.144:80) -d ~/Music/ -l 3600 >/dev/null 2>&1

This is just the tip I was looking for.  Works like a charm.  Thank you!

db

---

### Post by tweston on 2007-11-17
if you invoke your script from crontab, you need the --quiet option for the streamripper command within that script

interestingly, this isn't true if you start the same script directly as a command line (even with the "&" background option)

---

### Post by tweston on 2007-12-10
when running streamripper from crontab, you need to suppress the text output from streamripper

use the --quiet option in the streamripper command line

---

### Post by naildeca on 2010-07-18
Thanks, grahams and tweston, using the --quiet option seems to have solved my problem. It is odd that I did not have a problem when I was running Dapper Drake or Hardy Heron but upon upgrade to Lucid Lynx the problem cropped up for me. At the time of most of this tread you all were running the earlier versions, same as I was and I was not having this problem.

---

