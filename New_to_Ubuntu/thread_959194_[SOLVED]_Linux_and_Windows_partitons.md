---
title: "[SOLVED] Linux and Windows partitons"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by Crossyboi on 2008-10-26
Hey guys I need to know the following things!!


I want to switch over to ubuntu from windows,

so basically I need to know how to go about deleting all the windows partitions safely.

also i would like to reinstall ubuntu as i tried to extend the ubuntu partition but it wouldnt let me, there was a lock next to the partition, could someone explain this please?

So all i really need to know is how to practically 'Factory Wipe' my hard drive and reinstall ubuntu :)

---

### Post by drowner on 2008-10-26
Do you want to reinstall, or make your current Ubuntu partition bigger?

Were you using a LiveCD when you were trying to partition? You can't modify a partition that is currently mounted.

---

### Post by Crossyboi on 2008-10-26
> **drowner said:**
> Do you want to reinstall, or make your current Ubuntu partition bigger?

Were you using a LiveCD when you were trying to partition? You can't modify a partition that is currently mounted.


Well i have windows and ubuntu on dual boot, i want to 'delete' windows and just have ubuntu, yes i was using the liveCD, How do i Unmount the partition,

also would i be ok with just deleting the windows partition, or would this affect grub?

---

### Post by drowner on 2008-10-26
> **Crossyboi said:**
> Well i have windows and ubuntu on dual boot, i want to 'delete' windows and just have ubuntu, yes i was using the liveCD, How do i Unmount the partition,

also would i be ok with just deleting the windows partition, or would this affect grub?

Grub will most likely be affected, but you can reinstall grub.

If you want to totally rid yourself of windows, you can get a Live CD (either the ubuntu one, or perhaps a GParted live CD) and then delete all the non-linux partitions (after backing up!!!! very important) and extend the relevant ubuntu partitions.

You will probably have to reinstall grub, or at least edit it's files.

---

### Post by drowner on 2008-10-26
Alternatively, you could back up first, then get a Live ubuntu CD and reinstall, telling it to use the whole disk.

---

### Post by secondstage on 2008-10-26
I'm assuming that you were using Gparted, found at System > Administration > Partition Editor. To edit or format a partition you must unmount it first, the lock was there because you hadn't unmounted it yet. So right-click the specific partition and choose unmount. You should now be able to edit it freely. In your case you probably want to delete the partition, and have the ubuntu partition take that space over. So right-click the windows partition, and [make sure that you backed up and] choose delete. Next right-click , and resize the ubuntu partition so that it takes up the free space. For more information about this, check out [How to Partition]("https://help.ubuntu.com/community/HowtoPartition"). I don't know if the GRUB would remove it self, or if it would stay and only have the ubuntu options.

---

### Post by Swermed on 2008-10-26
Perhaps you need a startup disk:guitar:

---

### Post by drowner on 2008-10-26
> **secondstage said:**
> I'm assuming that you were using Gparted, found at System > Administration > Partition Editor. To edit or format a partition you must unmount it first, the lock was there because you hadn't unmounted it yet. So right-click the specific partition and choose unmount. You should now be able to edit it freely.

If he is not using a Live CD he won't be able to unmount, and hence extend, the partition he is currently working from ;)

---

### Post by Crossyboi on 2008-10-26
> **drowner said:**
> Grub will most likely be affected, but you can reinstall grub.

If you want to totally rid yourself of windows, you can get a Live CD (either the ubuntu one, or perhaps a GParted live CD) and then delete all the non-linux partitions (after backing up!!!! very important) and extend the relevant ubuntu partitions.

You will probably have to reinstall grub, or at least edit it's files.


Ok, could you explain how i would edit the files, and also how to unmount the  partition for ubuntu so i can extend it? thanks

---

### Post by drowner on 2008-10-26
> **Crossyboi said:**
> Ok, could you explain how i would edit the files, and also how to unmount the  partition for ubuntu so i can extend it? thanks



Sure!

We can't tell you how to edit grub's files until the partitioning is done, though.

To unmount the ubuntu partition you will need a Live CD. You could use the Gparted live cd for this, or i think even a normal ubuntu LiveCD. Do you have one?

The reason for this is that all your information, including, for instance the partitioning program reside on your Ubuntu installation - so you cannot unmount it AND run a program on it at the same time. You need to use a Live CD, which runs from the CD, not the hard drive

Have I explained well?

---

### Post by Dedoimedo on 2008-10-26
Hello,

Since my impression is that you do not really feel comfortable with Linux as yet, I would recommend booting from live CD, removing existing partitions and reinstalling (including GRUB).

You can also manually fix GRUB, but the question is: are you up to editing configuration files and running commands in terminal?

If so, you can check my grub tutorial for details.

Dedoimedo

---

### Post by Crossyboi on 2008-10-26
> **drowner said:**
> Sure!

We can't tell you how to edit grub's files until the partitioning is done, though.

To unmount the ubuntu partition you will need a Live CD. You could use the Gparted live cd for this, or i think even a normal ubuntu LiveCD. Do you have one?

The reason for this is that all your information, including, for instance the partitioning program reside on your Ubuntu installation - so you cannot unmount it AND run a program on it at the same time. You need to use a Live CD, which runs from the CD, not the hard drive

Have I explained well?


Yeah you have thankyou, i do have a disc so ill try it now :P wish me luck lol

thanks again!

---

### Post by drowner on 2008-10-26
> **Crossyboi said:**
> Yeah you have thankyou, i do have a disc so ill try it now :P wish me luck lol

thanks again!

BACK UP FIRST!

Always the best advice, ever.

remember: you about to DELETE all your windows data, and potentially compromise your ubuntu data - so spend the time to backup.

---

### Post by Dedoimedo on 2008-10-26
Excellent advice by drowner! Indeed, BACKUP!
Dedoimedo

---

### Post by Crossyboi on 2008-10-26
Thanks to all that helped :)

Ive got it all sorted now, ubuntu installed fine and i deleted all the partitions properly.

just awaiting the updates now :)


thanks again!

---

