---
title: "[SOLVED] Getting rid of ubuntu"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by mr-Kirch on 2008-08-12
im just having too many problems right now so im getting rid of it. will a vista recovery disk work by just overwriting ubuntu? im going to get ubuntu again when im done with my high school programming classes (im going to be a freshman in september)

---

### Post by SunnyRabbiera on 2008-08-12
Can you list your issues?
Also perhaps ubuntu isnt the distro for you, maybe trying out another one is a good idea as linux is filled with options.

---

### Post by hyper_ch on 2008-08-12
how did you install ubuntu?

---

### Post by kpkeerthi on 2008-08-12
> **mr-Kirch said:**
> im just having too many problems right now so im getting rid of it. will a vista recovery disk work by just overwriting ubuntu? im going to get ubuntu again when im done with my high school programming classes (im going to be a freshman in september)

[http://users.bigpond.net.au/hermanzone/p18.htm](http://users.bigpond.net.au/hermanzone/p18.htm)

---

### Post by mr-Kirch on 2008-08-12
> **hyper_ch said:**
> how did you install ubuntu?

when it was installing i just chose "choose partion with most extra space" or something

---

### Post by SunnyRabbiera on 2008-08-12
> **mr-Kirch said:**
> when it was installing i just chose "choose partion with most extra space" or something

so you used the live CD then and not wubi.
We just asked as wubi causes issues as its still new.

---

### Post by mr-Kirch on 2008-08-12
K so will using the vista recovery overwrite ubuntu?

---

### Post by hyper_ch on 2008-08-12
well, then

(1) boot from your windows cd
(2) start the windows installation until the point where you can select to enter the recovery console
(3) in the recovery console run
```

fixmbr

```
(maybe do some research first whether this is sufficient)
(4) then you should have the windows boot loader again... start windows to see if it works
(5) if everything is file, get a windows partitioning tool or run gparted from the ubuntu dekstop cd and (a) delete the existing linux partitions [swap/ext3] and (b) enlarge the windows one or make another ntfs partition.

---

### Post by Gone fishing on 2008-08-12
You need to delete the Linux partitions I think its done like so in Vista:

   1. Click on the Start Button and right click on Computer and select Manage.
   2. Expand the Storage section and select Disk Management.
   3. The delete the Linux partitions (be careful you can do real damage here)

Sorry if that sound a bit vague but I'm more used to XP

I think you can also expand the NTFS partitions or just create an new partition Windows partition. 

You will then need to Remove Grub like so:

Boot on the Vista install cd click repair your computer then at the command prompt and use the BootRec.exe /fixmbr command (apparently it replaces the fixmbr command in XP).

However, I think it more than worth keeping Ubuntu and with a little effort you will find it better than Vista - which I find just vile.

---

### Post by sandysandy on 2008-08-12
you can also try supergrub disk.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

regards

---

### Post by mr-Kirch on 2008-08-12
im in my disk management and im pretty sure i should just delete all the partions except for my c: and my recovery is that right?
because the other partions (there are two) one of them says 268.70 gigs and thats how much i gave to ubuntu and the other one says 8.33 gigs but i dont know what that one is. and should i delete the grub first or the ubuntu partions?

---

### Post by PCessna on 2008-08-12
> **mr-Kirch said:**
> im just having too many problems right now so im getting rid of it. will a vista recovery disk work by just overwriting ubuntu? im going to get ubuntu again when im done with my high school programming classes (im going to be a freshman in september)

Comon man, Try some other members of the Ubuntu family, Maybe KDE or XFCE, maybe some other Linux distros might float your boat, and with a little compiz action, who can resist it over Vista?

---

### Post by mlentink on 2008-08-12
Have you done the fixmbr thingy? If so, GRUB will already be gone, and you can delete the ext3 and swap partitions. 
If not, you will be able to delete them, but you will still need to fix your mbr.

---

### Post by bumanie on 2008-08-12
A recovery disk won't necessarily overwrite the ubuntu partitions. I believe if a recovery partition is activated, that will do it. Easiest thing to do as you have a recovery disk, is to re-write vista's bootloader and then use vista's partitioner to expand the partition over the ubuntu installation.

---

### Post by mr-Kirch on 2008-08-12
> **mlentink said:**
> Have you done the fixmbr thingy? If so, GRUB will already be gone, and you can delete the ext3 and swap partitions. 
If not, you will be able to delete them, but you will still need to fix your mbr.

so i should do the recovery disk, go to command prompt and put in fixmbr THEN delete ubuntu partions? if so i will have to wait till my dad gets home with a new vista recovery disk

---

### Post by dark_harmonics on 2008-08-12
I congratulate those who didn't try to reconvert this user.

 The partitions you are seeing are most likely ubuntu and its swap partition. You should really be very careful before doing any partition destroying actions though. 

From vista's winpe 2.0 i know you can use diskpart to wipe the disk and set another partition as active. Not sure if fixmbr still works but that was an excellent suggestion. Also using gparted from the live CD could help you with resizing as previously suggested (smart people on this forum :P )

Good luck!

---

### Post by mr-Kirch on 2008-08-12
> **dark_harmonics said:**
> I congratulate those who didn't try to reconvert this user.

 The partitions you are seeing are most likely ubuntu and its swap partition. You should really be very careful before doing any partition destroying actions though. 

From vista's winpe 2.0 i know you can use diskpart to wipe the disk and set another partition as active. Not sure if fixmbr still works but that was an excellent suggestion. Also using gparted from the live CD could help you with resizing as previously suggested (smart people on this forum :P )

Good luck!


well i know for sure that my 268 gig partion is ubuntu and my 86 gig partion is windows. not sure what my 8 gig partion is though so i just wont mess with that one

---

### Post by sandysandy on 2008-08-12
> **mr-Kirch said:**
> and should i delete the grub first or the ubuntu partions?

first get ur vista to boot independently of GRUB. then only delete partitions.

look here

[http://users.bigpond.net.au/hermanzone/p18.htm](http://users.bigpond.net.au/hermanzone/p18.htm)

regards

---

### Post by mr-Kirch on 2008-08-12
> **sandysandy said:**
> first get ur vista to boot independently of GRUB. then only delete partitions.

look here

[http://users.bigpond.net.au/hermanzone/p18.htm](http://users.bigpond.net.au/hermanzone/p18.htm)

regards

so use vista recovery disk and go to command prompt and type in fixmbr then delete ubuntu partions right?

---

### Post by mlentink on 2008-08-12
That would be my way of going at it, so yes. 
Do you see more info on that 8GB partition? It seems much to big to be a linux swap partition, so it might be a recovery partition of some sort. I would not delete it until I was absolutely certain what is was.

---

### Post by sandysandy on 2008-08-12
do u have easyBCD

see this thread also

[http://ubuntuforums.org/showpost.php?p=2668386&postcount=14](http://ubuntuforums.org/showpost.php?p=2668386&postcount=14)

regards

---

### Post by bumanie on 2008-08-12
> Not sure if fixmbr still works but that was an excellent suggestion. Also using gparted from the live CD could help you with resizing as previously suggested (smart people on this forum :P ) No, fixmbr does not work the same in vista as under xp. The vista recovery disk, basically searches for issues itself (unless the user directs an action via radio buttons) - it automatically finds the problem and fixes it. As for gparted (unless something has changed recently) it has been often advised that the vista partitioner is the preferred tool to partition vista with, although gparted works well on xp, vista, at times has had issues. Vista's partitioner can expand as well as shrink.

---

### Post by mr-Kirch on 2008-08-12
> **mlentink said:**
> That would be my way of going at it, so yes. 
Do you see more info on that 8GB partition? It seems much to big to be a linux swap partition, so it might be a recovery partition of some sort. I would not delete it until I was absolutely certain what is was.

its not recovery because my recovery partion says recovery

---

### Post by sandysandy on 2008-08-12
> **mr-Kirch said:**
> the other one says 8.33 gigs 

> **mr-Kirch said:**
> its not recovery because my recovery partion says recovery
 

post output of sudo fdisk -lu 

regards

---

### Post by mr-Kirch on 2008-08-12
> **bumanie said:**
> No, fixmbr does not work the same in vista as under xp. The vista recovery disk, basically searches for issues itself (unless the user directs an action via radio buttons) - it automatically finds the problem and fixes it. As for gparted (unless something has changed recently) it has been often advised that the vista partitioner is the preferred tool to partition vista with, although gparted works well on xp, vista, at times has had issues. Vista's partitioner can expand as well as shrink.

well what should i use instead of fixmbr then? will the recovery disk delete GRUB automatically?

---

### Post by mr-Kirch on 2008-08-12
> **sandysandy said:**
> do u have easyBCD

see this thread also

[http://ubuntuforums.org/showpost.php?p=2668386&postcount=14](http://ubuntuforums.org/showpost.php?p=2668386&postcount=14)

regards

thats what i used. thank you so much. now my grub is gone and all i have to do is delete partions

---

### Post by mr-Kirch on 2008-08-12
well guys i deleted my GRUB and i deleted my ubuntu partion

so how do i add back to my NTFS partion because when i deleted ubuntu that partion just says 268 gigs of free space and if i write click my NTFS partion there is: open, explore, change drive letter and paths, shrink volume, properties, and help options what one should i use?

---

### Post by aomlives on 2008-08-12
> **mr-Kirch said:**
> so how do i add back to my NTFS partion because when i deleted ubuntu that partion just says 268 gigs of free space and if i write click my NTFS partion there is: open, explore, change drive letter and paths, shrink volume, properties, and help options what one should i use?

I think this is what you want to do while under Vista:

[http://www.bleepingcomputer.com/tutorials/tutorial133.html#extend](http://www.bleepingcomputer.com/tutorials/tutorial133.html#extend)

Edit: Oops, this was already answered in another thread of yours, hope the solutions there worked.

---

### Post by mlentink on 2008-08-12
@mr-kirch:
Would you mind marking this thread [solved]? As you see, people come back with solutions which you no longer need, while they could be helping others.
Thanks.

---

### Post by hovzio on 2008-08-12
Please ignore: posted in wrong thread sorry:(

---

