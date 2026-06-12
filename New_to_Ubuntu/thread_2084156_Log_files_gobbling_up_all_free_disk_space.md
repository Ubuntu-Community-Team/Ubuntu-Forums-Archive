---
title: "Log files gobbling up all free disk space"
date: 2012-11-14
forum: New to Ubuntu
---

### Post by pjstock on 2012-11-14
I recently installed Xubuntu 11.10 on this 20GbHDD laptop and having battled my way through enabling the wifi (thanks to the intrepid efforts of people here.) I am now having a problem where my log files (like kern.log and syslog, under /var/log) are ballooning out of control, to 10+Gb each.

Very quickly (in the course of a few hours of even no actual use) the HDD free space is down to Zero and everything not surprisingly shuts down.

I can remove the offending log files with a sudo rm etc. but it just replicates itself.

someone has suggested that there must be something seriously wrong somewhere for the log files to grow like a nasty cancer cell.

can anyone advise?

Thanks

Peter

---

### Post by windscape on 2012-11-14
Hi,

It would help if you posted the last 10 lines or so from the log files.

---

### Post by steeldriver on 2012-11-14
Hi if you post some of the offending logfile entries maybe we can figure out what's causing them and fix it

---

### Post by dannyboy79 on 2012-11-14
i believe you can tell logrotate to not save as many files and possibly the size of a log file. look for /etc/logrotate.conf or similar.

---

### Post by pjstock on 2012-11-14
> **windscape said:**
> Hi,

It would help if you posted the last 10 lines or so from the log files.

good idea.
But my text editors don't seem to want to open the currently 3.5Gb syslog.1 file.

any suggestions for how I can get a peek at those last 10 lines or so?

Peter

---

### Post by windscape on 2012-11-14
Hi,

tail syslog.1 will give you the last 10 lines of the file.

---

