---
title: "Finding device number"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by balachandarlinks on 2008-06-07
I have a partition named candy in windows.. It is F:/ in windows....I installed ubuntu 8.04.....I want to find the */media/dev***_? _*****[B]for my F:/ drive***[/B]...how to find it....
         Help me........

---

### Post by st33med on 2008-06-07
F:? F drives in windows are usually removable drives, unless you made a lot of partitions...

---

### Post by RSingh on 2008-06-07
You can use Gnome Partition Editor. Its a nifty partition info utility.

Run terminal and type:

```
sudo aptitude install gparted

```

SYSTEM >> ADMINISTRATION >> PARTITION EDITOR

---

### Post by nick_h on 2008-06-07
You can list your partitions with:
```
sudo fdisk -l
```

If you want to automatically mount a partition you can edit your /etc/fstab file.  See [How to fstab](http://ubuntuforums.org/showthread.php?&t=283131).

---

### Post by balachandarlinks on 2008-06-07
Thank u RSingh.....ur solution solves my problemmm..:guitar::guitar::guitar::guitar::guitar::guitar::guitar::guitar::guitar:

---

### Post by RSingh on 2008-06-07
No Problem

---

