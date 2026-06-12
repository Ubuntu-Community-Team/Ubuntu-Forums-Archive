---
title: "What Is Polling My Disk?"
date: 2013-09-30
forum: New to Ubuntu
---

### Post by Robert_Adamson on 2013-09-30
I have a media server running Ubuntu 10.04. The system is on an SSD and the media is on a second drive /dev/sdb. The media drive is spun down for quietness when not in use. I have noticed that occasionally it spins up unexpectedly - don't know quite how often but I'd prefer it not to. How can I find out what is polling the drive so that I can try to stop it or reduce it's frequency?
The fstab entry is:
/dev/sdb1   /music   ext4   default   0   2
and the hdparm.conf is:
#spin media down after 10 minutes idle
/dev/sdb {
spindown_time = 120
}

I was earlier pointed to 
[[COLOR=#dd4814]http://zackreed.me/articles/60-spin-...dle-hard-disks[/COLOR]]("http://zackreed.me/articles/60-spin-down-idle-hard-disks")
to solve my spindown problem and there are other hints on that page but they don't seem to be what are causing it.

---

### Post by DuckHook on 2013-09-30
I'm not a HDD expert by any means, but there are many processes that access your HDD for multiple reasons from performing housekeeping to providing important system info. *smartd* is only one. *updatedb* is run regularly by *cron* to keep your *mlocate.db* current so that the *locate* command can find files for you. There are likely others that I haven't learned about.

To track what processes these are over time, you need to install *iotop* from the repositories and run it in batch mode.```
sudo apt-get install iotop
``````
sudo iotop -b
```*iotop* must be invoked with *sudo* and run as root. In batch mode, it will log I/O usage over time. Reviewing the log will help you determine what process(es) is accessing your HDD.

I would find the missing reassurance of smart monitoring and the missing functionality of *locate* an unacceptable price to pay just for spinning down a HDD, but that's just me. If you want to hobble these functions for the sake of a quiescent disk, it's your call.

---

### Post by theDaveTheRave on 2013-09-30
I was going to mention iotop also, this is the [link to the home page for iotop]("http://guichaz.free.fr/iotop/").

They mention on their page vmstat also, but I've never used it so you'll need to check the man page.

Also the utility of updateDB and smartd (and the probably other utilities).

Once you know what the processes are you will likely be able to find a way to reduce their regularity, no need to run updateDB more than once a day, maybe you can survive getting it down to a week.

Also you could probalby put the utilities into a script that will test if the drive is idle, and only run the utility if the drive is already awake (prevent it from waking up the drive specifically) again using a timer of 10 minutes for your script will likely mean that it catches the drives when they are awake.

If you are on a media server, you may be running a raid array, so there should be striping across all the disks, so in effect you should only need to spin up a single disk to run certain functions, I don't know if this is possible or if they will all spring to life (after all a raid array looks like a single disk, with the data spread over multple device for faster access and data integrity).

David

---

### Post by Robert_Adamson on 2013-09-30
Thanks for the pointers - I'll work on it.

> **DuckHook said:**
> If you want to hobble these functions for the sake of a quiescent disk, it's your call.

The server's a fanless Via Epia with a system SDD and fanless PSU and it's in the lounge so it's supposed to run silently. I don't mind the disk whirring when it's more or less eclipsed by the music but it's very noticeable otherwise.

---

### Post by theDaveTheRave on 2013-10-03
Robert_Adamson,

you've marked the thread solved.

Did you find what was poling your disk?

Have you implemented a solution, maybe a brief outline would be good?

Just a matter of interest, as I guess you aren't going to be the only person with a media server in the living room!

David

---

