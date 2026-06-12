---
title: "Deja-dup can't write to external drive"
date: 2011-10-02
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sgage on 2011-10-02
I'm experimenting with deja-dup, and set up a simple backup from my home directory to my external HD. The backup fails with"

Error creating directory: Permission denied

I have no issues with this drive using any other software. I can copy files, delete files, make directories, etc.

Any idea what's up?

---

### Post by mc4man on 2011-10-02
Just tried here - backup to external ntfs drive, worked ok for backup & restore.
Though I did create a backup folder _1st._ on the external & then specify it in the deja-dups settings

---

### Post by sgage on 2011-10-02
> **mc4man said:**
> Just tried here - backup to external ntfs drive, worked ok for backup & restore.
Though I did create a backup folder _1st._ on the external & then specify it in the deja-dups settings

I tried that first thing - no joy.

Very odd - everything else works fine. It is an ntfs driver. Perhaps you could tell me what options you used in mounting yours?

---

### Post by mc4man on 2011-10-02
Just whatever provided when plugging the drive in & having it automounted, I gather by 'gnome-fallback-mount-helper'

As seen in mtab
> /dev/sdb1 /media/WD1 fuseblk rw,nosuid,nodev,allow_other,blksize=4096,default_permissions 0 0

---

### Post by sgage on 2011-10-02
> **mc4man said:**
> Just whatever provided when plugging the drive in & having it automounted, I gather by 'gnome-fallback-mount-helper'

As seen in mtab

Exactly the same here, and still no go. How odd!

I'll keep fiddling...

---

### Post by sgage on 2011-10-02
I figured it out. In telling it where to store the backup, I preceded the folder name with a / (just like you do in grsync). Deja-dup doesn't like that. :KS

---

### Post by mc4man on 2011-10-02
At least here I'm finding a number of seemingly random, (don't think anything is truly 'random') & inconsistent misbehaviors. This is on a newish 09/29 install

I think I might switch to gdm for a day & see if there is any change(s), better or worse.

edit: - see you got this one...

---

