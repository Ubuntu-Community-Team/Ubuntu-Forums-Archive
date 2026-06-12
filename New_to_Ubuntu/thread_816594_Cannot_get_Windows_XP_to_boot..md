---
title: "Cannot get Windows XP to boot."
date: 2008-06-02
forum: New to Ubuntu
---

### Post by b-rob on 2008-06-02
i have tried several things please help.....

**fdisk -l shows this:**

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6d702ecc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1        9728    78140128+   f  W95 Ext'd (LBA)
/dev/sda5            1276        9728    67898691    7  HPFS/NTFS
/dev/sda6               1         122      979870+  82  Linux swap / Solaris
/dev/sda7             123        1275     9261441   83  Linux

Partition table entries are not in disk order

**menu.lst contains this:**

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=72d898e0-d6a0-4fcb-bfc2-1fbdc094d4f6 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=72d898e0-d6a0-4fcb-bfc2-1fbdc094d4f6 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title 		Microsoft Windows XP
root		(hd0,4)
savedefault
makeactive
chainloader	+1

when i try to boot it gives error 12: invalid device requested.
why will this not work?

---

### Post by ChameleonDave on 2008-06-02
Was this working before and it failed, or are you trying to set it up?

Are you sure that that is the correct partition for Windows?

See also: [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by ph1 on 2008-06-02
Hmm, hard to say what's wrong, your menu.lst doesn't have any glaring errors.  Where I would check first for an error would be in the hd(0,4) section--do you have multiple hard disks?  Is it really on the partition labeled 4 on the disk labeled 0?  If you install gparted, you can have a nice gui to look at and work with your partitions, which might be helpful.  Post back if you find out anything else and I'll see if I can come up with any more (possibly useless D:) advice.

---

### Post by fmartinez on 2008-06-02
> **b-rob said:**
> i have tried several things please help.....

**fdisk -l shows this:**

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6d702ecc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1        9728    78140128+   f  W95 Ext'd (LBA)
**/dev/sda5**            1276        9728    67898691    7  HPFS/NTFS
/dev/sda6               1         122      979870+  82  Linux swap / Solaris
/dev/sda7             123        1275     9261441   83  Linux

Partition table entries are not in disk order

**menu.lst contains this:**

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=72d898e0-d6a0-4fcb-bfc2-1fbdc094d4f6 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=72d898e0-d6a0-4fcb-bfc2-1fbdc094d4f6 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title 		Microsoft Windows XP
root		**(hd0,4)**
savedefault
makeactive
chainloader	+1

when i try to boot it gives error 12: invalid device requested.
why will this not work?

look at what i bolded in the out put in fdisk and your menu.lst file. looks like the menu.lst wants to boot XP from partition 4 which doesnt exist. from the output of fdisk it looks like XP lives in partition 5. make the necessary changes and update grub. I dont know what the syntax is for grub, but always do 
$man grub
in a terminal. 
Hope this helps.

---

### Post by b-rob on 2008-06-02
this is all on one hard drive....i am setting it up, i had xp installed first had created a separate partition prior to installing xp with intentions of installing ubuntu on that partition. now that i have ubuntu installed i tried to add xp to grub and have not been able to get it to work

---

### Post by b-rob on 2008-06-02
is there a way to get rid of the grub bootloader and revert back to using the windows bootloader?

---

### Post by kansasnoob on 2008-06-02
You have a major mess!

Ubuntu is (hd0,6) and Win XP is (hd0,4). (NEITHER MAKE SENSE)

Where you have only two OS's that ain't right!

What I would do (and this is only my opinion) is boot the live CD and use Gparted to delete everything but the Win XP partition.

Then I'd reinstall Ubuntu using the Live CD by choosing "install" and "use the largest continuous free space". That will totally restore GRUB and should not cause any further harm to your Win partition.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by b-rob on 2008-06-02
> **kansasnoob said:**
> You have a major mess!

Ubuntu is (hd0,6) and Win XP is (hd0,4). (NEITHER MAKE SENSE)

Where you have only two OS's that ain't right!

What I would do (and this is only my opinion) is boot the live CD and use Gparted to delete everything but the Win XP partition.

Then I'd reinstall Ubuntu using the Live CD by choosing "install" and "use the largest continuous free space". That will totally restore GRUB and should not cause any further harm to your Win partition.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

so by choosing that install option it will not try to install on the windows partition since it is the largest partition?

---

### Post by kansasnoob on 2008-06-02
"is there a way to get rid of the grub bootloader and revert back to using the windows bootloader?"

Yes. (I'm assuming you just want to go back to Windows) But you should first use Gparted to get rid of everything but the win XP partition.

Then you could just boot your computer from a Windows XP Installation CD, start Recovery Console and run fixmbr command.

---

### Post by kansasnoob on 2008-06-02
"so by choosing that install option it will not try to install on the windows partition since it is the largest partition?"

You must have "free space"!

If you don't have free space the 8.04 installer won't even give you that option.

You need to use the Live CD and go to Gparted (partition editor) and delete all partitions but the Windows partition. XP should be easily identified by Gparted. It'll normally be an NTFS partition.

---

### Post by meierfra. on 2008-06-02
Deleting Ubuntu will NOT solve your problem.  Also  "fixmbr" and "fixboot" will NOT solve your problem. This is what happened:  Windows always stores its booting information on one of the first four partitions. Then you installed Ubuntu you must of deleted this partition.
So the booting information for XP is gone. Deleting Ubuntu or Grub will not bring it back.  The easiest way to solve your problem is to deleted everything. Then Install XP and after that Ubuntu.

But if you are up to a learning experience I can show you how to fix your current setup. This [link]("http://ubuntuforums.org/search.php?searchid=42372833") shows you what needs to be done, but if you like I can  write  up the instruction in more details.

---

### Post by Yuki_Nagato on 2008-06-02
I hear Windows is pretty greedy and needs to be installed on the (hd 0,0) primary partition to work with an easy chainloader + 1.  But that is merely my experience.

I believe you have to "map" the windows partition into thinking it is on (hd 0,0)

---

### Post by kansasnoob on 2008-06-02
"Deleting Ubuntu will NOT solve your problem."

True! But freeing up some space for a new Ubuntu install, and then reinstalling Ubuntu, certainly will recreate GRUB! New GRUB .......... new game!

They already said they've tried everything!

---

### Post by meierfra. on 2008-06-03
Sorry kansasnoob, your approach will not help. The OP's problem is NOT a Grub problem.  

To be able to boot,  XP needs the files "boot.ini", "ntldr" and "ntdetect.com". All these files have been on the partition the OP deleted. 
These files are available on the web (for example you can follow the link I provided).  Or  one can copy them from a different computer.  Or one can reinstall Windows.

But without these files it is impossible to boot XP.

---

### Post by kansasnoob on 2008-06-03
Meierfra,

So the windows file system is damaged?

I stand corrected if so. Is that indicated by the "error 12"?

---

### Post by meierfra. on 2008-06-03
>  Is that indicated by the "error 12"? 

Error 12 comes from "root (hd0,4), makeactive". Grub cannot make a logical partition active. You can avoid  Error 12, by just leaving out the "makeactive".  Actually that is one of the things one needs to do the fix the problem. 

Windows always puts the three files "boot.ini,ntldr, ntdetect.com" on a primary partition (that is, a partition numbered 1,2, 3 or 4) If you look at the output of "fdisk" you see that the only primary partition is sda2, but that is an extended partition (So it is just a container for other partition, it does not contain any files).  It follows that the partition holding those three files must have been deleted. (And since /dev/sda1 does not appear in "fdisk" it is also clear that some some partition have been deleted.)

**Although there is one other possible explanation: ** The partition sda5 used to be a primary partition, but got moved. In this case one might be able to solve the problem via "fixboot" from the Windows recovery partition  and removing "makeactive" from "menu.lst"



> So the windows file system is damaged?

I don't think so. In fact one should be able to mount it in Ubuntu  and look at the files


```
sudo mkdir XP
sudo mount -ntfs /dev/sda5 XP
ls XP
```

This should confirm that the three files are indeed missing.

---

### Post by kansasnoob on 2008-06-03
My apologies! There is a reason "noob" is in my moniker.

I've just gotten so used to the dual boot environment I tend to think my way will solve everything. Obviously if someone has hosed their Windows already they're in trouble.

Again, my apologies and many thanks! You were right and I was wrong.

---

### Post by meierfra. on 2008-06-03
> 've just gotten so used to the dual boot environment I tend to think my way will solve everything.

There is hardly ever a case where one needs to reinstall to solve a problem. For example I do not know a single grub problem which requires reinstalling ubuntu.

> Obviously if someone has hosed their Windows

Windows is just missing three files  and these files  are available on the web. I wouldn't call that "hosed"


And maybe b-rob did actually moved the windows partition from /dev/sda1 to /dev/sda5. Then  "fixboot" will solve the problem.

---

### Post by shakir on 2008-06-04
hey guys,

I've been using ubuntu for a few days now. I wanted to switch to windows xp as I have some important things to do. when i chose windows xp as my os for that moment, a blank screen appears as if it's gonna start. but after few minutes, nothing appears. so i had to manually restart my pc. tried again but still the same problem. how do i fix this?? should i reformat my pc again???pls help. Thanks

---

### Post by Duck2006 on 2008-06-04
> /dev/sda2 * 1 9728 78140128+ f W95 Ext'd (LBA)
/dev/sda5 1276 9728 67898691 7 HPFS/NTFS

Are you sure windoze is on sda5, and not sda2, because if it is then it will not boot "extended partition" it should be a "primary partition" for windoze.

---

