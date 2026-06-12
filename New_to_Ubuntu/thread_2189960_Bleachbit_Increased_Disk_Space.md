---
title: "Bleachbit Increased Disk Space"
date: 2013-11-25
forum: New to Ubuntu
---

### Post by mahesh3 on 2013-11-25
Hi, 

I ran the bleachbit to clean up some of the apt data but there was "free disk space" option enabled which basically took more time to overwrite the data and now the disk space is increased. I dont know where this proxy file is stored which has increased the disk space size. 

I don;t know what that file is called and how to delete it. 

Any help to remove the extra disk space created by bleachbit to override the disk space, would be appreciated :)

---

### Post by Kirboosy on 2013-11-25
Welcome to the forums!

I believe it creates a temporary file under your home folder that is just a bunch of random jiberish. Called "tmp2343yrindoifhnw04jgsdgboidsafboid" or something like that. If you find it and delete it that would fix the problem.

If you are running it as root, check under /root/

Hope that helps!
~Caboose

---

### Post by mahesh3 on 2013-11-28
I didn't find any temporary file. I checked all the hidden files and didn't find any file which has high mb or gb to it. Any clue where the bleachbit hides this file?

---

### Post by deadflowr on 2013-11-28
How much space was added/taken up?

What is the disk space now used versus what the disk space you had before?

And what are you looking at that is showing the increase?(app-wise)

---

### Post by mahesh3 on 2013-11-28
The size was previously 150GB and now the size is now reduced to 70GB where the orginal size was 320. 

I am looking at the file managers status for drive where it shows 70GB. So after wipeout the space is 80GB added by bleachbit.

---

### Post by deadflowr on 2013-11-28
File Managers are murky little buggers.

Try this command in a terminal
```
df -h
```
Your main partition should be listed as the top entry (usually /dev/sda-somenumber)

What version of Ubuntu are you using, anyway?

---

### Post by mahesh3 on 2013-11-29
I am using Ubuntu 12.04 

Heres what the command line shows after executing the command. 

> :~$ df -h
df: `/root/.gvfs': Permission denied
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       289G  206G   69G  76% /
udev            942M  4.0K  942M   1% /dev
tmpfs           380M  928K  379M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            949M  8.1M  941M   1% /run/shm


---

### Post by Kirboosy on 2013-11-29
You could also try using the Disk Usage Analyzer. 

```
sudo apt-get install baobab
``` 

They renamed the tool to baobab but I will forever know it as Disk Usage Analyzer. 

Additional information may be found on the Ubuntu help page.  

https://help.ubuntu.com/community/Baobab

---

### Post by deadflowr on 2013-11-29
If 12.04, Just type Disk Usage Analyzer in the dash.
It is installed on Ubuntu.

Then when it launches click on the disk icon(it should say something like scan file system, that is the one you want to hit, NOT the one for home folder)
Let it run, and then the list will be from largest to smallest in terms of disk space used.
Ignore the percentage and focus on disk size listings.(The percentage is about the breakdown of where all the space is in use, and not confusingly about the drive/partitions total disk space)

---

### Post by Kirboosy on 2013-12-03
mahesh3 were you successfully able to figure it out?

~Caboose

---

