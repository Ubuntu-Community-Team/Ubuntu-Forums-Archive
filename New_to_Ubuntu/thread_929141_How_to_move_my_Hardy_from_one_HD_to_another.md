---
title: "How to move my Hardy from one HD to another"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by swarup on 2008-09-24
I just bought a new 750 GB internal HD. On my old 150 GB HD there is a Vista/Hardy dual boot. Using windows backup software, I made a mirror image of the old HD's Vista partition onto the new HD. And I left plenty of space empty for the Hardy partition. Now I want to create a mirror image of the old HD's Hardy, and put it onto the new HD. And I want the grub to also be setup as the same dual boot. 

If possible, I'd like to keep the same version of Hardy from the old HD, as it has all the current updates already on it. If I install a new version of Hardy and just bring over the home folder from the old HD's Hardy, then I'll have to download all the updates. 

What is the best way to do get this done?

---

### Post by caljohnsmith on 2008-09-24
You could use software like Clonezilla or even use the "dd" command to make a perfect clone of your Hardy installation over to your new drive, but there is really no reason to make it a perfect sector-by-sector cloned image; if you first create a partition on your new drive for your old Hardy install, and you can even make the partition bigger/smaller if you like as long as it is big enough for your current Hardy install, then you can just copy your entire Hardy file system over to the new partition with "cp -a". I've used this method so I know it works. But whether you copy the file system, or whether you use a cloning method, either way you will have to modify at least two files in your new Hardy partition to get it to work since the Hardy partition UUID will be different (and if you have a swap partition on your new drive, it will have a different UUID too):
[LIST=1]
[*]/boot/grub/menu.lst
[*]/etc/fstab
[/LIST]
If you want details of how to use the file system copy method, then first post:
```
sudo fdisk -l
```
And we can go from there. Or let me know if you want to do otherwise.

---

### Post by bodhi.zazen on 2008-09-24
I posted an overview of how to do this here :

