---
title: "Quick permissions question"
date: 2011-11-29
forum: New to Ubuntu
---

### Post by James.A.Parnell on 2011-11-29
I have just swapped out my girlfriends computer and added another hdd ( aptly named HDD#2)..however its been a while since i even uttered the word "Ubuntu" so i cant for the life of me remember how to change the permissions of said HDD from root so she can use this addition.

If it helps:

Path: /dev/sdb2
UUID: 886d07c3-32e7-47d0-ad68-c44746b9a5c0
Mount Point: Mounted on /media/HDD #2

---

### Post by Paqman on 2011-11-29
To make the whole drive owned by a single user:

```
sudo chown -R username:username /media/HDD\ #2 
```

You can do this in Nautilus by launching it as root. Hit Alt-F2 and:
```
gksudo nautilus
```
the navigate to the folder, right click > permissions and change the owner to whoever you want and check the "apply to files/folders within" (or words to that effect).

---

### Post by mcduck on 2011-11-29
Is the drive configured in /etc/fstab, or are you just using the desktop environment's automounting abilities? And what file system are you using on the drive?

Assumming it's formatted with a Linux filesystem, simply changing the ownership of the mount point should do the trick:
```
sudo chown username:username "/media/HDD #2"
```

For Windows filesystems you'll need to configure the drive in fstab and use the *uid* and *gid* options to set the drive's ownership to the desired user ID.

---

### Post by Bodsda on 2011-11-29
No point in explicitly changing ownership on every file... 

Use fstab to mount the volume and set the permissions

so the line may look like
```

/dev/sdb2 /media/hdd2 ext3 auto,users,rw

```

[Useful reading]("http://blog.bodhizazen.net/img/Understandingfstab.pdf")

---

### Post by James.A.Parnell on 2011-11-29
Thanks much :). first tip worked instantly. :)

---

