---
title: "daily cron job for reboot?"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by thepiston on 2008-06-12
I'd like to reboot my server every night at 3am.  I've never written a cron or know how to go about it - can anyone show me where to go?

---

### Post by Titan8990 on 2008-06-12
Here is the forum's crontab tutorial: [http://ubuntuforums.org/showthread.php?t=102626&highlight=cron](http://ubuntuforums.org/showthread.php?t=102626&highlight=cron)

---

### Post by HalPomeranz on 2008-06-12
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

Btw, you shouldn't really need to reboot your machine every night.  Why do you feel this is necessary?  Maybe there's something wrong with your setup that should be corrected...

---

### Post by Titan8990 on 2008-06-12
I agree, all my machines run 24/7.

---

### Post by thepiston on 2008-06-12
there's a nuance in our software that causes comboboxes to stall unless it's rebooted - i'm just doing this as a patch until we fix the problem.  

One problem - everytime I input "sudo reboot" it asks me for my password.  Do I need to do anything about that or can I just add this:

> 00 03 * * * sudo reboot

---

### Post by Titan8990 on 2008-06-12
That will not work. You will need to make the cron job as root to do commands that require root access. You can't "sudo" in scripts.

---

### Post by thepiston on 2008-06-12
> **Titan8990 said:**
> That will not work. You will need to make the cron job as root to do commands that require root access. You can't "sudo" in scripts.
I was root when I created the cron, is that what you mean?

---

### Post by ukripper on 2008-06-12
you can create bash script and add > 00 03 * * * reboot to it and place that bash script to /etc/rc.local so you don't have to put any password.

alternatively, go for editing sudoers route.

---

### Post by HalPomeranz on 2008-06-12
> **thepiston said:**
> I was root when I created the cron, is that what you mean?

That's what they meant.  If you're adding the reboot command to root's crontab, you don't need the "sudo" statement because the command will be run with root privileges by cron.

---

### Post by thepiston on 2008-06-12
ok, gotcha - i'll remove it

---

