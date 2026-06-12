---
title: "adding hard drives"
date: 2016-02-26
forum: New to Ubuntu
---

### Post by Norman_L_Bliss on 2016-02-26
My windows XP computer, “C” hard drive is now running Ubuntu. I have two other hard drives in this computer with XP files and folders. I’m thinking I may have to format the hard drives to make them compatible with Ubuntu. They may have a virus this is why I did a clean install of Ubuntu on the “C” hard drive. How do I remove the virus, save the files and folders and make them compatible with Ubuntu? Thanks for your help.

---

### Post by Bucky Ball on 2016-02-26
If they are NTFS or FAT filesystem partitions, they already are compatible with Ubuntu. 

You can launch Gparted and have a look or open a terminal and run this command:

> sudo blkid

Hit enter then type your password (it will be invisible, this is normal). At then end of each line of output it will let you know what filesystem each partition is.

They have a Windows virus? Completely irrelevant if you are running Ubuntu, or are you wanting to get rid of a virus so you can run these partitions with Windows? That is the stuff of another thread and we don't really deal with how you get rid of Windows viruses on these forums as they don't effect Ubuntu.

If you have an infected Windows you might (probably will) have more luck with that in a Windows forum.

---

### Post by Norman_L_Bliss on 2016-02-26
Thank You

---

