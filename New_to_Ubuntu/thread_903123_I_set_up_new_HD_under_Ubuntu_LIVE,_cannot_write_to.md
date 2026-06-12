---
title: "I set up new HD under Ubuntu LIVE, cannot write to it."
date: 2008-08-28
forum: New to Ubuntu
---

### Post by egalvan on 2008-08-28
I installed a new 750g HD, then booted a LiveCD (PartedMagic) and set it up as 'ext3'.

Now booting the same machine with a Hardy 8.04 LiveCD, I cannot write to the new drive.
(either new documents, or copying/moving files)

I'm very hazy with the 'permissions' commands.

ErnestG

n.b. this is a WinXP machine, with three hard drives.
 I want to use *nix tools to set up the second and third drives as ext3, to use as storage. (and as a learning experience)
Then I want to move files off the WinXP drive to the storage for safe-keeping.
And lastly, erase and shrink the XP partition from it's original 250GB to 20GB,
 reload WinXP, then load Hardy 8.04.1.

Thanks.

ErnestG

:popcorn:

---

### Post by Crafty Kisses on 2008-08-28
Can I see your /etc/fstab?

---

### Post by egalvan on 2008-08-28
> **Codename said:**
> Can I see your /etc/fstab?


Remember, I'm in a LiveCD environment at the moment.

```
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
```


ErnestG

:popcorn:

---

### Post by egalvan on 2008-08-28
OK, running 


```
gksudo nautilus
```


lets me move the files.

But I really want to learn how to set the permissions correctly.

ErnestG

:popcorn:

---

### Post by egalvan on 2008-09-06
bump

---

