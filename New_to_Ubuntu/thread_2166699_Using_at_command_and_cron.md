---
title: "Using at command and cron"
date: 2013-08-10
forum: New to Ubuntu
---

### Post by macstl on 2013-08-10
I am trying to learn shell commands. I type in terminal:
at now +2 minutes
at>ls -la
at> i use control d
it then shows a job number but nothing ever happens.??

Trying to use cron.
I type crontab -e

using nano in the file present under the cron headings I type ***** ls -la
then save. nothin happens??

---

### Post by Linux90s on 2013-08-10
did you use:

sudo nano /etc/crontab

the crontab file is owned by root and is read only for others

---

### Post by papibe on 2013-08-10
Hi macstl.

Probably it's happening in the background.

Since the main purpose of those tools is to take care of unattended and non interactive tasks, both at and crontab will detach from the current terminal. Thus, writing to the standard input won't have any effect on your current terminal window.

The common practice is to redirect the output to a log (a file), that can be reviewed later. For instance:
```
at now +2 minutes
warning: commands will be executed using /bin/sh
at> ls -la > /home/youruser/file.log
at> <EOT>

```
You can actually open a window and run something interactive, but that requires a bit more work. Is that what you are looking for?

Hope that helps. Let us know how it goes.
Regards.

---

### Post by macstl on 2013-08-10
papibe:
What you said works! Thank you for telling me about it working in background

---

