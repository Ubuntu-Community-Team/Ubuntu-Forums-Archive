---
title: "browse NFS shares from fresh ubuntu install?"
date: 2012-11-16
forum: New to Ubuntu
---

### Post by evolutionNeedsActiveSync on 2012-11-16
We have a one segment lan with no frills.  The always on media center has some NFS shares, some restricted to certain IP addresses.   It has two samba shares so the windows maachines can put files in a certain applications blackhole directory.

How can one browse NFS shares of another machine?  This would be handy when I do not remember the entire list as can happen when I haven't eaten recently

---

### Post by audiomick on 2012-11-16
Have you looked under "network" in the file manager? You should be able to see them there.

EDIT: Oops, that's not right. I was thinking of Samba shares... #-o

---

### Post by LewisTM on 2012-11-16
Sadly, there is no built-in graphical NFS browser for Ubuntu.
You can install package **nfs-common** and execute this command in a terminal
```
showmount -e  <server address>
```
This will give you a list of shares.
You can then proceed to mount the desired share manually of through an fstab entry.
```
sudo mount -t nfs <server>:/<share> <mount point>
```
Dolphin, the KDE file manager, will let you browse NFS shares provided you know the server address. Hit Ctrl-L and type
[FONT="Courier New"]nfs://<server>[/FONT]
It's a bit clumsy though, it treats an NFS share like an FTP site. A filesystem mount is much more seamless, it's behaves just like a local directory.

Cheers!

---

