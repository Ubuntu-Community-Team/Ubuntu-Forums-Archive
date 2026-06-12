---
title: "How often do you update your system?"
date: 2015-07-17
forum: New to Ubuntu
---

### Post by huff2 on 2015-07-17
Hey guys,

I'm just curious, how often do you update your system? Once a month, twice,, weekly, etc. I seem to be updating mine like once a week.

---

### Post by Bashing-om on 2015-07-17
huff2; Welp .

In my case, I run a minimal install booting to terminal rather then a GUI. As I generally shut my system down when not in use, each and every time I boot up I check for updates. It only takes a few seconds and is the habit I have become accustomed to.

My thoughts, security
[INDENT][INDENT][INDENT]can not be too careful
[/INDENT][/INDENT][/INDENT]

---

### Post by toxx on 2015-07-17
Usually once a week, or as required when adding new PPAs, or when some piece of software starts acting buggy/weird.

---

### Post by monkeybrain20122 on 2015-07-17
Almost everyday. I feel something is missing if there is no update. :)

---

### Post by Frogs Hair on 2015-07-17
Daily after first boot. My computers are also shutdown when not in use.

---

### Post by deadflowr on 2015-07-17
One machine runs [unattended-upgrades]("https://help.ubuntu.com/community/AutomaticSecurityUpdates#Using_the_.22unattended-upgrades.22_package") so it gets updated whenever new updates come automatically.
Main machine I update whenever updates show as available, usually within the 1st half hour after login.

I also subscribe to the [Ubuntu Security Notices]("http://www.ubuntu.com/usn/") mailing list so if any random zero-day exploit fix comes I can update it immediately instead of waiting for the system to do it's automagical re-check for new packages, which usually happens once per day.
I apply those random security updates to both machines if both are affected.

Also run updates whenever I install new programs/packages, just to make sure all my ducks are in line.
(I think one of the more common errors people get is when they try installing something, their existing system has an out-of-date dependency that throw a bunch of dpkg errors at them)

---

### Post by ajgreeny on 2015-07-17
Daily, as you and everyone else ought to, in my opinion.

I also shut down totally at the end of each day, unless I'm running a long video encoding job or similar, or also if I'm using Plexmedia Server, which is installed on my Desktop machine, to view things on my TV.

---

### Post by huff2 on 2015-07-17
Thanks for the advice! I think I'll start updating daily.

---

### Post by Bucky Ball on 2015-07-17
Weekly with:

```

sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```	

My computer gets switched off every two or three months in the normal scheme of things. The lid gets closed when I'm not using. Rock solid 14.04 LTS.

---

### Post by QIII on 2015-07-18
Daily for my machines at home.

Twice daily for my web server.

---

### Post by jason_gibson2 on 2015-07-18
Have a script on my server that runs updates every Sunday at 1 am then reboots.  The server is an apt-cacher-ng proxy so the kvm virtual machines update 2 hours after the host updates. I do the same on my laptop however it typically is running Arch rather than Kbuntu. I hop between the 2

Relevant section...

```
apt-get update
apt-get -y autoremove
apt-get -y dist-upgrade
apt-get -y autoclean
reboot
```

---

### Post by earruda on 2015-07-20
At work: whenever the project is on low demand, before starting a new project, or when necessary to use a newer lib or program.
At home: whenever I turn my notebook on.

---