[http://ubuntuforums.org/showthread.php?t=316237](http://ubuntuforums.org/showthread.php?t=316237)

---

### Post by swarup on 2008-09-24
> **caljohnsmith said:**
> If you want details of how to use the file system copy method, then first post:
```
sudo fdisk -l
```
And we can go from there.

This is the output for my old HD:

```
~$ sudo fdisk -l
[sudo] password: 

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2               6        1311    10485760    7  HPFS/NTFS
/dev/sda3   *        1311       18178   135481344    7  HPFS/NTFS
/dev/sda4           18179       19452    10233405    5  Extended
/dev/sda5           18179       19392     9751423+  83  Linux
/dev/sda6           19393       19452      481918+  82  Linux swap / Solaris

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0b78093d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          24      192748+  de  Dell Utility
/dev/sdb2              25         677     5245222+   7  HPFS/NTFS
/dev/sdb3   *         678       88395   704594835    7  HPFS/NTFS
/dev/sdb4           88396       91201    22539195    5  Extended
/dev/sdb5           89928       91141     9751423+  83  Linux
/dev/sdb6           91142       91201      481918+  82  Linux swap / Solaris
~$ 
```

And actually, I should add one piece of information. When I used the Windows-based Seagate software to clone the old HD contents onto the new HD, it actually did reproduce the contents of the Ubuntu and Swap partitions. So on the new HD, there is already now an extended partition containing and Ext3 partition with Hardy supposedly in it, and a Swap partition. But when I open Gparted and look at the contents of the new HD, then regarding the Ubuntu partition I get the message: "Unable to find mountpoint. Unable to read contents of this filesystem!" So because of this, I thought easiest thing might be to just delete what the entire extended partition which the Seagate software made, and start over using your guidance and instruction. But if you think that what the seagate software did may be fine. Then we could try and use what it made, instead. But we would have to fix this issue about not being able to find the mountpoint. --I'd be just as happy deleting what seagate made and starting over, if you think that's better.

Your "cp -a" system sounds fine to me. Please kindly give details.

I looked at bodhi.zazen's post, but it seemed rather lengthy and complex. So I think I'd like to follow your "cp -a" method.

---

### Post by caljohnsmith on 2008-09-24
OK, so when you did the Seagate clone of your 160 GB HDD to the 750 GB HDD, did you use some sort of "proportional copy" feature or something with your NTFS partitions sda2 and sda3 and also the Dell partition sda1? I'm just wondering because those partitions are about 5X the size on your new HDD compared to the old HDD. Or did you clone them over and then resize them? 

Let's see first if we can use the Ubuntu partition that Seagate cloned for you; how about booting into your old Ubuntu, and then trying to mount your new Ubuntu partition to see what errors it might give:
```
sudo mkdir /media/sdb5
sudo mount /dev/sdb5 /media/sdb5
```
If it gives some sort of file system error like gparted did, run a fsck on it:
```
sudo umount /dev/sdb5
sudo fsck -y /dev/sdb5
```
Let me know how it goes, and please post the output of all the above commands.

---

### Post by swarup on 2008-09-24
> **caljohnsmith said:**
> OK, so when you did the Seagate clone of your 160 GB HDD to the 750 GB HDD, did you use some sort of "proportional copy" feature or something with your NTFS partitions sda2 and sda3 and also the Dell partition sda1? I'm just wondering because those partitions are about 5X the size on your new HDD compared to the old HDD. Or did you clone them over and then resize them? 

When I did the clone procedure, there was an option for "manual" versus "automatic". I selected "manual", and that allowed me to set the size of each partition. I mostly increased my main NTFS partition to fill out the drive. I wanted to increase the size of the Linux partitions as well, but the Seagate software would not allow me to change their size. So I kept an extra 10 GB as free unallocated, next to the Extended Linux partition, so as to be able to increase its size myself after the clone software finished its job.

> **caljohnsmith said:**
> Let's see first if we can use the Ubuntu partition that Seagate cloned for you...

I am doing the HD work for a colleague on his computer, and will not have access to it again until tomorrow evening around 6 pm EST. I'll check it around that time, and post the results of your requests. Thanks very much for your interest and kind support. :)

---

### Post by swarup on 2008-09-25
> **caljohnsmith said:**
> Let's see first if we can use the Ubuntu partition that Seagate cloned for you; how about booting into your old Ubuntu, and then trying to mount your new Ubuntu partition to see what errors it might give:
```
sudo mkdir /media/sdb5
sudo mount /dev/sdb5 /media/sdb5
```

It did not give any error. Here is what happened:

```
:~$ sudo mkdir /media/sdb5
[sudo] password: 
:~$ sudo mount /dev/sdb5 /media/sdb5
:~$ 
```

Now when I open Nautilus, there is one partition mounted, called "sdb5", which cannot be unmounted. And it seems to contain all the Ubuntu files and folders in it. 

So does it sound like the Seagate software may have successfully made the Ubuntu clone? If so, then what do I need to do so it will boot up properly and so I can set up grub to work for the dual boot?

---

### Post by caljohnsmith on 2008-09-25
OK, that's great news; it looks like your Seagate software may have done just fine cloning over your Ubuntu partition.

While you are in Ubuntu, and have sdb5 mounted on /media/sdb5, please do the following:
```
sudo blkid
sudo cp /media/sdb5/etc/fstab /media/sdb5/etc/fstab.backup
gksudo gedit /media/sdb5/etc/fstab &
```
The last command will pull up your fstab file, and you will need to edit the line that looks similar to:
```
UUID=77677cb5-6e56-4936-a373-80c15de06bca [COLOR="Red"]/ ext3[/COLOR] nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
```
Don't worry if all the options are different then yours, just find the line that shows the mount point "/" like above, and then change the UUID to match the UUID for sdb5 that the blkid command gave. Also look for the line in fstab that has "swap":
```
UUID=e01cf0e2-3ae1-42f0-a07f-c5167cba8ae5 none [COLOR="Red"]swap[/COLOR] sw 0 0
```
And change its UUID to match sdb6 from the blkid command. Then save the fstab file. Next open your menu.lst:
```
gksudo gedit /media/sdb5/boot/grub/menu.lst
```
Find the Ubuntu entries, similar to:
```
title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=[COLOR="Red"]77677cb5-6e56-4936-a373-80c15de06bca[/COLOR] ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

```
And change the UUIDs in all the Ubuntu entries to be the UUID for sdb5 that blkid gave; then save the file. Next install Grub to the sdb drive MBR:
```
sudo grub
grub> root (hd1,4)
grub> setup (hd1)
grub> quit
```
That should be enough that you can now boot from your sdb drive, and you should be able to boot into Ubuntu OK. There are just a few small details left; but see if you can get this far, and if not, let me know.

---

### Post by swarup on 2008-09-26
I followed what you wrote above, and everything went quite smoothly. But actually, I didn't need to change anything in the fstab or menu.1st file, because all the UUID's listed in those files matched exactly the UUID listed for sba5 and sba6 for ext3 and swap respectively, in the terminal window, given by the blkid command. I hope it's ok that they were the same. I checked very carefully. No changes needed to be made.

Then I did what you said to do for grub, and that went smoothly too. Here was the output for the grub code:

```
grub> root (hd1,4)

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+16 p (hd1,4)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.

grub> 


```

> **caljohnsmith said:**
> That should be enough that you can now boot from your sdb drive, and you should be able to boot into Ubuntu OK. There are just a few small details left; but see if you can get this far, and if not, let me know.

OK. I'll try now switching the new HD to master and the old one to slave, and see if I can boot using it. Should I be able to boot now in both Unbuntu and Vista, or have we only set up the Ubuntu side so far? I noticed in the Menu.1st file that of course the Vista option is also listed there. I suppose that listing should work for Vista as well, right?

---

### Post by caljohnsmith on 2008-09-26
> **swarup said:**
> I followed what you wrote above, and everything went quite smoothly. But actually, I didn't need to change anything in the fstab or menu.1st file, because all the UUID's listed in those files matched exactly the UUID listed for sba5 and sba6 for ext3 and swap respectively, in the terminal window, given by the blkid command. I hope it's ok that they were the same. I checked very carefully. No changes needed to be made.
I think you might have mixed up sda5 with sdb5 when checking the UUIDs. Your new drive is sdb, correct? If that is the case, you will need to use the UUIDs for sdb5, not sda5 (and also sdb6 instead of sda6) when modifying those files in your sdb5 partition. :)

