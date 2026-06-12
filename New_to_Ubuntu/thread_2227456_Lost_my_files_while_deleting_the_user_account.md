---
title: "Lost my files while deleting the user account"
date: 2014-06-02
forum: New to Ubuntu
---

### Post by sandy3 on 2014-06-02
Hai friends,
                I was using ubuntu 8.04 LTS and while installing some software my laotop was get crashed and it was not able to boot. Now my friend got my laptop upgraded to ubuntu 14.10 LTS. In previous version i had 2 user accounts and for this version i had 1 user account. The data and the files all were recovered from the installation. The previous versions user accounts name were in home directory. I wanted the user account of previous versions name so i created a user account of the same name that was there in the home folder. Then i suddenly deleted the user account, while deleting the pop up came as delete files, keep files and cancel. By mistake i pressed delete files. so all the files from the user account is deleted. Is there any way to recover all those files? I need all those files very badly, please help me to recover all those files which i deleted when i deleted that user account.
Thanking you :)

---

### Post by matt_symes on 2014-06-02
Hi

*Sigh*

1. Testdisk/Photorec from a liveCD/USB ?

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

2. extundelete from a LiveCD/USB ?

```
sudo apt-get install extundelete
```

Any files that are not backed up, are files that you are not worried about losing.

My backup strategy is to archive all my devices to my server. These archives are encrypted using encfs and that encrypted directory get uploaded to cloud storage.

Kind regards

---

