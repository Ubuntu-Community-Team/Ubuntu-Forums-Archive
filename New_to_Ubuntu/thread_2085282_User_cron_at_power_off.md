---
title: "User cron at power off?"
date: 2012-11-17
forum: New to Ubuntu
---

### Post by honeybear on 2012-11-17
Hi,

crontab -e 

```
@reboot sh ~/myscript.sh 
@poweroff sh ~/myoffscript.sh
```

@reboot works, but not @poweroff. Is there a possibility to run my script at power off using cron? 

thank you

---

### Post by Lars Noodén on 2012-11-17
[crontab](http://manpages.ubuntu.com/manpages/precise/en/man5/crontab.5.html) shows no @poweroff.  That doesn't exist, as nice as it would be to have it.  

What you might do is set your script up as an [upstart](http://upstart.ubuntu.com/cookbook/) job that is activated when runlevel 0.

---

### Post by papibe on 2012-11-17
Hi honeybear.

Crontab will only help you with reboot.

AFAIK, for a shutdown script you have 2 options: an upstart script (see [here]("http://askubuntu.com/questions/109488/how-can-i-run-this-script-on-startup-restart-and-shutdown")), or a level 6 system script (read [here]("http://askubuntu.com/questions/48746/how-to-configure-shutdown-tasks")).

Let us know how it goes.
Regards.

---

