---
title: "Automatic backups to FAT partition"
date: 2014-03-06
forum: New to Ubuntu
---

### Post by jwn-2 on 2014-03-06
I want to use the rsync command to make automatic backups of my data at startup to a FAT partition on my disk. The rsync command works from a terminal, but only once I have vissited the FAT partition at least once. At startup it seems the FAT partition is not available. How can I make this FAT partition available before I execute the rsync command?

---

### Post by TheFu on 2014-03-06
You need to mount it before attempting to use it.
```
sudo mount /dev/path /mnt/point
```
Mount can only be performed by root.
Or you could use the fstab
Or you could use autofs
Or you could write a small script that **mount**s and does the **rsync** then **umount**s. Be certain to validate that the mount succeeded. Those are the commands in bold. Use **df** to check the mount worked.

FAT is not the best type of partition for linux backups, but it is fine for purely data stuff where permissions don't matter.

---

### Post by Lars Noodén on 2014-03-06
> **TheFu said:**
> FAT is not the best type of partition for linux backups, but it is fine for purely data stuff where permissions don't matter.

A better format would be one of the EXT file systems.  That would allow you to keep your permissions.  If something is forcing you to use FAT, then you might look to tar instead.  It will be slower but you won't lose anything like you would using rsync on FAT.

---

### Post by jwn-2 on 2014-03-06
Thanks guys. It seems as if fstab would be the best way to do it. HOWEVER, I am unable to change the contents of /etc/fstab. How do I establish permission to change it?

---

### Post by nunecas123 on 2014-03-06
Go to your terminal and write this down:
```
sudo gedit /etc/fstab
```

You must have root permissions to be able to edit system parts ;)

---

### Post by TheFu on 2014-03-06
With **sudo**.  Be careful. Understand the settings and understand that you can't just grab the drive and walk away without doing an **umount **first.  Data corruption is likely - even 5 minutes after the last write, the disk buffers may not have been flushed.

Manually type :
```
sync; sync; sync
```
to flush buffers. Most of the time, this typing will be enough delay that the last sync is instantaneous. Don't copy/paste the command or script it! This is an old UNIX-admin tip that still applies for small files. Clearly, if a 20G file is being copied, it will take a very long time to sync the disks. ;)

---

### Post by jwn-2 on 2014-03-06
Okay guys, I really need help here.

I have now tried the following:

1) sudo mount /dev/sda3 /media/jonnie

This works, but it has some problems: a) --/jonnie becomes my FAT partition, instead of adding it as a sub-dir in --/jonnie. I even added a / after jonnie with no difference. b) If I add the name I want it to be (/Backup) after jonnie (/media/jonnie/Backup), I get an error (directory doesn´t exist). c) I need to enter my password before this is executed, which makes it unable to automate.

2) Adding ¨LABEL=Backup /media/jonnie/¨ to fstab.

This gives me an error while booting, and the partition is completely unavailable after booting. What should I enter in fstab?

3) autofs I can´t quite figure out how to use.

Sorry for asking so much questions, but if I never ask, I will never know!

---

### Post by TheFu on 2014-03-06
Setup the backup command to run without a password.  **man sudoers** will explain how. I don't know off the top of my head. Only allow 1, exact-with-all-options command, not every command, to run without a sudo password.

If the directory doesn't exist - create it - on the FAT partition. Or create it on the main file system and mount the FAT partition on Backup instead.  

Permissions with FAT will be ignored. Only the options to the mount will control them.

I've never used Labels - however - I would avoid having funny characters or spaces.  That means don't use '/' in the label.

No need to reboot to test the mount aspects. Use **sudo mount -a** - it will read the fstab and mount any partitions not already mounted.

autofs is non-trivial, but has some handy capabilities. Added complexity is the tradeoff. If you use the fstab, then autofs should not be used.

---

### Post by oldfred on 2014-03-06
Do not mix up the mount point and a folder name inside the mount.
I might make the mount backup and then you use rsync to copy to folder jonnie in your backup mount.

An example of editing fstab.
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.


 [https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

Very simple script:
      
 Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh

   Bit more advanced script.
Sample rsync file by TheFu
[http://ubuntuforums.org/showthread.php?t=2200427&p=12911880#post12911880](http://ubuntuforums.org/showthread.php?t=2200427&p=12911880#post12911880)

 Backup to external with check of mounted & email
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)
rsync confirmation list:
[http://ubuntuforums.org/showthread.php?t=1692800](http://ubuntuforums.org/showthread.php?t=1692800)

But I had backed up to FAT32 partition for about a year, when first using Linux. What ever I used made a 4GB image. But it seemed strange at the time that the 4GB image never grew larger? 
Later I learned that FAT32 has a max of 4GB and I never had a full backup.
Also FAT does not have a journal so recovery with chkdsk may take longer or not even work. If you need Windows compatibility use NTFS. And you need Windows to run the chkdsk regularly. Every 40 or 60 boots Ubuntu runs fsck on Linux file systems but cannot do that on Windows file systems.

---

### Post by TheFu on 2014-03-06
> **oldfred said:**
>    Bit more advanced script.
Sample rsync file by TheFu
[http://ubuntuforums.org/showthread.php?t=2200427&p=12911880#post12911880](http://ubuntuforums.org/showthread.php?t=2200427&p=12911880#post12911880)


That is NOT an rsync script. It uses rdiff-backup. It is non-networked, so good only for simple, directly connected backups.

The perl script that I really use for backups is here. [http://blog.jdpfu.com/2013/10/20/rdiff-backup-real-use](http://blog.jdpfu.com/2013/10/20/rdiff-backup-real-use) with a link near the bottom of the article.  It needs to be customized slightly before use - things removed, things added, other important directories added based on the local needs. Stuff like that.  It uses a networked backup server - not local disks, so the userid and server would need to be modified too.  It is NOT plug-n-use.

---

### Post by oldfred on 2014-03-06
Thanks TheFu, I will update notes.

---

### Post by jwn-2 on 2014-03-07
&#65279;Thanks guys, you have been a great help so far. One more (hopefully the last) question:

The syntax in sudoers.d for running backup without a password is (I think):

jonnie [host_name] = NOPASSWD: ---/Backup

The host_name is apparently my machine name. What is the machine´s name and/or where do I find it.

---

### Post by TheFu on 2014-03-07
type '**hostname**' into a terminal (no ticks).
But is that really needed when it is on the localhost? I haven't read the man page recently so don't worry if it is required.

---

### Post by jwn-2 on 2014-03-08
&#65279;Thanks guys for all your help here, especially TheFu. My automatic backup is now running smoothly. Without you guys I would not be able to do it. And I learned a lot about Ubuntu, Linux and Unix in the process.

---

### Post by TheFu on 2014-03-08
Happy to have helped.  Please mark the thread as **SOLVED** to help others.

---

### Post by jwn-2 on 2014-03-08
Okay, another question: How do I mark it as solved?

---

### Post by Iowan on 2014-03-08
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by jwn-2 on 2014-03-08
Thanks and done!

---

