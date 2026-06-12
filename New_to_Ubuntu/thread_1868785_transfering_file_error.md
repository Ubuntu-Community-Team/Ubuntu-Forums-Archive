---
title: "transfering file error"
date: 2011-10-24
forum: New to Ubuntu
---

### Post by hookitup on 2011-10-24
Hello folks, after no having issues with ubuntu for a wile now, a slight one appeared so im back here at the friendly forums for some help. 

soooo when i am backing up my files (by backing up i mean, copying them to my other computer with a bigger HD ) i send it over the network. the pc with the original files is my ubuntu 10.04 box, and the "backup pc" is winodws 7, so i have no problem opening the network folding and jumping into my ther pcs harddrive that are for "share". i can transfer any files with no problem unless they are over 3.8 gbs, i get an error , check the picture to see what it looks likes, and yes i hit details and it says "no space left on device", or something like that. but i still have over 400 GBs of space left, makes no sense to me, please help


Thanks

---

### Post by papibe on 2011-10-24
Which file system is the "backup pc"? NTFS or FAT?

If it's FAT, that could be problem since FAT has a file size limit of 4Gb.

Regards.

---

### Post by hookitup on 2011-10-25
its fat 32, cause ntfs wouldnt talk to my ubuntu box. so basically anything under 4gb can be stored on it ? but i can still fill up the 400gb of free space with files under 4gb ?

---

### Post by dFlyer on 2011-10-25
It's the fat file size limit that's causing the error. Either use NTFS or ext4 for your backups of linux.

---

### Post by hookitup on 2011-10-26
thanks for the info folks, i formatted to NTFS and changed some permissions and it seemed to work great and i now can transfer my files that are greater then 4. gbs

---

