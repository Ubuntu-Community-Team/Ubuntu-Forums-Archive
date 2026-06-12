---
title: "difficulty creating tar.gz file for &quot;home&quot; folder"
date: 2014-03-16
forum: New to Ubuntu
---

### Post by gregg3 on 2014-03-16
I was unable to copy my home folder (I wanted to back it up) to a flash drive. and someone here in the forum suggested putting the contents of the home folder into a tar.gz file. So I learned how to make tar.gz files via  this formula:

tar czf new-tar-file-name.tar.gz file-or-folder-to-archive

However when I tried to make a tar.gz file for the home folder and entered this (in the terminal):

tar czf BackupSpecial.tar.gz home 

(I'm naming my file BackupSpecial) it didn't work.

Here's the screenshot. 

Can somebody please help me get this to work? Thanks.

---

### Post by sandyd on 2014-03-16
> **gregg3 said:**
> I was unable to copy my home folder (I wanted to back it up) to a flash drive. and someone here in the forum suggested putting the contents of the home folder into a tar.gz file. So I learned how to make tar.gz files via  this formula:

tar czf new-tar-file-name.tar.gz file-or-folder-to-archive

However when I tried to make a tar.gz file for the home folder and entered this (in the terminal):

tar czf BackupSpecial.tar.gz home 

(I'm naming my file BackupSpecial) it didn't work.

Here's the screenshot. 

Can somebody please help me get this to work? Thanks.

Your in your root directory, which you do not have permission to write to.

Perhaps,
```

sudo mkdir /opt/backup
sudo chown -R gregory:gregory /opt/backup
tar czf /opt/backup/HomeBackup.tar.gz /home
```

Which will create a HomeBackup.tar.gz file in /opt/backup that you can access.

There are also other ways of backing up automatically, such as using duplicity, crashplan, rsync, and clonezilla to name a few.

---

### Post by gregg3 on 2014-03-18
> **sandyd said:**
> Your in your root directory, which you do not have permission to write to.

Perhaps,
```

sudo mkdir /opt/backup
sudo chown -R gregory:gregory /opt/backup
tar czf /opt/backup/HomeBackup.tar.gz /home
```

Which will create a HomeBackup.tar.gz file in /opt/backup that you can access.

There are also other ways of backing up automatically, such as using duplicity, crashplan, rsync, and clonezilla to name a few.

Thanks sandyd. I tried your suggestion. Unless I did something wrong, it didn't seem to work. (see screenshot) And I've read using 

sudo thunar

can work to copy the home folder and paste it to a usb drive. True?

---

### Post by The Cog on 2014-03-18
I think you will find that worked apart from a couple of folders that you don't really want backed up anyway.

Don't use sudo thunar to copy the files to the pen drive. The pen drive will have a filesystem that cannot store unix file permissions, so although the file contents might look OK, copying the files back from the pen drive will mess up all the file permissions and cause some odd breakages. It's OK to store just documents that way, but not all the settings files etc. that you get in a backup of your whole home folder.

tar will store the file attributes correctly and will restore them as you extract the files again.

---

### Post by sandyd on 2014-03-18
try
```

tar -zcvf /tmp/mybackup.tar.gz --exclude='/home/gregory/.cache/dconf' --exclude='/home/gregory/.dbus' /home
```
try
```

tar -zcvf /tmp/mybackup.tar.gz --exclude='home/gregory/.cache/dconf' --exclude='home/gregory/.dbus' /home
```
if it still complains

---

### Post by gregg3 on 2014-03-19
> **The Cog said:**
> I think you will find that worked apart from a couple of folders that you don't really want backed up anyway.

Don't use sudo thunar to copy the files to the pen drive. The pen drive will have a filesystem that cannot store unix file permissions, so although the file contents might look OK, copying the files back from the pen drive will mess up all the file permissions and cause some odd breakages. It's OK to store just documents that way, but not all the settings files etc. that you get in a backup of your whole home folder.

tar will store the file attributes correctly and will restore them as you extract the files again.

Thanks Cog. That's very good to know. Appreciate it.

---

### Post by gregg3 on 2014-03-19
> **sandyd said:**
> try
```

tar -zcvf /tmp/mybackup.tar.gz --exclude='/home/gregory/.cache/dconf' --exclude='/home/gregory/.dbus' /home
```
try
```

tar -zcvf /tmp/mybackup.tar.gz --exclude='home/gregory/.cache/dconf' --exclude='home/gregory/.dbus' /home
```
if it still complains

Thanks, Sandy. I ran the first command and the computer ran through a million files, but I don't know what it ended up creating or doing. I took a screenhot of it when it was done so maybe you can tell me? Thanks.

---

