---
title: "[SOLVED] Changing file permissions"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by Bakon Jarser on 2008-05-24
I copied all of my music onto an ext3 partition from dvd's and now all files are read only.  I managed to get all the folders to rw but all files are still read only.  How do I do this without using chown on each folder (there are hundreds of folders).  

These are the commands that I tried.

```
chown -hR Bakon /media/sda3/Music

```

```
chown -hR Bakon /media/sda3/Music/*

```

---

### Post by sam_delta on 2008-05-24
you can read the "Recursive Permission Changes" section under
[https://help.ubuntu.com/community/FilePermissions#head-187da5d5dd0fb3dd3b612ebc7a2bcb5cda9bfd8b](https://help.ubuntu.com/community/FilePermissions#head-187da5d5dd0fb3dd3b612ebc7a2bcb5cda9bfd8b)

to resume the whole chapter, you can type the following to make it read/write to the owner, group and other users```
sudo chmod 666 -R /path/to/someDirectory
```

666 means read/write to owner, group and other users. if you only wish to make it read/write to the owner and just read to group and other users, just replace 666 with "644" 

sam

---

### Post by sdennie on 2008-05-24
I think you'll want to do:

sudo chown -R Bakon:Bakon /media/sda3/Music

---

### Post by Bakon Jarser on 2008-05-24
> **sam_delta said:**
> you can read the "Recursive Permission Changes" section under
[https://help.ubuntu.com/community/FilePermissions#head-187da5d5dd0fb3dd3b612ebc7a2bcb5cda9bfd8b](https://help.ubuntu.com/community/FilePermissions#head-187da5d5dd0fb3dd3b612ebc7a2bcb5cda9bfd8b)

to resume the whole chapter, you can type the following to make it read/write to the owner, group and other users```
sudo chmod 666 -R /path/to/someDirectory
```

666 means read/write to owner, group and other users. if you only wish to make it read/write to the owner and just read to group and other users, just replace 666 with "644" 

sam

Uh oh, I tried this and then opened nautilus to see if they were still read only.  They were gone.  I then opened up nautilus using gksudo and they are there. All files are read write now and still owned by me.  Why can't I see them without root privelages?

---

### Post by sdennie on 2008-05-24
It's possible that you don't have read permissions to one of the parent directories of your Music directory.

---

### Post by Bakon Jarser on 2008-05-24
> **vor said:**
> It's possible that you don't have read permissions to one of the parent directories of your Music directory.

You were right.  It changed the permission on my music folder to no access for some reason.  Thanks.

---

