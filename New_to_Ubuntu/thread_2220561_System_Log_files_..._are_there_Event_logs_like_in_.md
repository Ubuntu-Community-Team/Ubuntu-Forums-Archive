---
title: "System Log files ... are there Event logs like in Windows?"
date: 2014-04-28
forum: New to Ubuntu
---

### Post by cwmoser on 2014-04-28
I am very familiar with the Event logs in Windows operating systems.

I got curious when I suspected my PC rebooted after stepping away for a few hours
and wondered if there are logs that I can review to see what was the reason for the
reboot.  I've used the **dmesg** command in the past to discern USB connections
but little else.  Can someone tell me a little more about Linux log files and some utilities
for viewing them?

Thanks

Carl

---

### Post by slickymaster on 2014-04-28
Please see this: [LinuxLogFiles]("https://help.ubuntu.com/community/LinuxLogFiles")

---

### Post by cwmoser on 2014-04-28
Thanks for that description of Linux Log Files.

Unlike with Windows, I know I have not been pressed to examine the log files with Ubuntu.
But, it does appear that the Linux log files are quite a bit more cryptic than Windows OS's.

Carl

---

### Post by squakie on 2014-04-28
Does not syslog (and it's saved older versions) not show the date/time of a booting process?

---

### Post by slickymaster on 2014-04-29
**syslog** collects messages of various programs and services including the kernel, and stores them, depending on setup, in a bunch of log files typically under /var/log.

---

### Post by SeijiSensei on 2014-04-29
> **cwmoser said:**
> But, it does appear that the Linux log files are quite a bit more cryptic than Windows OS's.

Funny, the last time I looked at Windows Event Viewer I thought it provided remarkably little useful information compared to Unix logs.

Every boot is logged in /var/log/syslog, usually with the same level of detail as provided by dmesg.  If you have logrotate running, you'll see that each week's version of syslog is dated.  Just pick the one that includes the period when your machine went down.  If you know it happened on April 23rd at 15:42, you just can open the log in a text editor and search for "Apr 23 15:4" to see all the entries between 15:40 and 15:49.

---

