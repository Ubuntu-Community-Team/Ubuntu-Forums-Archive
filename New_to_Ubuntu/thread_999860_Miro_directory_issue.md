---
title: "Miro directory issue"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by Thelasko on 2008-12-02
I use Miro and have noticed that sometimes it can't find my files.  This is quite frustrating, because once Miro loses files, I can't add them back.  The files are still watchable, but Miro will try to download them again.

I have discovered the root cause.  I store my files on a separate, and larger, hard disk partition.  If I haven't accessed this partition after I boot the machine, Miro can't find it.  If I use Nautilus to navigate to that drive, it works fine.  I suspect that this drive isn't being mounted on boot (although I can see it in Nautilus).

Is there some scripting I can use to make sure this drive is mounted when I start Miro?

---

### Post by taurus on 2008-12-02
There should be an entry in /etc/fstab to mount that drive upon boot.  Do you have any line in there for that drive?

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by Thelasko on 2008-12-03
nope, fstab appears to have just two entries, ext3 and swap.

It's strange how Nautilus displays it though.

P.S. Is this a problem with Miro, or should I setup my machine to mount this drive on boot?

---

### Post by taurus on 2008-12-03
Do you want to mount that large harddrive/partition upon boot?

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
```

---

### Post by Thelasko on 2008-12-04
> **taurus said:**
> Do you want to mount that large harddrive/partition upon boot?

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
```

not really

---

### Post by Paqman on 2008-12-04
> **Thelasko said:**
> not really

It's the only way to solve your Miro problem. You can have it mount to a mount point like /mnt, so it wouldn't even show up on the desktop. It would happen in the background and be completely invisible to you.

---

