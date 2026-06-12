---
title: "Changing Permissions and Ownership of External HD"
date: 2011-10-27
forum: New to Ubuntu
---

### Post by Mega_Fauna on 2011-10-27
Hi,

I'd like to change the ownership and permissions of an external hard-drives to root so I don't accidentally work on it as it is a backup. The drive is Ext3.

I have read (most of) [_this_]("https://help.ubuntu.com/community/FilePermissions") and below is what I've done, but it's not working correctly!

```
sudo chown root:root /media/ST_ISIDORE

sudo chmod 744 -R /media/ST_ISIDORE
```

The hard drive is unseeable except by root (good) but everything on it is still owned and editable by me (bad).

---

### Post by mcduck on 2011-10-27
What filesystem are you using on that drive? You need to use some Linux filesystem to be able to set permissions for the contents of the dive, windows filesystems like FAT and NTFS lack support for POSIX permissions.

---

### Post by Mega_Fauna on 2011-10-27
> **mcduck said:**
> What filesystem are you using on that drive? You need to use some Linux filesystem to be able to set permissions for the contents of the dive, windows filesystems like FAT and NTFS lack support for POSIX permissions.

Hi, should have put that in. The drive is Ext3.

---

### Post by mcduck on 2011-10-27
Ok. In that case you'll simply need to run a recursive chown on the directory.

```

sudo chown -R root:root /media/ST_ISIDORE
```

(in the commands you ran you only changed the ownership of /media/ST_ISIDORE itself, not it's contents.)

---

### Post by Mega_Fauna on 2011-10-27
Thanks!

And I learnt a bit too:)

---

