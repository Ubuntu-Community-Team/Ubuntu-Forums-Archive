---
title: "sbackup just not running"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by spotteddog on 2008-05-24
Running Hardy. 

sbackup never runs anymore. It ran for a few days, but hasn't run in weeks, unless I run it manually.
I have it set to "custom", only because I have the backups going to another hdd. I have it set to run daily at 1600. Everything else is set to the default settings. 
It runs fine and gives me a good backup, if I run it manually. But it won't run automatically.



Any ideas?

Thanks.

---

### Post by tamoneya on 2008-05-24
I had a similar problem.  In my case I was backing up over ssh and I changed some permissions on the server so i wasnt able to back up to the directory anymore and it kept trying to backup and couldnt so it would just stop.  Make sure you still have permissions to write to your backup.

---

### Post by spotteddog on 2008-05-24
> **tamoneya said:**
> I had a similar problem.  In my case I was backing up over ssh and I changed some permissions on the server so i wasnt able to back up to the directory anymore and it kept trying to backup and couldnt so it would just stop.  Make sure you still have permissions to write to your backup.
Tamoneya,

I'm only into my 6th week with Ubuntu. How do I check/enable permissions to write to the other hhd? I am just writing to a 3rd hdd on the same PC. (C = Vista, E = Backups and SHaring files with Ubuntu, F = Ubuntu (Hardy))

Thanks.

---

### Post by tamoneya on 2008-05-25
> **spotteddog said:**
> Tamoneya,

I'm only into my 6th week with Ubuntu. How do I check/enable permissions to write to the other hhd? I am just writing to a 3rd hdd on the same PC. (C = Vista, E = Backups and SHaring files with Ubuntu, F = Ubuntu (Hardy))

Thanks.

First tell me where it is attempting to back the files up to.  This is in the sbackup config section under destination.

---

### Post by spotteddog on 2008-05-25
> **tamoneya said:**
> First tell me where it is attempting to back the files up to.  This is in the sbackup config section under destination.
I have "use custom local backup directory", which is E> UbuntuSbackups. If I click "run now", it runs fine. But it has never done automatic backup, since the first week or so I used it. 
I read another post which suggested that if I manually "delete" any of the backups, it messes up the whole thing. I figured that might have been it, so I deleted everything in the UbuntuSbackup folder and ran a manual backup (which worked), but it still will not do them automatically.

The biggest hurdle for my total migration to Ubuntu from Vista is managing data. I have mucho important stuff that I could never replace, if I would loose it, say, 2 or 3 months after the migration. In Vista, I trust Acronis True Image, but haven't found anything in Ubuntu to repalce it (other than maually backing up to another drive).

---

### Post by mdpalow on 2008-05-25
I don't really know anything about sbackup since I've never used it, so can't comment on it. However, you could use QuickStart, which a lot of people have said is a better back-up tool. I developed it, so if you have any questions, you can ask me directly. :)

good luck

---

### Post by spotteddog on 2008-05-25
> **mdpalow said:**
> I don't really know anything about sbackup since I've never used it, so can't comment on it. However, you could use QuickStart, which a lot of people have said is a better back-up tool. I developed it, so if you have any questions, you can ask me directly. :)

good luck
Thanks, mdpalow, I'll give it a try later today.

---

### Post by spotteddog on 2008-05-25
mdpalow,

Installed Quickstart and set up a daily schedule (for now). Ran fine and gives me what I need. Thanks.

I read your instructions by clicking on "Display Help". But I do have a few questions. 

1. Since I am doing daily backups right now, to save space, can I manually delete backups I no longer need without creating a problem?

2. How can I change (edit) a scheduled backup. Will just going back to "Create A Back-up Schedule" over write my original settings? In other words, is it _not_ possible to create different (multiple) scheduled backups?

Thanks again.

---

### Post by mdpalow on 2008-06-06
> **spotteddog said:**
> mdpalow,

Installed Quickstart and set up a daily schedule (for now). Ran fine and gives me what I need. Thanks.

I read your instructions by clicking on "Display Help". But I do have a few questions. 

1. Since I am doing daily backups right now, to save space, can I manually delete backups I no longer need without creating a problem?

2. How can I change (edit) a scheduled backup. Will just going back to "Create A Back-up Schedule" over write my original settings? In other words, is it _not_ possible to create different (multiple) scheduled backups?

Thanks again.

Sorry for the VERY long delay, but I'm not following this thread and just stumbled into it again. Would suggest you contact me from the QuickStart forum with further questions; you'll get a reply the same day. 

To answer your questions:

1. Yes, you can delete old back-ups manually if you like. No problem.

2. You can simply create a new scheduled back-up and it will overwrite the first schedule you created. Or, you can go into that menu option and select the option that deletes the scheduled back-up and create another one. However, that's really the long way around. Just use the first method.

You can't have more than one scheduled back-up at a time. I did that because I was afraid people might not know how to clean up their cron file and that could potentially cause them a lot of problems.

See my link for the forum where you can ask questions and get a much more time answer. :)

good luck

---

