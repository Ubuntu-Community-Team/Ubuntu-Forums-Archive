---
title: "Partition re-size round-a-bout"
date: 2011-10-04
forum: New to Ubuntu
---

### Post by Vege 4wd on 2011-10-04
Hi all I am on Lucid, trying to resize nfts partitons on an external drive. (1 tig )

First I had to rename them without spaces. One will not be renamed. I get an error about scheduled check and re-boot windows twice.

Problem is I do not have access to a windows box. The drive is old and I can not remember if it was formatted with gparted or under windows.:confused:

Anyway to do this under Ubuntu?
I have tried fsck but I get an error saying nfts not found. Probably because of the space in the volume label no mount point is found.

All help/advice is welcome and appreceiated.

---

### Post by coffeecat on 2011-10-04
The message that includes "an error about scheduled check and re-boot windows twice" means that the NTFS filesystem is damaged and that it needs to be repaired with Windows' chkdsk. You can try with ntfsfix from the terminal, but you are unlikely to achieve anything much. From man ntfsfix:

> ntfsfix  is a utility that fixes some common NTFS problems.  ntfsfix is
       NOT a Linux version of chkdsk.  It only repairs some  fundamental  NTFS
       inconsistencies,  resets  the  NTFS  journal file and schedules an NTFS
       consistency check for the first boot into Windows.

> **Vege 4wd said:**
> I can not remember if it was formatted with gparted or under windows.

Doesn't make any difference. Sorry - there's no way around needing to find a Windows system to fix this. NTFS is a Microsoft filesystem and if you use it, you need Windows for this eventuality.

---

### Post by mikewhatever on 2011-10-04
Fsck doesn't work on ntfs. You could try installing ntfsprogs from the repositories, and then using ntfsfix and ntfslabel (which are included in ntfsprogs).
Labels and mount points are different things, but you shouldn't mount the partition to resize it or fix errors.

---

### Post by Vege 4wd on 2011-10-04
Ok thanks. I will try that. Or ask around for a windows box.

---

