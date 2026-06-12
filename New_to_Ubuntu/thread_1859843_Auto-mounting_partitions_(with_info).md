---
title: "Auto-mounting partitions (with info)"
date: 2011-10-14
forum: New to Ubuntu
---

### Post by omallz on 2011-10-14
Hey all :)

I want to auto-mount my ntfs partition with my music on it so Banshee can load my library from it no problems.
In the past I reboot and try to get Banshee to play my library (imported from another partition) and it will not play any of them.

I have tried using a few programs to mount the partition/s, but they already get mounted by Ubuntu ( I dual-boot with Windows 7) and so any additions to fstab do nothing of use.

[B]fdisk -l output
[/B]
Disk /dev/sda: 500.1 GB, 500107862016 bytes
240 heads, 63 sectors/track, 64601 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa94cfe9b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *      206848    86018047    42905600    7  HPFS/NTFS/exFAT
/dev/sda2        86032800   976769930   445368565+   7  HPFS/NTFS/exFAT

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfed905a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   910359044   455178498+   7  HPFS/NTFS/exFAT
/dev/sdb2       910360574   976771071    33205249    5  Extended
/dev/sdb5       968390656   976771071     4190208   82  Linux swap / Solaris
/dev/sdb6       910360576   960006143    24822784   83  Linux
/dev/sdb7       960008192   968382463     4187136   82  Linux swap / Solaris

Partition table entries are not in disk order

[B]/etc/fstab output
[/B]
UUID=4084fe14-51e4-413c-8c11-21fc54a591f0 swap swap sw 0 0
UUID=ac508ba7-c994-49b2-a363-e60886f111c0 / ext4 defaults 0 1
UUID=94e95b17-7c50-4317-821b-8c248f414604 swap swap sw 0 0

Help?

---

### Post by WasMeHere on 2011-10-14
Hello omallz,

Welcome to the Ubuntu Forums. We are many people around to help you, and it will be easier if you

- describe your computer (hardware and operating system(s) and versions)

- post the output of some more terminal commands.
```
df
```
```
sudo blkid
```

It is important to know how your 'music disk partition' is connected.

Have fun finding out about Ubuntu
Olle

---

### Post by omallz on 2011-10-14
Sorry, of course.
I'm running 11.10 32-bit on a dual-core E6600. 
I have fixed this problem once before I believe.

The music is on the 'media' partition.

