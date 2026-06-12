---
title: "External HDD problems"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by Crafty Kisses on 2008-09-28
So I just bought a brand new external HDD, a Maxtor OneTouch 4 Mini to be exact, and I formatted it ext3 via gparted, now everytime I drag files into the HDD i get this error "The folder "Emerald Themes" cannot be copied because you do not have permissions to create it in the destination."

Any ideas. :(

---

### Post by howefield on 2008-09-28
<alt>+F2

gksudo nautilus

Locate /media and right click the folder representing the partition you want to change permissions for.

Select Properties and click on the permissions tab 

Change permissions for "Other" as required, all I did was change folder access option to Create and Delete files, then press Apply Permissions to Enclosed Files.

---

### Post by Crafty Kisses on 2008-09-28
That's weird it lets me write obviously only as root, I'd ran a fsck -a on the drive and I didn't get anything back, I guess I can format it as an NTFS.

---

### Post by PurposeOfReason on 2008-09-28
Have you tried to chmod and chown -R the directory?

---

### Post by Crafty Kisses on 2008-09-28
Yep, I've almost tried every solution, still won't let me mount, I've also edited my fstab, and I did it correctly, it still didn't want to mount.

---