### Post by dannyboy79 on 2012-11-14
as I said, check out /etc/logrotate.conf and use the size option to keep them small in size and then use the rotate count of 3 (that's what I use. Here's a guide of sorts

[http://www.techrepublic.com/article/manage-linux-log-files-with-logrotate/1052474](http://www.techrepublic.com/article/manage-linux-log-files-with-logrotate/1052474)

---

### Post by pjstock on 2012-11-14
> **windscape said:**
> Hi,

It would help if you posted the last 10 lines or so from the log files.


I deleted that 3.5Gb syslog.1 file, rebooted and then caught Syslog while it was still manageably small:

```
Nov 14 16:29:01 peter-Latitude-D505 rtkit-daemon[1534]: Watchdog thread running.
Nov 14 16:29:01 peter-Latitude-D505 rtkit-daemon[1534]: Canary thread running.
Nov 14 16:29:02 peter-Latitude-D505 dbus[531]: [system] Activating service name='org.freedesktop.UDisks' (using servicehelper)
Nov 14 16:29:02 peter-Latitude-D505 dbus[531]: [system] Successfully activated service 'org.freedesktop.UDisks'
Nov 14 16:29:04 peter-Latitude-D505 kernel: [   60.796203] composite sync not supported
Nov 14 16:29:05 peter-Latitude-D505 rtkit-daemon[1534]: Successfully made thread 1562 of process 1532 (n/a) owned by '1000' RT at priority 5.
Nov 14 16:29:05 peter-Latitude-D505 rtkit-daemon[1534]: Supervising 2 threads of 1 processes of 1 users.
Nov 14 16:29:05 peter-Latitude-D505 rtkit-daemon[1534]: Successfully made thread 1563 of process 1532 (n/a) owned by '1000' RT at priority 5.
Nov 14 16:29:05 peter-Latitude-D505 rtkit-daemon[1534]: Supervising 3 threads of 1 processes of 1 users.
Nov 14 16:29:07 peter-Latitude-D505 rtkit-daemon[1534]: Successfully made thread 1570 of process 1570 (n/a) owned by '1000' high priority at nice level -11.
Nov 14 16:29:07 peter-Latitude-D505 rtkit-daemon[1534]: Supervising 4 threads of 2 processes of 1 users.
Nov 14 16:29:07 peter-Latitude-D505 pulseaudio[1570]: [pulseaudio] pid.c: Daemon already running.
Nov 14 16:29:21 peter-Latitude-D505 dbus[531]: [system] Activating service name='org.blueman.Mechanism' (using servicehelper)
Nov 14 16:29:22 peter-Latitude-D505 blueman-mechanism: Starting blueman-mechanism 
Nov 14 16:29:22 peter-Latitude-D505 dbus[531]: [system] Successfully activated service 'org.blueman.Mechanism'
Nov 14 16:29:22 peter-Latitude-D505 blueman-mechanism: loading Network 
Nov 14 16:29:22 peter-Latitude-D505 blueman-mechanism: loading Config 
Nov 14 16:29:22 peter-Latitude-D505 blueman-mechanism: loading RfKill 
Nov 14 16:29:22 peter-Latitude-D505 blueman-mechanism: loading Ppp 
Nov 14 16:29:24 peter-Latitude-D505 kernel: [   80.728545] b43legacy-phy0 ERROR: PHY transmission error
```

---

### Post by dannyboy79 on 2012-11-14
that doesn't show us anything wrong. We would need to look at a log after it got to be of some size so we can see what error or message was repeating.

This is 3rd time I have said it, IF you want to save your hard drive from log files eating up space please see my last 2 threads.

---

### Post by pjstock on 2012-11-14
> **windscape said:**
> Hi,

tail syslog.1 will give you the last 10 lines of the file.

Thank you.

peter@peter-Latitude-D505:/var/log$ tail syslog
Nov 14 21:48:55 peter-Latitude-D505 kernel: [19242.906746] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Nov 14 21:48:55 peter-Latitude-D505 kernel: [19242.906769] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Nov 14 21:48:55 peter-Latitude-D505 kernel: [19242.906793] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Nov 14 21:48:55 peter-Latitude-D505 kernel: [19242.906816] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Nov 14 21:48:56 peter-Latitude-D505 kernel: [19242.906840] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Nov 14 21:48:57 peter-Latitude-D505 kernel: [19242.906864] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Nov 14 21:48:58 peter-Latitude-D505 kernel: [19242.906887] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Nov 14 21:48:59 peter-Latitude-D505 kernel: [19242.906911] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Nov 14 21:49:00 peter-Latitude-D505 kernel: [19242.906s

> **windscape said:**
> Hi,

tail syslog.1 will give you the last 10 lines of the file.

and thank you again. here is the tail of kern.log

Nov 14 2peter@peter-Latitude-D505:/var/log$ tail kern.log
Nov 14 21:48:47 peter-Latitude-D505 kernel: [19242.906070] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Nov 14 21:48:48 peter-Latitude-D505 kernel: [19242.906093] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Nov 14 21:48:49 peter-Latitude-D505 kernel: [19242.906117] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Nov 14 21:48:50 peter-Latitude-D505 kernel: [19242.906141] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Nov 14 21:48:51 peter-Latitude-D505 kernel: [19242.906165] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Nov 14 21:48:52 peter-Latitude-D505 kernel: [19242.906176] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Nov 14 21:48:53 peter-Latitude-D505 kernel: [19242.906199] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Nov 14 21:48:54 peter-Latitude-D505 kernel: [19242.906223] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Nov 14 21:48:55 peter-Latitude-D505 kernel: [19242.906247] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times

---

### Post by steeldriver on 2012-11-14
sounds like the same intel graphics problem I had a while back - I thought that recent kernels fixed it but there is a suggested workaround here:

[http://ubuntuforums.org/showthread.php?t=2003173&page=2&highlight=drm](http://ubuntuforums.org/showthread.php?t=2003173&page=2&highlight=drm)

---

### Post by vasa1 on 2012-11-15
> **steeldriver said:**
> sounds like the same intel graphics problem I had a while back - I thought that recent kernels fixed it but there is a suggested workaround here:

[http://ubuntuforums.org/showthread.php?t=2003173&page=2&highlight=drm](http://ubuntuforums.org/showthread.php?t=2003173&page=2&highlight=drm)

I looked at that thread but am still confused ... Why doesn't logrotate work in such situations?

---

### Post by steeldriver on 2012-11-15
> **vasa1 said:**
> I looked at that thread but am still confused ... Why doesn't logrotate work in such situations?

afaik logrotate works just fine however this issue causes a FLOOD of errors (possibly tens of GB per day) - imo it's better to fix that rather than just keep rotating out the logs

---

### Post by vasa1 on 2012-11-15
> **steeldriver said:**
> afaik logrotate works just fine however this issue causes a FLOOD of errors (possibly tens of GB per day) - imo it's better to fix that rather than just keep rotating out the logs
Okay, thanks for that. I looked at some .conf files and it appears that there isn't a file size limit specified by default. So, if something does go crazy, a log can get large as reported here even if logrotate is working "normally".

And, as you say, in any case it's better to fix the root cause.

---

### Post by dannyboy79 on 2012-11-15
> **vasa1 said:**
> I looked at that thread but am still confused ... Why doesn't logrotate work in such situations?
you have to specify a size within logrotate.conf so it knows when to backup that log file and start a new one. I am surprised Ubuntu default conf file doesn't have a size set.

as others have said, it's more important to fix the error to begin with BUT you might as well set a default size for log files just in case some other errant error starts filling your log files.

you can get examples from the man pages: [http://linux.die.net/man/8/logrotate](http://linux.die.net/man/8/logrotate)

---

### Post by vasa1 on 2012-11-15
> **dannyboy79 said:**
> ... I am surprised Ubuntu default conf file doesn't have a size set.
...
you can get examples from the man pages: [http://linux.die.net/man/8/logrotate](http://linux.die.net/man/8/logrotate)

That's why I'm reluctant to change anything. What if there's some thinking behind not setting sizes that we don't get?

How updated is man from linux.die.net compared to man on our systems? Which is a preferable source?

---

### Post by dannyboy79 on 2012-11-15
> **vasa1 said:**
> That's why I'm reluctant to change anything. What if there's some thinking behind not setting sizes that we don't get?

How updated is man from linux.die.net compared to man on our systems? Which is a preferable source?I am not sure which is more relavent, you can always open man on your computer to be sure.

Logically thinking there is no downfall to setting a max size a log file can get. Once it reaches that size, it'll be backed up and a new log file created. Rotate 5 for example would keep 5 old log files. I changed mine to 3 and I set size to 500M as my / partition is only 10gb and I can't afford for any large log files.

Think about it, how many times do you read your log files? Probably only when there is an issue, in that case there will be a total of 4 sitting there to read and 50megabytes of text is enough to figure out what the issue is IMO.

---

### Post by pjstock on 2012-12-03
> **steeldriver said:**
> sounds like the same intel graphics problem I had a while back - I thought that recent kernels fixed it but there is a suggested workaround here:

[http://ubuntuforums.org/showthread.php?t=2003173&page=2&highlight=drm](http://ubuntuforums.org/showthread.php?t=2003173&page=2&highlight=drm)

Hello again, 
sorry, I was busy with all kinds of stuff.
So, I've just tried this DRIRC trick.

How do I know if it actually did anything?
Do I just wait 6 hours and see if the Log files grow crazily or not? I guess I can do that but...

---

### Post by dannyboy79 on 2012-12-04
> **pjstock said:**
> Hello again, 
sorry, I was busy with all kinds of stuff.
So, I've just tried this DRIRC trick.

How do I know if it actually did anything?
Do I just wait 6 hours and see if the Log files grow crazily or not? I guess I can do that but...you can view the syslog or kern.log anytime to see if that error is still being logged. if it's not, then you fixed the issue.

---

### Post by pjstock on 2012-12-04
I don't know how to mark a thread SOLVED but the DRIRC fix seems to have done the trick.
This morning there are no out of control log files. Free Space is a nice steady 13.8Gb.

Thanks to you all for your help.

Peter

---

### Post by philinux on 2012-12-04
> **pjstock said:**
> I don't know how to mark a thread SOLVED but the DRIRC fix seems to have done the trick.
This morning there are no out of control log files. Free Space is a nice steady 13.8Gb.

Thanks to you all for your help.

Peter

See top of your Thread. "Thread Tools" is a drop down menu. :P

---

### Post by pjstock on 2012-12-04
Thanks. I knew it was there somewhere.
(Interesting they don't offer the Thread Tools option when one is actually preparing the Reply that would usually sign off a solved problem.)

---

