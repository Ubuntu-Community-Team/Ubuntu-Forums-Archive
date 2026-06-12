---
title: "upgrading and installing"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by boywholinuxed on 2008-05-31
hi,
i wanted to know the difference between upgrading a version of kubuntu and installing new version of kubuntu from a live cd?

i want to know why people prefer  to upgrade?

---

### Post by Inxsible on 2008-05-31
When you upgrade, you don't have to format the drive and so you don't lose all the settings and the apps that you have installed over time.  But, upgrading can be cumbersome - as in it takes more time since old packages need to be removed and new ones installed. In my experience installing a new OS from a Live CD is much faster than the upgrade.   Also, upgrade will not work, if you have removed any of the default apps that come bundled with your distro. So for eg if you remove kubuntu-desktop, then you will have to install it again prior to the upgrade.

---

### Post by boywholinuxed on 2008-05-31
so that means it would be smarter and easier if i copy the contents of my folder (home/j) into a pen drive and install the latest kubuntu from live cd?

would the above be equivalent to upgrading?

---

### Post by Inxsible on 2008-05-31
If you have a separate home drive, you dont even need to do that. Simply use the same home during the installation and make sure you DONT format it.

---

### Post by boywholinuxed on 2008-05-31
i know this sounds like a stupid question,but i'm  a newbie!
how do you know if you got a separate home drive and how do you make sure you dont format it at the time of installation?

---

### Post by Inxsible on 2008-05-31
Post the output of the following command here and we can tell you```
df -h
``` and ```
sudo fdisk -l
``` -l is lowercase L

---

### Post by sayakb on 2008-05-31
+1 to what Inxsible said. Its better not to upgrade. Upgrades freeze up, kill HAL etc. and your PC might become unusable. Though you can save your data through the LiveCD after upgrade screws up, but why take chances.. ;)

---

### Post by boywholinuxed on 2008-06-01
here is the output for the first code

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              36G  3.0G   32G   9% /
varrun                125M  136K  125M   1% /var/run
varlock               125M     0  125M   0% /var/lock
udev                  125M   68K  125M   1% /dev
devshm                125M     0  125M   0% /dev/shm
lrm                   125M   34M   91M  28% /lib/modules/2.6.22-14-generic/volatile

here is the out put in the second code

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x35023501

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4772    38331058+  83  Linux
/dev/sda2            4773        4865      747022+   5  Extended
/dev/sda5            4773        4865      746991   82  Linux swap / So

---

### Post by tom56 on 2008-06-01
A separate partition for /home is not required any more. The install CD will detect that you already have a /home folder and ask you if you want to delete it. If you say no then it will delete everything except /home and install a clean system. You get the advantage of a separate /home without the mucking around with partitioning and fstab.

---

### Post by boywholinuxed on 2008-06-02
u sure?
i never saw it when i installed 7.10 via live cd
must be a new feature of 8.04!

---

### Post by tom56 on 2008-06-02
Not entirely sure because I haven't tried it my self but I'm 95% sure. At any rate it should ask you before the formatting stage so if it doesn't then cancel there and nothing will have been written to disk yet.

---

### Post by rajaram_s on 2008-06-02
I am facing a lot of problems since I upgraded my comp from gutsy to hardy. I am reluctant to reinstall it for the only very reason that I have lots and lots of application packages installed and also indirect data which cannot be backed up directly like the mysql databases and amarok cached lyrics.. can anyone suggest me a way in which I can back up those stuff too?

---

### Post by Xiong Chiamiov on 2008-06-02
That's the reason why I chose to upgrade rather than reinstall - I install lots of crap.

If you have PHPMyAdmin installed, then you can back up MySQL fairly easily, through the tab "backup" (or export, or something like that).  If you don't (eg, you're using it for amarok), then you can back it up like so:
```

mysqldump -u [username] -p [password] [databasename] > [backupfile.sql]

```

---

### Post by boywholinuxed on 2008-06-03
y cant u save it to a pendrive or save it online?

---

