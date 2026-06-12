---
title: "Copy to another computer using Samba"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by Mauler5858 on 2008-11-11
I need to be able to copy a folder from one computer to another.  The source computer is Ubuntu, and the destination is a Windows XP machine.

Also, how can i schedule this to happen once a week?

---

### Post by Kellemora on 2008-11-12
Hi Mauler

You'll have to study up on fstab to mount the drive (I think)
But mainly you'll have to learn how to use Crontab....

It's here in in community under CronHowTo

Sorry I can't be of more help yet, I'm learning too!

TTUL
Gary

---

### Post by handydan918 on 2008-11-12
> **Mauler5858 said:**
> I need to be able to copy a folder from one computer to another.  The source computer is Ubuntu, and the destination is a Windows XP machine.

Also, how can i schedule this to happen once a week?

I couldn't do this in a few minutes, but I think I know the genereal parts and pieces you need to research to get it to happen. 

The copy part should be handled by rsync, and the "once a week" thing is definitely a cron job. As a bona fide KDE user, I have no idea (and less interest!) what semi-functional gnome app might pretend to be a gui for cron, but KDE has one, so I'm sure (!) that one exists for gnome, too.

---

### Post by damis648 on 2008-11-12
Do in terminal:
```
sudo apt-get install gnome-schedule
```
and then manage events at Applications>System Tools>Scheduled Tasks. Good luck!

---

