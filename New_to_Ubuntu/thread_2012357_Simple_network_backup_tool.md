---
title: "Simple network backup tool"
date: 2012-06-29
forum: New to Ubuntu
---

### Post by pmohankumar on 2012-06-29
Hi friends,

Kindly refer me a recommended network backup tool for ubuntu 10.04.

Thanks,
Mohan
EMG

---

### Post by ubudog on 2012-06-29
I am pretty sure Deja Dup can do network backups, or you could setup rsync and a cron job.  

If not installed, you can install Deja Dup like so:
```
sudo apt-get install deja-dup
```

And rsync like so:
```
sudo apt-get install rsync
```

Best of luck,
ubudog

---

### Post by raja.genupula on 2012-06-29
> **ubudog said:**
> I am pretty sure Deja Dup can do network backups, or you could setup rsync and a cron job.  

If not installed, you can install Deja Dup like so:
```
sudo apt-get install deja-dup
```And rsync like so:
```
sudo apt-get install rsync
```Best of luck,
ubudog


+1 to Ubudog and some more useful information for you 
[https://help.ubuntu.com/community/BackupYourSystem#Backup_Methods](https://help.ubuntu.com/community/BackupYourSystem#Backup_Methods)

---

### Post by HermanAB on 2012-06-29
Howdy,

All Linux backup utilities use rsync underneath.  So look in your software installer and search for 'backup' and have fun.

---

