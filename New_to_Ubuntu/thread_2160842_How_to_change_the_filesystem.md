---
title: "How to change the filesystem?"
date: 2013-07-08
forum: New to Ubuntu
---

### Post by AADAS on 2013-07-08
I have dual boot : win 7 and ubuntu.The ubuntu have  ntfs file sys.I want to change it to ext4.How to do this?

---

### Post by deadflowr on 2013-07-08
Backup your files you want and reinstall.
Changing filesystems will automatically reformat the partition.

---

### Post by dannyboy79 on 2013-07-08
that's impossible that ubuntu was installed to a NTFS filesystem. Can you type in the following command, it will print out your hard drives and partitions for each drive. We can better understand what you're dealing with
```
sudo fdisk -l
```

---

### Post by slickymaster on 2013-07-08
> **dannyboy79 said:**
> that's impossible that ubuntu was installed to a NTFS filesystem. Can you type in the following command, it will print out your hard drives and partitions for each drive. We can better understand what you're dealing with
```
sudo fdisk -l
```

Exactly. Never heard of it before.

You really should post the output of dannyboy's command.

---

### Post by oldos2er on 2013-07-08
> **dannyboy79 said:**
> that's impossible that ubuntu was installed to a NTFS filesystem. 

It's possible if OP installed using Wubi, but we do need to see *sudo fdisk -l* output.

---

### Post by slickymaster on 2013-07-08
> **oldos2er said:**
> It's possible if OP installed using Wubi, but we do need to see *sudo fdisk -l* output.

Well, I must confess that I've never used Wubi, but I didn't knew that. Thanks for that.

---

### Post by newb85 on 2013-07-08
I'm not experienced with Wubi, either, but from what I've read, it installs Ubuntu on a virtual Ext4 partition within the NTFS position used by Windows. 

Also, I believe there's a designed method for moving a Wubi install to a real partition. A search of the forum will probably bring it up.

---

### Post by slickymaster on 2013-07-08
> **newb85 said:**
> ...

Also, I believe there's a designed method for moving a Wubi install to a real partition...

Here's a few links on that:
[MigrateWubi]("https://help.ubuntu.com/community/MigrateWubi")
[Discussion - https://help.ubuntu.com/community/MigrateWubi]("http://ubuntuforums.org/showthread.php?t=2012400")
[LVPM: Upgrades Wubi installs to dedicated-partition Ubuntu installs]("http://ubuntuforums.org/showthread.php?t=438591")
[Moving a wubi partition to its own]("http://ubuntuforums.org/showthread.php?t=1922931")
[How to convert Wubi install into regular install?]("http://askubuntu.com/questions/635/how-to-convert-wubi-install-into-regular-install")

---

### Post by mastablasta on 2013-07-09
i think you can install to NTFS, only it will be messy and also some things might not work later on due to the way NTFS handles permissions.

---

### Post by dannyboy79 on 2013-07-09
> **mastablasta said:**
> i think you can install to NTFS, only it will be messy and also some things might not work later on due to the way NTFS handles permissions.**please don't post inaccurate information.** **You can NOT install Ubuntu "onto" a NTFS filesystem.** You can install Ubuntu into a virtual disk within Windows which is installed onto a NTFS, which is what Wubi does.

---

### Post by dino99 on 2013-07-09
Wubi should have been never built. Now canonical has finaaly understood its mistake, and have killed that project. So no worry if you had not heard about it before, you miss nothing.

---

### Post by dannyboy79 on 2013-07-09
> **dino99 said:**
> Wubi should have been never built. Now canonical has finaaly understood its mistake, and have killed that project. So no worry if you had not heard about it before, you miss nothing.wubi is good for certain people and certain situtations. i think a lot of the trouble is that people don't really understand what Wubi does and how there Ubuntu is running.

It's funny there are so many responses to the OP but he/she hasn't even been back to clarify what he needs help with. lol

---