---

### Post by swarup on 2008-09-27
> **caljohnsmith said:**
> I think you might have mixed up sda5 with sdb5 when checking the UUIDs. Your new drive is sdb, correct? If that is the case, you will need to use the UUIDs for sdb5, not sda5 (and also sdb6 instead of sda6) when modifying those files in your sdb5 partition. :)

I see that I referred to them incorrectly above, writing "sba" instead of "sdb". But I am pretty certain that I didn't make any error in the actual operation when I carried it out. I executed the terminal window order as you gave it, which only output the UUID for sdb5 and sdb6. I copied and pasted the orders as you gave them above, and because of that I don't think there was any question of mixing up sdb with sda. As, information for sda was not output in the terminal window. Were you expecting the UUID to necessarily be different from the one for the old HD version?

I haven't been back to that computer yet but will exchange master for slave this evening on it, and see if it boots up.

---

### Post by swarup on 2008-09-29
> **caljohnsmith said:**
> I think you might have mixed up sda5 with sdb5 when checking the UUIDs. Your new drive is sdb, correct? If that is the case, you will need to use the UUIDs for sdb5, not sda5 (and also sdb6 instead of sda6) when modifying those files in your sdb5 partition. :)

Here below is the proof that the UUID for Ubuntu and Swap in both sda and sdb is the same. Here below is the output for blkid. Please compare sda5 and sda6, with sdb5 and sdb6. The UUID's are the same:

