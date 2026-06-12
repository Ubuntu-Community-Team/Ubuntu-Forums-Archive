---
title: "Crontab Help"
date: 2012-08-01
forum: New to Ubuntu
---

### Post by d4m1r on 2012-08-01
Hey guys, basically I installed Ubuntu on an old Dell desktop but the problem is it lacks fans and even the space to install new ones so it runs quite hot....I need it to run 24/7 but I am worried about the internals frying. Specifically, the HDD which is a Seagate (max operating temp = 50c) as it gets up to 47c sometimes which is too close for comfort....

I found a potential command I can use (thanks to hddtemp) to shutdown the computer if temperatures ever hit a specific degree and I'd like to implement it, but have never manually added a job to crontab. Keep in mind it is a headless PC so I'll be doing this via command line and yes I do know where the crontab file is.

Command:

```
$(hddtemp /dev/sda | awk '{ print $4}' | awk -F '°' '{ print $1}') -ge 50 ] && /sbin/shutdown -h 0 || :
```

^Do I just copy/paste that into the file? The stock options already there seem to be formatted completely different....Also, I have to use sudo to get a reading from hddtemp, do I have to specify that in the crontab?

---

### Post by spjackson on 2012-08-01
You don't want to use sudo from your crontab. Instead use sudo to add the job to root's crontab, i.e.
```

sudo crontab -e

```When you have a fairly complex command with subshells, pipes and quotes, I would put all that in a script and run the script from crontab. For example create a script /usr/local/sbin/check-hddtemp
```

#!/bin/bash
your command here

```Then in crontab, supposing you want to run it once a minute,
```

* * * * * /usr/local/sbin/check-hddtemp

```

---

### Post by d4m1r on 2012-08-01
Thanks for the reply! What if I want it to check every 15min instead? Also, how does the below bash script look?

 [http://paste2.org/p/2090899](http://paste2.org/p/2090899)

---

### Post by hwttdz on 2012-08-01
If you want it to run every 15:
*/15 * * * * /path/to/script
wikipedia does a respectable job of covering the syntax: [http://en.wikipedia.org/wiki/Crontab#CRON_expression](http://en.wikipedia.org/wiki/Crontab#CRON_expression)

I'd also like to second everything said above, put it in root's crontab, and put it in a script instead of having a complicated command called from the crontab.

Also, linebreaks in your script?

---

### Post by d4m1r on 2012-08-01
Thanks for the help guys but I can't seem to get this to work....Here's what I've done:

1) Copied [THIS]("http://paste2.org/p/2090974") script to /usr/local/sbin and called it check-hddtemp

2)sudo chmod +x

3)Tried to run it (./) and nothing happens...no message nothing. Does this still mean it's working but didn't shutdown because the temperature is >50c?

Should I now just specify that script location and the 15min formatting in my crontab file? Since I need need sudo to use hddtemp do I specify that in the crontab file or does it automatically run the file as root?

---

### Post by spjackson on 2012-08-02
> **d4m1r said:**
> Thanks for the help guys but I can't seem to get this to work....Here's what I've done:

1) Copied [THIS]("http://paste2.org/p/2090974") script to /usr/local/sbin and called it check-hddtemp

2)sudo chmod +x

3)Tried to run it (./) and nothing happens...no message nothing. Does this still mean it's working but didn't shutdown because the temperature is >50c?

The script you posted on pastebin doesn't output anything if the temperature is less than the threshold. For testing purposes, you could add an else branch with a message if the temperature is OK.

> 
Should I now just specify that script location and the 15min formatting in my crontab file? Since I need need sudo to use hddtemp do I specify that in the crontab file or does it automatically run the file as root?
Yes. If you use ```
sudo crontab -e
``` you will be editing the crontab that belongs to the root user and the job will run as root. There's no need to put sudo in the crontab file.

---

### Post by d4m1r on 2012-08-02
Perfect! Think I got it working...it does do some logging to /var/logs/syslog.

---

