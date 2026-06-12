---
title: "Does apt-get log updates?"
date: 2005-01-25
forum: Repositories &amp; Backports
---

### Post by RichardA on 2005-01-25
There's a how-to on the wiki about using cron to get and apply updates. Does apt-get log its activity?

I think /var/log/syslog tells me if cron has run, but how can I know if it has run the update script? And how can I know what has been updated?

I really expected to find a /var/log/apt-get, or something. I suppose there's a way to write stuff from the script into a log. Perhaps the output of apt-get can be redirected into one, too. Is that what I need to do? Seems... messy.

---

### Post by mendicant on 2005-01-25
If you just have warty main and restricted, the only updates you should get are security ones.  For those, you can get information from the security updates:

[http://www.ubuntulinux.org/support/documentation/usn/](http://www.ubuntulinux.org/support/documentation/usn/)

Doesn't cron usually mail any error output to the root alias?

---

### Post by RichardA on 2005-01-27
> Doesn't cron usually mail any error output to the root alias?

It does? So if there's no mail, it either works or is completely and utterly broken :-)

Could I get the script to mail the output of the update command to root?

I'm still surprised apt-get doesn't log everything that it does.

---

### Post by mendicant on 2005-01-28
You can--what script are you using now?

---

### Post by RichardA on 2005-01-28
richard@dva:~ $ cat /etc/cron.weekly/autoupdate
#!/bin/bash
apt-get update
apt-get upgrade -y
apt-get autoclean

---

### Post by mendicant on 2005-01-28
You have a couple of options here, depending on what information you want.  You can change to using aptitude, which does have a log (/var/log/aptitude), and which is also listed under /etc/logrotate.d.  This only gives you a certain amount of information, though.

If you want even more info than that, you can run something like:
Start of *untested* script----->
#!/bin/bash

tmpfile=$(mktemp)

echo "aptitude update" >> ${tmpfile}
aptitude update >> ${tmpfile} 2>&1
echo "" >> ${tmpfile}
echo "aptitude dist-upgrade" >> ${tmpfile}
aptitude -y dist-upgrade >> ${tmpfile} 2>&1
echo "" >> ${tmpfile}
echo "aptitude clean" >> ${tmpfile}
aptitude clean >> ${tmpfile} 2>&1

mail -s 'Aptitude cron $(date)' root < ${tmpfile}
rm -f ${tmpfile}
<--- end of untested script

You can increase the verbosity by adding one or more -v options.

By default, aptitude gives the following type of info:
Aptitude 0.2.11.1: log report
Sat Nov 27 18:09:34 2004


IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 1 packages, and remove 1 packages.
-155648 bytes of disk space will be freed
===============================================================================
[REMOVE, DEPENDENCIES] lpr
[INSTALL] cupsys-bsd
===============================================================================

Log complete.

---

### Post by RichardA on 2005-01-29
Aptitude looks to do what I want. I'll test that script, and maybe add it to the Ubuntu wiki.

Mendicant, thanks for all your help.

---

