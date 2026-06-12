---
title: "Unable to access mount in Nautilus"
date: 2017-02-11
forum: New to Ubuntu
---

### Post by studipity on 2017-02-11
Hi,

I have spent a couple of days on Google searching for a resolution to this, but have not been successful - hence this post.

Sorry if this is a simple one, but it has me stumped.

Essentially, I have followed the instructions at the following URL in order to mount a network share:
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

(Section: **Mounting unprotected (guest) network folders**)

... and the share _has_ mounted successfully in the terminal, but when I try to open it using Nautilus, I get the following error:

> 
[B]Unable to access "shared_videos"
mount: only root can mount //192.168.0.5/public/shared videos on /media/shared_videos
[/B]

The line I have added to /etc/fstab is as follows:
```
//192.168.0.5/public/shared\040videos /media/shared_videos cifs guest,uid=1000,iocharset=utf8,dir_mode=0777,file_mode=0777 0 0
```

The directory listing for /media when the fileshare is mounted is as follows:
```
drwxrwxrwx  2 stuart root    0 Apr 30  2016 shared_videos
```

The directory listing for /media when the fileshare is _not_ mounted is as follows:
```
drwxr-xr-x  2 root root 4096 Feb 11 16:25 shared_videos
```

Hoping someone has a simple trick to fix this?

Thanks,
Stu

---

### Post by TheFu on 2017-02-11
Try installing samba-client, gigilo and gvfs.

[https://askubuntu.com/questions/56428/how-to-automount-a-gvfs-file-system-on-logon](https://askubuntu.com/questions/56428/how-to-automount-a-gvfs-file-system-on-logon) seems related.

---

### Post by sdolen01 on 2017-03-03
I've been fighting this same problem for a few days now.  The same fstab string works fine in Ubuntu 15.04 and 16.04, just not in 16.10.  If you add the users option, then you don't get any error in nautilus, just nothing happens at all.  Aldo there are no eject icons on the mounts in nautilus.

---

