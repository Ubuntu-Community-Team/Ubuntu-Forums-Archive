---
title: "[SOLVED] Accessing the network for Picasa"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by TideMan on 2008-10-13
I'm trying to configure Picasa so that it looks at a directory on xcase, a Win XP machine, which I can see here: smb://xcase/My Pictures but I'm having trouble figuring out where that is in terms of a folder.
Actually, I guess my problem is not with Picasa, but with finding smb: so that I can point to it in Picasa.

---

### Post by superzorro on 2008-10-13
Have you tried mounting the shared folder to a specific mount point?

Then you can just point Picasa to look in that specific folder

---

### Post by TideMan on 2008-10-13
> Have you tried mounting the shared folder to a specific mount point?

That sounds good.
Ummmmm.  How do I do that exactly?

---

### Post by superzorro on 2008-10-13
I'm not quite an expert. However, as general rule you can use smbmount

smbmount //server/folder /media/Pictures

This will mount the shared folder of the server to the mount point /media/Pictures/ with this you can go to Picasa and select that folder.

However, it might not be that simple because of file permission and so forth.

For a more complete explanation you can read these threads:

[HOWTO: Mounting SMB/CIFS Shares]("http://ubuntuforums.org/showthread.php?t=280473")

[Mount Network File systems (NFS,Samba) in Ubuntu]("http://www.ubuntugeek.com/mount-network-file-systems-nfssamba-in-ubuntu.html")

Hope this helps

---

### Post by TideMan on 2008-10-13
Thanks to superzorro, I've got this working now.

Here's the relevant command to mount my network directory on xcase:
```
sudo mount -t smbfs -o username=me,password=mine "//xcase/My Pictures" /home/me/Pictures

```
Then in Picasa, Tools/Folder Manager to locate My Pictures and scan it.

---