[CODE :~$ sudo blkid
[sudo] password: 
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D7-0605" TYPE="vfat" 
/dev/sda2: UUID="62B01238B01212E1" LABEL="D DRIVE" TYPE="ntfs" 
/dev/sda3: UUID="E6C4163AC4160D85" LABEL="C Drive" TYPE="ntfs" 
/dev/sda5: UUID="084b393c-3b8e-43a0-ae60-6bc65b35e808" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sda6: TYPE="swap" UUID="96931e52-1008-428e-896d-0067517ec7f4" 
/dev/sdb1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D7-0605" TYPE="vfat" 
/dev/sdb2: UUID="62B01238B01212E1" LABEL="D DRIVE" TYPE="ntfs" 
/dev/sdb3: UUID="E6C4163AC4160D85" LABEL="C Drive" TYPE="ntfs" 
/dev/sdb5: UUID="084b393c-3b8e-43a0-ae60-6bc65b35e808" TYPE="ext3" 
/dev/sdb6: TYPE="swap" UUID="96931e52-1008-428e-896d-0067517ec7f4" 
:~$ 
[/CODE]

I tried booting to the new HD. It won't boot. If I remove the old HD, the computer won't boot even thought the new HD is in the boot sequence. And if I put the old HD back alongside the new one, then the computer will only boot to the old one.

---

### Post by caljohnsmith on 2008-09-29
Yes, my brain was obviously 404, because of course your UUIDs would be the same since you cloned the partitions; my mistake. #-o 

So when you say the computer won't boot your new 750 GB HDD, what exactly happens on start up when you only have the new HDD connected? Any errors?

---

### Post by swarup on 2008-09-29
> **caljohnsmith said:**
> So when you say the computer won't boot your new 750 GB HDD, what exactly happens on start up when you only have the new HDD connected? Any errors?

When only the new HD is connected, then it just keeps giving over and over a message that there is no bootable medium present in the computer.

---

### Post by caljohnsmith on 2008-09-29
> **swarup said:**
> When only the new HD is connected, then it just keeps giving over and over a message that there is no bootable medium present in the computer.
Have you gone into your BIOS and selected the new HDD as first to boot? You also might possibly have to change other BIOS settings related to your new HDD, such as whether it uses "auto", "LBA", "RAID", "CHS", etc. If that doesn't work, then boot your Live CD (or you could boot into your old HDD if you want to connect it again), and do the following:
```
sudo dd if=/dev/[COLOR="Red"]<drive>[/COLOR] bs=512 count=20 | gzip -c > ~/Desktop/MBR.bin.gz
```
But replace <drive> with sda/sdb or whichever is the new HDD. That command will create a "MBR.bin.gz" file on your desktop; please attach that file to your next message so I can look at it.

---

### Post by swarup on 2008-09-29
> **caljohnsmith said:**
> Have you gone into your BIOS and selected the new HDD as first to boot?

I wasn't certain how to move it up to first in the boot sequence. Right now it is listed in the boot sequence, albeit as #6 in the order of where the computer looks. But the only other currently bootable option is the other HDD, which is listed as #3 in the boot sequence, and that I have deselected. So it should go right to #6. Which I think it did, but could not boot.

> **caljohnsmith said:**
>  You also might possibly have to change other BIOS settings related to your new HDD, such as whether it uses "auto", "LBA", "RAID", "CHS", etc.

Both my HDD's are listed as non-RAID, yet as "controlled by the RAID bios". As both HD's are the same, so it doesn't seem I'll have to change anything there. And we already know that the HD is recognized fine by the computer, since when booted to the old HD, the new HD is fully visible with all its files.

> **caljohnsmith said:**
> If that doesn't work... create a "MBR.bin.gz" file on your desktop; please attach that file to your next message so I can look at it.

That I shall do right now and post here, in five minutes.

---

### Post by swarup on 2008-09-29
Sorry for the delay. For some reason, I couldn't attach the file in the other computer. Here now attached, is the file you requested.

---

### Post by caljohnsmith on 2008-09-29
So is there no way to actually change your BIOS boot sequence other than de-selecting the other drives so that it should be the first to boot? All the BIOSes that I've dealt with allow some way of changing the boot order of drives. I think that may be the key here.

Just as a test, I've slightly modified the MBR that you posted, so let's see if the modification will help at all. Download the attached "MBR2.bin.gz" file to your desktop, and then do:
```
cd ~/Desktop
gunzip MBR2.bin.gz
sudo dd if=MBR2.bin of=/dev/<drive>
```
Make sure <drive> is your new HDD. Reboot, and let me know if anything changes.

---

### Post by swarup on 2008-09-29
> **caljohnsmith said:**
> So is there no way to actually change your BIOS boot sequence other than de-selecting the other drives so that it should be the first to boot? All the BIOSes that I've dealt with allow some way of changing the boot order of drives. I think that may be the key here.

I found out how to change the boot order, and made the new HD the first to boot. It didn't make any difference.

> **caljohnsmith said:**
> Just as a test, I've slightly modified the MBR that you posted, so let's see if the modification will help at all... 
I followed your direction, and it went smoothly. But didn't make any difference. Still boots to the old HD. (That is, sda is still the old HD, and sdb is still the new HD. Because the material on the two HD's is completely identical, the only way for me to tell which it has booted to, is to open gparted in ubuntu and is if sda is the small 150 GB (old) HD, or the big 750 GB (new) HD.)

I can't understand why it isn't working?!

Perhaps I'll just post the menu.1st file for the sdb Ubuntu (i.e. the Ubuntu on the new HD). It looks fine to me, but perhaps you may see something which I missed.

```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=084b393c-3b8e-43a0-ae60-6bc65b35e808 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=084b393c-3b8e-43a0-ae60-6bc65b35e808 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=084b393c-3b8e-43a0-ae60-6bc65b35e808 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=084b393c-3b8e-43a0-ae60-6bc65b35e808 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04.1, kernel 2.6.24-17-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=084b393c-3b8e-43a0-ae60-6bc65b35e808 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=084b393c-3b8e-43a0-ae60-6bc65b35e808 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=084b393c-3b8e-43a0-ae60-6bc65b35e808 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=084b393c-3b8e-43a0-ae60-6bc65b35e808 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Dell Utility Partition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1
```

