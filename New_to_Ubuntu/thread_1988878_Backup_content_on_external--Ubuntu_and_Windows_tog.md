---
title: "Backup content on external--Ubuntu and Windows together"
date: 2012-05-28
forum: New to Ubuntu
---

### Post by Wheel on 2012-05-28
I've been dual booting for a while now.
I've also been putting backups: images, data backups as well as some individual files onto my external HD.

My external drive is formatted NTFS.  It's just now occurred to me that this might pose a problem or create a possible conflict with my Linux content saved there.
(Although I did successfully restore a Clonezilla image once before.)

I never bothered to partition the external drive; I've just put various content into folders on the external.

I already have GParted on a CD.  I have virtually no experience using GParted other than simply using it to look at the drives/partitions.

Do you think it would be worth my while to format the external and create 2 separate partitions, one as NTFS for Windows stuff and one as EXT for Linux stuff?

Any thoughts would be appreciated.

---

### Post by jtarin on 2012-05-28
Personally I use Fat32 for my external and save NTFS and Ext. without any problems.

---

### Post by mlentink on 2012-05-28
> **jtarin said:**
> Personally I use Fat32 for my external and save NTFS and Ext. without any problems.
For small files, probably.
But not for Clonezilla-images of complete partitions. 

NFTS should be fine for this though, as long as you don't backup individual files and want to retain user priviliges. Those will be lost when stored on NTFS, as it doesn't support linux priviliges.

---

### Post by Wheel on 2012-05-28
> **mlentink said:**
> 
NFTS should be fine for this though, as long as you don't backup individual files and want to retain user priviliges. Those will be lost when stored on NTFS, as it doesn't support linux priviliges.

That's reassuring.   I'm not backing up files that way.

Apart from my images and data backups I  manually copy/paste some simple text files to the external.  (These text files also live on Dropbox, so I have that added layer of protection as well.)

And I copy/paste the occasional picture to the external.   Even these are not "cherished family photos",  just cool pics I find on various web pages.

Thanks.

---

### Post by jtarin on 2012-05-28
> **mlentink said:**
> For small files, probably.
But not for Clonezilla-images of complete partitions
Your 100% correct my friend....I use Partition Manager images instead........on entire partitions copied to FAT32 external HDD......been doing it for years and not one problem from Win,Linux or BSD.:P

---

