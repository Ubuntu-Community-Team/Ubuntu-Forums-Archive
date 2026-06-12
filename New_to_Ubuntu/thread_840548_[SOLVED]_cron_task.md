---
title: "[SOLVED] cron task"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by Inxsible on 2008-06-25
I use Debian core + Xfce and Debian core + fluxbox as my OS.

how would I create a cron task to upgrade all my software every week. Kinda like update manager in Ubuntu...but I want it to run once per week.

I do not have synaptic installed. I do all my installing/uninstalling at the command line and occasionally go into 'aptitude' as root.

the cron task could either use the CLI or the Aptitude. It doesn't matter to me


any inputs are welcome.

---

### Post by HalPomeranz on 2008-06-25
"sudo crontab -e" and add a line like this:

```

0 0 * * 1 apt-get -qy update; apt-get -qy upgrade

```

That'll do the update at midnight as Sunday changes into Monday.

---

### Post by Inxsible on 2008-06-25
Cool. Thanks.

Can you point me to a link which details what the leading 0 and * do in a cronjob?


EDIT: Looking at the crontab file, i can see that its the min, hour day of month, month, day of week? and then the command correct?

0 = sunday, 1 = monday
* = all

---

### Post by HalPomeranz on 2008-06-25
I think you'll find this useful:  [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

Btw, note that I just recently edited my original posting above to add the "-qy" options to apt-get, making it more suitable for running via cron.

---

### Post by Dr Small on 2008-06-25
```
minute  hour  day-of-month  month  day-of-week  command
```

Of course, you can use @'s too:
```
	      string	     meaning
	      ------	     -------
	      @reboot	     Run once, at startup.
	      @yearly	     Run once a year, "0 0 1 1 *".
	      @annually      (same as @yearly)
	      @monthly	     Run once a month, "0 0 1 * *".
	      @weekly	     Run once a week, "0 0 * * 0".
	      @daily	     Run once a day, "0 0 * * *".
	      @midnight      (same as @daily)
	      @hourly	     Run once an hour, "0 * * * *".

```


[http://www.unixgeeks.org/security/newbie/unix/cron-1.html](http://www.unixgeeks.org/security/newbie/unix/cron-1.html)

---

