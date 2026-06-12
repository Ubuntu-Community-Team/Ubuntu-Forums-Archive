---
title: "Adding a hard drive."
date: 2008-05-04
forum: New to Ubuntu
---

### Post by prenger745 on 2008-05-04
Ok I installed ubuntu 8.04.  I installed it on a 20gb hard drive in the Master position.  I have an 80gb ide in the slave position that I would like to use to store whatever...videos, music, documents etc.  I have read some about mounting drives and such but when I try some of the commands I get errors and I am so new to this that I don't really understand.  Here is what I have:

Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x943d4143

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2327    18691596   83  Linux
/dev/sda2            2328        2434      859477+   5  Extended
/dev/sda5            2328        2434      859446   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xba416bc6

   Device Boot      Start         End      Blocks   Id  System
dmcgurk@dan:~$ sudo mkdir /media/sdb
mkdir: cannot create directory `/media/sdb': File exists
dmcgurk@dan:~$ sudo mount /dev/sdb /media/sdb
mount: you must specify the filesystem type


I am trying to mount /dev/sdb.  I would like for it to mount on boot so it is always there.  Is there a way to do this?

Thanks,
Dan

---

### Post by finer recliner on 2008-05-04
the drive may have to be formatted if it isnt already.

you can make the drive mounted at start-up by adding an entry to your /etc/fstab file.

---

### Post by prenger745 on 2008-05-04
Ok I formatted it using Sytem>admin>partition editor (gparted).  I now show a hard drive /dev/sdb in Gparted with 73gb unused.  But when I go to Place>Computer  all I see in there is my cdrom and filesystem harddrive (20gb).

Again, I would like for this drive to be accessible all the time and not have to manually mount it.

Thanks again,
Dan

---

### Post by Eisenwinter on 2008-05-04
Alright.
I have never edited fstab by myself, so I give no warranity here.

The information I will supply here, is given by what I understand from reading [this]("http://www.tuxfiles.org/linuxhelp/fstab.html") page.

In fstab, add this.
```
/dev/sdb /home/<username>/STORAGE_DISK ext3 defaults 1 1
```

After you added this, reboot.
NOTE: do **NOT** touch _ANYTHING ELSE_ in /etc/fstab, or you may break your system.

Anyway, try what I just told you, and report results.
/dev/sdb should be mounted as a folder, in /home/<your username>/STORAGE_DISK.

No warranity given, again.

---

### Post by finer recliner on 2008-05-04
> **Eisenwinter said:**
> Alright.
I have never edited fstab by myself, so I give no warranity here.

The information I will supply here, is given by what I understand from reading [this]("http://www.tuxfiles.org/linuxhelp/fstab.html") page.

In fstab, add this.
```
/dev/sdb /home/<username>/STORAGE_DISK ext3 defaults 1 1
```

After you added this, reboot.
NOTE: do **NOT** touch _ANYTHING ELSE_ in /etc/fstab, or you may break your system.

Anyway, try what I just told you, and report results.
/dev/sdb should be mounted as a folder, in /home/<your username>/STORAGE_DISK.

No warranity given, again.


the line he's asking you to add is partially wrong. first he's assuming you formatted you disk to ext3. if you did, thats fine, if not, be sure to tell the fstab the correct format. second that line says to link the device to some spot in home directory. most linux distros put storage devices on /mnt, or in ubuntu's case, /media. most people use 0 1 for the last 2 arguments.

---

### Post by prenger745 on 2008-05-05
I found a different tutorial and things were going smooth until I tried to mount the drive.  Here is what I have from terminal:

Disk /dev/sdb: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xba416bc6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9733    78180291   83  Linux
dmcgurk@dan:~$ sudo mkdir /media/harddrive
dmcgurk@dan:~$ sudo chmod 777 /media/harddrive
dmcgurk@dan:~$ sudo mount /dev/sdb /media/harddrive
mount: you must specify the filesystem type


I am basically just cutting and pasting these commands and they had nothing about the filesystem type....but I feel like I am getting closer.  Any suggestions?

Thanks,
Dan

---

### Post by prenger745 on 2008-05-05
Wow my first breakthrough with Linux (ubuntu).  I figured out I was mounting the wrong thing.  I should have been mounting sdb1...not sdb.  Why?  I don't know.  Can anyone explain?

Thanks,
Dan


I found a different tutorial and things were going smooth until I tried to mount the drive. Here is what I have from terminal:

Disk /dev/sdb: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xba416bc6

Device Boot Start End Blocks Id System
/dev/sdb1 1 9733 78180291 83 Linux
dmcgurk@dan:~$ sudo mkdir /media/harddrive
dmcgurk@dan:~$ sudo chmod 777 /media/harddrive
dmcgurk@dan:~$ sudo mount /dev/sdb /media/harddrive
mount: you must specify the filesystem type


I am basically just cutting and pasting these commands and they had nothing about the filesystem type....but I feel like I am getting closer. Any suggestions?

Thanks,
Dan

---

### Post by 1875 on 2008-05-05
> **prenger745 said:**
> Wow my first breakthrough with Linux (ubuntu).  I figured out I was mounting the wrong thing.  I should have been mounting sdb1...not sdb.  Why?  I don't know.  Can anyone explain?

Thanks,
Dan


I found a different tutorial and things were going smooth until I tried to mount the drive. Here is what I have from terminal:

Disk /dev/sdb: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xba416bc6

Device Boot Start End Blocks Id System
/dev/sdb1 1 9733 78180291 83 Linux
dmcgurk@dan:~$ sudo mkdir /media/harddrive
dmcgurk@dan:~$ sudo chmod 777 /media/harddrive
dmcgurk@dan:~$ sudo mount /dev/sdb /media/harddrive
mount: you must specify the filesystem type


I am basically just cutting and pasting these commands and they had nothing about the filesystem type....but I feel like I am getting closer. Any suggestions?

Thanks,
Dan

sbd refers to the whole harddrive. Every partition on the drive is given a numeric i.e sbd1 sbd2 etc. When you mount a drive you are really mounting a partition, as the drive may well have multiple partitions on it
you need to give the exact value.

---

