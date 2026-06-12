---
title: "How to set flags in anacron"
date: 2014-10-15
forum: New to Ubuntu
---

### Post by Hellboy256 on 2014-10-15
Hi,
I now when calling anacron manually I simply enter a command like ```
anacron -d ...
```.
But when defining anacron jobs in the /etc/anacrontab where do I put the -d flag so when the jobs are executed I receive dialogs in foreground??

---

### Post by ian-weisser on 2014-10-15
Cron/anacron opening a root window on your display is generally considered a bad idea from both security and design viewpoints.
Cron and anacron are designed to run headless and as root (not your user). They are designed to send output to a log or to an email address.
They should not be used interactively.

You can define user-level jobs in a separate anacrontab...but that's rather arcane.

What exactly are you trying to do?
Are you trying to run some kind of once-a-day post-login task? If so, anacron is the wrong tool for that task.

---

### Post by Hellboy256 on 2014-10-17
I'm trying to run a backup once a week with truecrypt which prompts the password login window.
What technique/task would you recommend for that?

---

### Post by ian-weisser on 2014-10-17
One way:
A script to determine if a week has passed since the last backup. If so, backup again.
Run the script in Startup Applications, which runs after you login (so after your display is assigned, so your password prompt will properly appear) .

---