I believe this post is related to my problem. 
[http://ubuntuforums.org/showthread.php?t=1742893](http://ubuntuforums.org/showthread.php?t=1742893)

The files will play if I add them back in from the file system, but won't from the library itself. 

**fd**

Filesystem           1K-blocks Used Available Use% Mounted on
/dev/sdb6             24432772   3508284  19683352  16% /
udev                   2055048         8   2055040   1% /dev
tmpfs                   824828       844    823984   1% /run
none                      5120         0      5120   0% /run/lock
none                   2062064      3416   2058648   1% /run/shm
/dev/sda1             42905596  23165680  19739916  54% /media/windows
/dev/sda2            445368564 413359196  32009368  93% /media/data
/dev/sdb1            455178492 442361980  12816512  98% /media/media

**blkid**
/dev/sda1: LABEL="Windows 7 SP1 x64" UUID="C0AC600AAC5FF97C" TYPE="ntfs" 
/dev/sda2: LABEL="Data" UUID="14764F6D764F4F24" TYPE="ntfs" 
/dev/sdb1: LABEL="Media" UUID="7C64A0C064A07E90" TYPE="ntfs" 
/dev/sdb5: UUID="4084fe14-51e4-413c-8c11-21fc54a591f0" TYPE="swap" 
/dev/sdb6: UUID="ac508ba7-c994-49b2-a363-e60886f111c0" TYPE="ext4" 
/dev/sdb7: UUID="94e95b17-7c50-4317-821b-8c248f414604" TYPE="swap"

---

### Post by WasMeHere on 2011-10-14
> **omallz said:**
> ...
**df**

Filesystem           1K-blocks Used Available Use% Mounted on
/dev/sdb6             24432772   3508284  19683352  16% /
udev                   2055048         8   2055040   1% /dev
tmpfs                   824828       844    823984   1% /run
none                      5120         0      5120   0% /run/lock
none                   2062064      3416   2058648   1% /run/shm
/dev/sda1             42905596  23165680  19739916  54% /media/windows
/dev/sda2            445368564 413359196  32009368  93% /media/data
[COLOR="Red"]/dev/sdb1            455178492 442361980  12816512  98% /media/media[/COLOR]

**blkid**
/dev/sda1: LABEL="Windows 7 SP1 x64" UUID="C0AC600AAC5FF97C" TYPE="ntfs" 
/dev/sda2: LABEL="Data" UUID="14764F6D764F4F24" TYPE="ntfs" 
[COLOR="Red"]/dev/sdb1: LABEL="Media" UUID="7C64A0C064A07E90" TYPE="ntfs" [/COLOR]
/dev/sdb5: UUID="4084fe14-51e4-413c-8c11-21fc54a591f0" TYPE="swap" 
/dev/sdb6: UUID="ac508ba7-c994-49b2-a363-e60886f111c0" TYPE="ext4" 
/dev/sdb7: UUID="94e95b17-7c50-4317-821b-8c248f414604" TYPE="swap"
Is it the [COLOR="Red"]media[/COLOR] partition that you want to mount (in a better way so that Banshee can read from it?

It is not in your /etc/fstab file, so you have to mount in manually, which is very easy using Nautilus. Just select it, and it will be mounted. When you ran [COLOR="Red"]df[/COLOR] it was mounted. Do you remember how? Can Banshee play its files now? In that case read the content of your /etc/mtab file.

But you can also try to add the following line to /etc/fstab using
```
sudo nano /etc/fstab
```

```
UUID=7C64A0C064A07E90 /mnt/media ntfs defaults,uid=1000,windows_names 0 0
``` and create that directory 
```
sudo mkdir /mnt/media
``` and then reboot your computer.

Good luck
Olle

---

### Post by omallz on 2011-10-14
I'll give this a go now Olle. 

At the moment it is just recognized in the 'Devices' pane in Nautilus and I can browse it. This happens each time I install Ubuntu (it coming up in the pane) and  I feel like this makes any mounting I do in fstab redundant as it will just be pointing to the same place, correct me if I'm wrong :)

**mtab**

/dev/sdb6 / ext4 rw,commit=0 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/jason/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=jason 0 0


Edit: Ok I added it all to fstab, and the media partition/drive is now not in the sidebar of nautilus. That's a good thing I suppose. Will post results of banshee soon.
Edit 2: It works :D Thanks a lot! I am curious about this though. Eg why does Ubuntu show it as a device, and can I just mount the other drives in /mnt if I want the same thing to occur?
Edit 3: Quick question also - I can't open .docx and seemingly .doc files with LibreOffice Writer. Any tips?

---

### Post by WasMeHere on 2011-10-14
> **omallz said:**
> I'll give this a go now Olle. 

At the moment it is just recognized in the 'Devices' pane in Nautilus and I can browse it. This happens each time I install Ubuntu (it coming up in the pane) and  I feel like this makes any mounting I do in fstab redundant as it will just be pointing to the same place, correct me if I'm wrong :)
Well, it is recognized but not mounted until you try to enter into it with Nautilus. Then it will be mounted and you will see the 'eject' symbol in the left panel of Nautilus. Of course you can also mount/unmount it manually from the terminal or with some other tool. In this mode you mount it as user (your own [un]qualified user account).
> **omallz said:**
> 
**mtab** 
...
Edit: Ok I added it all to fstab, and the media partition/drive is now not in the sidebar of nautilus. That's a good thing I suppose. Will post results of banshee soon.
Edit 2: It works :D Thanks a lot! I am curious about this though. Eg why does Ubuntu show it as a device, and can I just mount the other drives in /mnt if I want the same thing to occur?
Edit 3: Quick question also - I can't open .docx and seemingly .doc files with LibreOffice Writer. Any tips?
1+2: It is convenient to show partitions that can be easily mounted or unmounted as devices. You can mount any partition via fstab, but your system will complain if it is absent during boot (unless you set it not to mount during boot), and the standard setting is that you mount/umount it as root ```
sudo [u]mount
```
So don't enter your USB drives into fstab!

3: The main task of LibreOffice Writer is to read and write such files. Something is very wrong! But you are running 'bleeding edge' 11.10, and you must expect lots of bugs during the next few weeks. If your problem with LibreOffice will not be solved soon enough, I suggest that you start a new thread about that problem.

So right now, if you need a production tool, run an older version of  Ubuntu!

Have fun finding out about Ubuntu
Olle
ps/ When you feel confident that your problem is solved, please mark this thread SOLVED! /ds

---

