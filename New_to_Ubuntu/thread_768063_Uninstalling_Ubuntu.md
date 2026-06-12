---
title: "Uninstalling Ubuntu ?"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by JULEZAH on 2008-04-26
So basically My Ubuntu install has gone all wrong.
Being fairly noob at all this, i tried to install Ubuntu again, just off the CD.
Dunno if that was a really, really stupid thing to do, or not :S

I've got XP Pro on my C Drive (Or Partition 1 or whatever)
And i want to rid Ubuntu of my D Drive (Partition 6 i think)

Also, GRUB had a heart attack, so i had to use SuperGRUB to boot up either Ubuntu or XP again; both work fine.

Will booting XP and then clicking format D: have any negative effects?
(On the first install, i gave XP like 3 gb, and then i installed again and gave it about 20gb)

HELP!?!

---

### Post by tamoneya on 2008-04-26
your D drive does ultimately need to be removed. Removing it through windows as opposed to linux doesnt matter. Either way is fine.  Be aware that you will cause grub to throw some more errors because it will not be able to find the partition that you just deleted.  At this point you will have two options. A) use super grub again and fix your boot loader. B) Use the windows XP install disk and use the command prompt repair mode to run```
fixmbr
``` This will overwrite grub with the windows bootloader and will erase all memory of linux on you computer.  The best option of these two is the second one but not everyone has a xp install CD since some computer manufactures do not supply them with the computer.

---

### Post by Riffer on 2008-04-26
No, reformatting won't change your boot problems.  Grub does write to your MBR and that needs to be fixed.  If memory serves you need to use "fdisk" and I THINK the command is 

fdisk /mbr

edit:  I didn't know the "fixmbr" way cool.

---

### Post by c4v3m4n on 2008-04-26
Every time i've reinstalled new linux I have just installed over my old one and didn't have any problems.  Sounds weird.

---

### Post by HunterThomson on 2008-04-26
What is wrong exactly? What do you want to do??? If you want to get rid of Ubuntu all together, this is how you do it...

Pop in ubuntu live cd....

use gparted to format the partition that ubuntu is on... format it to a NTFS partition.

Then add that NTFS partition to the windows partition...

Then you will need to run the super grub CD in order to get window$ XP in to boot again.

---

### Post by JULEZAH on 2008-04-26
mm

what i meant was, will reformatting the d drive cause me to lose everything that was partitioned for Ubuntu ?

So, should i just right-click the d drive, go format and then fix my bootloader ?

I don't want to screw anything else up :S

---

### Post by warbread on 2008-04-26
If you format your Ubuntu partition, you will lose your data.

---

### Post by c4v3m4n on 2008-04-26
If you format you will lose everything, so back up important stuff before you format.

---

### Post by JULEZAH on 2008-04-26
That's cool, i've got nothing on there anyway :D

I am worried about just losing the space that was given to ubuntu.
As i can't access it through windows.

Can you assure me that if i click on format, i will be able to access the full 80gb ?

---

### Post by HunterThomson on 2008-04-26
The next time you install set it up in the manual partitioner like this

100MB     label /boot                              format ext2
2000MB    label /swap
10000MB   label  /    this is the root partition   format ext3
the rest of the space label /home                  format ext3

This way you will not lose any data net time you reinstall

---

### Post by c4v3m4n on 2008-04-26
Lol well that makes it easier.  You can format it back to be part of your windows partition.  Format it to NTFS and just add it to your windows.

---

### Post by JULEZAH on 2008-04-26
What?

I still don't get it.
Do i format the drive via XP Pro, or Ubuntu?

Dunno what to do in ubuntu... :S

---

### Post by HunterThomson on 2008-04-26
In the manual partitioner (when you are installing ubuntu from the live CD just click the manual partition option) you just highlight the ubuntu partition and click remove partition. You mite also want to make a FAT32 partition to swap files to you window$ OS.

---

### Post by c4v3m4n on 2008-04-26
You can do it in Ubuntu.  Run "sudo gparted" and unmount then format the partition.

---

### Post by tamoneya on 2008-04-26
it doesnt matter whether you format from linux or windows.  What I recommend doing personally is putting in the ubuntu liveCD and running ```
sudo gparted
```This will load a graphic partition manager.  In this you should delete all of your linux partitions.  Then instead of making a new NTFS partition you should resize your old one.  Make the NTFS partition larger.  Then you will have one large NTFS partition spanning the entire disk instead of two smaller ones.  Then boot into recovery console on the windows XP install disk and replace grub with ```
fixmbr
```

---

### Post by JULEZAH on 2008-04-26
If i put in the LiveCD, where do i put in the command to run ?

---

### Post by tamoneya on 2008-04-26
applications -> accessories -> terminal

---

### Post by JULEZAH on 2008-04-26
AHA!

now i feel like a real idiot...

mmk let's see here....

---

### Post by sandysandy on 2008-04-26
some links

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

regards

---

### Post by JULEZAH on 2008-04-26
YAYAYAY!
IT WORKED!

omg thanks sooo much :D:D:D

i deleted all the linux partitions and then resized the little 3gb partition to fill up the whole D drive :)


WOOHOOO

I'll be back sometime, to try ubuntu once again :D

---

### Post by tamoneya on 2008-04-26
We all hope you come back soon.  We'll be here to help you out when you do.

---

