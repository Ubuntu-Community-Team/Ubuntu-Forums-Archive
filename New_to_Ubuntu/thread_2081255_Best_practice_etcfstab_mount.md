---
title: "Best practice /etc/fstab mount"
date: 2012-11-06
forum: New to Ubuntu
---

### Post by supermario87 on 2012-11-06
Hi!!I've one question for you..

I need to mount some EXT4 partitions automatically on boot through fstab file. The mountpoints are /mnt/<name> etc etc.  I want to give writing permission to some users and groups with something like 775(I will choose later).

So here is the problem... what's the best practice??


[LIST=1]
[*]Create the folders in /mnt and give them the right permissions, like 775 and user:group owner. I must preserve this scheme for all the files that will be written, it is no good if a program run by an user will write stuff with different permissions.
[*]Create the folders in /mnt as root, so with 755 and root:root owner and add some mount options in fstab file. As said before, I must preserve permissions for all the files within.
[/LIST]


Thanks!

---

### Post by dannyboy79 on 2012-11-06
what filesystem are the partitions?

---

### Post by arpanaut on 2012-11-06
This will give you the basics, should be easy to figure out from there.
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by PinkFloyd102489 on 2012-11-06
You can use the "uid" and "gid" options in the fstab.

Example:

```

/dev/sdc1 /mnt/share ext4 rw,uid=1000,gid=1000 0 0

```

Just substitute the correct uid or gid for the given user.

---

### Post by supermario87 on 2012-11-06
Partitions will be ext4.

---

### Post by supermario87 on 2012-11-06
> **PinkFloyd102489 said:**
> You can use the "uid" and "gid" options in the fstab.

Example:

```

/dev/sdc1 /mnt/share ext4 rw,uid=1000,gid=1000 0 0

```Just substitute the correct uid or gid for the given user.

I think that ext4 FS does not support uid and gid options!

---

### Post by LewisTM on 2012-11-06
The proper permissions should be set in each partitions root directory, not on the mount points (your #1).

You are right to say ext4 does not support fstab-derived UIDs. It's all done at the fs level.

Ubuntu's umask is 0002 so all apps should create 775 files with the current user:group as owner, unless the app is misbehaved.

Your best bet would be to set the SGID bit for your directories in your individual partitions. It will force all new files to acquire the group that owns the directory. 
```
sudo chmod g+s -R /mnt/<name>
```
You could also go with a more user-centric approach with ACLs (access control lists). 
Set default directory ACLs and also add them to existing files, independent of ownership.
```
sudo setfacl -R -d -m <user>:rwX /mnt/<name>
sudo setfacl -R -m <user>:rwX /mnt/<name>
```
Good luck!

---

