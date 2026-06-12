---
title: "Clone partition"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by shodan on 2008-08-23
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1        9791    78646173    7  HPFS/NTFS
/dev/sda3            9792       77825   546483105    5  Extended
/dev/sda5            9792       64666   440783406    7  HPFS/NTFS
/dev/sda6           64667       77284   101354053+  83  Linux
/dev/sda7           77285       77825     4345551   82  Linux swap / Solaris

```

Since I discovered VMWare I don't need dual boot anymore.
I want to move ubuntu to primary partition and resize it to whole disk + swap.

I spend too much time making it look nice, so i REALLY don't want to reinstall....

Any tips how to do it?
I have empty 100GB exteral Firewire drive i can use :)

---

### Post by youthforlinux on 2008-08-23
I dont think that you can extend the partition to areas before only after....an idea is to completely back up the drive to the external drive and then redo your partition table using a live CD and then restore your backup to the new drive.

These links might help:

[http://ubuntuforums.org/showthread.php?t=35087]("http://ubuntuforums.org/showthread.php?t=35087")


[https://help.ubuntu.com/community/BackupYourSystem]("https://help.ubuntu.com/community/BackupYourSystem")

If you aren't good with the command line try this:

[https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite]("https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite")


and you can do a manual backup of the root filesystem to your drive and remember to exclude the directory with the windows partition and the external drive!!!!

---

### Post by M4rotku on 2008-08-23
If I am understanding your post correctly and you want to delete you Windows partition and resize the Ubuntu partition, then running gparted off of the live cd would be the best bet.

Steps:

1) backup your Ubuntu system using the following [link.]("http://ubuntuforums.org/showthread.php?t=35087")

2) boot the live cd and use gparted to delete windows and resize Ubuntu, it is very intuitive.  (System -> Administration -> Partition Editor)

3) Hopefully your system will still be intact, but if not, the link I gave you has instructions on how to restore as well.

Good Luck

---

### Post by Too Late on 2008-08-23
> **youthforlinux said:**
> I dont think that you can extend the partition to areas before only after....an idea is to completely back up the drive to the external drive and then redo your partition table using a live CD and then restore your backup to the new drive.
With GParted you can grow your partitions to any direction.

edit: But extending the partition to areas before takes much more time.

---

### Post by youthforlinux on 2008-08-23
> **Too Late said:**
> With GParted you can grow your partitions to any direction.

edit: But extending the partition to areas before takes much more time.

Good to know that I had read before that you couldn't, never have had a need to tho....thanks

---

### Post by Too Late on 2008-08-23
> **youthforlinux said:**
> Good to know that I had read before that you couldn't, never have had a need to tho....thanks
I have to add that, on one computer, I just enlarged the extended partition "to the left" with GParted, and created a new logical partition on that empty space. Everything seemed to work well (even Windows on that disk!), but when trying to start cfdisk in Linux, it just says "FATAL ERROR: Bad logical partition 6: enlarged logical partitions overlap". I don't know if that's only a bug in cfdisk, or something else. Other partition editors work well, too. And the partition table of that disk was already quite messy (thanks to eg. BSD).

With primary partitions, I've never had such "problems" after enlarging (to the left or right).

edit: I apologize the word order mistakes I have everywhere, English is not my native language.

---

### Post by shodan on 2008-08-23
That backup thingie... one line only.... niiiice
I remember how painful was it under windows :)

My Ubuntu partiton is inside Extended.
I know you can resize primary partitions both ways but i don't think i will be able to move it outside Extended.

Backup takes a while so no experiments for now ;)

---

