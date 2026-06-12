---
title: "Help recovering from reformatted ext3"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by bbukh on 2008-09-28
I had two ext3 partitions on my harddrive. One of them contain Ubuntu file system system with all my data. The other contained junk. I decided to install a newer Ubuntu on the second (junk) partition. I used live-cd, and chose to reformat the partition (it is junk anyways). However, I accidentially I chose the wrong partition, so new ubuntu was installed to the partition containing all the data. The new partition type is also ext3. Since the partition is huge, it is highly unlikely that that the data I need most was overwritten.

Goal: to recover the following files in the order of priority.

1) A TrueCrypt volume in a file
2) Bunch of photographs (in JPEG)
3) Miscellaneous text files

Note that photorec does not detect TrueCrypt volumes (since it looks like noise). Is there hope to recover enough directory structure to recover an arbitrary file like that?

Boris

---

### Post by Pro-reason on 2008-09-28
See [https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem) and  [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery).  Good luck.

---

### Post by bbukh on 2008-09-29
> **Pro-reason said:**
> ...Good luck.

Thanks, I need something more than luck, though.  I used standard carvers to recover jpeg's and text files. However, TrueCrypt volume is a real, real problem. It has no signature whatsoever that a carver can use. The only thing I know is that my passphrase decrypts it. So, I wrote a simple carver that tries to decrypt every 4096 bytes (block size) of the harddrive using my passphrase (for that I had to tweak TrueCrypt source code quite a bit, but the result works). The problem is that trying to decrypt a header is a very slow process. Given the size of my harddrive and the speed of the program my current estimate is about 80-120 days of computer time will be required to find the first block of the encrypted volume (if it is still there).

Question: Is there any way to locate TrueCrypt volume faster. I either need to speed up checking whether passphrase decrypt the block, or to narrow the choice of blocks to check.  It is easy to eliminate blocks taken by text files of executables because the statistical byte distribution is far from uniform, which is quick to check. However, according to my recollection the partition contained a good share of archives and a few video files which look almost like noise.

I tried looking at everything that resembles an inode on the partition, and trying decrypting what inode points to, but with no results.

Any ideas will be appreciated.

Boris

---

