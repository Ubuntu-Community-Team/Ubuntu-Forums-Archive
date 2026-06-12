---
title: "Internal drives' owner is root"
date: 2014-09-30
forum: New to Ubuntu
---

### Post by HeroCC on 2014-09-30
Hello! This is my first post here, so be nice.

[s]I have an **internal SATA** SSD that I recently** formated to ext4** (for ubuntu filesystem permissions) and now that it formatted, it's **owner is root** and I cant change it. It was NTFS before I formatted it. I used GParted to format it.[/s] Nevermind! Fixed

Also, before it was formatted, it was in /media/name/SSD, I thought that was only for external drives, but I may be wrong. Anyway, it is in /media/name/ssd now, and I can't r/w to it. I wolud like it to be in the proper /mnt/ directory.  

Any help is appreciated!

---

### Post by HeroCC on 2014-09-30
Sorry! I found it! I forgot the -R tag in chown, silly me. I wilud still appreciate help with the incorrect mounting location though, thanks!

---

### Post by Bashing-om on 2014-09-30
HeroCC; Hi ! Welcome to the forum .

Depending on the usage of this now "internal" hard drive, it is generally "auto mounted" at startup from the " /etc/fstab " file.
Have a read:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131) <-bodhi.zazen-Understanding fstab

If this meets your needs and you want additional assistance, we will continue this discussion.

Else; we find some other means to meet your desires.

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]more than any 1 path to an end
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by HeroCC on 2014-10-02
> **Bashing-om said:**
> HeroCC; Hi ! Welcome to the forum .

Depending on the usage of this now "internal" hard drive, it is generally "auto mounted" at startup from the " /etc/fstab " file.
Have a read:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131) <-bodhi.zazen-Understanding fstab

If this meets your needs and you want additional assistance, we will continue this discussion.

Else; we find some other means to meet your desires.
[INDENT][INDENT]'buntu[INDENT][INDENT][INDENT]more than any 1 path to an end
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Thanks for the link Bashing, and it is auto mounted. My question is if there is a way to Disable UnMounting (as it is an internal drive, and I want to be safe from mistakes as it is written to a lot). The way I understand it is that if it is in /media/ than it can be unmounted, and if I wanted to I could unmount it, but I want to prevent that, and have it be a perminate drive. Thanks for the help!

---

### Post by Bashing-om on 2014-10-02
HeroCC; Humm ..

Not real sure about what results if mounted from /media.

I am very particular about my data and backup partition and drive.
I do mount them as needed as "on demand" from terminal.
My backup drive is 'sdb' and I have made my mount point in '/mnt':
```

sudo mkdir /mnt/backup

```

Now when I need/want access to this hard drive;
Terminal command:
```

sudo mount /dev/sdb1 /mnt/backup

```
for instance, gives me access to that 1st partition on drive 'sdb'

Now, when one mounts a file system ('sdb') manually in this manner, it is on you to (UN-)mount it when done !
```

sudo umount /mnt/backup

```
Failure to do so will result in file system corruption at some level; any pending operations ( flushing the cache to disk, say) are then completed and it is safe to reboot/turn the system off.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by Impavidus on 2014-10-03
If it's mounted in /media and you can simply unmount it with a few clicks, it's automounted by your file manager when you click on the partition. The file manager always mounts things in /media. Automounting something at boot time is something different. It's done via the /etc/fstab file. You can have the partition mounted wherever you want (some choices are wiser than others) and set some options, like whether you want it to mount automatically at boot or not and whether any user is allowed to mount and unmount it. For example, you could say that only root can mount and unmount the partition and that it has to be mounted at boot time. In this case the partition will always be mounted, unless you use root permissions to unmount it. This seems to be what you want.

Bashing-om just described how to manually mount and unmount some partition.

---

