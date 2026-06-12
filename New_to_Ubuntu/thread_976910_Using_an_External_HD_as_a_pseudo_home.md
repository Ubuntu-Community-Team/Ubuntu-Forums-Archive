---
title: "Using an External HD as a pseudo /home?"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by EPrips on 2008-11-09
So I recently installed Ubuntu using a Guided Partition (Use all available free space) because I didn't trust myself to manually partition. I believe this means that I don't have a separate /home partition, which seems to be a very popular partition to have. With this is mind, is there anyway I can use my external HD as a pseudo /home partition?

---

### Post by sdowney717 on 2008-11-09
well you could use it as a backup, copy /home over to the external drive.
really it is little trouble to restore your home folder or even create a new user and copy your /home/username into the new user, you just have to change permission and group of those restored file to be owned by the new 
user.

simply it is just this one command
sudo chown -R username:username /home/username

and you can restore /home and all menu items, desktop, user settings are as before. Although you might have to reinstall some programs which are in the filesystem.
separate partitions for home are not needed, what is needed is a good backup.

---

### Post by EPrips on 2008-11-09
Thanks sdowney, exactly what I was looking for.

---

### Post by sdowney717 on 2008-11-09
if you want to spin down your second drive you can do something like this

scott@scott-desktop:~$ sudo hdparm -S 24 /dev/sdb

/dev/sdb:
 setting standby to 24 (2 minutes)
scott@scott-desktop:~$ 


this will after 2 minutes spin down the drive. when you need it, it will spin up again. I have a second drive and if I dont run this, it will spin down after 15 minutes, I think due to the bios setting, but you can control this yourself, using this command. The number after the -s '24' determines how long till spin down. I think this command will only work for each session, but you could set it to run at startup automatically.

24 gives 2 minutes.

---

