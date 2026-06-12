---
title: "problem with folder permissions"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by Matt26 on 2008-11-20
i have two local NTFS volumes that auto-mount when ubuntu loads (8.10)... the mount points are located in a directory under my home folder- when the volumes are mounted i cannot create shares for any of the sub directories because permissions for the volume's mount point are limited to root, but when i unmount the volumes i have full access to change the permissions- as soon as i mount the volumes again, permissions are again set to only root.  how do i make the permissions i want to set stay permanently?  this worked fine under 8.04.

thanks.

---

### Post by taurus on 2008-11-20
Can you post your /etc/fstab since those two ntfs partitions mount at boot?

```
cat /etc/fstab
```

---

### Post by Matt26 on 2008-11-20
> **taurus said:**
> Can you post your /etc/fstab since those two ntfs partitions mount at boot?

```
cat /etc/fstab
```

here are the entries in my fstab for the NTFS volumes i want to be able create shares under...

[B][I]/dev/sdb6 /home/matthew/NTFS/Stuff ntfs-3g defaults,locale=en_CA.UTF-8 0 0
/dev/sdb5 /home/matthew/NTFS/Downloads ntfs-3g defaults,locale=en_CA.UTF-8 0 0[/I][/B]

my initial post was inaccurate- i have not actually successfully attempted this process under ubuntu 8.04- i was thinking of the shares that i had created under my Home folder.  sorry for any confusion.

---

### Post by Matt26 on 2008-11-20
i got this figured out- i needed to add the following need to my /etc/samba/smb.conf file:

usershare owner only = False

i should have done this to begin with, considering this was mentioned in the error message i received when i first tried to create a share...

---

