---
title: "dual boot problem, menu.lnk ready for your signal"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by morrillt on 2008-06-19
grubs did not detect my Windows....



fdisk -l prints

/dev/hda5 has an ntfs partition... so i guess thats the baby...

Have menu.lnk up from /boot/grub

Have tried 
title Win
rootnoverify (hd0,0) and seperately (hd0,1) (hd0,2) (hd0.5)
makeactive
chainloader +1

what am i missing?

---

### Post by Dynaflow on 2008-06-19
Have you tried just ```
root    (hd0,5)
``` rather than rootnoverify?

Can you post the output of your fdisk -l, and attach a copy of your /boot/grub/menu.lst ?

---

### Post by meierfra. on 2008-06-19
Did you delete any partitions while installing Ubuntu?

---

### Post by morrillt on 2008-06-19
tried the root (hd0, 5) no work.

am writing from a different comp so copying is a bit tedious.... 

will post it tomorrow if i dont get an answer.

---

### Post by Dynaflow on 2008-06-19
It's odd that Windows would be residing on the fifth partition.  

I take it this isn't the original, pre-installed OS we're looking for?  Specifically, did you install Windows *after* whatever else you've got on that drive?

---

### Post by kansasnoob on 2008-06-19
Generally hda (or sda) 5 (if that's the proper location of your OS) would be 0.4 in GRUB, but that's not always true.

Like I have a multi-boot where OS's have been removed and replaced and I'm into the triple digits.

Sometimes a separate GRUB partition is the best thing.

---

### Post by meierfra. on 2008-06-19
> It's odd that Windows would be residing on the fifth partition. 

That's why I asked whether the OP deleted any partitions. Windows always puts the booting information  on a primary partition (one of the first four) So I'm worried that the OP deleted the partition containing the boot information.  


morrillt:  "menu.lst" is not that important. Just post "sudo fdisk -l" for now.

---

### Post by morrillt on 2008-06-20
Device Boot      Start         End      Blocks   Id  System
/dev/hda2   *           1        9732    78172258+   f  W95 Ext'd (LBA)
/dev/hda5             638        9732    73055556    7  HPFS/NTFS
/dev/hda6               1         584     4690885+  83  Linux
/dev/hda7             585         637      425691   82  Linux swap / Solaris


So the thing is i have an hp, and when windows was installing i made two partions, a 5 gig and a 75gig, i made a 5gig for the dvd only boot up os, which i could subsequently never get working. Windows was installed on d: and d: was used for booting.
So i was thinking why not put ubuntu on that 5gig partition. so i installed ubuntu on it, but alas... as i was doing it it said swap partition needed so i deleted the 5 gig partition and made it into 2 partitions... one 500meg one, and one 4500 meg one....

Also when i was installing ubuntu i mounted my windows partition as /windows which i can browse and see currently..... hope i can get windows back

:)

---

### Post by meierfra. on 2008-06-20
> hope i can get windows back

Follow these instruction and there is a good chance that you get Windows back:

[B]Step 1) Mount your windows partition in Linux
[/B]
```
sudo mkdir /windows   (although you probably already have the folder)
sudo mount /dev/hda5 /windows
ls  /windows

```
The last command list all the files in the System directory of your Windows Partition. If the files "boot.ini", "NTLDR" and "NTDETECT.COM" are on this list you can  skip Step 2.


[B]Step 2) Get the boot files and extract them to your Windows partition
[/B]

