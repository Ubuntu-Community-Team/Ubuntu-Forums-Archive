---
title: "Schedule Wake Up from Suspend"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by henryrhenryr on 2008-06-16
I finally worked out the right settings to get my machine to suspend and wake up.

Currently I can only get it to wake up by pushing the power button.  This computer is only for running regular tasks and nothing else so I don't want to waste power and ideally I can get it to start up when a new task is required to run - ie add command to crontab or simply wake up when a task starts to run.

I've been searching around but not luck.  Are there any ways I can try and get this to work?

Thanks

ps. Ubuntu Dapper 6.06

---

### Post by henryrhenryr on 2008-06-16
I worked it out:

/proc/acpi/alarm

Something like 

```
echo "+00-00-00 00:03:00" > /proc/acpi/alarm
```

---

### Post by balpo on 2008-10-30
How did you manage to wake from suspend?

What does [FONT="Courier New"]echo "+00-00-00 00:03:00" > /proc/acpi/alarm[/FONT] mean?

Thanx

---

### Post by van_Zeller on 2008-12-03
bump...same problem here. I programmed cron to wake me up to the sweet sound of music, but dont want the pc running all night. help please...

---

### Post by a_toff on 2009-02-07
> **balpo said:**
> How did you manage to wake from suspend?

What does [FONT="Courier New"]echo "+00-00-00 00:03:00" > /proc/acpi/alarm[/FONT] mean?

Thanx

I'd also like to request a more detailed explanation of how to set this up... please and thank you! :)

---

### Post by kalug on 2009-10-03
> **a_toff said:**
> I'd also like to request a more detailed explanation of how to set this up... please and thank you! :)
Hi all,

same question here... in bios I cannot find anything like APM and I do not have /proc/acpi/alarm... can I create it somehow?
Is it possible that my mobo just does not support such a wake-up trick?

Thanks

PS: motherboard: MS-1221; Intel CoreDuo T7300;

---

### Post by sa_venkatesan on 2010-05-27
Hi,

Please checkout the following link.

[http://blog.gulfsoft.com/2010/05/scheduled-wakeup-in-ubuntu.html](http://blog.gulfsoft.com/2010/05/scheduled-wakeup-in-ubuntu.html)

I have tested the steps on Ubuntu Lucid Lynx but should work on any other Ubuntu system with latest Kernel.  

Hope you find it useful.

-venkat

---

