---
title: "[SOLVED] How do I check if ubuntu is resuming from suspend?"
date: 2008-01-18
forum: Programming Talk
---

### Post by oodlesOfmoodles on 2008-01-18
Is there a way to check if ubuntu is resuming from suspend?

I want to create a script that will fire:

```
sudo /etc/init.d/networking restart
```

When the computer resumes from suspend.


Thanks!!

---

### Post by oodlesOfmoodles on 2008-01-19
bump?

---

### Post by oodlesOfmoodles on 2008-01-23
bump?

---

### Post by nick_h on 2008-01-23
You could add a script in /etc/acpi/resume.d - these scripts are run when resuming from suspend.  There is already a script, 62-ifup.sh, which brings the network back up.

If you just want to stop a service during suspend consider just putting an entry in STOP_SERVICES in /etc/default/acpi-support

---

### Post by oodlesOfmoodles on 2008-01-23
Thanks for your help! It worked!

---

