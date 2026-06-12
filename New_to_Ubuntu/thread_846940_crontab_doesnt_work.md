---
title: "crontab doesnt work"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by shashank.ks on 2008-07-02
hi,

    I tried to schedule some application to start some time using crontab . But the application dont come up at the required time. I tried restarting the crond server and created the /etc/cron.allow /etc/cron.deny file . But nothing worked. It doesnt give any error message also. 


my entry in the crontab file is something like this 

00 11 * * * echo "HELLO WORLD"

---

### Post by HalPomeranz on 2008-07-02
When a cron job produces an error message or other output (like your "HELLO WORLD" example) that output gets emailed to the user who the cron job is running as.  But if outgoing email isn't working on your machine you'll never see it.  So before you start thinking that cron is broken, you might first check to see if it's not outgoing email that's your problem.

Some other things to try:

1) Enable cron logging on your machine.  "sudo vi /etc/syslog.conf" and remove the "#" character from the beginning of this line:

```

#cron.*                         /var/log/cron.log

```

Then "sudo /etc/init.d/sysklogd restart".  Once you do that you should be able to look in /var/log/cron.log to see if your jobs are being executed or not.

2) Set up a test cron job:

```

0 * * * * touch /tmp/crontest

```

That will cause the timestamps on the file /tmp/crontest to be updated every hour.  That's easy to check with "ls -l /tmp/crontest".

---

### Post by Dr Small on 2008-07-02
Where did you expect to see "HELLO WORLD" print at?
Sure, I bet cron is running, but did you expect the text to be printed on the screen or something?

---

### Post by ibuclaw on 2008-07-02
All STDOUT and STDERR messages get sent to your mailbox.

Install **mailx** and type in "mail" in the terminal to see your messages.

Regards
Iain

---

