---
title: "Change file permissions of Windows folders/partitions"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by hoverX on 2008-10-05
Hey Everyone,

I have a desktop running Ubuntu 8.04 (recently converted from XP).  This particular machine also has a few windows partitions where i store a large majority of my files.  How do i change the file permissions of these partitions so other Ubuntu machines (my laptop)  can copy and delete files from these partitions?

---

### Post by rybaxs on 2008-10-05
You can directly copy and delete the files from the other disk..

Places -> Disk name    just open-
Try to see at the desktop if there are any disk.. then open it..

no need to change permission.
only unix files or Ubuntu files had permission settings..

tips for permission
go to terminal

```

$ chmod --help

```

---

### Post by hoverX on 2008-10-05
I get an error message "Read only filesystem"

---

### Post by hwnddawg on 2008-10-05
> **hoverX said:**
> I get an error message "Read only filesystem"
The Windows partition(s) are usually un-mounted, or if mounted, are read-only.  You can change these settings in /etc/fstab, then reboot.

On Kubuntu, instead of directly editing fstab, i can also use the "System Settings -> Advanced -> Disk & Filesystems" utility.

HTH,

Wyn

P.S.  as rybaxs says - AFAIK, there's no way to set permissions *within* the Windows partitions.  i wish there were, as my box is a dual-boot machine with multiple users who need to read/write their Windows "My Documents" folders, but i'd like to prevent those users from stepping all over each others' data.

---

### Post by hoverX on 2008-10-05
thanks for the input!  The thing that i don't understand is that when accessing these partitions on the machine they belong to i have read/write access.  it's only when accessing them over the network do i have these read-only problems.

---

### Post by kansasnoob on 2008-10-05
I use ntfsprogs and I can access anything on any ntfs drive without any special privileges. Well, it may ask for my password once in a while.

Just know that you need to know what you're doing!

[http://www.linux-ntfs.org/doku.php](http://www.linux-ntfs.org/doku.php)

It's in the repos so you can either install it from synaptic or:

```
sudo apt-get install ntfsprogs
```

---

### Post by kansasnoob on 2008-10-05
I should have also said that ntfs-config is an option, I just prefer ntfsprogs. ntfs-config is also in the repos.

---

