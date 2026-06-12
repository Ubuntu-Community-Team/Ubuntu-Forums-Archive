---
title: "time is incorrect in ubuntu"
date: 2012-08-08
forum: New to Ubuntu
---

### Post by paichkash on 2012-08-08
hi
i have dual boot in xp the time is ok but in ubuntu its wrong..now its 2:34 am date is 9 august 2012 in xp (and my watch) and in ubuntu its 9 august 2012 but time is 7:37 AM ?
please help me do the following..

ubuntu show correct time 
and at times when my bios resets the time (due to drained battery) it updates time from nntp server (update time online)

i am in pakistan so my time zone is +5 GMT.. 

when i click the clock click edit in the "clock prefrences" window i select the region Islamabad Asia/karachi and click on edit my time zone is shown as GMT+5 which should be gmt+5 .. dont know where is the issue..
help


thanks

---

### Post by Karlchen on 2012-08-08
Hello, paichkash.

Everyone dual-booting Windows and Ubuntu is likely to encounter the reported problem. Therefore there are tons of more or less helpful instructions out there telling how to resolve the problem. Here is one of them: **[How to fix the time sync issue when dual-booting Ubuntu and Windows]("http://operating-systems.wonderhowto.com/how-to/fix-time-sync-issue-when-dual-booting-ubuntu-windows-340402/")**
The source of trouble is that Windows assumes your hardware clock has been set to your local time, but Ubuntu assumes the hardware clock has been set to UTC.
So the solution is to teach both OSes to make the same assumption. (see article above)

HTH,
Karl

---

### Post by paichkash on 2012-08-11
ok i solved this issue.. 
i changed utc=no in the config file... now is ok in both os'es..
thanks

---

