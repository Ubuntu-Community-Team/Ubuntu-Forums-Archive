---
title: "Partitioning for Samba with Raid"
date: 2011-11-30
forum: New to Ubuntu
---

### Post by Entropie on 2011-11-30
Folks, I hope that you can help. I have a low end PC that I runs on Ubuntu 11.10 desktop. I now want to add 2 1TB hard drives and set them up as Raid 1 so that I can run Samba to store my files, music and video. All files will need to be access by Ubuntu, Win XP and Mac PCs.
 
This has raised a couple of questions that I hope that the experts can help me with.
 
1) What format do I partition the drives (ext3, NTFS, etc.) as it will need to be accessed by machines running on different OS's. 
 
2) I want the machine to also pull mail from my service provider and allow access to the mail box from all the machines. Will Evolution suffice if I store the mailbox file on the shared disks?

---

### Post by Entropie on 2011-12-06
I have had a trawl through all the documentation and it seems that exFat is the partioning option of choice.  Will I be able to set up the drives as RAID1 and can I install Samba?

---

