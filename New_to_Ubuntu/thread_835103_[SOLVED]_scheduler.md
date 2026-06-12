---
title: "[SOLVED] scheduler??"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by bkamalnivas on 2008-06-20
Is there any option in ubuntu to schedule particular application(eg.torrent download)??

---

### Post by dracayr on 2008-06-20
It's called cron

It's a command-line program.

dracayr

---

### Post by fatality_uk on 2008-06-20
You can schedule most things in Ubuntu (Linux) by using a system called crontab. Bit too detailed to go into here I suggest.

From synaptec package manager, you call install a GUI front end called gcrontab. I havent used it but I have heard that it works well.

---

### Post by dracayr on 2008-06-20
there is a GUI for cron called gnome-schedule (or Kcron for KDE)

dracayr

---

### Post by bkamalnivas on 2008-06-20
some of the softwares i try to install says "not authenticated ...could damage the system"

is it safe enough to use them?

---

### Post by fatality_uk on 2008-06-20
How are you trying to install them. For instance to install gcrontab, you just need to go into system->administration->Synaptic Package Manager and do a searc for gcrontab in there. It's safer to install using this method.

---

### Post by hyper_ch on 2008-06-20
did you add any further repositories?

---

### Post by bkamalnivas on 2008-06-20
yeah...that's the way i do...

---

### Post by aeiah on 2008-06-20
cron and its gui friend are great, but if you just want to schedual torrents there is probably an option in your bittorrent software somewhere. i use deluge, and can schedual it so it only uses say, 50% of my bandwidth between certain hours of the day. that might be useful if you want more than just on/off functionality for your torrents.

---

### Post by kpkeerthi on 2008-06-20
> **bkamalnivas said:**
> some of the softwares i try to install says "not authenticated ...could damage the system"

is it safe enough to use them?

You might have added third party repositories that does not provide GPG encryption. What does your /etc/apt/sources.list file look like?

---

### Post by kpkeerthi on 2008-06-20
> **bkamalnivas said:**
> Is there any option in ubuntu to schedule particular application(eg.torrent download)??

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)
[ Gnome-schedule, A cron GUI]("http://www.ubuntugeek.com/schedule-tasks-using-gnome-schedule-a-cron-at-gui-in-ubuntu.html")
[Schedule GUI applications with cron]("http://ubuntuforums.org/showthread.php?t=185993")

---

### Post by bkamalnivas on 2008-06-20
cant get u...
but found that a GPG encryption tool remains uninstalled..

---

### Post by bkamalnivas on 2008-06-20
cant get u...
i get dat msg everytime i try to install an open source application

---

### Post by bkamalnivas on 2008-06-25
s

---

