---
title: "bash script not working from cron"
date: 2009-01-08
forum: Programming Talk
---

### Post by rosv on 2009-01-08
Hi,
I have a script that that is supposed to send me an e-mail when a host is not responding to ping:

#!/bin/bash
/bin/ping -c 1 -w 5 myhost.mynetwork.intra &>/dev/null
if [ $? -ne 0 ] ; then
/usr/bin/mailx -s "Server down " [email]john.doe@domain.com[/email] < ./status.txt
fi

The script works fine when I execute it directly but when cron executes it, the ping error is never picked up by the script so the if statement is ignored.

What have I done wrong?

Crontab entry:
*/1 * * * * /home/user/scripts/checkstatus.sh >/dev/null 2>&1

---

### Post by Cracauer on 2009-01-08
How about not throwing away the error messages?

---

### Post by dwhitney67 on 2009-01-08
> **rosv said:**
> Hi,
I have a script that that is supposed to send me an e-mail when a host is not responding to ping:

#!/bin/bash
/bin/ping -c 1 -w 5 myhost.mynetwork.intra &>/dev/null
if [ $? -ne 0 ] ; then
/usr/bin/mailx -s "Server down " [email]john.doe@domain.com[/email] < ./status.txt
fi

The script works fine when I execute it directly but when cron executes it, the ping error is never picked up by the script so the if statement is ignored.

What have I done wrong?

Crontab entry:
*/1 * * * * /home/user/scripts/checkstatus.sh >/dev/null 2>&1

Where have you placed the file ./status.txt??

I would recommend that you replace the ./ with the full path name as to where that file exists.

---

### Post by dwhitney67 on 2009-01-08
[Ubuntu Forum problems again... Post deleted]

---

### Post by dwhitney67 on 2009-01-08
[Ubuntu Forum problems again... Post deleted]

---

### Post by monkeyking on 2009-01-08
I think cron runs as root,
so try sudo su
and then run your script.
Just to check...

I have a folder just for my script which is rarther nice.
Just remember to add the path to your /etc/environment

I haven't played around with this stuff in the latest versions of ubuntu,
but it should work.


good luck

---

### Post by skoorbevad on 2009-01-25
You're backgrounding the process you're using to check and then expecting a valid exit code, which is always going to be 0.

Note the following ('false' always exits non-zero):

```

dbrooks@argon:~ $ false
dbrooks@argon:~ $ echo $?
1
dbrooks@argon:~ $ false &
[1] 3120
dbrooks@argon:~ $ echo $?
0

```

...See how our exist status becomes 0 once we background the process?  You're basically tossing out all the useful info you want with the ampersand.

Try something like this:

```

#!/bin/bash
#
set -e

ping -c 1 -w 5 some.host.com &>/dev/null || {
  mailx -s "OH GOD" john@doe.com < ./status.txt
}

```

Note that &> and & are two different things.

---