---

### Post by caljohnsmith on 2008-09-29
OK, if you detach the old HDD, is it still the same behavior, i.e. computer complains there is no bootable drive? 
[QUOTE=swarup]Both my HDD's are listed as non-RAID, yet as "controlled by the RAID bios". As both HD's are the same, so it doesn't seem I'll have to change anything there. And we already know that the HD is recognized fine by the computer, since when booted to the old HD, the new HD is fully visible with all its files.[/QUOTE]
Yes I agree, your new drive is fully accessible when you boot your old drive, but the fact the computer complains there is no bootable drive when you try and boot the new HDD (instead of giving at least some sort of Grub error) makes me think that a BIOS issue is still highly likely. Can you change your new HDD's BIOS settings to see if it makes any difference? You can make a note beforehand of what the settings are so you can revert back to them. Your new HDD's MBR looks like it should boot just fine, so I think the BIOS HDD settings are the most likely culprit. If that doesn't work, we could temporarily put another boot loader in your MBR just to see if it makes any difference.

---

### Post by swarup on 2008-09-30
> **caljohnsmith said:**
> OK, if you detach the old HDD, is it still the same behavior, i.e. computer complains there is no bootable drive?

I'll try again this morning and let you know. 

> **caljohnsmith said:**
> Yes I agree, your new drive is fully accessible when you boot your old drive, but the fact the computer complains there is no bootable drive when you try and boot the new HDD (instead of giving at least some sort of Grub error) makes me think that a BIOS issue is still highly likely. Can you change your new HDD's BIOS settings to see if it makes any difference?

I'll be glad to try changing the BIOS settings. Please tell me what sort of changes you had in mind, so I can get some idea of what to look for. What category in the BIOS Setup would it likely come under, and what are the parameters you want me to change? I have looked there over the past few days, and didn't see much that could be changed. "RAID" can be globally turned on and off, that is about as much as I noticed. But if you point me in the right direction, I may be able to find something more.

---

### Post by caljohnsmith on 2008-09-30
> **swarup said:**
> 
I'll be glad to try changing the BIOS settings. Please tell me what sort of changes you had in mind, so I can get some idea of what to look for. What category in the BIOS Setup would it likely come under, and what are the parameters you want me to change? I have looked there over the past few days, and didn't see much that could be changed. "RAID" can be globally turned on and off, that is about as much as I noticed. But if you point me in the right direction, I may be able to find something more.
I wish I could just tell you what to change your BIOS settings to in order to make you HDD bootable, but unfortunately BIOSes can be so different about what options they offer related to HDD setup that I don't think I can give specific advice. For instance, I've actually heard of people solving their HDD booting problems by turning on RAID when they clearly don't have a RAID setup, so sometimes the answer is far from obvious; therefore, I would try changing any parameters in BIOS you can find that are related to your HDDs. Just make sure that you write down the value of the BIOS setting before you change it, so you can return to your original settings. :)

---

### Post by swarup on 2008-09-30
> **caljohnsmith said:**
> OK, if you detach the old HDD, is it still the same behavior, i.e. computer complains there is no bootable drive?
Guess what? It worked!!! I just detached the old HD, and started up the new one alone. It did complain that it could not find a HD on Port 0 (the port of the old HD), but then it went right to the GRUB and booted right up. It boots fine into Ubuntu. And it gets to the profile login of Vista but then for some reason, can't login to the profile. But that is some sort of Vista issue. I'll have to ask a windows person about it. The boot procedure for both Ubuntu and Vista is working fine. I don't know what the change was or why it is working now, but it is working.

So I guess there is no need to play with the BIOS.

The last step, which I'll do now, is to reconnect the old HD and see if it will still boot to the new HD, which is 1st in the boot sequence. 

And also, you had mentioned a few days ago that there are still a few details left to attend to. What are those?

======================

ADD: I just reconnected the old HD. So both HD's are connected. Even though the new HD is 1st in the boot sequence, the computer is booting preferentially to the old HD. I can't get the computer to boot to the new HD when the old HD is also connected. I'll go back into the BIOS now to see what else I may be able to find about this. But aside from setting the boot sequence--which is already done--I don't know what else to do.

---

### Post by bumanie on 2008-09-30
This has been a long post covering many days, what OS is meant to be on the original hard drive and what OS is on the new hard drive?

---

