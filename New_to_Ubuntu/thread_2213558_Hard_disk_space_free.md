---
title: "Hard disk space free"
date: 2014-03-27
forum: New to Ubuntu
---

### Post by james104 on 2014-03-27
Hello all,

You may recall I had issues before with hard disk space however that was successfully solved by moving my home directory to a new partition.

Today I am faced with another dilemma and I dont understand how this has occurred.

Upon powering up I was greeted with a message stating my system was running in low graphics mode.

After some TShooting it was down to hard disk space. I am logged in now and after running df -h I am told dev/sda5 is 11gb in size with 11gb used 175 mb available (99%) use...

I dont understand how this has happened and also I am unsure how or even what to remove or at least what is safe to remove!

my usage was around 8gb previously so 3gb used over the course of 2 weeks on the OS partition. (I would understand it if it was the home directory on my other partition!)

Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5        11G   11G  175M  99% /
udev            987M  4.0K  987M   1% /dev
tmpfs           200M  872K  199M   1% /run
none            5.0M     0  5.0M   0% 

[IMG]http://i57.tinypic.com/2946mow.jpg[/IMG]

---

### Post by steeldriver on 2014-03-27
Can you post the full output from the df command please? 

```
df -h | grep ^/dev
```

What you have shown in your 1st post doesn't seem to indicate a separate /home partition

---

### Post by james104 on 2014-03-27
> **steeldriver said:**
> Can you post the full output from the df command please? 

```
df -h | grep ^/dev
```

What you have shown in your 1st post doesn't seem to indicate a separate /home partition

james@Bumblebee:~$ df -h | grep ^/dev
/dev/sda5        11G   11G   75M 100% /
/dev/sda4        15G  8.0G  5.6G  60% /home

---

### Post by mcduck on 2014-03-27
You could start by doinf some system cleanup:

```
sudo apt-get autoremove
sudo apt-get clean
```

The first command uninstalls any leftoorver packages thata ren't needed any more, for example stuff that has been installed as a dependency for something else that doesn't exist any more. And the second command deletes the packages apt-get has cached when you've installed anything o updated your system.

If that doesn'r clear up enough space, then the usual stpes would be checking that there's nothing in root user's thrash, and that no log file has grown due to some errors (in which case make sure to check the errors before deleting the log file so that you can fix the actual program). 

...and since you've moved your home recently, make sure you had actually deleted any fiels in the old /home directory on the root partiton, otherwise they'll still take space even though they aren't visible as the new home partition is mounted on top of the old /home...

---

### Post by james104 on 2014-04-01
Hello,

Above command seemed to work ok in the end, I had some teething problems with Steam too which left me with no option but to delete my Ubuntu partition and reinstall with a greater partition size! Working nicely now so will mark this thread as solved.

---

