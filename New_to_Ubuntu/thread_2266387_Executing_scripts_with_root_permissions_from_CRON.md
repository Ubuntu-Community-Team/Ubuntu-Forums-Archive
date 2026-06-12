---
title: "Executing scripts with root permissions from CRON"
date: 2015-02-22
forum: New to Ubuntu
---

### Post by Alex_Botev on 2015-02-22
Hi,

So I thought before that setting something to run with **crontab, **under root, would make it execute with root permissions, but it either does not execute at all or not with the right permissions. For instance for the last whole day I had this in my root **crontab**, which require root permissions:
```
25 * * * * touch /home/my.txt
```
Yet it did not execute even once. I thought something my not have been updated or so so I rebooted my computer with no luck.
Additionally on my personal user **crontab**:
```
30 * * * * touch /home/alex/my.txt
```
And it also does not execute. Am I'm so stupid or don't understand something really important why this is not working?

PS: In my syslog I get these to entries corresponding to CRON, which seem to tell me that it is executing it, but I do not understand the message why unsuccessfully:
```

Feb 22 17:25:01 botev-ThinkPad-T440 CRON[3413]: Cannot make/remove an entry for the specified session
Feb 22 17:30:01 botev-ThinkPad-T440 CRON[3507]: Cannot make/remove an entry for the specified session

```

---

### Post by ian-weisser on 2015-02-22
It's unwise to ask root to muck about in your non-root home directory. For testing, /tmp is a good place.
Remember to use full paths or a specified $PATH with cron. '/usr/bin/touch' instead of 'touch'
A datestamp can he handy, so you don't get fooled by leftover results from a previous test.

There are two different types of root crontab. One is created with 'sudo crontab -e', the other lives in /etc/cron*
```
* * * * * root /bin/date > /tmp/crondir_test_result      # /etc/cron*       - easier to maintain, good practice
* * * * * /bin/date > /tmp/crontab_test_result           # sudo crontab -e  - convenient, harder to maintain
```

The syslog error looks like a PAM error to me, not a cron error.

---

### Post by Alex_Botev on 2015-02-23
I'm also starting to thing that there might be a PAM problem, reason is that the 'pam.d/cron' include @common-auth, which in my case also includes a finger print reader, which might be making the problem.

As for the other I'm sure **cron **is set up as root, and the reason I do this to system folder is that I have a small device on which I want weekly/monthly to use cron to clean /var/log from the archives.  As mentioned the root cron tries to do it in /home, while I've set up the user cron to do in /home/user/, but both don't work.

---

### Post by SeijiSensei on 2015-02-23
Root-executed cron jobs can be created 
[LIST=1]
[*]with "sudo crontab -e" which places the result in /var/spool/cron/root
[*]by editing as root /etc/crontab, or by
[*]creating a symlink in /etc/cron.[hourly|daily|weekly|monthly] to an executable file.
[/LIST]
For periodic jobs, I prefer the last of these.  I keep all my system-level scripts in /usr/local/sbin and link to them from the /etc/cron.* directories. For jobs on an unconventional schedule, I usually use /etc/crontab so everything is consolidated in one place.

In /etc/crontab, your job would have the entry:
```
25 * * * * root touch /home/alex/rootfile.txt
```
You could also create the job:
```
25 * * * * alex touch /home/alex/alexfile.txt
```
And you'll get two files with different permissions.

---

### Post by Alex_Botev on 2015-02-24
That might be a better idea to keep them that way, would probably stick to it - at least learning some good practice :)

As for the problem it turned out I had some problems really with the PAM module, so fixing that fixed the permissions problem and everything works fine now.

---

