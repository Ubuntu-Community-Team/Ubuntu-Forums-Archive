---
title: "Ubuntu 12.04 not booting sometimes"
date: 2012-09-14
forum: New to Ubuntu
---

### Post by darkeale on 2012-09-14
Hi,

Sometimes when I try to boot into Ubuntu it doesn't work.  It just freezes with the purple background and nothing happens.  Keyboard presses and shortcuts don't do anything.  I have to press and hold the power button to turn the computer off then turn it on again.  Seems to happen about 1 in 5 boot ups.  Anyone know what I can do to try to find the problem. I have a Fujitsu Siemens Amilo li1718 laptop with ATI Radeon Xpress 200M graphics card.

Thanks,
Alex

---

### Post by fernandohleme on 2012-09-14
Absolute beginer talk, and absolute beginner solution. Have you tried reinstalling it? When I get these weird bugs I just do it all over again and it works fine. Much better than trying to fix it.

---

### Post by 2F4U on 2012-09-14
Directly after a failed boot when you are able to get into the system again look into the system log and search for the failed boot attempt. The system log should have the reason why the boot failed.

---

### Post by darkeale on 2012-09-14
This seems to be a recurring problem for me with Linux.  It happened with Debian and with previous versions of Ubuntu as well

---

### Post by newb85 on 2012-09-14
> **2F4U said:**
> Directly after a failed boot when you are able to get into the system again look into the system log and search for the failed boot attempt. The system log should have the reason why the boot failed.

Since this is Absolute Beginner Talk, perhaps you could explain how to do this...

---

### Post by darkeale on 2012-09-14
I'm looking at syslog from today (a crash happened this morning) and I don't see anything resembling an error message there, although to be honest I'm not sure what I should be looking out for

---

### Post by darkeale on 2012-09-14
I wonder if I might have found something.  I am looking at syslog in log file viewer.  At the time I booted up and it failed there is only one record:-

Sep 14 14:17:01 alex-AMILO-Li-1718 CRON[3260]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

This same message appears earlier in the log too, at the same time as another failed boot attempt.  These messages seem to only appear with failed boots, and they are the only message recorded at that boot attempt.  Could it be the problem, and what does it mean?

---

### Post by muteXe on 2012-09-14
> **fernandohleme said:**
> Absolute beginer talk, and absolute beginner solution. Have you tried reinstalling it? When I get these weird bugs I just do it all over again and it works fine. Much better than trying to fix it.

Bad advice in my opinion.

---

### Post by darkeale on 2012-09-14
In auth.log, there is only this at the same time as the failed boot attempts:

Sep 14 14:17:01 alex-AMILO-Li-1718 CRON[3259]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 14 14:17:01 alex-AMILO-Li-1718 CRON[3259]: pam_unix(cron:session): session closed for user root

---

### Post by darkeale on 2012-09-15
Ok, I think I may have a solution...The cron.hourly folder was empty apart from a .placeholder file, so I have commented out the line in crontab relating to cron.hourly, and so far so good. will test for a few more days before marking as solved.  Hope it does work because this problem has plaged every Linux distro I have tried on this laptop!

---

### Post by yoreei on 2012-09-15
This has happens to me too but I it wasn't that much of a 'problem' for me because when it happens:
1) I click CTRL+ALT+F1
2) Write my username and password
3) type **startx**
And everything works fine. This is not a complete solution but a temporal work-around for the problem.
By the way, are you using the Ubuntu Minimal CD? I am asking this because this only happens to me on my laptop - my only computer that runs on Ubuntu Minimal installation.

---

### Post by darkeale on 2012-09-15
I have tried that workaround but it didn't work for me.  No I'm not using the minimal version, just the standard version.

Thanks

---

### Post by Bashing-om on 2012-09-15
darkeale; Hi !

Just a comment. I have been involved with fault isolation for some little time. In your instance I am aware of only two things that can cause this:
  1. Graphics card issues
   2. Two wireless modules being loaded.( the erroneous sometimes loaded prior to system startup)

If 1) boot up with the parameter "nomodeset" see what haps.
if 2) run the command lsmod from terminal and if two mods for same device loaded, blacklist one of them.

// as it happens with a number of different versions/distros...something in common with the kernels ?//[INDENT]my attempt to help ==>BDQ
[/INDENT]

---

### Post by darkeale on 2012-09-18
Hi,

Thanks for your advice.  I have tried to nomodeset fix before without any luck.  But let's try it again combined with the crontab changes.  And no mods for same device loaded.  I have been problem free for nearly a week after commenting out the line in crontab, but today there was a crash again.  No traces of it in any of the logs

---

### Post by Bashing-om on 2012-09-18
Not good ! Amongst all the logs you have looked into ...how bout the ~/.xsession-errors.
see if 'X" reports anything ???

 It probably wont help, can't hurt.

---

