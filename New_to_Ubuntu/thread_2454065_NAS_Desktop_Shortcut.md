---
title: "NAS Desktop Shortcut"
date: 2020-11-22
forum: New to Ubuntu
---

### Post by skybird182 on 2020-11-22
I would like to place a shortcut to a NAS drive on my desktop.

I cannot seem to find an answer.

Thanks

---

### Post by TheFu on 2020-11-22
gnome3  doesn't allow this.
Other DEs do. Which do ou run?

Also, "NAS" could, mean nfs or cifs. Which do you use?  NFS looks like a local directory, so a normal _symbolic link_ works.

---

### Post by ActionParsnip on 2020-11-22
Once you mount it, run:
```

mount

```
What is the output please?

---

### Post by skybird182 on 2020-11-22
I am using Xubuntu 20.04.1 LTS using XFCE desktop. The drive is a Buffalo NAS using SAMBA. It is connected properly to my router, but I do not want to drill through the drive tree to access the NAS drive.

How could I use a symbolic link ?

---

### Post by TheFu on 2020-11-22
Sorry, I don't know anything about XFCE and very little about Samba.

But a guess would be that you need to mount the storage using the fstab with a cifs mount (no point-n-click), then use a normal symbolic link (ln -s) to make the link.  I don't know whether symlinks work to Samba mounts. They definitely do work to NFS mounts, but if you can't or won't use NFS, I just don't know. Sorry.

---

### Post by Morbius1 on 2020-11-23
Does this fulfill your use case:

Right click the desktop and select: Create Launcher

Then fill in the blanks. For example I will create one for a subfolder ( Documents ) of a share ( Public ) on a server ( Orion ):
[ATTACH=CONFIG]287432[/ATTACH]

It wasn't clear if you wanted a subfolder of a share or the share itself. If you just want the share then I would just drop the "/documents" part of the path and just specify the share itself ( public ).

---

