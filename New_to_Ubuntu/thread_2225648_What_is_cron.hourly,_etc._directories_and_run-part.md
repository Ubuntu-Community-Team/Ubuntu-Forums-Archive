---
title: "What is cron.hourly, etc. directories and run-parts lines in crontab for?"
date: 2014-05-22
forum: New to Ubuntu
---

### Post by vRanger on 2014-05-22
In the etc directory I have:
> user:~$ ls /etc/ | grep cron.
cron.daily
cron.hourly
cron.monthly
cron.weekly

And in the crontab file I have:
> user:~$ cat /etc/crontab
SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )

Can anyone please explain what these directories and crontab entries are actually doing.  There is nothing in the cron.daily directory, so why is it even there?  Google is usually my friend, but is silent on this topic.  Or more likely, I just don't know how to ask the question correctly.  Hope you can help.

Thanks.

---

### Post by QIII on 2014-05-22
They contain files that cause certain routine tasks to be executed periodically.

You can also place your own scripts in any of those directories to have the script run at that interval.  I have one in .daily, for instance, that trims my SSD.

Don't remove them.  Directories in your /etc directory are system files you don't want to mess with.

---

### Post by vRanger on 2014-05-22
This:
> [COLOR=#000000]*17 * * * * root cd / && run-parts --report /etc/cron.hourly*[/COLOR]
means:
Every 17th minute of the hour, as user "root" change directory to "/" (meaning root directory) and ( "&&" ) using function called "run-parts" with option "--report" execute any script (file ending with ".sh") in directory "/etc/cron.hourly".

Do I have that right?

---

