---
title: "[SOLVED] Simple Backup Config/Restore"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by MooseMagnet on 2008-07-25
Found in System > Administration > Simple Backup

How can I use this tool to backup to my external drive? The GUI allows me to backup to /var/backup, root, desktop, or SSH or FTP. Can I do a complete, scheduled backup to my USB drive with this tool?

Thanks.

---

### Post by jimv on 2008-07-25
You know, I had some issues with that not actually creating complete backups...as in not all the files were include that were supposed to be.

I prefer using the PartImage live cd to create an image my entire Ubuntu partition.

---

### Post by DGortze380 on 2008-07-25
you can also use the rsync command if you just want backups of the files and not an iso.. well, you could make an iso using rsync, but that involves some more command combinations.

man rsync for more info, but you probably want something along the lines of:

```

sudo rsync -vrlpogxz --delete --progress /source/directory /destination/directory

```

This will copy all the files from source directory to destination directory with the options: verbose, recursive, links, permissions, owner, group, one file system, compress. It will also update any files on the destination that have been changed on the source, and delete any files on the destination that have been delete on the source. Remove the --delete flag to stop it from deleting any files.

for automatic backups add that command to cron.

```

man cron

```

---

### Post by bobnutfield on 2008-07-25
Thank you for that.....very good use of the rsync command.

Bob

---

### Post by DGortze380 on 2008-07-25
> **bobnutfield said:**
> Thank you for that.....very good use of the rsync command.

Bob

Not a problem. I just set it up myself, just had to post the command.

---

### Post by AndyCooll on 2008-07-25
DGortze380 has given you the essence of rsync. However the command can be simplified to:
```
sudo rsync -avz --delete /source/directory /destination/directory
```
the "-a" (archive mode) is a combination of "-rlptgoD" basically it works recursively and maintains file information such as creation dates, permissions etc.

And if you're just copying your home directory you don't need the "sudo" either.

:cool:

---

### Post by MooseMagnet on 2008-07-26
I'll need to study more. The commands are still confusing to me.
In "How Linux Works" the author recommends creating a tar archive for full and incremental backups.

You prefer rsync ?

---

### Post by DGortze380 on 2008-07-26
> **MooseMagnet said:**
> I'll need to study more. The commands are still confusing to me.
In "How Linux Works" the author recommends creating a tar archive for full and incremental backups.

You prefer rsync ?

A .tar archive is similar to a .zip file in windows. It's a way to compress files. 

rsync is a versatile command but one way to use it is to have it go through an make copies of all the files in a particular directory (/  if you want the whole system backed up). You can then use the command to maintain the backup by checking for changes on the system and updating the destination directory.  

The command I provided above does all of that. Run it once to create a backup, and run it as often as you like to update your backup. You could then make a tar archive of that backup if space is an issue.

---

### Post by bab1 on 2008-07-26
A little clarification -- A tar file is for archiving, but it does not have compression.  You need to gzip it to compress it.  Hence, tar.gz.

---

### Post by MooseMagnet on 2008-07-26
rich@rich-laptop:~$ sudo rsync -avz --delete /dev/sda1 /dev/sdb1
building file list ... done
sda1

sent 72 bytes  received 26 bytes  196.00 bytes/sec
total size is 0  speedup is 0.00
rich@rich-laptop:~$ 

I'm not doing something correctly?

---

### Post by AndyCooll on 2008-07-26
That should be something like:
```
rsync -avz --delete /home/yourusername /mnt/backup/yourusername
```

And with reference to tar archiving files, rsync can do that too. In essence it's saving your backup file as a compressed format rather than simply a copy-for-copy format. It's your choice. 
:cool:

---

### Post by MooseMagnet on 2008-07-26
With this example:
sudo rsync -avz --delete /source/directory /destination/directory

is "/destination/directory"  the label I assigned the USB drive,
or is it /dev/dvb1  ?

---

### Post by MooseMagnet on 2008-07-26
I've been able to drag and drop, so I know I have permissions.

I've tried every combination I can think of, but none of it works.

Tried simplifying it down to this:
cp /home/rich/Test.odt /media/my_external/Backup

But that doesn't work either.

What the heck am I doing wrong?

---

### Post by DGortze380 on 2008-07-26
> **MooseMagnet said:**
> I've been able to drag and drop, so I know I have permissions.

I've tried every combination I can think of, but none of it works.

Tried simplifying it down to this:
cp /home/rich/Test.odt /media/my_external/Backup

But that doesn't work either.

What the heck am I doing wrong?

You need to copy to a mounted drive. so I think what you're looking for is this (assuming your root partition ( / ) is on sda1 and USB is the name of the drive mounted from sdb1.

```

sudo rsync -vrlpogxz --delete --progress / /media/USB

```

If you just wanted to backup your home directory you would want something like this (again assuming the drive you're writing to is mounted as USB and replace anything in <>)

```

sudo rsync -vrlpogxz --delete --progress /home/<username> /media/USB

```


 You need to use mounted directories in the command. drive IDs won't work.
You don't really want to use cp or drag and drop because it doesn't guarantee that you'll maintain all the permissions/owners/groups etc. that you may need.

---

### Post by MooseMagnet on 2008-07-27
It is mounted. Its mount point is /media. It is /media/my_external.
It seemed the question changed enough from the original, that I started a different thread. Hope that doesn't violate any rules.

It is here:
[http://ubuntuforums.org/showthread.php?t=871321](http://ubuntuforums.org/showthread.php?t=871321)

---

### Post by MooseMagnet on 2008-08-11
I was able to backup to my USB
/rich
/etc
/var
/usr

I put them on the USB in a folder named "07_31_2008"

My system crashed this morning. I NEED to restore this info. But I can not figure out the correct rsync command to do it.

I have tried this:

rich@rich-laptop:~$ sudo rsync /media/USB/07_31_2008/etc /etc
sudo: unable to initialize PAM: No such file or directory
skipping directory /media/USB/07_31_2008/etc
rich@rich-laptop:~$ 

Can you please help?? What am I doing wrong.
Thank you!!!

---

### Post by MooseMagnet on 2008-08-11
Dang. The "options" in the rsync command are NOT OPTIONAL. 
You MUST include at least on OPTION.

This continues to trick my pea brain. Arrgghhh!!!!

Got it fixed. Back to work.

Rich

---

### Post by MooseMagnet on 2008-08-11
Well, I don't quite have it back okay after all.

The .jpg images are NOT timy pictures, they are blue thumbnails. Just little blue boxes - not previewed small images.

Any ideas on how to restore the tiny previews of the jpg pics?

Thanks.

---

