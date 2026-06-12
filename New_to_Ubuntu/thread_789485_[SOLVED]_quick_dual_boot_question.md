---
title: "[SOLVED] quick dual boot question"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by tjwoosta on 2008-05-10
i just got a computer from a friend that came to me with windows xp installed 

its his old computer that he no longer uses (because its too slow)

i am planning to shrink my xp partiton and dual boot with something a little more lightweight (like xubuntu or fluxbuntu or maybe puppy linux)

the problem is that this computer came to me with four partitions 
(no idea what two of em are for)

(this is what i got from the windows XP disk management)

the first partition  is  FAT and says Healthy(EISA configuration)

the second  is NTFS   (this is the C: partition for windoze)

the third   is NTFS (this is the backup for windoze)

then the fourth  is FAT32  and says (unknown partition)

i have done some google searching and found that the FAT (EISA configuration) is probably from when my buddy must have run a system restore to his windows.

i have also asked him about the FAT32 partition and he says he has never messed with partitions at all and never tried another OS (so what is it?)


my main question is can i safely delete all the partitions except for the main C: partition without messing anything up?

i plan to delete all of them (including backup)except for the main windows C:  partition

this will free up 25GB wich i plan to install the new OS to (havnt decided which to use yet)

EDIT: by the way i do not have another copy of the windows xp that is on the computer 
(this is why i am even asking this question)
otherwise i would just completely reinstall

---

### Post by sujoy on 2008-05-10
yes you can, AFAIK windows only uses its root partition (here c drive) to store the OS related files.

---

### Post by tjwoosta on 2008-05-10
in that case what could the unknown FAT32 partition be?

and the EISA partition?  

are they just a pointless wast of space or what?



Edit: i just deleted the partitions (all worked great)

by the way i found out that the unknown partition was the Dell maintenece partition (whatever that is, i deleted it)

thanks for your help

---

### Post by sujoy on 2008-05-11
yes i remember the EISA partition from my friends laptop who had vista preinstalled, manufacturers restore data and such things. good to know things worked. :)

---

### Post by dtrot55 on 2008-05-11
I would take the Hard drive or Hard drives....put them in a different computer and format it or them and then do fresh installs of Xp and Ubuntu...this way you can drop the FAT32 and go NTFS...if you dont want to go that way..get Partition Magic (windows) and format through that to NTFS and then install ubuntu on one of the partitions.

---

### Post by tjwoosta on 2008-05-11
> I would take the Hard drive or Hard drives....put them in a different computer and format it or them and then do fresh installs of Xp and Ubuntu...this way you can drop the FAT32 and go NTFS...if you dont want to go that way..get Partition Magic (windows) and format through that to NTFS and then install ubuntu on one of the partitions.

what? why?  
i just used the gparted thats on the live cd  and deleted both of the FAT partitions (as they were nothing but unnessisary garbage that dell decided to throw on there) then i also deleted the windows recovery partiton (i dont need it) 
then i shrunk the xp partition a little and installed fluxbuntu on all the free space i made (ext3)

by the way fluxbuntu is awesome!

i did all of this from my computer (why would using a different computer help?)

also if you didnt notice above i mentioned that i dont have the XP disc to do a clean install

---

