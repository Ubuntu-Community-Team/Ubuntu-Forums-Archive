---
title: "[SOLVED] Mounting a NAS in Hardy Server"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by Nxion on 2008-05-02
I have at home a 250GB USB external hard drive that is connected to a Linksys Network storage link ([http://en.wikipedia.org/wiki/NSLU2](http://en.wikipedia.org/wiki/NSLU2)). I put a Linux firmware on it. 

That is connected to my router via ethernet cable.

What I would like to do is mount that in hardy server so I can transfer files from the NAS to the server. 

How would I mount it on the server ?

Any thoughts ?

---

### Post by Golem XIV on 2008-05-02
You could try something like

```
sudo mkdir /mnt/samba
sudo mount -t smbfs -o username=user //server/share /mnt/samba

```

replacing the *user*, *server* and *share* fields with those defined on the NAS.

Also check out this article:

[How to Mount Samba or Windows Shares at Boot Time via /etc/fstab]("http://kim.biyn.com/Linux/how_to_mount_samba_windows_shares_at_boot_time_via_fstab")

Good luck!

---

### Post by Nxion on 2008-05-02
> **Golem XIV said:**
> You could try something like

```
sudo mkdir /mnt/samba
sudo mount -t smbfs -o username=user //server/share /mnt/samba

```replacing the *user*, *server* and *share* fields with those defined on the NAS.

Also check out this article:

[How to Mount Samba or Windows Shares at Boot Time via /etc/fstab]("http://kim.biyn.com/Linux/how_to_mount_samba_windows_shares_at_boot_time_via_fstab")

Good luck!

Thanks for the info, I will try that tonight.

---

### Post by Nxion on 2008-05-04
It worked perfect !! thanks !!

---

### Post by Nxion on 2008-05-07
Can someone make this thread as solved? I can't seem to do it.

---

