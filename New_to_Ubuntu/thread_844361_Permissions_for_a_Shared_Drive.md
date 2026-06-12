---
title: "Permissions for a Shared Drive"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by fballem on 2008-06-29
I'm really close, but I'm not quite there yet on Shared Drives, so a little specific advise would be most helpful.

The problem is that I have a share, called mediashare, on an NAS. I have the following line in /etc/fstab:

```
//192.168.2.52/media /media/Media-NAS cifs user=[NASUser],password=[NASPassword],rw,iocharset=utf8,gid=users,user 0 0
```

[NASUser] and [NASPassword] are for a user on the share, and are correct in the real file.

The device mounts, and a logged in user on my computer can see the drive. The problem is that I want a logged in user to be able to Create and Delete folders and be able to read and write files.

When, as a logged in user, I try to create a new folder using Nautilus, the option to do so is not enabled.

I have a feeling that there is problem with the line in /etc/fstab, but if someone could provide me with a checklist, then I'll happily go through it.

I've been at it for a while and I'm frustrated.

Thanks,

---

### Post by stoneybroke on 2008-06-30
In Ubuntu-7.10 there was a folder called shared drives its not available in Ubuntu 8.04 what you need to do is go to File-System/usr/bin and double click on Shares-Admin and it will work. Just set the permissions you want and it should all work.

Hope that helps

---

