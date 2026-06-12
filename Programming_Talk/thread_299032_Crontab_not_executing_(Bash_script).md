---
title: "Crontab not executing (Bash script)"
date: 2006-11-13
forum: Programming Talk
---

### Post by neoaddict on 2006-11-13
Hello, for some reason, my crontab is not getting executed.  Here's what I have in my crontab file:

> 0 */3 * * * gnome-terminal -e /root/Desktop/shellscript.sh

Yes, I know being the root user is a security risk, but I like being it.  o_O  Anyways, I tried doing it manually and using gnome-schedule to no effect - it's just not getting run.

Here's my bash script:

```
#!/bin/bash

/opt/lampp/lampp startapache
cd /opt/lampp/bin
/opt/lampp/bin/php ../htdocs/script.php
/opt/lampp/bin/php ../htdocs/script2.php
dialog --infobox "You can close Apache if you want.  ~Script" 12 32
sleep 30
sudo echo "Ran" >> /root/Desktop/log.log
sudo date >> /root/Desktop/log.log
exit 0

```

Any suggestions?  Thanks.

---

### Post by johnnymac on 2006-11-13
Your asking it to open gnome-terminal??  Why??  Making the script an executable should do the trick.  I myself have never tried to run a graphical tool from crontab so I'm at a loss if your able to do that or not.

---

### Post by neoaddict on 2006-11-13
Hmm.. that might be it.  I'll just wait for another few hours to see if it'll run.

I wanted it to open in gnome-terminal because I wanted to see the output.

---

### Post by johnnymac on 2006-11-13
If you want output your best bet would be to add logging to your script.

---

### Post by neoaddict on 2006-11-13
OK, I got it working - turns out the cron daemon was off for some reason...
Is there any way I can restart cron on startup?

Can I do this via Gnome Session's Startup Programs:

/etc/init.d/cron restart

---