### Post by swarup on 2008-09-30
> **bumanie said:**
> This has been a long post covering many days, what OS is meant to be on the original hard drive and what OS is on the new hard drive?

Hi there--
I had a dual boot internal HDD 150GB with Vista/Hardy. I then purchased another internal HDD 750 GB, and wanted to shift the entire operation from the old HDD to the new one so as to have more space on my primary HDD. The new one is a Seagate, and it came with cloning software which I used to clone the old one over to the new one, manually adjusting the partition sizes so as to take up the space on the new HD. caljohnsmith has been extremely kind and helpful in guiding me to get the Grub set up properly. And the new HDD is now working fine, so long as the old one is disconnected. But if I connect both HDD's, then even though the new one is designated to boot primarily as I set up the boot sequence, even then, the old one boots up if I have both connected. Any ideas?

---

### Post by caljohnsmith on 2008-09-30
That's great the new HDD is finally booting. One trick you can do to know for sure which Ubuntu on which HDD you've booted into is to use:
```
mount | grep " / "
```
That will tell you which Ubuntu partition you've booted into, e.g. sdb5, and of course you can double-check that "sdb" is truly your new HDD with:
```
sudo fdisk -l
```
About the "other details" you should take care of, since the UUIDs are the same for Ubuntu on both drives, there actually aren't any more changes you need to make that I'm aware of. :)

And about Vista, do you have a Vista Recovery CD? If not you can download one [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"). I would recommend booting that up and simply doing a "Vista Repair" to see if it corrects your problems about booting into Vista. If not, I have some commands you can run from the command line in the Vista Recovery CD that might be enough to get it working again.

---

### Post by swarup on 2008-09-30
Before we get any further, I just wanted to thank you for all your help. You really have stuck with it and taken me along all the way. :)

I do have the question still as to how to get the new HDD to be the primary (boot) HDD, when both HDD's are connected. I can always tell by going into gparted, which ubuntu has booted. Because the one that boots is labeled sda, and the other HDD (which has not booted) is labeled as sdb (isn't that true?). The sda HDD is always the one that shows up when you first open gparted. In order to see the non-boot HDD (sdb) in gparted, you have to select it. Otherwise the booted HDD (sda) is the one that shows up. And sda is always the 150GB HDD. 

I don't have a Vista recovery CD. It is a Dell E520 computer, and it came with a special separate recovery partition made for reinstalling Vista if there should come to develop any problem with the OS. Perhaps that partition also has a recovery function. I will look and see. Otherwise I'll download from the site you gave. Thanks.

---

### Post by meierfra. on 2008-09-30
> Because the one that boots is labeled sda, and the other HDD (which has not booted) is labeled as sdb (isn't that true?)

That is not true. Changing the boot order in the bios usually does not effect  the sdX label.


> I do have the question still as to how to get the new HDD to be the primary (boot) HDD, when both HDD's are connected.

I suggest to change the UUID's of your new Ubuntu partition:

```
sudo tune2fs -U random /dev/sdb5
```

This will asssign a random UUID to /dev/sdb5.  
Of course, you  have to change the UUID's in menu.lst and  /etc/fstab  accordingly.

---

### Post by swarup on 2008-10-01
> **meierfra. said:**
> That is not true. Changing the boot order in the bios usually does not effect  the sdX label.

Oh, I did not know that. But when I open gparted from within Ubuntu, won't it default to showing the currently booted HDD? (And if you want to view a HDD other than the one which has been booted to, then you have to select it from the drop-down menu. Right?)

> **meierfra. said:**
>  I suggest to change the UUID's of your new Ubuntu partition:

```
sudo tune2fs -U random /dev/sdb5
```

This will asssign a random UUID to /dev/sdb5.  
Of course, you  have to change the UUID's in menu.lst and  /etc/fstab  accordingly.

Wow, that makes total sense! You mean the reason it won't boot to the new HDD when the old HDD is present, is because the Ubuntu partitions on both HDD's have the same UUID? 

I'll try switching the UUID in the morning, and see if it solves the problem. Thanks! :)

---

### Post by meierfra. on 2008-10-02
> You mean the reason it won't boot to the new HDD when the old HDD is present, is because the Ubuntu partitions on both HDD's have the same UUID?

Yes, I think so.  Both menu.lst and  fstab identify the partitions by their UUID and will just load the first partition which has a matching UUID.


You could also change all "UUID=..." in menu.lst and fstab  by "/dev/sdb5". But I think changing the UUID of sdb5  is the better solution.

---

