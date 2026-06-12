---
title: "BASH Command To Deactivate Elevated Privileges?"
date: 2011-10-05
forum: Programming Talk
---

### Post by dniMretsaM on 2011-10-05
I'm writing a Python script that will be running some BASH commands with elevated privileges. However, since when you run a command with [FONT=Courier New]sudo[/FONT] it keeps the elevated privileges for a period of time, I want to require the password again even if the user entered it before they run the script (just to help keep people from doing something accidentally). What command do I need to run to force this time to end and require the password again?

---

### Post by Arndt on 2011-10-05
> **dniMretsaM said:**
> I'm writing a Python script that will be running some BASH commands with elevated privileges. However, since when you run a command with [FONT=Courier New]sudo[/FONT] it keeps the elevated privileges for a period of time, I want to require the password again even if the user entered it before they run the script (just to help keep people from doing something accidentally). What command do I need to run to force this time to end and require the password again?

See the man page for 'sudo'.

---

### Post by karlson on 2011-10-05
> **dniMretsaM said:**
> I'm writing a Python script that will be running some BASH commands with elevated privileges. However, since when you run a command with [FONT=Courier New]sudo[/FONT] it keeps the elevated privileges for a period of time, I want to require the password again even if the user entered it before they run the script (just to help keep people from doing something accidentally). What command do I need to run to force this time to end and require the password again?

Do you need to run everything with elevated privileges or just some portions?

---

### Post by dniMretsaM on 2011-10-05
> **Arndt said:**
> See the man page for 'sudo'.

Ok thanks, found that [FONT=Courier New]sudo -v[/FONT] resets the time stamp. It says in the man page that it doesn't run a command. Does this mean I need to run [FONT=Courier New]sudo -v[/FONT] and then run [FONT=Courier New]sudo command[/FONT] and not just [FONT=Courier New]sudo -v command[/FONT]?

> **karlson said:**
> Do you need to run everything with elevated privileges or just some portions?

Just certain parts (although most of it will require elevated privileges).

---

### Post by Lars Noodén on 2011-10-05
Try [sudo -k](http://manpages.ubuntu.com/manpages/oneiric/en/man8/sudo.8.html) or **sudo -K**.  That will cancel the escalated privileges.  When you run sudo again it will ask for the password after that.

---

### Post by dniMretsaM on 2011-10-05
> **Lars Noodén said:**
> Try [sudo -k]("http://manpages.ubuntu.com/manpages/oneiric/en/man8/sudo.8.html") or **sudo -K**.  That will cancel the escalated privileges.  When you run sudo again it will ask for the password after that.

Ok, that'll work. Big thanks.

---

### Post by ajgreeny on 2011-10-05
Alternatively if you want the sudo elevated permissions to always disappear after the command has been run, independent of your script, and for all users, you can set the timeout to zero by editing the /etc/sudoers file.  Do this only with the command```
sudo visudo
``` and then  look for the line ```
Defaults        env_reset
``` and add to it so it looks like ```
Defaults        env_reset, timestamp_timeout=0
```

---

