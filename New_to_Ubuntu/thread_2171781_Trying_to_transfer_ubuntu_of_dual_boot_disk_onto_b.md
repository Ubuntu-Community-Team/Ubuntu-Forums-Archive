---
title: "Trying to transfer ubuntu of dual boot disk onto bigger one"
date: 2013-09-01
forum: New to Ubuntu
---

### Post by wesley3 on 2013-09-01
Okay, so I have Ubuntu and Windows 7 on the same hard drive. How would I go about relocating Ubuntu onto another, non Dual Boot drive?

---

### Post by rai_shu2 on 2013-09-01
I just did a drive transplant, myself. I used [clonezilla]("http://clonezilla.org/"). Maybe not the most user-friendly way to do it, but it gets the job done, all right.

---

### Post by wesley3 on 2013-09-01
How would I get rid of the ubuntu left on my Windows drive?

---

### Post by Impavidus on 2013-09-02
I've never done this, but I'd say
- Boot from a live disk and format the new drive in a convenient way.
- Copy everything from the old partitions to the new, using whatever disk or file copy tool you wish. I'd use rsync.
- Modify /etc/fstab on the new drive.
- Disable the old install. Renaming /boot should work. This way grub-install will think it's no longer there.
- Reinstall grub, so that it can find Ubuntu on your new drive and still find your Win7.
- Reboot from the internal drive and test everything.
- If OK, delete the Linux partitions on the old drive and use Windows tools to expand the Win partitions into the new space, or do whatever else you want to do with that disk space.
- If not OK, try Boot-Repair to reinstall grub and/or restore your old installation by restoring the /boot directory on the old drive.

---

### Post by rai_shu2 on 2013-09-02
> **wesley3 said:**
> How would I get rid of the ubuntu left on my Windows drive?

Unless you want to reinstall Windows, I suppose the best way would be to reformat the partition you had Ubuntu on (after you've moved it, of course).

---

