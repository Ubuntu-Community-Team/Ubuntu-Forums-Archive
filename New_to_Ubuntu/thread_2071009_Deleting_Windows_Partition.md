---
title: "Deleting Windows Partition"
date: 2012-10-14
forum: New to Ubuntu
---

### Post by Norm24 on 2012-10-14
I'm dual booting with Vista/12.04 and have not used Windows in several years and see no point in having it waste space.I have two questions in regards to deleting the Windows partition.

1.Once the windows partition is deleted is the unallocated space available to Ubuntu or must I do something to make one large Ubuntu partition?

2.Hows does this affect Grub?

Thanks.

---

### Post by g_s_patra on 2012-10-14
You can use Partition Manager (gparted) to resize or merge them. But if you are determined to use Ubuntu only, then move all the Home-Folder to removable disks or other computer, & have a fresh installation - do take care about the options.

---

### Post by zombifier25 on 2012-10-14
1. If you want to remove Windows, like suggested, simply use GParted to reformat Windows' partition to ext4 and use it as an extra partition. If you want to actually merge the partition to Ubuntu's, you must use a liveCD because you cannot modify a partition that it in use. GParted's LiveCD is one you can use, along with Ubuntu LiveCD, etc.

2. It should not affect Grub. After removing Window, run this command to update it:
```
sudo update-grub
```

---

### Post by ajgreeny on 2012-10-14
If you try to extend your ubuntu OS partition into the now empty windows space be prepared for a very long job. Depending on the partition sizes it can take a long long time to do the initial partition check, then extend the partition, then do another partition check.

If I was in the same situation I would just format the empty space to ext4, then edit /etc/fstab to make the partition mount at boot time, and finally use the terminal to change ownership (chown) and/or the read/write permissions (chmod) of the new partition's mountpoint folder to allow read and write by you as user.

---

