---
title: "Security on .sh running at startup"
date: 2012-02-28
forum: New to Ubuntu
---

### Post by Eniliad on 2012-02-28
Hello,

Running Xubuntu 11.10,

I have an issue concerning a  script that I have set to run at login. Right now, I have it set to do  two things: At login, it runs xrandr to set up my multi-monitor display  (set one monitor as "primary", then make the other one --right-of the  first). Then, it disables power management to my wlan0 in order to solve  an issue I'm having with my USB dongle (namely, Power Management chokes  off power to my USB WiFI, which of course causes my Internet connection  to slow down; disabling power management fixes this.)

All is  well except for one little problem: My startup .sh file now requires my  password in order to run the command which disables power management to  my USB WiFi device. This is rather annoying and I'd like to be able to  bypass it - for this command only. Solutions I've found online require  me to make exceptions to the sudo password requirement rules, which  would compromise my computer's security. For obvious reasons, I'd like  to avoid this. Unfortunately, the command *must* be executed as su - attempting to run it without su privileges returns a Permission Denied error.

Is there a way to get just this one command, or possible file if necessary, to run a sudo command automatically?

---

### Post by sudodus on 2012-02-28
You can run that command as a cron job as root, which will be done automatically and you need not supply any password (except when you enter the command into the crontab (cron table file)).

```
sudo crontab -e
```

See the following posts

[[COLOR="Red"]_http://ubuntuforums.org/showpost.php?p=11723012&postcount=3_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11723012&postcount=3")

[[COLOR="Red"]_http://ubuntuforums.org/showpost.php?p=11720933&postcount=25_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11720933&postcount=25")

---

### Post by chipbuster on 2012-02-28
Have you considered putting an entry in rc.local?

---

### Post by kevdog on 2012-02-28
I'd just second the rc.local entry.  Scripts referenced in this file (above exit 0) run as root at startup.

---

### Post by Eniliad on 2012-02-29
/facepalm

I even... I even knew about rc.local. Why didn't I think of that?

Anyway, thanks a ton guys! :D

---

