---
title: "Truecrypt 4.3a error..."
date: 2008-05-06
forum: New to Ubuntu
---

### Post by hopelessone on 2008-05-06
Hi All,

I downloaded Truecrypt 4.3a and am following the guide [https://help.ubuntu.com/community/TruecryptHiddenVolume](https://help.ubuntu.com/community/TruecryptHiddenVolume)
when step 3 comes along...

#3 Map the corresponding volume (ex: on /dev/sdb1), but do not mount it:
```

truecrypt /dev/sdb1
```

i get this?

Enter password for '/dev/sdc1': 
FATAL: Module truecrypt not found.
Failed to load TrueCrypt kernel module

what do i do?

thanks..

---

### Post by ephro on 2008-05-06
Try this first:

```
sudo modprobe truecrypt
```

---

### Post by hopelessone on 2008-05-06
redox@redox-desktop:~$ sudo modprobe truecrypt
FATAL: Module truecrypt not found.

---

### Post by ephro on 2008-05-06
Are you running 08.04 or 07.10? If it's 08.04 then 4.3a doesn't support the newest kernel, however you can install 08.04 and everything should work find (except creating hidden partitions, aka plausible deniability partitions.) If you are ok with that then you can get the installer here:

[http://www.truecrypt.org/downloads.php](http://www.truecrypt.org/downloads.php)

I should point out that you can *mount* hidden partitions in the new version. If you need to make them you have one of two options:


[LIST=1]
[*]Make the partition in 07.10 and move the drive
[*]Make the partition on a windows machine and move the drive
[/LIST]

---

### Post by hopelessone on 2008-05-07
Ahh...ok...went do you think version 6 will come out?

thanks...

---

### Post by dmub82 on 2008-05-08
Have you tried the latest Truecrypt? 5.1a is the latest stable version [here]("http://www.truecrypt.org/downloads.php").

edit: Nevermind, I see that note about hidden volumes not being implemented for Linux in the new versions. D'oh.

---