Download this file: [http://ubuntuforums.org/attachment.php?attachmentid=73056&d=1212690573](http://ubuntuforums.org/attachment.php?attachmentid=73056&d=1212690573)
and save it to your  home folder (/home/your_username/) Then

```
cd /windows
tar -xvzf /home/your_username/Archive.tar.gz
ls  /windows
```

Make sure you now have the files "boot.ini", "NTLDR" and "NTDETECT.COM"

[B]
Step 3 Edit menu.lst:[/B]

```
gksudo gedit /boot/grub/menu.lst
```

Replace your Windows item by

title XP
rootnoverify (hd0,4)
chainloader +1

So do NOT use "makeactive"

Save the file and  reboot. 

**If this did not work**

**Step  4  Fix the Windows boot sector**

Install and run "testdisk" via


```
sudo apt-get install testdisk

sudo testdisk /dev/sda
```

Press "enter" to "proceed"
Press "enter" to select "intel"
Use the "down arrow" and "enter" to select "advanced"
Use the down error to select the "XP" partition and then "enter" to select "boot"
Use the "right arrow" key and "enter" to select "Rebuild BS"
This might take a while. Once done just follow the instruction on the screen to save the new boot sector and quit testdisk.

 Reboot and hope for the best.

( You can deleted "Archive.tar.gz" at any time, but I would wait until you successfully booted into XP)
__________________

---

### Post by unutbu on 2008-06-20
> mkdir /windows
**sudo mount /dev/hda5 /Win** 
ls  /windows

meierfra., just a small thing -- to better help morrillt, perhaps edit your last post so the second command is "sudo mount /dev/hda5 /windows".

---

### Post by meierfra. on 2008-06-20
Thanks. (I had used /Win all the way, but when I realized that the OP  had previously mounted Windows at /windows I changed all "/Win" to "/windows.  Of course, I forgot one)

---

### Post by morrillt on 2008-06-20
Huh tried it and got to the starting up.... 

which i believe is part of the grub system as it does a similar text when i load ubuntu.

Then it hangs.

Will try your program, but just curious you say 
rootnoverify (hd0,4)u dont mean(hd0, 5) do you? maybe the first partition is a 0, anyway i am a newb.... will try the rest of the commands and c what happens

---

### Post by meierfra. on 2008-06-20
> maybe the first partition is a 0,

yes it is. Grubs start counting at 0.

---

### Post by morrillt on 2008-06-20
got it got it got it,, yea yea yea... only question i have is how the hell did my boot sector get changed? i guess when i was loading ubuntu it read all the partitions and when i put hte label /windows on that partition, it got messed.... ?

ANyway thanks so much

---

### Post by unutbu on 2008-06-20
My guess is that when you installed Ubuntu, the LiveCD installer also installed GRUB on the MBR of /dev/sda. (It overwrote Window's bootloader). GRUB uses /boot/grub/menu.lst to give you options to dual boot. Unfortunately, it got the location of your windows partition wrong -- instead of (hd0,0), it should have written (hd0,4). 

The LiveCD may have simply assumed Windows is on the (hd0,0) partition since for the majority of Windows users, Windows is installed on the first partition of the first hard drive.

PS. I don't think it has anything to do with putting the /windows label on the /dev/hda5 partition.

---

### Post by meierfra. on 2008-06-20
> got it got it got it,, yea yea yea... only question i have is how the hell did my boot sector get changed?

The boot sector  actually did not get changed. Let me explain what happened:

Windows always puts the boot files   on a primary partition. (This is just due to the fact how the Windows boot loader works).  In your case the boot information was on 5GB partition which you erased.  So you need to replace the boot files (Step 2).

Grub cannot apply "makeactive" to a logical  partition (any partition numbered 5 or higher). So you need to leave out "makeactive" (Step 3). (Makeactive puts a boot flag on a partition, But there actually is no reason for the Windows partition to have a boot flag)

The  boot sector of an NTFS  partition stores the number of sectors from the MBR  to the partition. A  logical partition comes with its own MBR, so this number is often 63:  the number of sector from the MBR of the  partition to the partition  But if you actually  want to boot Windows  from a logical partition, this numbers need to be the the number of sectors from the MBR of the hard drive to the partition. Step 4 took care of this problem.

> i guess when i was loading ubuntu it read all the partitions and when i put hte label /windows on that partition, it got messed.... ?
No, mounting Windows at /windows  does not do any harm.

---

### Post by meierfra. on 2008-06-20
> My guess is that when you installed Ubuntu, the LiveCD installer also installed GRUB on the MBR of /dev/sda. (It overwrote Window's bootloader).

This is slightly misleading.  The MBR only contains a very small part of Windows boot loader. The actually booting is done by the boot sector of the Windows boot  partition and  by the three boot files, which are are on the Windows boot partition (and by some other files on the Windows partition)

The MBR essentially only had one function:  Look for a primary partition with the boot flag and start running the code contained in the boot sector of that partition. 

The MBR only can only look at primary partitions. That is the reason why the Windows puts the boot information on a primary partition.

---

### Post by unutbu on 2008-06-20
meierfra., please tell me if I'm understanding this right:

Below, since a single hard disk can have many MBRs, I label them MBR(a), MBR(b), etc.

Before installing Ubuntu:
The BIOS would pass control to the MBR(a) located at the very beginning of the hard drive (the very first 512 bytes of hda). MBR(a) would pass control to the boot loader located in the 63 boot sectors immediately following the MBR. Those boot sectors contain the number of sectors from MBR(a) to hda5, which in this case is 10249470. (Since a sector = 512 bytes, and hda5 starts at the 638th cylinder, and 1 cylinder=8225280 bytes, hda5 begins at the 638*8225280/512=10249470th sector.) The boot loader reads boot.ini, NTDETECT.COM and NTLDR which were all located in the NTFS filesystem in the 5GB partition now occupied by hda6 and hda7. The boot loader plus those files boot Windows NT, creating the OS's filesystem using the files located in hda5.

After installing Ubuntu + after your fix:
When Windows is selected from the GRUB boot menu, GRUB stage 2 passes control to the MBR(b) located at the first 512 bytes of hda5. MBR(b) passes control to the boot loader residing on the 63 boot sectors following it (also on hda5). MBR(b) and the adjoining boot loader are what was created by Step 4. The boot sectors contain the number of sectors from MBR(b) to the hda5 partition, which now is 63. The boot loader in the boot sectors reads boot.ini, NTDETECT.COM and NTLDR (now part of the hda5 filesystem) and boots Windows NT.

---

### Post by Duck2006 on 2008-06-20
Some reading that may help.

[http://www.justlinux.com/forum/showthread.php?t=143973](http://www.justlinux.com/forum/showthread.php?t=143973)

---

### Post by meierfra. on 2008-06-20
> Before installing Ubuntu:
The BIOS would pass control to the MBR(a) located at the very beginning of the hard drive (the very first 512 bytes of hda)
Yes.
> MBR(a) would pass control to the boot loader located in the 63 boot sectors immediately following the MBR. 
False.  Those  63 sectors are not used.  MBR(a) passes control directly the the boot sector of the active partition,
> Those boot sectors contain the number of sectors from MBR(a) to hda5, which in this case is 10249470.

The MBR itself contains information about the beginning of each of the primary partitions. The first sector of extended partition is actually the MBR of the first logical partition. The MBR of each logical partition contains information about the location of the MBR of the next logcial partition.
> (Since a sector = 512 bytes, and hda5 starts at the 638th cylinder, and 1 cylinder=8225280 bytes, hda5 begins at the 638*8225280/512=10249470th sector.)
To avoid this calulations, you can use "sudo fdisk -lu". This will give all the start and end points in sectors.
> The boot loader reads boot.ini, NTDETECT.COM and NTLDR which were all located in the NTFS filesystem in the 5GB partition now occupied by hda6 and hda7. The boot loader plus those files boot Windows NT, creating the OS's filesystem using the files located in hda5.
Yes. To be more precise:  the boot sectors calls on NTLDR and NTLDR then calls on the other files.
> After installing Ubuntu + after your fix:
When Windows is selected from the GRUB boot menu, GRUB stage 2 passes control to the MBR(b) located at the first 512 bytes of hda5.
Not quite.  The first 512 bytes of hda5 are called  the boot sector of hda5.  Before each logical partition there are 63 sectors which don't belong to any partitions (the extended MBR of the logcial partitions)  The stage2 files pass control directly to the boot sector of hda5.
>  MBR(b) passes control to the boot loader residing on the 63 boot sectors following it (also on hda5). 

No, see last paragraph. MBR(b) is not really involved
> MBR(b) and those boot sectors are what was created by Step 4. The boot sectors contain the number of sectors from MBR(b) to the hda5 partition, which now is 63. 
No. MBR(b) was not changed at all. The boot sector already existed. Only one numbers in the boot sector was changed.  Before Step 4, it had stored the "number 63" in a certain place. Step 4 changed this number to "10249470" (So one could skip Step 4 and use "dd" to directly write this number to the boot sector)
>  The boot loader in the boot sectors reads boot.ini, NTDETECT.COM and NTLDR (now part of the hda5 filesystem) and boots Windows NT.
Yes.


Of  course there is a lot of information available on the Web. For example"

[http://www.goodells.net/multiboot/index.htm](http://www.goodells.net/multiboot/index.htm)

[http://www.geocities.com/thestarman3/asm/mbr/index.html](http://www.geocities.com/thestarman3/asm/mbr/index.html)
 
But none of theses article will make sense (at least to me) until you  get your  hands  dirty:  

Use "dd" to actually copy the MBR's and boot sectors to  files. 
 
For example before and after Step 4, copy the boot sector of the partition to a file. Then compare the two files.
(You have to use a Hex Editor, I like  emacs in "hexl-mode" and KHexEdit)

---

### Post by unutbu on 2008-06-21
Thank you very much for the information, meierfra.!

---

