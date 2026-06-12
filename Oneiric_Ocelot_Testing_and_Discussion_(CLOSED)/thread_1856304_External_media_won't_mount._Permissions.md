---
title: "External media won't mount. Permissions?"
date: 2011-10-08
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by rscow on 2011-10-08
I'm running the beta of Oneiric and have come up against a problem with mounting external media.  Can't mount an iPhone, or a USB stick, or external drive.  The internal drive shows up, and so does the second drive I installed in the DVD drive's place. 

A window pops up and says only root can mount stuff.  I'm the only user, but only have the normal owner privileges.  It is attached.

I also can't rename files on the drive.

Didn't have this problem in 11.04.

How do I fix this?

Roger

---

### Post by OpSecShellshock on 2011-10-08
Is your user account in the plugdev group? In prior releases that's been something to check. Not sure why it would have spontaneously changed if you had been before, though.

---

### Post by rscow on 2011-10-10
I am not familiar with the plugdev group. Just the usual ones you see when you change permissions. 

Maybe I should do chown on the partitions. Can one even do that?

---

### Post by cariboo on 2011-10-10
I had the same problem early on it the development cycle. Updates have solved the problem. Make sure you are using the Main Mirror, and you are totally up-to-date.

---

### Post by rscow on 2011-10-11
I do have the standard sources.list. I am updating daily.  I will see what happens on 13th.

---

### Post by rscow on 2011-10-11
I did some reading, and yes my user account is admin and I am part of the plugdev group.  This is frustrating.  I can create and delete files, but can't change names, etc., in the GUI.  I haven't tried to use su in the command line...but shouldn't have to.

---

### Post by cariboo on 2011-10-11
How is your external drive formatted? If it's HPFS/NTFS/exFAT, you may be missing a needed package.

---

### Post by rscow on 2011-10-11
Tried three different ones:  one HFS, other two FAT.

Some buzz about this being a "widespread" bug in lightdm.

I'm not sure how to upgrade to an upstream version of lightdm.

Maybe patience better than mucking around too much.

---

### Post by mc4man on 2011-10-11
Maybe try creating a new 'standard' user, login to it & try one of your flash drives (FAT), no need for admin permissions

Have only seen an issue with mounting external media for a very short time - images from 09/27 > 10/04 but it was a sporadic thing & more than just not being able to (auto) mount ext. media was involved.

(you can install gdm, switch to it & see, or try a new install with the current image

---

