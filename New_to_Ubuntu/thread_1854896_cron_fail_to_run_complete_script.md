---
title: "cron fail to run complete script"
date: 2011-10-05
forum: New to Ubuntu
---

### Post by Frozen Forest on 2011-10-05
I have a script that download and compile files, basically a build script. When I start the script manually do it complete but when running it through cron doesn't it. Could the problem be that the script take somewhere around 20min to complete?

the root crontab, unsure if the script run on user crontab if that user isn't logged in.
```

15 13 * * * /usr/bin/sudo -u frozen /home/frozen/build.sh

```

---

### Post by HermanAB on 2011-10-05
Howdy,

Cron has a very limited environment.  You should specify the full path of each and every command in a cron script, else you will run into trouble.  Chances are that the script fails when some command in the script cannot be found.

---

### Post by WasMeHere on 2011-10-05
... and also full path to data-files. Environment variables and aliases as well as files (e.g. from your .bashrc) are not recognized.

You start your job once each hour, and if it finishes in 20 minutes it should be OK.

Good luck
Olle

---

### Post by collisionystm on 2011-10-05
> **Frozen Forest said:**
> I have a script that download and compile files, basically a build script. When I start the script manually do it complete but when running it through cron doesn't it. Could the problem be that the script take somewhere around 20min to complete?

the root crontab, unsure if the script run on user crontab if that user isn't logged in.
```

15 13 * * * /usr/bin/sudo -u frozen /home/frozen/build.sh

```

First, open Terminal as regular user.

```
crontab -e
```

remove your cron entry.

now ```
sudo crontab -e
```

put your entry in.

At the top of cron, put ```
MAILTO=youremailaddress
```

cron will now email you if you have any errors.

Always edit your crontab with sudo unless you are running something that only involves your /home/username directory.

---

### Post by Frozen Forest on 2011-10-05
Trying to get it working but no luck so far. How do you get cron to log stdout stderr into a log file?

```

Oct  5 16:15:01 ubuntu-server CRON[1158]: (root) CMD (/usr/bin/sudo -u frozen /home/frozen/build.sh > /home/frozen/cron_log.log)
Oct  5 16:17:01 ubuntu-server CRON[1169]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

``````

PATH=/usr/bin:/usr/sbin:.
SHELL=/usr/bin/sh
# m h  dom mon dow   command
15 16 * * * /usr/bin/sudo -u fozen /home/frozen/build.sh > /home/frozen/cron_log.log


```

---

### Post by WasMeHere on 2011-10-05
> **Frozen Forest said:**
> Trying to get it working but no luck so far. How do you get cron to log stdout stderr into a log file?

```

Oct  5 16:15:01 ubuntu-server CRON[1158]: (root) CMD (/usr/bin/sudo -u frozen /home/frozen/build.sh > /home/frozen/cron_log.log)
Oct  5 16:17:01 ubuntu-server CRON[1169]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

``````

PATH=/usr/bin:/usr/sbin:.
SHELL=/usr/bin/sh
# m h  dom mon dow   command
15 16 * * * /usr/bin/sudo -u [COLOR="Red"]fozen[/COLOR] /home/frozen/build.sh > /home/frozen/cron_log.log


```

Is [COLOR="Red"]fozen[/COLOR] a typing error? What if you edit it?

---

