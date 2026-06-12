---
title: "New version install."
date: 2012-01-24
forum: New to Ubuntu
---

### Post by melrokz on 2012-01-24
I'm running Ubuntu 11.10 and my disk has 3 partitions: 
> / 
/home
swap

When I do a fresh install of 12.04, I'd like to use the same /home drive. When I install 12.04, at the partitioning screen I chose to use /home, which was used by 11.10. Once 12.04 has been installed, will it configure the required owner and permissions for the home folder correctly, or will I have to set the permissions manually?

---

### Post by SuaSwe on 2012-01-24
I believe that when you go through the install for 12.04, set the mount point for your home partition to /home and ensure that 'format' is NOT ticked or otherwise selected, nothing on that partition will be changed; it will simply be used as the location for all users' home directories in the new install.

---

### Post by melrokz on 2012-01-24
So I believe I'll have to change the uid and gid after installation?

---

### Post by melrokz on 2012-01-24
When I installed 11.10 in this way, whenever I open my home folder, the system used to hang. Anyone knows about this?

---

### Post by Cheesemill on 2012-01-24
The UID and GUID of files are preserved when you install keeping an old home folder.

That means the first user you create will have correct permissions for the first home folder created during the previous install, and so on for the second, third, etc...

If you only have one user then it will all be smooth sailing, if you have more than one just make sure you create them in the same order as before.

---

