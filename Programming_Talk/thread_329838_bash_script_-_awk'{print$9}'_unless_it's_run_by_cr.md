---
title: "bash script - awk'{print$9}' unless it's run by cron then its $8"
date: 2007-01-02
forum: Programming Talk
---

### Post by bdgenz on 2007-01-02
Why the output of ps aux or ls -la differs is a mystery to me.

I notice this issue when I ssh from differrent clients executing scripts also.

On one client I have to awk'{print$9}' running bash scripts, ssh from another and I have to print$8 (putty in windows vs konsole on a mepis workstation) to get the same output.

I've never had to change a script executing as root vs executing from root's crontab! On one of my boxes (ubuntu "server") I have to, wheras the same script on another box (gentoo "server") does not require any changes.

The issue has to be related in my mind, just don't understand why it is.

Ideas?

TIA

---

### Post by yaaarrrgg on 2007-01-06
You might try to print out the vars in your script (like  $1, $2, $3, ...)  to see what all is actually  getting parsed.  My guess would be something at the front of the line would be causing the problem (might be shifting over).   Sorry if my answer isn't much help, but perhaps  you can see what's happening directly on each machine?

---

### Post by bdgenz on 2007-01-08
The output is different.

Test by using a couple different ssh clients.

My question is WHY???

TIA

---

### Post by Arndt on 2007-01-09
> **bdgenz said:**
> The output is different.

Test by using a couple different ssh clients.

My question is WHY???

TIA

You mention 'ls' and 'ps'. Show us the output from both, in both the different versions, and maybe some idea may pop up.

---

### Post by Sindre on 2009-03-23
> **bdgenz said:**
> Why the output of ps aux or ls -la differs is a mystery to me.

I notice this issue when I ssh from differrent clients executing scripts also.

On one client I have to awk'{print$9}' running bash scripts, ssh from another and I have to print$8 (putty in windows vs konsole on a mepis workstation) to get the same output.

I've never had to change a script executing as root vs executing from root's crontab! On one of my boxes (ubuntu "server") I have to, wheras the same script on another box (gentoo "server") does not require any changes.

The issue has to be related in my mind, just don't understand why it is.

Ideas?

TIA

You have probably solved this already, as it was posted two years ago, but since I recently had the same problem without managing to google the solution, I'll post the answer here.

The cron shell lacked the following environmental variable:

LANG=en_US.UTF-8

Apparently "ls" changes its output depending on that, and probably other commands as well.

---

### Post by akvino on 2009-03-23
So what did you do - did you add this syntax to the script:

LANG=en_US.UTF-8

setting LANG to utf-8 - or did that get added somewhere else?

---

### Post by bdgenz on 2009-03-23
I now run dpkg-reconfigure locales as a first step to building a machine (mostly Debian servers)

add en_US ISO-8859-1 and choose:

en_US for the default locale

I've got a mix of a few distros strewn between 50 servers, some are still unconfigured (or not exactly the same) so I do keep an eye on the logs/cronjobs, especially when a script is copied from one box to another ;~)>

---

### Post by Sindre on 2009-03-24
> **akvino said:**
> So what did you do - did you add this syntax to the script:

LANG=en_US.UTF-8

setting LANG to utf-8 - or did that get added somewhere else?

Yes, I added that line, and an "export LANG" line to the script.

Works like a charm.

This is probably quite old news for anyone with scripting experience, but still took me an hour to figure it out.

If the above changes the default locale for everything, including cron, then that's probably a better solution.

---

### Post by Nephiel on 2009-09-22
Sorry to dig up an old thread but I ran into this issue.

You can change your default locale system-wide in /etc/default/locale, but this seems to have no effect on cron.

If I run "locale" from the shell, I get:
```
LANG=en_US.UTF-8
LANGUAGE=en
LC_CTYPE=en_US.UTF-8
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=
```which matches my /etc/default/locale, just like I want. But if I run locale from a cron job I get:
```
LANG=
LC_CTYPE="POSIX"
LC_NUMERIC="POSIX"
LC_TIME="POSIX"
LC_COLLATE="POSIX"
LC_MONETARY="POSIX"
LC_MESSAGES="POSIX"
LC_PAPER="POSIX"
LC_NAME="POSIX"
LC_ADDRESS="POSIX"
LC_TELEPHONE="POSIX"
LC_MEASUREMENT="POSIX"
LC_IDENTIFICATION="POSIX"
LC_ALL=
```

There's this option in /etc/default/cron, set to yes by default:
```
# Whether to read the system's default environment files (if present)
# This will make cron set a proper charset for the mails it sends
# Comment this or set it to something other than 'yes' to prevent
# cron from reading it. 
READ_ENV="yes"
```
but it seems to have no effect? :confused: I have to specify my locale on all my crontabs.

---

### Post by Ganton on 2010-01-25
> **Nephiel said:**
> I have to specify my locale on all my crontabs.
Someone advised to specifiy it just in the file /etc/environment and then reboot. (Well, I know there are other there ways without rebooting, but the easiest way for you is to reboot).

---

### Post by D3V11 on 2010-01-25
ps is the command to list processes. ls is used to list files.

---

### Post by akvino on 2010-01-25
just type this on top of your script


./etc/profile

---

