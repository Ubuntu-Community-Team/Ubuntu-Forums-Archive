---
title: "Using crontab - syntax help"
date: 2011-11-16
forum: New to Ubuntu
---

### Post by HackOmikron on 2011-11-16
Hi everyone.  I'm trying to use cron to schedule a system backup.  Basically, I need a complete backup for the entire system to happen every Saturday at 1:00 AM, and then a daily backup to backup the contents of my /project and /data directories every day at 9:00 PM.
 
I am really bad at figuring out syntaxes :(  Can anyone help?

---

### Post by Lars Noodén on 2011-11-16
You can see the syntax in the manual page for [crontab](http://manpages.ubuntu.com/manpages/precise/en/man1/crontab.1posix.html).  

```

00  01  *  *  6  /path/to/some/script

```

In the columns you have:
[indent]
"1. Minute [0,59]
 2. Hour [0,23]
 3. Day of the month [1,31]
 4. Month of the year [1,12]
 5. Day of the week ([0,6] with 0=Sunday)"
[/indent]

---

### Post by HackOmikron on 2011-11-16
How do I specify that I need it to run a backup though?  From what I've read, (and I'm only learning from my brothers school books) you can use it to schedule all kinds of things.

---

### Post by Lars Noodén on 2011-11-16
You can use it to schedule any program you can run or any script you can write.  What do you normally type in to run your backup?  Put that in your crontab entry.

---

### Post by Jacobonbuntu on 2011-11-16
> **HackOmikron said:**
> How do I specify that I need it to run a backup though?  From what I've read, (and I'm only learning from my brothers school books) you can use it to schedule all kinds of things.

if you are unsure about the backup command, use grsync to create it; create your backup in grsync, run the backup once and copy the output.

---

