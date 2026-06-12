---
title: "Username of who invoked install?"
date: 2009-11-19
forum: Packaging and Compiling Programs
---

### Post by Locke_99GS on 2009-11-19
In the postinstall section of the deb package control file, I'm attempting to add a line to crontab, but cron must run the line as the user that is installing the package, *not* root. Cron is capable of this, but I cannot seem to get the package to do this.

I've tried $USER, which contains "root", and even tried $SUDO_USER (thinking it was invoked with sudo?) which still contains "root". How can I get the expected relative output of $USER within a postinstall script?

This must be run hourly, otherwise I would simply use anacron, and apparently I am unable to edit the user's own crontab, that I'm aware of anyways.

Thanks in advance.

---

### Post by sisco311 on 2009-11-19
The crontab entry should be added when the user first runs the application. NOT at installation time.

---

### Post by Locke_99GS on 2009-11-19
Most users of this won't run the program the first time, the point of them installing it is generally to have it function automatically. Cron integration at install would be expected by them, in this case.

I suppose I could have it run at login, and have it check and add internally the cronjob, though I'd rather not go this route.

---

### Post by Locke_99GS on 2009-11-19
Ok, I figured it out. Actually, I had it figured out earlier, but apparently I was doing *something* wrong. Wish I knew what.

The $SUDO_USER variable functions as expected from within the postinst of a debian package.

---

