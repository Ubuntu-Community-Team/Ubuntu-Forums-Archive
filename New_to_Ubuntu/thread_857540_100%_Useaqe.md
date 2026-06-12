---
title: "100% Useaqe"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by misterfixit on 2008-07-12
Hi Group,  this is more of a philosophical question than an "OMG I need help!" question.  I've done a bit of searching about the system load going to 100% after starting an application, but really would like to have a layman's explanation.

Every so often my system monitor shows 100% in use.  This is almost always after I have started one or another application.  Exiting the application does not stop the 100% use;  Now in some cases, when I open system monitor I will see that a process is "sleeping" or "zombie".  Once I kill that process, the system use drops dramatically frm 10% to usually about 5%.

However there are times when the only application which is showing close to 100% use of memory is the gnome-system-monitor, hovering around 50% to 95%.

I looked at the faq's for zombie and sleeping processes and think that zombie and sleeping processes are not actually taking up RAM.  But how does that account for the system monitor showing 100% use?

[I]Here is my system:

Ubuntu 8.04
Kernel Linux 2.6.24-19-generic
Memory 3.2GB
Processor AMD Athlon 64 Processor 3700+[/I]

Firefox is a constant problem; anytime a exit and hours or days later attempt to use it again, the message "Firefox is already in Use" appears.  I then have to go to TOP and kill FF.

*Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9) Gecko/2008061015 Firefox/3.0*

Open Office 2.4 will work once and then ***all*** subsequent attempts to open any of the OO Suite results in a message *"The application cannot be started, the user interface language cannot be determined"*  At that point in the loading of OO, system monitor shows a 100% use of the system and a 99% use by OO, which then goes to zombie in a few seconds.

May I have some pointers to other FAQ's or some advice on what to do?

Thanks

Dave

---

### Post by cmnorton on 2008-07-14
Is there anything tell-tale in your logs?

/var/log/messages
/var/log/syslog
/var/log/kern.log

---

### Post by LowSky on 2008-07-14
seems to be a windows issue as well
 found this on linux.com
[http://www.linux.com/articles/48144](http://www.linux.com/articles/48144)

---

### Post by dhughes on 2008-07-14
This is a bug.

 Do you have System Monitor added to a panel? I think that's what causes trouble not so much starting System Monitor but having it on the panel.

 I just found this out myself yesterday!

 Remove it from the panel, if you do have it there, and see if that helps. I even had to power down my system for a few minutes since removing System Monitor from the panel didn't seem to help right away and even rebooting didn't help. 

 Removing System Monitor from the panel and powering down for a few minutes seemed to fix my system.

edit: oops wrong link, here it is, [https://bugs.launchpad.net/gnome-system-monitor/+bug/93847](https://bugs.launchpad.net/gnome-system-monitor/+bug/93847)

---

