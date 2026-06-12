---
title: "UEFI and LEGACY"
date: 2014-07-27
forum: New to Ubuntu
---

### Post by thibault3 on 2014-07-27
Hello community,
I googled but I can't really find an answer there,
I  don't know what the difference is between Legacy and UEFI but i know  Ubuntu 14.04 works in both modes, if installed in one, it works in that  one.
Can anyone help me? 

Thanks!

---

### Post by impliedconsent2 on 2014-07-27
> **thibault3 said:**
> I  don't know what the difference is between Legacy and UEFI but i know  Ubuntu 14.04 works in both modes, if installed in one, it works in that  one.

Legacy is the old BIOS established in the 70's.  UEFI is the latest and greatest popping up around 2010.  The biggest advantage, from what I have found, is secure-boot.  The old BIOS has security vulnerbilities.  Here's a good article to read up on. [UEFI, SecureBoot, and dual booting Windows 8 and Linux]("http://blog.malwarebytes.org/development/2014/05/uefi-secureboot-and-dual-booting-windows-8-and-linux").  

I was skeptical as well, but now I'm using pure UEFI and have not had an issue since 12.04.

---

### Post by whitesmith on 2014-07-27
This is the Wikipedia take: [http://en.wikipedia.org/wiki/Uefi](http://en.wikipedia.org/wiki/Uefi)

---

### Post by thibault3 on 2014-07-27
**impliedconsent2 **thank you for the reply!
My next question is, where is the MBR now, and is it still needed or not?
Or should I ask somewhere else?

Thanks

---

### Post by Bucky Ball on 2014-07-27
One of the major differences is that with legacy you can only have four partitions on any single physical drive. These can be three primary partitions and an extended partition. The extended partition can have as many logical drives (partitions) in there as you like (theoretically, depends on hardware in reality). The extended partition is like a container. This gets around the four partition limitation. Boot manager is at the MBR (master boot record at the beginning of the drive).

With EFI, you can have as many partitions as you like on a single physical drive (caveat as above). With EFI, boot loaders from installed OS's are stored in a small FAT partition.

This is my understanding of it. The partition number limitation is the most important difference for the end-user, IMHO. ;)

---

### Post by oldfred on 2014-07-27
With UEFI you use gpt(GUID) partitioning not the old MBR(msdos) partitioning. With gpt there still is a MBR with one partition entry saying it is gpt, so old partition tools like fdisk do not attempt to reformat it since fdisk does not otherwise see the gpt partitioning.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

      
 [http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

---

### Post by thibault3 on 2014-07-28
Oke, thank you for all the informative replies!
Because of this forum I fell in love with ubuntu even more :)

---

