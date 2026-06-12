---
title: "Missing mount point /home ?"
date: 2019-01-04
forum: New to Ubuntu
---

### Post by pmaff on 2019-01-04
Hello,

I am new to Ubuntu but not to Linux, was using SuSE before. 
I installed Ubuntu 18.04 on a dual boot system and so far everything is running fine. 

 I installed a separate /home partition on a 2TB SSD together with some D-device ("Laufwerk" in German) of Windows 10,
 but when doing a df -k the /home mount point does not show up.

I do have an icon with "1.4TB Volume" on my XFCE desktop, when double clicking this, a
/dev/sdb3 with /media/pmaff/... and some numbers/characters is mounted.

From SuSE I am used to the /home just being mounted normally at boot time so what am I doing wrong here?
Can I simply use gnome-disks to change this mount point?

gnome-disks currenlty says that "Mount Point" is /mnt/ and the same numbers/characters combination as shown under /media/pmaff and
that "User Session Defaults" is "ON" with all the options greyed out there.
I can only change mount point when putting "User Session Defaults" "OFF" for ext4 partition sdb3.

Also please excuse possible English mispellings as this is not my native language.

BR Pete

P.S.: when formatting this posting, all gets into one big chunk after previewing the post. :-(

---

### Post by CatKiller on 2019-01-04
Partition mounting at boot time (which is what you want if you're mounting /home) is handled by entries in the /etc/fstab file.

---

### Post by Impavidus on 2019-01-04
If df doesn't list your /home partition, it's not mounted at /home. When you use the file manager to mount something, it gets mounted at /media/username/UUID/. Nothing should get mounted automatically at /mnt.

Have a look at your /etc/fstab. Use it to tell your system to mount your /home partition at boot. Assuming you already have some files in /home, be sure not to hide them under the mountpoint, but transfer them to the /home partition. There are some GUI tools meant to make it easier to make changes to fstab, but in fact it's already so easy that those tools are little more than one more thing that can go wrong.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by pmaff on 2019-01-06
> **Impavidus said:**
> If df doesn't list your /home partition, it's not mounted at /home. When you use the file manager to mount something, it gets mounted at /media/username/UUID/. Nothing should get mounted automatically at /mnt.

Have a look at your /etc/fstab. Use it to tell your system to mount your /home partition at boot. Assuming you already have some files in /home, be sure not to hide them under the mountpoint, but transfer them to the /home partition. There are some GUI tools meant to make it easier to make changes to fstab, but in fact it's already so easy that those tools are little more than one more thing that can go wrong.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

I do have access to /home so it should be mounted. /etc/fstab does only show  / , /swapfile and /boot/efi although at installation I set /home on this separate 2TB SSD.

The links you named end with "Internal Server Error".

---

### Post by jeremy31 on 2019-01-06
Try the links again, the server does seem to be running a bit slow now

---

### Post by pmaff on 2019-01-06
> **jeremy31 said:**
> Try the links again, the server does seem to be running a bit slow now

Thanks, works.

Maybe I should be more accurate: I do not want to move /home to another disk.
It looks as if it is already mounted at /mnt on the 2TB disk in /dev/sdb3, it should stay there but it should be mounted at /home at boot time.
Can I simply use gnome-disks, disable "User Session Defaults" and change the Mount point from 
/mnt/<looks like the UUID> 
to
/home
?

Thanks in advance

---

### Post by CatKiller on 2019-01-06
Mounting at boot time is controlled by /etc/fstab. You can add a new entry.

---

### Post by jdeca57 on 2019-01-06
You should modify /etc/fstab adding a line that makes the association between the disk partition and /home. Normally, the disk is identified with UUID but you can refer to the block device and the line should be (if the block device is /dev/sdb3)
/dev/sdb3 /home ext4 defaults 0 0
Of course, that is if you use ext4. See man fstab for more information, or the link provided earlier. After a reboot the actual /home will be replaced with the one on /dev/sdb3

---

### Post by Impavidus on 2019-01-06
If the partition intended to be your /home partition is not mounted, you still have access to /home. That's just your /home directory on the root partition. So, if I get this right, the partition intended to be your /home partition is currently mounted at /mnt or /media/whatever and you want it at /home. The guide I linked to explains how to do this.

It seems something went wrong during installation. The /home partition was not mounted and the installer created an ordinary home directory instead and filled it with some default files that give you the standard configuration of a Xubuntu system.

Let's see this, for an overview:```
cat /etc/fstab
sudo parted -l
df -h
```

I don't use gnome-disks to configure were to mount stuff. It's yet another GUI tool to do what can easier be done from command line.

---

### Post by pmaff on 2019-01-06
> **Impavidus said:**
> If the partition intended to be your /home partition is not mounted, you still have access to /home. That's just your /home directory on the root partition. So, if I get this right, the partition intended to be your /home partition is currently mounted at /mnt or /media/whatever and you want it at /home. The guide I linked to explains how to do this.

It seems something went wrong during installation. The /home partition was not mounted and the installer created an ordinary home directory instead and filled it with some default files that give you the standard configuration of a Xubuntu system.

Let's see this, for an overview:```
cat /etc/fstab
sudo parted -l
df -h
```

I don't use gnome-disks to configure were to mount stuff. It's yet another GUI tool to do what can easier be done from command line.

I fear that you are right: when changing /etc/fstab to mount /home of the /dev/sdb3 then there is some home directory with my user directory but with very old content,
so some files are missing.
Maybe the installation process somehow ignored my wish to mount  /dev/sdb3  on /home and installed /home on / which is on another disk.
Where the older content of /dev/sdb3 comes from I do not know, maybe Acronis went amok there...

I will try to mount sdb3 to home_better, transfer the files, rename the old home to home_old as root and mount sdb3 to /home, so then it should be possible
to delete the old /home on / .

---

### Post by CatKiller on 2019-01-06
An arguably tidier way to do it would be from the live USB. Update the other partition with the contents of your Home folder on the / partition, edit your fstab to mount the /home partition, then reboot.

---

### Post by pmaff on 2019-01-06
Thanks for all your help. 
The dedicated /home on sdb3 works after some rsync.
I have the last home from / in home_old now.
I will recheck all together but it should be ok now.

---

