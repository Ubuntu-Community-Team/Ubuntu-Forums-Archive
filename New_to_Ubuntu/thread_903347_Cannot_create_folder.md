---
title: "Cannot create folder"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by thetaskmaster on 2008-08-28
Hi all. New to UBUNTU. Just performed a clean install of UBUNTU and all updates, no problem. Once I was happy it was working OK I then installed a slave drive. Formatted with GPARTED to ext2. Drive is mounted and showing in places - shows as 41.1 GB Media. When I browse to the drive I cannot right-click to create a new folder, the option is greyed. Am I missing something obvious?

---

### Post by Theo148 on 2008-08-28
By default, the drive's permissions are set so that only root can create folders and stuff. You'll need to use the command 'sudo mkdir path/to/folder/you/want/to/make'. :)

---

### Post by sh4d0w808 on 2008-08-28
I think U've made the new partition as root, but try to create a direcory as user. Change the ownership from root to your user ID and then the creation should work as normal user.

sudo chown <youruserID.yourusergroup> <drive_identifier>

---

### Post by drs305 on 2008-08-28
> **thetaskmaster said:**
> Hi all. New to UBUNTU. Just performed a clean install of UBUNTU and all updates, no problem. Once I was happy it was working OK I then installed a slave drive. Formatted with GPARTED to ext2. Drive is mounted and showing in places - shows as 41.1 GB Media. When I browse to the drive I cannot right-click to create a new folder, the option is greyed. Am I missing something obvious?

When you add a new partition by default it is owned by root. As a normal user you can't access it. You can change the entire partition's ownership to yourself or just some of the folders. To do this:

```
sudo chown -R *username:username* /mountpoint
chmod -R 755 /mountpoint
```

Example:
sudo chown -R myusername:myusername /media/mypartition
chmod -R 755 /media/mypartition

---

### Post by thetaskmaster on 2008-08-28
thanks for the quick response guys.
okay, where do I type the sudo code? In terminal?
sorry if I sound lame, but this is new to me

I go applications>accessories>terminal

and I get the name of the pc come up   haulrite@haulrite-server:~$

---

### Post by thetaskmaster on 2008-08-28
Sorted! Thanks guys!

---

