---
title: "Using Windows to TRIM an UBUNTU partiton? is it possible?"
date: 2014-03-07
forum: New to Ubuntu
---

### Post by LinuxVirgin2000 on 2014-03-07
Right I'm really stuck here,

I have been trying for weeks now to find a solution to this problem. I need a shared partition between windows 8.1 and Ubuntu 12.04 on my SSD, 

The problem is that windows will only TRIM NTFS (I tried with FAT32 it dosen't work) and Ubuntu can not TRIM NTFS.

My last option is to use an NTFS partition and just accept that it can not be TRIM'ed by Ubuntu. My question is if I periodically boot into windows and TRIM the partition will this also account for any files that have been deleted while booted into Ubuntu?

If so then that should mean that the SSD performance won't slow down over time as long as I regularly boot into windows and TRIM the partition. Am I correct?

---

### Post by whitesmith on 2014-03-07
TRIM is just a mechanism that allows an OS to tell an SSD which blocks of data are no longer used and thus may safely be wiped. So, yes, Windows could be used as you indicate, since it is aware of all NTFS activity. Of course, this would be a total non-issue if Windows was not a closed, proprietary black box that attempts keeping everything it does a secret, whilst rejecting open-source approaches that Redmond believes no revenue can be derived from (the Ballmer "communist software" non sequitur). You have not told us which Windows programs you use. I would look to these and migrate the bunch to Linux, using Wine or other means as required. Doing so will enable you to use more efficient filesystems (ext4, for example) than NTFS, a c. 1991 borrowing from OS/2's earlier HPFS. Cheers.

---

