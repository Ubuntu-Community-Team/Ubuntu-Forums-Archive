---
title: "Getting Skype to run when the system boots"
date: 2020-08-19
forum: New to Ubuntu
---

### Post by paradoxparadigm on 2020-08-19
Hi all,

I was wondering, what command do I need to enter into the crontab to get Skype to run at boot time if I installed it through the software store? This is my first time messing with crontab, and I'm using the instructions here: [https://www.simplified.guide/linux/automatically-run-program-on-startup#automatically-run-program-on-linux-startup-via-cron](https://www.simplified.guide/linux/automatically-run-program-on-startup#automatically-run-program-on-linux-startup-via-cron)

Thanks!

---

### Post by TheFu on 2020-08-19
GUI programs can't be run from cron before a user login session exists. Don't confuse running at boot, pre-login, with running after login.  Unless you have a need to run some kind of skype server, which would be very odd for any end-user, the crontab is the wrong way.

Look for "startup applications" in the control panel or desktop startup settings.
The _Ubuntu Desktop Guide_ should have detailed instructions.

---

### Post by SeijiSensei on 2020-08-20
If you log in and run Skype, then log out, in my experience it will be available again the next time you log in.

---

### Post by monkeybrain20122 on 2020-08-20
Click the three dots at Skype's left top corner choose Settings > General and the first entry is "Automatically start Skype".

---

