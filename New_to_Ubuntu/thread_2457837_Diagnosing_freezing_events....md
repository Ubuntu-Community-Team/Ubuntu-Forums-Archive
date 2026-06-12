---
title: "Diagnosing freezing events..."
date: 2021-02-10
forum: New to Ubuntu
---

### Post by Innernet on 2021-02-10
Hello all.
Is there a log of trouble events saved in the bowels of the operative system ?
In the event of freezing, slowing, crashing, self shut-off or other troubles where mouse/keyboard get no response to try to discern what is the cause or plainly quit properly instead of hitting the 'power off';  seems to me that after power cycling and restarting, some log could be accessed, copied and pasted on the forum for experts to interpret what went wrong last session and how to fix it / prevent it in the future.
Or an application that _creates_ such logging of events to have it later available for experts inspection ?  Perhaps kept for the last activity hour? could suffice ?

What does "var" in the command cd/var/log means ?

---

### Post by DuckHook on 2021-02-10
Diagnosing freezes and outright crashes is difficult. Often, the event destabilizes the system to the point that the logging daemons also crash. If so, then there will obviously be nothing written to the logs. Sometimes, the log entries immediately prior to the crash may yield some useful hints, but more often, this leads nowhere either. If the crash leaves a screendump on the console, taking a photo is often useful. However, with the advent of GUIs, new users especially will never run a console, so this is not practicable.

A softer crash could give the logging subsystem sufficient time to record something useful. If so, the first places to look are /var/log/syslog , /var/log/kern.log , /var/log/apport.log and /var/log/dmesg , including the version just rotated into *.old* . Since the advent of systemd, it is also very important to look at journalctl.

It is not possible to get you up to speed on log entries and understanding the Linux file structure in a forum thread. I recommend that you have a look at the resources in my sig "Resources for Newcomers" as well as the following link: [https://linuxjourney.com/](https://linuxjourney.com/)

Linuxjourney will prove especially helpful since it describes in user-friendly terms both the filesystem and logging—both of which are central to your question.

---

### Post by deadflowr on 2021-02-10
You can get a more or less basic idea of journalctl here: [https://documentation.suse.com/sles/12-SP5/html/SLES-all/cha-journalctl.html]("https://documentation.suse.com/sles/12-SP5/html/SLES-all/cha-journalctl.html")

> What does "var" in the command cd/var/log means ?
Well /var is a directory, and from my understanding is it stands for variable.
From wikipedia: [https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard]("https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard")
> /var | Variable files: files whose content is expected to continually change during normal operation of the system, such as logs, spool files, and temporary e-mail files.

---

